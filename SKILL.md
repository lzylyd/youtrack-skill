---
name: youtrack
description: "Use when working with YouTrack - issues, knowledge base articles, projects, users, tags, or work items. Triggers: YouTrack, ticket, issue, task, article, KB, knowledge base, sprint, board, PROJ-XXX IDs, task tracking."
---

# YouTrack MCP

YouTrack (≥ 2024.3) has a built-in MCP server at `{baseUrl}/mcp`. Register it as an MCP server in your agent, then use the tools below. No CLI scripts required — zero install, zero dependencies.

## Quick Start

### 1. Register the MCP server

In your agent's MCP configuration (`opencode.json` or equivalent):

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

Generate a permanent token in YouTrack: **Settings → Account → Authentication → New token**.

### 2. Verify

```
Call `get_current_user` — should return your login and email.
Call `find_projects` with `query: ""` — should list all projects.
```

### 3. Use

Any mention of YouTrack terms (issue, ticket, article, KB, sprint) triggers this skill. The agent invokes MCP tools directly — no CLI needed.

## Tool Reference (22 tools)

### Issues (12 tools)

| Tool | Purpose | Required Params | Key Optional Params |
|------|---------|----------------|---------------------|
| `search_issues` | Search issues with query language | `query` | `customFieldsToReturn`, `offset`, `limit` (max 20) |
| `get_issue` | Full issue details + recent comments | `issueId` | `recentCommentsCount` (default 5) |
| `create_issue` | Create issue in a project | `project`, `summary` | `description`, `customFields`, `parentIssue`, `permittedUsers`, `permittedGroups` |
| `create_draft_issue` | Create draft (current-user only) | `project`, `summary` | — |
| `update_issue` | Update summary, description, custom fields, subscription, or vote | `issueId` | `summary`, `description`, `customFields`, `subscription`, `vote` |
| `change_issue_assignee` | Set or unset assignee | `issueId` | `assigneeLogin` (null to unassign) |
| `add_issue_comment` | Add Markdown comment | `issueId`, `text` | `permittedUsers`, `permittedGroups` |
| `get_issue_comments` | Paginated comment list | `issueId` | `offset`, `limit` (max 10) |
| `get_issue_fields_schema` | JSON schema for custom fields in a project | `projectKey` | — |
| `manage_issue_tags` | Add or remove tag | `issueId`, `tag`, `operation` | — |
| `link_issues` | Link two issues (subtask, depends on, etc.) | `targetIssueId`, `linkType`, `issueToLinkId` | — |
| `log_work` | Log spent time on an issue | `issueId`, `durationMinutes` | `description`, `date`, `workType`, `workItemAttributes` |

**Issue search query language quick reference:**

```
Free text:      'login button bug', 'summary: log*'
Project:        'project: {My Project}', 'project: PRJ'
Assignee:       'for: me', 'for: admin'
State/Fields:   'State: Open', 'Priority: Critical', 'Type: Bug'
Date:           'created: today', 'updated: {This week}'
Combined:       'project: PRJ for: me State: Open'
Keywords:       '#Unresolved', '#Resolved'
Has/No:         'has: attachments', 'has: -comments'
```

### Articles / Knowledge Base (4 tools)

| Tool | Purpose | Required Params | Key Optional Params |
|------|---------|----------------|---------------------|
| `search_articles` | Search KB articles | `query` | `offset`, `limit` (max 20) |
| `get_article` | Full article + sub-articles | `articleId` | `linesOffset` (default 0), `linesCount` (default 500) |
| `create_article` | Create article in a project | `project`, `summary` | `content` (Markdown), `parentArticle`, `permittedUsers`, `permittedGroups` |
| `update_article` | Update summary, content, or parent | `articleId` | `summary`, `content`, `append` (default false), `parentArticleId` |

> ⚠️ **No `delete_article` tool exists.** Do NOT attempt to delete articles. Archive or mark as obsolete via update if needed.

**Article search query reference:**

```
Free text:      'deployment', '"getting started"'
Project:        'project: HELP', 'project: {Mobile App}'
Author/Updater: 'author: me', 'updated by: admin'
Date:           'created: {This month}', 'updated: today'
Tag:            'tag: faq', 'tag: {internal docs}'
Content flags:  'has: attachments', 'has: comments', 'has: content'
Negation:       'tag: -outdated', 'project: -{Archived}'
```

### Projects (2 tools)

| Tool | Purpose | Required Params |
|------|---------|----------------|
| `find_projects` | Search projects by name | `query` (empty string = all) |
| `get_project` | Full project details | `projectKey` |

### Users & Groups (4 tools)

| Tool | Purpose | Required Params |
|------|---------|----------------|
| `get_current_user` | Authenticated user info | — |
| `find_user` | Find user by login/email | `loginOrEmail` |
| `find_user_groups` | Search groups/teams | `nameContains` |
| `get_user_group_members` | List members of a group | `group` |

### Other (1 tool)

| Tool | Purpose |
|------|---------|
| `get_saved_issue_searches` | Your favorited saved searches |

## Common Workflows

### View my open tasks
```
search_issues(query: "for: me State: Open") → list
get_issue(issueId: "PROJ-42") → full details
```

### Create a task
```
find_projects(query: "my project") → get project key
get_issue_fields_schema(projectKey: "PROJ") → see required fields
create_issue(project: "PROJ", summary: "Fix login", customFields: {"Type": "Bug", "Priority": "Major"})
```

### Close a task
```
get_issue(issueId: "PROJ-42") → see current State
update_issue(issueId: "PROJ-42", customFields: {"State": "Fixed"})
add_issue_comment(issueId: "PROJ-42", text: "Fixed in commit abc123.")
```

### Find and read KB articles
```
search_articles(query: "project: HELP deployment") → list
get_article(articleId: "HELP-A-1") → full content
```

### Create KB article
```
create_article(project: "HELP", summary: "How to deploy", content: "# Deployment Guide\n\n1. ...")
```

### Update KB article (append safely)
```
update_article(articleId: "HELP-A-1", content: "\n\n## New section\n...", append: true)
```

### Assign a task
```
find_user(loginOrEmail: "john") → get login
change_issue_assignee(issueId: "PROJ-42", assigneeLogin: "john.smith")
```

### Track time on a task
```
log_work(issueId: "PROJ-42", durationMinutes: 120, description: "Investigated root cause", date: "2025-06-15", workType: "Development")
```

## Knowledge Base Rules

1. **Read freely**: `search_articles` and `get_article` have no side effects — use anytime.
2. **Create freely**: `create_article` to add new knowledge.
3. **Update carefully**: `update_article` with `append: true` to add content safely.
4. **Never delete**: There is no delete tool. If content is wrong, update it — don't remove.
5. **Project context**: Always specify the correct `project` when creating articles. Use `find_projects` first if unsure.

## Troubleshooting

| Error | Fix |
|-------|-----|
| MCP tools unavailable | Check the MCP server is registered in agent config and the token is valid |
| `auth_failed` (401) | Token is expired or invalid — regenerate in YouTrack |
| `forbidden` (403) | Token lacks permissions — grant Project Admin or appropriate role |
| Tool not found | Ensure YouTrack version ≥ 2024.3 (built-in MCP) |
| No articles returned | The project may not have the Knowledge Base feature enabled — check project settings |
