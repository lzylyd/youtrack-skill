# get_issue

Get a single issue by its ID with full details.

## Args
- issueId (string, required): The issue ID (e.g. PROJ-123)
- recentCommentsCount (integer, optional, default 5): Number of recent comments to include

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"get_issue","arguments":{"issueId":"PROJ-123","recentCommentsCount":5}}}
```
