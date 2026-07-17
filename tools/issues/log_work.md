# log_work

Log work time on an issue.

## Args
- issueId (string, required): Issue ID
- durationMinutes (integer, required): Positive minutes worked
- description (string, optional): Work description
- date (string, optional): "yyyy-MM-dd"
- workType (string, optional): Name from get_project workTypes
- workItemAttributes (object, optional): Additional attributes

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"log_work","arguments":{"issueId":"<id>","durationMinutes":60}}}
```
