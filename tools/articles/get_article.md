# get_article

Get a single article by its ID.

## Args
- articleId (string, required): ID of the article to retrieve
- linesOffset (integer, optional, default 0): Number of content lines to skip
- linesCount (integer, optional, default 500): Max content lines to return

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"get_article","arguments":{"articleId":"1-2","linesOffset":0,"linesCount":500}}}
```
