# update_issue

Update an existing issue's fields.

## Args
- issueId (string, required): The issue ID (e.g. PROJ-123)
- summary (string, optional): New summary/title
- description (string, optional): New description in markdown
- customFields (object, optional): Custom field values to update
- subscription (boolean, optional): Subscribe or unsubscribe
- vote (boolean, optional): Add or remove vote

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"update_issue","arguments":{"issueId":"PROJ-123","summary":"Updated summary","customFields":{"State":"Fixed"},"subscription":true,"vote":true}}}
```
