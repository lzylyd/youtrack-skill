# search_issues

Search for issues across projects using a query string.

## Args
- query (string, required): The search query string
- customFieldsToReturn (array of strings, optional, default ["Type","State","Assignee"]): Custom fields to include in results
- offset (integer, optional, default 0): Number of results to skip
- limit (integer, optional, default 20, max 20): Max results to return

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"search_issues","arguments":{"query":"project: myProject","customFieldsToReturn":["Type","State","Assignee"],"offset":0,"limit":20}}}
```
