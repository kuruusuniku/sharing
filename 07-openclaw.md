---
layout: default
title: OpenClaw — 個人用AIアシスタント
---

# 7. OpenClaw — 個人用AIアシスタント

![OpenClaw 概要](assets/images/ch07-openclaw.svg)

ここまでの章では、コーディングや業務タスクにフォーカスしてきました。この章では視点を変えて、**日常生活全体をAIでアシストする**ツールを紹介します。

私も使っていますが、正直まだ使いこなせていません。一緒に育てていきましょう。

## OpenClaw とは

[OpenClaw](https://openclaw.ai/) は、オープンソースの個人用AIアシスタントです。自分のPC上で動作し、複数のチャットアプリ・サービスと連携して、日常のあらゆるタスクを自動化できます。

**一言でいうと：** 「自分専用の Siri / Google Assistant を、好きなLLMで、好きなサービスと繋げて作れる」ツールです。

- GitHub: [github.com/openclaw/openclaw](https://github.com/openclaw/openclaw)
- ドキュメント: [docs.openclaw.ai](https://docs.openclaw.ai)
- コミュニティ: [Discord](https://discord.gg/clawd)
- ライセンス: MIT

## 他のツールとの違い

| | ChatGPT / Claude Desktop | OpenClaw |
|--|--------------------------|----------|
| **LLM** | 固定（各社のモデル） | 自由に選べる（Claude, GPT, ローカルLLM等） |
| **データ** | クラウドに送信 | ローカルに保存 |
| **連携先** | 限定的 | 自由に拡張可能 |
| **カスタマイズ** | プロンプトのみ | ワークフロー全体を自由に設計 |
| **料金** | サブスク | LLMのAPI費用のみ |

## 主な機能

| 機能 | 説明 |
|------|------|
| **マルチチャット連携** | Telegram, Discord, Slack, LINE 等を一元管理 |
| **ワークフロー自動化** | 「毎朝ニュースを要約して送る」等のルーティン |
| **ファイル処理** | PDF要約、画像分析、音声文字起こし |
| **記憶** | 会話の文脈を長期記憶として保持 |
| **ツール連携** | カレンダー、メール、Notion 等への操作 |

## セットアップ

```bash
# Docker で起動（推奨）
docker compose up -d

# 設定
# http://localhost:3000 にアクセスして初期設定
```

必要なもの：
- Docker
- LLMのAPIキー（Claude, GPT 等）
- 連携したいサービスのAPIキーやBot Token

## 活用アイデア

- **朝の情報収集自動化** — ニュース、天気、今日の予定を毎朝まとめて送信
- **メッセージの自動振り分け** — 複数チャットの通知を重要度で整理
- **議事録の自動作成** — 会議音声を文字起こし→要約→関係者に共有
- **学習サポート** — 読書メモの整理、復習リマインダー

## 注意点

- まだ発展途上のプロジェクト（バグあり）
- セットアップにある程度の技術知識が必要
- LLMのAPI費用は自己負担

---

[← 目次に戻る](./) | [前: Skills](06-skills) | [次: クローズドLLM →](08-closed-models)
