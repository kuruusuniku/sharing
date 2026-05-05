---
layout: default
title: Claude Code 以外の選択肢
---

# 12. Claude Code 以外の選択肢

Claude Code が最高だと言い切りたいところだけど、正直に言います。人によっては他のツールの方が合うかもしれない。GUIが好きな人、VS Codeを離れたくない人、コストを抑えたい人——それぞれに最適解は違います。

この資料では Claude Code を中心に紹介してきましたが、AIコーディングツールは群雄割拠の時代です。自分のワークスタイルに合ったツールを選ぶことが大事なので、主要な選択肢を概観します。

## AI搭載IDE（エディタ一体型）

### Cursor

公式サイト: [cursor.com](https://www.cursor.com/)

VS Code ベースのAI搭載IDE。最も勢いのあるツールの一つで、200万ユーザーを突破しています。

| 特徴 | 説明 |
|------|------|
| **タブ補完** | コード補完が非常に高速。Supermaven 買収により強化 |
| **Composer** | 複数ファイルにまたがる編集をAIが一括で行う |
| **チャットUI** | エディタ内でAIと対話しながらコーディング |
| **モデル選択** | Claude, GPT 等の複数モデルに対応 |

| プラン | 月額 |
|--------|------|
| Hobby | 無料（制限あり） |
| Pro | $20 |
| Pro+ | $60 |
| Ultra | $200 |

**Claude Code との違い：** Cursor は「エディタの中にAIがいる」体験。GUIで直感的に使える。Claude Code は「ターミナルからAIが全てを操作する」体験。自動化・スクリプト連携に強い。

### Windsurf（旧 Codeium）

公式サイト: [windsurf.com](https://windsurf.com/)

Cognition AI（Devin 開発元）が買収したAI搭載IDE。エージェント駆動のフローに強みがあります。

| 特徴 | 説明 |
|------|------|
| **Cascade** | 自動エージェントがコードベースを理解して自律的に作業 |
| **SWE-1.5** | 独自モデル。高速推論 |
| **Codemaps** | コードベースの構造を可視化 |

| プラン | 月額 |
|--------|------|
| Free | 無料（制限あり） |
| Pro | $15 |
| Ultra | $60 |

**Claude Code との違い：** Windsurf はエージェント的な自律動作と Cursor に近いGUI体験を両立。価格も比較的安い。

### Antigravity（Google）

公式サイト: [antigravity.google](https://antigravity.google/)

Google が開発したAI搭載IDE。複数エージェントの並列実行とブラウザ統合が特徴。

| 特徴 | 説明 |
|------|------|
| **複数エージェント並列** | 複数のAIエージェントが同時に作業 |
| **ブラウザ統合** | Webアプリの動作確認をIDE内で完結 |
| **Claude Opus 対応** | Google 製だが Anthropic のモデルも使える |

| プラン | 月額 |
|--------|------|
| Starter | $20 |
| Pro | $249 |

**Claude Code との違い：** IDE内で複数エージェントが並列動作する点が独自。大規模リファクタリングに向いている。

## VS Code 拡張（既存エディタに追加）

### GitHub Copilot

公式サイト: [github.com/features/copilot](https://github.com/features/copilot)

最も普及しているAIコーディングアシスタント。VS Code, JetBrains, Neovim 等に対応。

| 特徴 | 説明 |
|------|------|
| **インライン補完** | コードを書いている途中でリアルタイム提案 |
| **Agent Mode** | エージェント的にタスクを自律実行 |
| **GitHub 統合** | PR レビュー、Issue 連携がシームレス |

| プラン | 月額 |
|--------|------|
| Free | 無料（制限あり） |
| Pro | $10 |
| Pro+ | $39 |

**Claude Code との違い：** Copilot は「補完」がメイン。書いているコードの続きを提案する。Claude Code は「指示ベース」で、タスク全体を任せられる。

### Cline（オープンソース）

公式サイト: [cline.bot](https://cline.bot/)

VS Code 拡張のオープンソースAIエージェント。450万インストール。

| 特徴 | 説明 |
|------|------|
| **透明なエージェント** | 全ての操作を人間がレビューしてから実行 |
| **複数LLM対応** | Claude, GPT, ローカルLLM 等を自由に選択 |
| **無料** | ツール自体は無料。LLMのAPI費用のみ |

**Claude Code との違い：** Cline は VS Code 内で動くので GUI 操作。Claude Code はターミナル。Cline は API キーを自分で用意する（従量課金）ので、使い方次第でコストを抑えられる。

## CLI ツール

### OpenAI Codex

公式サイト: [openai.com](https://openai.com/)

OpenAI が提供する Claude Code の対抗馬。GPT モデルをバックエンドに使うCLIツール。

| 特徴 | 説明 |
|------|------|
| **GPT ベース** | GPT-5.5, o3 等の最新モデルを利用 |
| **CLI 体験** | Claude Code と同様のターミナルベース |

**Claude Code との違い：** バックエンドのモデルが違う。現時点では Claude Code の方がコーディングタスクでの評価が高い。

### Gemini CLI

Google が提供する無料のCLIツール。1日1000リクエストまで無料で使えます。

**Claude Code との違い：** 無料枠が大きいのが魅力。性能はまだ Claude Code に及ばない。

## 比較まとめ

| ツール | 種類 | 月額 | 強み |
|--------|------|------|------|
| **Claude Code** | CLI | $100（Max） | エージェント能力、コード品質、自動化 |
| **Cursor** | IDE | $20〜 | GUI体験、タブ補完、Composer |
| **Windsurf** | IDE | $15〜 | エージェント自律、コスパ |
| **Antigravity** | IDE | $20〜 | 複数エージェント並列、Google統合 |
| **Copilot** | 拡張 | $10〜 | 補完速度、GitHub統合、普及率 |
| **Cline** | 拡張 | 無料+API | オープンソース、透明性、柔軟性 |
| **Codex** | CLI | — | GPTモデル |
| **Gemini CLI** | CLI | 無料 | コストゼロ |

## どう選ぶか

- **ターミナル派・自動化重視** → Claude Code
- **GUI でサクサク書きたい** → Cursor or Windsurf
- **既存の VS Code を離れたくない** → Copilot or Cline
- **コストを抑えたい** → Cline（API従量課金）or Gemini CLI（無料）
- **Google エコシステム** → Antigravity

**大事なのは「どのツールが正解か」ではなく「自分の作業スタイルに合うか」です。** 複数ツールを併用するのも全然アリ。例えば、日常のコーディングは Cursor、大きなタスクの自動化は Claude Code、というスタイルも有効です。

---

[← 目次に戻る](./) | [前: API経由でのLLM利用](11-api-usage) | [次: LLMを支える仕組み →](13-llm-internals)
