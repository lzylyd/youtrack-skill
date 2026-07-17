<!-- AGENT_READABLE_START -->
name: youtrack-skill
description: YouTrack MCP integration skill — register the built-in MCP server to access issues, knowledge base articles, projects, users, tags, and work items via 22 MCP tools. Zero install, zero dependencies.
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

An agent skill for YouTrack's **built-in MCP server** (>= 2024.3). Register the MCP endpoint once, then your agent has access to 22 tools — issues, knowledge base articles, projects, users, tags, work items. No CLI, no npm install, zero dependencies.

## Install

Copy this directory to your agent's skill location:

```bash
# OpenCode / WorkBuddy
cp -r youtrack-skill ~/.agents/skills/youtrack

# Claude Code
cp -r youtrack-skill ~/.claude/skills/youtrack
```

## Configure

Add the MCP server to your agent's config (`opencode.json` or equivalent):

```json
{
  "mcpServers": {
    "youtrack": {
      "url": "http://your-youtrack.example.com:8080/mcp",
      "headers": {
        "Authorization": "Bearer perm-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
      }
    }
  }
}
```

Generate a permanent token in YouTrack: **Settings > Account > Authentication > New token**.

## Verify

Call `get_current_user` — should return your login and email. Call `find_projects` with `query: ""` to list all projects.

## Tools (22 total)

| Category | Tools |
|----------|-------|
| Issues | `search_issues`, `get_issue`, `create_issue`, `create_draft_issue`, `update_issue`, `change_issue_assignee`, `add_issue_comment`, `get_issue_comments`, `get_issue_fields_schema`, `manage_issue_tags`, `link_issues`, `log_work` |
| Knowledge Base | `search_articles`, `get_article`, `create_article`, `update_article` |
| Projects | `find_projects`, `get_project` |
| Users & Groups | `get_current_user`, `find_user`, `find_user_groups`, `get_user_group_members` |
| Other | `get_saved_issue_searches` |

Full tool reference and query language guide: `SKILL.md`.

## License

MIT
