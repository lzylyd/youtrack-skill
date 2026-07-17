# manage_issue_tags

Add or remove a tag from an issue.

## Args
- issueId (string, required): Issue ID
- tag (string, required): Tag ID or name
- operation (string, required): "add" or "remove"

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"manage_issue_tags","arguments":{"issueId":"<id>","tag":"<tag>","operation":"add"}}}
```
