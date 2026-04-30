---
layout: default
title: API経由でのLLM利用
---

# 11. API経由でのLLM利用

ChatGPT や Claude Desktop はチャットUIで使いますが、**API経由で使う**ことで、自分のツールやワークフローにLLMを組み込めます。

## 主要APIプロバイダー

### 直接API — モデル提供元から直接利用

| プロバイダー | 主なモデル | 特徴 |
|-------------|-----------|------|
| **OpenAI API** | GPT-5.5, GPT-4o, o3 | 最も広く使われている。豊富なエコシステム |
| **Anthropic API** | Opus, Sonnet, Haiku | 高品質なコード生成。バッチAPI対応 |
| **Google AI** | Gemini Pro, Flash | 長文コンテキスト。Google Cloud 統合 |

### アグリゲーター — 複数プロバイダーをまとめて利用

| プロバイダー | 特徴 |
|-------------|------|
| **OpenRouter** | 多数のモデルを統一APIで利用可能。モデルの比較・切り替えが容易。従量課金 |
| **Groq** | 超高速推論。オープンモデル（Llama, Mistral等）を高速で実行。無料枠あり |
| **OpenCodeGo** | OpenAI互換APIで複数モデルにアクセス |

**アグリゲーターの利点：**
- 1つのAPIキーで複数のモデルを使える
- モデルの切り替えがエンドポイントの変更だけで済む
- コスト比較が容易

## OpenAI互換API という共通規格

LLMのAPIには事実上の標準があります。それが **OpenAI互換API**（OpenAI-compatible API）です。

```
POST /v1/chat/completions
{
  "model": "モデル名",
  "messages": [
    {"role": "user", "content": "こんにちは"}
  ]
}
```

この形式は OpenAI が最初に定めたものですが、今では多くのプロバイダー・ツールがこの形式に対応しています。

### なぜ重要なのか

**OpenAI 互換API に対応しているツールなら、バックエンドを自由に差し替えられます。**

```
ツール（LM Studio, OpenCode, 自作アプリ等）
    ↕ OpenAI互換API
┌──────────┐ ┌──────────┐ ┌──────────┐
│ OpenAI   │ │OpenRouter│ │ LM Studio│
│ (クラウド) │ │ (クラウド) │ │ (ローカル) │
└──────────┘ └──────────┘ └──────────┘
```

つまり：
- **開発中はローカルLLM**（LM Studio）でコストゼロ
- **本番ではクラウドAPI**（OpenAI / Anthropic）で高品質
- **エンドポイントURLを変えるだけ**で切り替え可能

### 対応しているサービス・ツール

| サービス/ツール | OpenAI互換API |
|---------------|:---:|
| OpenAI | ○（本家） |
| OpenRouter | ○ |
| Groq | ○ |
| LM Studio | ○（ローカルサーバー） |
| Ollama | ○ |
| vLLM | ○ |
| Azure OpenAI | ○（一部差異あり） |

## 料金体系の基本

APIは**トークン単位の従量課金**が基本です。

### トークンとは

テキストを処理する最小単位。日本語は英語より多くのトークンを消費します。

- 英語: 1単語 ≈ 1〜2トークン
- 日本語: 1文字 ≈ 1〜3トークン
- 目安: 日本語1000文字 ≈ 1500〜2500トークン

### 主要モデルの料金比較（入力/出力 per 1Mトークン）

| モデル | 入力 | 出力 | 備考 |
|--------|------|------|------|
| Claude Sonnet | $3 | $15 | 日常の開発に最適 |
| Claude Opus | $5 | $25 | 最高性能。以前より大幅値下げ |
| GPT-4o | $2.5 | $10 | バランス型 |
| GPT-4o-mini | $0.15 | $0.6 | 大量処理向け |
| Gemini Flash | $0.075 | $0.3 | 最安クラス |

**コスト最適化のポイント：**
- 軽いタスクには軽量モデル（Haiku, Flash, 4o-mini）を使う
- 重要な判断だけ高性能モデル（Opus, GPT-5.5）を使う
- ローカルLLMを併用すればAPIコストゼロのタスクを増やせる

## 実際のAPI呼び出し例

### Python（OpenAI SDK）

```python
from openai import OpenAI

# OpenAIの場合
client = OpenAI(api_key="sk-xxx")

# OpenRouterの場合（エンドポイントを変えるだけ）
# client = OpenAI(
#     api_key="sk-or-xxx",
#     base_url="https://openrouter.ai/api/v1"
# )

# LM Studioローカルの場合
# client = OpenAI(
#     api_key="dummy",
#     base_url="http://localhost:1234/v1"
# )

response = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "user", "content": "Pythonでフィボナッチ数列を実装して"}
    ]
)

print(response.choices[0].message.content)
```

**注目ポイント：** `base_url` を変えるだけで、クラウド↔ローカル↔別プロバイダーを切り替えられます。コードの変更は最小限。

### Python（Anthropic SDK）

Anthropic のモデルを使う場合は、専用の SDK もあります。

```python
from anthropic import Anthropic

client = Anthropic(api_key="sk-ant-xxx")

message = client.messages.create(
    model="claude-sonnet-4-6",
    max_tokens=1024,
    messages=[
        {"role": "user", "content": "Pythonでフィボナッチ数列を実装して"}
    ]
)

print(message.content[0].text)
```

**ストリーミング（リアルタイム出力）：**

```python
with client.messages.stream(
    model="claude-sonnet-4-6",
    max_tokens=1024,
    messages=[{"role": "user", "content": "Hello"}]
) as stream:
    for text in stream.text_stream:
        print(text, end="", flush=True)
```

**プロンプトキャッシング（コスト削減）：**

長いシステムプロンプトやドキュメントを繰り返し使う場合、キャッシュすることでコストを最大90%削減できます。

```python
message = client.messages.create(
    model="claude-sonnet-4-6",
    max_tokens=1024,
    system=[{
        "type": "text",
        "text": "あなたは○○の専門家です。以下のドキュメントを参照して回答してください...(長文)",
        "cache_control": {"type": "ephemeral"}
    }],
    messages=[{"role": "user", "content": "質問"}]
)
```

### curl

```bash
curl https://api.openai.com/v1/chat/completions \
  -H "Authorization: Bearer sk-xxx" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gpt-4o",
    "messages": [{"role": "user", "content": "Hello"}]
  }'
```

## API活用のユースケース

| ユースケース | おすすめ |
|-------------|---------|
| プロトタイプ開発 | OpenRouter（モデル切り替えが容易） |
| 大量バッチ処理 | Anthropic Batch API / GPT-4o-mini |
| リアルタイム応答 | Groq（超低レイテンシ） |
| コスト最小化 | ローカルLLM + LM Studio |
| 最高品質が必要 | 直接API（Opus / GPT-5.5） |

## APIキーのセキュリティ

APIキーは**パスワードと同等**です。漏洩すると第三者に課金される危険があります。

### やるべきこと

```bash
# 環境変数で管理する（コードに直書きしない）
export ANTHROPIC_API_KEY="sk-ant-xxx"
export OPENAI_API_KEY="sk-xxx"
```

```python
import os
from anthropic import Anthropic

# 環境変数から読み込む
client = Anthropic(api_key=os.environ["ANTHROPIC_API_KEY"])
```

### やってはいけないこと

```python
# NG: コードにAPIキーを直書き
client = Anthropic(api_key="sk-ant-api03-xxxxx")

# NG: .mcp.json にトークンを直書きしてgit commit
```

### チェックリスト

- `.env` ファイルは `.gitignore` に追加する
- APIキーはダッシュボードで定期的にローテーションする
- 使用量アラートを設定して異常な課金を検知する
- 不要になったキーは即座に無効化する
- MCPの設定ファイル（`.mcp.json`）をgitにコミットしない

---

[← 目次に戻る](./) | [前: 用途特化モデル](10-specialized-models) | [次: Claude Code以外の選択肢 →](12-alternatives)
