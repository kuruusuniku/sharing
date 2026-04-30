---
layout: default
title: 用語集
---

# 用語集

この資料で使われる主要な用語をまとめています。

---

### A

**API（Application Programming Interface）**
ソフトウェア同士が通信するための仕様。LLMのAPIを使うと、プログラムからAIモデルを呼び出せる。→ [11章](11-api-usage)

**Attention（アテンション）**
Transformer の中核メカニズム。入力テキストのどの部分に「注目」すべきかを計算する仕組み。

### C

**CLI（Command Line Interface）**
ターミナル（コマンドライン）から操作するツール。Claude Code は CLI ツール。

**CLAUDE.md**
Claude Code がプロジェクト開始時に自動で読み込む設定ファイル。コーディング規約やプロジェクト情報を記載する。→ [1章](01-claude-code)

**コンテキストウィンドウ**
LLM が一度に処理できるテキストの最大量。トークン数で測る。会話が長くなると性能が低下する原因。→ [5章](05-claude-code-best-practices)

### D

**Dense（デンス）モデル**
全パラメータを毎回の推論で使う従来型のモデル。MoEの対義語。→ [9章](09-open-models)

### E

**Embedding（埋め込み）**
テキストをベクトル（数値の列）に変換すること。類似度検索や RAG の基盤技術。→ [10章](10-specialized-models)

### F

**Fine-tuning（ファインチューニング）**
既存のモデルを特定のタスクやデータに合わせて追加学習させること。

### G

**GGUF**
ローカルLLM実行に最適化されたモデルファイル形式。LM Studio や Ollama で使える。→ [9章](09-open-models)

### H

**Hallucination（ハルシネーション）**
LLM がもっともらしいが事実と異なる情報を生成する現象。「幻覚」とも訳される。

**Hooks（フック）**
Claude Code のワークフロー中の特定タイミングで自動実行されるスクリプト。CLAUDE.md の指示と違い、確実に実行される。

### L

**LLM（Large Language Model）**
大規模言語モデル。大量のテキストデータで学習した AI モデル。Claude, GPT, Gemini 等。

### M

**MCP（Model Context Protocol）**
Anthropic が策定したオープンプロトコル。LLM に外部ツールやデータソースへのアクセスを提供する。「LLM版のUSBポート」。→ [3章](03-mcp-servers)

**MoE（Mixture of Experts）**
推論時にモデルの一部のパラメータ（Expert）だけを活性化するアーキテクチャ。総パラメータ数が大きくても計算コストを抑えられる。→ [9章](09-open-models)

### O

**OpenAI互換API**
OpenAI が定めた API の形式（`/v1/chat/completions`）。多くのプロバイダーやツールがこの形式に対応しており、バックエンドを自由に差し替えられる。→ [11章](11-api-usage)

### P

**Prompt（プロンプト）**
LLM に与える入力テキスト。指示、質問、コンテキスト情報などを含む。

**Prompt Caching（プロンプトキャッシング）**
長いプロンプトをキャッシュして再利用する機能。繰り返し同じシステムプロンプトを使う場合にコストを最大90%削減できる。→ [11章](11-api-usage)

### Q

**量子化（Quantization）**
モデルの精度を少し落としてファイルサイズを圧縮する技術。Q4_K_M が品質と圧縮のバランスが良い。→ [9章](09-open-models)

### R

**RAG（Retrieval-Augmented Generation）**
検索拡張生成。外部のドキュメントを検索してLLMに渡すことで、回答の正確性を向上させる手法。→ [14章](14-rag)

**RLHF（Reinforcement Learning from Human Feedback）**
人間のフィードバックによる強化学習。LLM を人間の好みに合わせて調整する学習手法。

### S

**Skill（スキル）**
Claude Code の再利用可能なワークフロー定義。SKILL.md ファイルで作成し、必要なときだけ読み込まれる。→ [6章](06-skills)

**Streaming（ストリーミング）**
LLM の出力をトークン単位でリアルタイムに受信する方式。応答全体の生成を待たずに表示を開始できる。

### T

**Token（トークン）**
LLM がテキストを処理する最小単位。英語は1単語≈1〜2トークン、日本語は1文字≈1〜3トークン。API の料金はトークン数で決まる。

**Transformer**
現代のLLMの基盤アーキテクチャ。Attention メカニズムにより、テキストの長距離の関係を効率的に学習できる。2017年の論文 "Attention Is All You Need" で提案された。

---

[← 目次に戻る](./)
