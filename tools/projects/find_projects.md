# find_projects

Search for projects in YouTrack.

## Args
- query (string, required): Search string — empty string "" lists all projects
- offset (integer, optional, default 0): Skip N results for pagination
- limit (integer, optional, default 20, max 20): Max results per page

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"find_projects","arguments":{"query":"","offset":0,"limit":20}}}
```
