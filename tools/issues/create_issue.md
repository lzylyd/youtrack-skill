# create_issue

Create a new issue in a project.

## Args
- project (string, required): Project ID or short name
- summary (string, required): Issue summary/title
- description (string, optional): Issue description in markdown
- customFields (object, optional): Custom field values keyed by field name
- parentIssue (string, optional): Parent issue ID for sub-tasks
- permittedUsers (array of strings, optional): Usernames to grant access
- permittedGroups (array of strings, optional): Group names to grant access

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"create_issue","arguments":{"project":"PROJ","summary":"Issue summary","description":"Optional description","customFields":{"Type":"Bug","State":"Submitted"},"parentIssue":"PROJ-100","permittedUsers":["jdoe"],"permittedGroups":["developers"]}}}
```
