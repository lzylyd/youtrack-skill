# create_article

Create a new knowledge base article.

## Args
- project (string, required): Project key (e.g. HELP, DEV)
- summary (string, required): Article title
- content (string, optional): Article body in Markdown
- parentArticle (string, optional): Parent article ID for hierarchy
- permittedUsers (array of strings, optional): Usernames with access
- permittedGroups (array of strings, optional): Group names with access

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"create_article","arguments":{"project":"HELP","summary":"New article","content":"# Content"}}}
```
