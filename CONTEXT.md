# YouTrack Skill

A cross-platform agent skill that lets AI agents (OpenCode, WorkBuddy) interact with YouTrack via the built-in MCP server. Agents discover tools through `tools/index.md`, then load individual tool templates on demand.

## Language

**YouTrack Instance**:
A specific YouTrack server identified by a base URL. The MCP endpoint is at `{baseUrl}/mcp`.
_Avoid_: Server, tracker, YT

**MCP Tool**:
A named function exposed by the YouTrack MCP server (e.g., `search_issues`, `create_article`). Invoked via JSON-RPC `tools/call` method.
_Avoid_: Endpoint, API call, command

**Article**:
A YouTrack Knowledge Base document. Created and updated via MCP tools. No delete tool exists.
_Avoid_: KB page, wiki page, doc

**JSON-RPC Envelope**:
The request format for MCP calls: `{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"<tool>","arguments":{}}}`.
_Avoid_: REST call, curl command

**Progressive Discovery**:
Loading strategy where the agent reads `tools/index.md` to find a tool, then loads only that tool's file. Avoids loading all 23 tool descriptions at once.
