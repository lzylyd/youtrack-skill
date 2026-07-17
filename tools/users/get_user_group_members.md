# get_user_group_members

Get members of a user group or project team.

## Args
- group (string, required): Group name or project team name.
- offset (integer, optional, default 0): Skip the first N results.
- limit (integer, optional, default 20, max 20): Max results to return.

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"get_user_group_members","arguments":{"group":"","offset":0,"limit":20}}}
```
