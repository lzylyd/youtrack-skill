# YouTrack Skill

A cross-platform agent skill that lets AI agents (OpenCode, WorkBuddy) interact with YouTrack via the built-in MCP server. No CLI scripts needed — agents invoke MCP tools directly.

## Language

**YouTrack Instance**:
A specific YouTrack server identified by a base URL. The MCP endpoint is at `{baseUrl}/mcp`.
_Avoid_: Server, tracker, YT

**MCP Tool**:
A named function exposed by the YouTrack MCP server (e.g., `search_issues`, `create_article`). The agent calls these directly through the MCP protocol — no CLI or REST wrapper needed.
_Avoid_: Endpoint, API call, command

**Article**:
A YouTrack Knowledge Base document. Articles are organized in projects and can have parent/child hierarchies. Created and updated via MCP tools (`create_article`, `update_article`).
_Avoid_: KB page, wiki page, doc

**Permanent Token**:
A long-lived YouTrack authentication token generated at Settings → Account → Authentication. Used in the MCP server's `Authorization` header.
_Avoid_: API key, password, secret
