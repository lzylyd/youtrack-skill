<!-- AGENT_READABLE_START -->
name: youtrack-skill
description: YouTrack MCP skill — 渐进式发现 23 个工具（issues、知识库、项目、用户），通过 JSON-RPC 裸调。零安装，按需加载工具模板。
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

基于 YouTrack **内置 MCP 服务器**（≥ 2024.3）的 Agent skill。设置两个环境变量后，Agent 通过 JSON-RPC 调用 23 个工具——只加载需要的工具模板，零常驻上下文开销。

## 安装

```bash
cp -r youtrack-skill ~/.agents/skills/youtrack
```

## 配置

设置两个环境变量：

```bash
export YOUTRACK_URL=http://youtrack.example.com:8080
export YOUTRACK_TOKEN=perm-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

生成 Token：YouTrack → Settings → Account → Authentication → New token。

## 使用

Agent 读取 `tools/index.md` → 找到工具 → 读取 JSON-RPC 模板 → POST 到 `$YOUTRACK_URL/mcp`。只加载需要的工具文件。

## 工具一览（23 个）

| 分类 | 数量 | 详情 |
|------|------|------|
| Issues | 13 | `tools/issues/` — 搜索、查看、创建、更新、评论、标签、链接、工时 |
| 知识库 | 4 | `tools/articles/` — 搜索、查看、创建、更新文章 |
| 项目 | 2 | `tools/projects/` — 搜索项目、项目详情 |
| 用户/组 | 4 | `tools/users/` — 当前用户、查找用户、群组、成员 |

渐进式发现：`tools/index.md` → `tools/<分类>/<工具>.md`。完整模板见 `SKILL.md`。

## License

MIT
