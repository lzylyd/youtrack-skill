# update_article

Update an existing knowledge base article.

## Args
- articleId (string, required): ID of the article to update
- summary (string, optional): New title
- content (string, optional): New content in Markdown
- append (boolean, optional, default false): If true, appends to existing content
- parentArticleId (string, optional): New parent article ID

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"update_article","arguments":{"articleId":"1-2","summary":"Updated title","append":false}}}
```
