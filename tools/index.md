# Tool Index

One-line index of all YouTrack MCP tools. Read this first, then read only the tool file you need.

## Issues (13)

| Tool | Description | File |
|------|-------------|------|
| `search_issues` | Search issues with query language | [→](issues/search_issues.md) |
| `get_issue` | Full issue details + recent comments | [→](issues/get_issue.md) |
| `create_issue` | Create issue in a project | [→](issues/create_issue.md) |
| `create_draft_issue` | Create draft visible only to you | [→](issues/create_draft_issue.md) |
| `update_issue` | Update summary, description, custom fields | [→](issues/update_issue.md) |
| `change_issue_assignee` | Set or unset assignee | [→](issues/change_issue_assignee.md) |
| `add_issue_comment` | Add Markdown comment to issue | [→](issues/add_issue_comment.md) |
| `get_issue_comments` | Paginated issue comment list | [→](issues/get_issue_comments.md) |
| `get_issue_fields_schema` | Custom field schema for a project | [→](issues/get_issue_fields_schema.md) |
| `manage_issue_tags` | Add or remove tag on issue | [→](issues/manage_issue_tags.md) |
| `link_issues` | Link two issues (subtask, depends on) | [→](issues/link_issues.md) |
| `log_work` | Log spent time on an issue | [→](issues/log_work.md) |
| `get_saved_issue_searches` | Your favorite saved searches | [→](issues/get_saved_issue_searches.md) |

## Articles / Knowledge Base (4)

| Tool | Description | File |
|------|-------------|------|
| `search_articles` | Search knowledge base articles | [→](articles/search_articles.md) |
| `get_article` | Full article + sub-articles | [→](articles/get_article.md) |
| `create_article` | Create article in a project | [→](articles/create_article.md) |
| `update_article` | Update summary, content, or parent | [→](articles/update_article.md) |

## Projects (2)

| Tool | Description | File |
|------|-------------|------|
| `find_projects` | Search projects by name | [→](projects/find_projects.md) |
| `get_project` | Full project details (fields, work types) | [→](projects/get_project.md) |

## Users & Groups (4)

| Tool | Description | File |
|------|-------------|------|
| `get_current_user` | Your user info | [→](users/get_current_user.md) |
| `find_user` | Find user by login or email | [→](users/find_user.md) |
| `find_user_groups` | Search groups and project teams | [→](users/find_user_groups.md) |
| `get_user_group_members` | List members of a group | [→](users/get_user_group_members.md) |

## Common Workflows

- **My open tasks**: `search_issues` → `query: "for: me State: Open"`
- **Create task**: `find_projects` → `create_issue`
- **Close task**: `get_issue` → `update_issue` → `add_issue_comment`
- **Find KB article**: `search_articles` → `get_article`
- **Track time**: `log_work` with `durationMinutes` + optional `workType` from `get_project`
