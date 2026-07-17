# find_user

Find a user by login or email.

## Args
- loginOrEmail (string, required): The login or email address to search for. Use "me" for the current user.

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"find_user","arguments":{"loginOrEmail":"me"}}}
```
