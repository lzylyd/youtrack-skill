<!-- AGENT_READABLE_START -->
name: youtrack-skill
description: YouTrack MCP 集成 skill — 注册内置 MCP 服务器后可通过 22 个 MCP 工具操作 issues、知识库文章、项目、用户、标签、工时。零安装，零依赖。
platforms: OpenCode, WorkBuddy, Claude Code, Cursor
requires: YouTrack ≥ 2024.3
entry: MCP server at {baseUrl}/mcp
<!-- AGENT_READABLE_END -->

# YouTrack MCP Skill

[![OpenCode](https://img.shields.io/badge/OpenCode-ready-7c3aed)](https://github.com/lzylyd/opencode)
[![DeepSeek](https://img.shields.io/badge/DeepSeek_V4-powered-4d6bfe)](https://deepseek.com)
[![YouTrack](https://img.shields.io/badge/YouTrack-≥2024.3-fa602d?logo=youtrack)](https://www.jetbrains.com/youtrack/)
[![MCP](https://img.shields.io/badge/MCP-standard-5a67d8)](https://modelcontextprotocol.io)
[![English](https://img.shields.io/badge/docs-English-blue)](README.md)

> 🇺🇸 [English docs](README.md)

基于 YouTrack **内置 MCP 服务器**（≥ 2024.3）的 Agent skill。注册 MCP endpoint 后，Agent 即可通过 22 个 MCP 工具操作 issues、知识库文章、项目、用户、标签、工时。无需 CLI，无需 npm install，零依赖。

## 安装

将本目录复制到 Agent 的 skill 路径：

```bash
# OpenCode / WorkBuddy
cp -r youtrack-skill ~/.agents/skills/youtrack

# Claude Code
cp -r youtrack-skill ~/.claude/skills/youtrack
```

## 配置

在 Agent 的 MCP 配置中注册服务器：

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

生成永久 Token：YouTrack → Settings → Account → Authentication → New token。

## 验证

调用 `get_current_user` 应返回当前用户信息。调用 `find_projects(query: "")` 应列出所有项目。

## 工具一览（22 个）

| 分类 | 工具 |
|------|------|
| Issues | `search_issues`、`get_issue`、`create_issue`、`create_draft_issue`、`update_issue`、`change_issue_assignee`、`add_issue_comment`、`get_issue_comments`、`get_issue_fields_schema`、`manage_issue_tags`、`link_issues`、`log_work` |
| 知识库 | `search_articles`、`get_article`、`create_article`、`update_article` |
| 项目 | `find_projects`、`get_project` |
| 用户/组 | `get_current_user`、`find_user`、`find_user_groups`、`get_user_group_members` |
| 其他 | `get_saved_issue_searches` |

完整工具参考和查询语法指南见 `SKILL.md`。

## License

MIT
