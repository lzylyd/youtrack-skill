# get_saved_issue_searches

Get saved issue searches.

## Args
- offset (integer, optional, default 0): Pagination offset
- limit (integer, optional, default 20, max 20): Max searches to return

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"get_saved_issue_searches","arguments":{"offset":0,"limit":20}}}
```
