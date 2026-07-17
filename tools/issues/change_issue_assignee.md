# change_issue_assignee

Change or remove the assignee of an issue.

## Args
- issueId (string, required): The issue ID (e.g. PROJ-123)
- assigneeLogin (string, optional — null to unassign): Login of the user to assign

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"change_issue_assignee","arguments":{"issueId":"PROJ-123","assigneeLogin":"jdoe"}}}
```
