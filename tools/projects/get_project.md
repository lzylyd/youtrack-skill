# get_project

Get a single project by key, including work types and work item schema.

## Args
- projectKey (string, required): Project key (e.g. "DEMO")

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"get_project","arguments":{"projectKey":"DEMO"}}}
```
