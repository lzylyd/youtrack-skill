<!-- AGENT_READABLE_START -->
name: youtrack-skill
description: YouTrack MCP skill — progressive-discovery access to 23 tools (issues, articles, projects, users) via JSON-RPC calls. Zero install, loads only needed tool templates. Triggers: YouTrack, ticket, issue, article, KB.
platforms: OpenCode, WorkBuddy, Claude Code, Cursor
requires: YouTrack >= 2024.3
entry: MCP server at {baseUrl}/mcp
<!-- AGENT_READABLE_END -->

# YouTrack MCP Skill

[![OpenCode](https://img.shields.io/badge/OpenCode-ready-7c3aed)](https://github.com/lzylyd/opencode)
[![DeepSeek](https://img.shields.io/badge/DeepSeek_V4-powered-4d6bfe)](https://deepseek.com)
[![YouTrack](https://img.shields.io/badge/YouTrack-%E2%89%A52024.3-fa602d?logo=youtrack)](https://www.jetbrains.com/youtrack/)
[![MCP](https://img.shields.io/badge/MCP-standard-5a67d8)](https://modelcontextprotocol.io)
[![中文](https://img.shields.io/badge/文档-中文-red)](README.zh-CN.md)

> 🇨🇳 [中文文档](README.zh-CN.md)

An agent skill for YouTrack's **built-in MCP server** (>= 2024.3). Set two environment variables, then invoke any of 23 tools via JSON-RPC — the agent loads only the tool template it needs from `tools/`. No CLI, no npm install, no MCP server registration, zero context overhead.

## Install

```bash
# OpenCode / WorkBuddy
cp -r youtrack-skill ~/.agents/skills/youtrack
```

## Configure

Set two environment variables:

```bash
export YOUTRACK_URL=http://youtrack.example.com:8080
export YOUTRACK_TOKEN=perm-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

Generate the token in YouTrack: **Settings > Account > Authentication > New token**.

## Usage

The agent reads `tools/index.md` → finds the tool → reads the JSON-RPC template → POSTs to `$YOUTRACK_URL/mcp`. Only the needed tool file is loaded into context.

## Tools (23 total)

| Category | Count | Full list |
|----------|-------|-----------|
| Issues | 13 | `tools/issues/` — search, get, create, update, comment, tag, link, log work |
| Knowledge Base | 4 | `tools/articles/` — search, get, create, update articles |
| Projects | 2 | `tools/projects/` — find, get project details |
| Users & Groups | 4 | `tools/users/` — current user, find user, groups, members |

Full JSON-RPC templates and query language guide: `SKILL.md`. Progressive discovery: `tools/index.md` → `tools/<cat>/<tool>.md`.

## License

MIT
