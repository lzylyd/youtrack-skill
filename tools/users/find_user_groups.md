# find_user_groups

Find user groups whose name contains a given string.

## Args
- nameContains (string, required): Filter by group name substring. Empty string "" lists all groups.
- offset (integer, optional, default 0): Skip the first N results.
- limit (integer, optional, default 20, max 20): Max results to return.

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"find_user_groups","arguments":{"nameContains":"","offset":0,"limit":20}}}
```
