---
name: youtrack
description: "Use when working with YouTrack - issues, knowledge base articles, projects, users, tags, or work items. Triggers: YouTrack, ticket, issue, task, article, KB, knowledge base, PROJ-XXX IDs."
slash: true
---

# YouTrack MCP

YouTrack (>=2024.3) exposes a built-in MCP server at `{baseUrl}/mcp`. Invoke tools via JSON-RPC — no npm install, no SDK, no CLI scripts.

## Quick Start

### 1. Configure credentials

This skill reads credentials from environment variables:

| Variable | Required | Description |
|----------|----------|-------------|
| `YOUTRACK_URL` | Yes | YouTrack instance URL, e.g. `http://192.168.0.29:8080` |
| `YOUTRACK_TOKEN` | Yes | Permanent token from YouTrack |

**If either variable is not set**, ask the user for the values. Generate a permanent token in YouTrack: **Settings > Account > Authentication > New token**.

### 2. Invoke the MCP endpoint

Every tool call follows the same pattern. Replace `{baseUrl}` with `$YOUTRACK_URL` and `{token}` with `$YOUTRACK_TOKEN`:

```
POST {baseUrl}/mcp    ← $YOUTRACK_URL + "/mcp"
Authorization: Bearer {token}   ← $YOUTRACK_TOKEN
Content-Type: application/json
Accept: application/json, text/event-stream

{"jsonrpc":"2.0","id":1,"method":"tools/call",
 "params":{"name":"<tool>","arguments":{<params>}}}
```

### 3. Test connectivity

Use `get_current_user` (no arguments) to verify credentials work:

## Tool Discovery

This skill uses **progressive loading** to keep context minimal:

1. **`tools/index.md`** — one-line index of all tools grouped by category. Read this first to find the tool you need.
2. **`tools/<category>/<tool>.md`** — each tool file contains a JSON-RPC call template with all parameters. Read only the tool you need, copy its template, fill in the arguments.

**Do NOT read all tool files at once. Read the index, pick the relevant tool, read only that file.**

Example:
```
1. Read tools/index.md → find "search_issues" under Issues
2. Read tools/issues/search_issues.md → copy the JSON-RPC template
3. Fill in your query, POST to /mcp
```

## Knowledge Base Rules

1. **Read freely**: `search_articles` and `get_article` have no side effects — use anytime.
2. **Create freely**: `create_article` to add new knowledge.
3. **Update carefully**: `update_article` with `append:true` to add content safely.
4. **Never delete**: There is no delete article tool. If content is wrong, update it — don't remove.
5. **Project context**: Always specify the correct `project` when creating articles. Use `find_projects` first if unsure.

## Troubleshooting

| Error | Fix |
|-------|-----|
| Tool call fails | Check token is valid and baseUrl is correct |
| 401 Unauthorized | Regenerate permanent token in YouTrack |
| 403 Forbidden | Token lacks permissions — grant appropriate role |
| "method not found" | Ensure YouTrack >=2024.3 (built-in MCP) |
| No articles | Project may not have Knowledge Base enabled |
