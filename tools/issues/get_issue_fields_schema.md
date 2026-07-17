# get_issue_fields_schema

Get the field schema for a project.

## Args
- projectKey (string, required): Project key

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"get_issue_fields_schema","arguments":{"projectKey":"<key>"}}}
```
