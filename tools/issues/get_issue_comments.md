# get_issue_comments

Get comments for an issue.

## Args
- issueId (string, required): Issue ID
- offset (integer, optional, default 0): Pagination offset
- limit (integer, optional, default 10, max 10): Max comments to return

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"get_issue_comments","arguments":{"issueId":"<id>","offset":0,"limit":10}}}
```
