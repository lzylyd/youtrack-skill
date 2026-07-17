# add_issue_comment

Add a comment to an issue.

## Args
- issueId (string, required): Issue ID
- text (string, required): Comment text
- permittedUsers (array of strings, optional): Users with visibility
- permittedGroups (array of strings, optional): Groups with visibility

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"add_issue_comment","arguments":{"issueId":"PROJ-123","text":"Comment text in Markdown"}}}
```
