---
layout: default
title: MCP サーバーの活用
---

# 3. MCP サーバーの活用

![MCP サーバー構成](assets/images/ch03-mcp.svg)

## MCP（Model Context Protocol）とは

MCP は Anthropic が策定したオープンプロトコルで、LLM に外部ツールやデータソースへのアクセスを提供します。「LLM版のUSBポート」のようなもので、様々なサービスをプラグインとして接続できます。

```
Claude Code / Claude Desktop
    ↕ MCP プロトコル
┌─────────┐ ┌─────────┐ ┌─────────┐
│  JIRA   │ │ GitHub  │ │  Slack  │
│ Server  │ │ Server  │ │ Server  │
└─────────┘ └─────────┘ └─────────┘
```

## 設定方法

### Claude Code の場合

プロジェクトルートに `.mcp.json` を作成するか、`claude mcp add` コマンドで追加します。

```bash
# MCP サーバーを追加
claude mcp add server-name -- npx @some/mcp-server

# 設定ファイルで管理する場合
cat .mcp.json
```

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "ghp_xxxxx"
      }
    }
  }
}
```

### Claude Desktop の場合

設定画面 → Developer → MCP Servers から追加できます。設定ファイルは以下にあります：

- macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
- Windows: `%APPDATA%\Claude\claude_desktop_config.json`

## タスク管理への応用

### JIRA 連携

MCP サーバーを通じて、Claude から直接 JIRA のチケットを操作できます。

**できること：**
- チケットの作成・更新・検索
- ステータス変更（Todo → In Progress → Done）
- コメント追加
- スプリント情報の取得

**使い方の例：**
```
> 今週のスプリントのチケット一覧を見せて
> このバグのチケットを作成して、優先度Highで
> PROJ-123 のステータスを In Progress に変更して
```

### GitHub Issues 連携

GitHub の MCP サーバーを使えば、Issue の管理も Claude から直接行えます。

**できること：**
- Issue の作成・編集・クローズ
- ラベルの付与
- PR の作成・レビュー確認
- リポジトリの検索

**使い方の例：**
```
> このバグの Issue を作成して
> 未解決の Issue を一覧表示して
> PR #42 のレビューコメントを確認して
```

## その他の便利な MCP サーバー

| MCP サーバー | 用途 |
|-------------|------|
| **Slack** | チャンネル閲覧・メッセージ送信 |
| **Google Calendar** | 予定の確認・作成 |
| **Filesystem** | ローカルファイルの読み書き |
| **PostgreSQL** | データベースへの直接クエリ |
| **Brave Search** | Web検索 |

## MCP サーバーの探し方

- [MCP Server Registry](https://github.com/modelcontextprotocol/servers) — 公式リポジトリ
- npm で `@modelcontextprotocol/` や `mcp-server-` で検索

---

[← 目次に戻る](./) | [前: AI エージェントパターン](02-agent-patterns) | [次: オーケストレーションツール →](04-custom-orchestration)
