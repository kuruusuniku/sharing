---
layout: default
title: クローズドLLMモデル概説
---

# 8. クローズドLLMモデル概説

モデルが多すぎて選べない、という声をよく聞きます。私も最初はそうでした。でも実際に使い比べてみると、各社の哲学の違いが見えてきて面白い。この章では、主要なクローズドモデルの特徴と使い分けを整理します。

ソースコードや重みが非公開の、企業が提供するLLMサービスです。高性能だが、各社のAPI・アプリ経由でのみ利用できます。

## 主要モデル一覧

### Anthropic — Claude

公式サイト: [anthropic.com](https://www.anthropic.com/) / [claude.ai](https://claude.ai/)

| モデル | 特徴 |
|--------|------|
| **Opus 4.7** | 最高性能。複雑な推論・長文コード生成・設計に最適 |
| **Sonnet 4.6** | 速度と性能のバランス。日常の開発作業に最適 |
| **Haiku 4.5** | 高速・低コスト。軽量タスク・分類・要約向け |

**強み：** コーディング能力、長文コンテキスト（100K〜1Mトークン）、指示追従性の高さ、Claude Code によるエージェント的活用

**利用方法：** Claude Desktop（チャット）、Claude Code（CLI）、API

### OpenAI — GPT

公式サイト: [openai.com](https://openai.com/) / [chatgpt.com](https://chatgpt.com/)

| モデル | 特徴 |
|--------|------|
| **GPT-5.5** | 最新フラッグシップ。推論力・マルチモーダル |
| **GPT-4o** | マルチモーダル（テキスト・画像・音声）の統合モデル |
| **o3 / o4-mini** | 推論特化（Reasoningモデル）。数学・論理・コード |

**強み：** マルチモーダル統合、ChatGPTの巨大なエコシステム、DALL-E による画像生成、プラグイン・GPTs

**利用方法：** ChatGPT（チャット）、Codex（CLI）、API

### Google — Gemini

公式サイト: [deepmind.google](https://deepmind.google/technologies/gemini/) / [gemini.google.com](https://gemini.google.com/)

| モデル | 特徴 |
|--------|------|
| **Gemini 3.1 Pro** | 最新フラッグシップ。複雑な多段階エージェントワークフローに最適化 |
| **Gemini 3.1 Flash** | 高速・低コスト。日常利用向け |
| **Gemini 3.1 Flash Live** | リアルタイム音声対話に対応 |

**強み：** 超長文コンテキスト、Google 検索との統合、Android/Google Workspace連携、Computer Use対応、ロボティクスモデル

**現状：** 仕事で本格的に使うにはまだ閾値を超えていない印象。日常的な調べものや要約には十分使える。今後の進化に期待。

### xAI — Grok

公式サイト: [x.ai](https://x.ai/) / [grok.com](https://grok.com/)

| モデル | 特徴 |
|--------|------|
| **Grok 4.3 Beta** | 200万トークンのコンテキスト（西側クローズドモデル最大）、16エージェント並列処理、ネイティブ動画理解 |
| **Grok 5**（予定） | 2026年Q2にベータ公開見込み |

**強み：** 超大規模コンテキスト、リアルタイム情報（X プラットフォーム統合）、マルチエージェント並列処理

**現状：** Grok 4.3 は SuperGrok Heavy（月額$300）限定のEarly Access。高額だが、コンテキスト長と並列処理能力は突出。エンジニアリング用途での実用性は今後に期待。

## 比較まとめ

| 観点 | Claude | GPT | Gemini | Grok |
|------|--------|-----|--------|------|
| **コーディング** | ◎ | ◎ | ○ | △ |
| **推論・分析** | ◎ | ◎ | ○ | ○ |
| **マルチモーダル** | ○ | ◎ | ◎ | ○ |
| **日本語** | ◎ | ◎ | ○ | △ |
| **エージェント活用** | ◎ | ○ | △ | △ |
| **コンテキスト長** | ◎ | ○ | ◎ | ○ |
| **エコシステム** | ○ | ◎ | ○ | △ |

## どう使い分けるか

- **仕事の開発・設計** → Claude（Claude Code / Opus）
- **日常の相談・調べもの** → ChatGPT or Gemini で十分
- **画像生成が必要** → ChatGPT（DALL-E）
- **リアルタイム情報** → Grok or Gemini
- **コスト重視の大量処理** → 各社の軽量モデル（Haiku, Flash, 4o-mini）

---

[← 目次に戻る](./) | [前: OpenClaw](07-openclaw) | [次: オープンLLM →](09-open-models)
