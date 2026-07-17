# search_articles

Search articles across YouTrack with query support.

## Args
- query (string, required): Search query — supports fields like 'deployment', '"getting started"', 'project: HELP', 'author: me', 'tag: faq', 'created: {This month}'
- offset (integer, optional, default 0): Number of results to skip
- limit (integer, optional, default 10, max 20): Max results per page

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"search_articles","arguments":{"query":"deployment","offset":0,"limit":10}}}
```
