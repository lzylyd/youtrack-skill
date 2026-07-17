# create_draft_issue

Create a draft issue without publishing it.

## Args
- project (string, required): Project ID or short name
- summary (string, required): Issue summary/title

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"create_draft_issue","arguments":{"project":"PROJ","summary":"Draft issue summary"}}}
```
