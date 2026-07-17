# link_issues

Link two issues together.

## Args
- targetIssueId (string, required): Target issue ID
- linkType (string, required): e.g. "relates to", "subtask of", "depends on", "duplicates", "blocked by"
- issueToLinkId (string, required): Issue to link to target

## Call
POST {baseUrl}/mcp
Authorization: Bearer {token}
Content-Type: application/json
Accept: application/json, text/event-stream

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"link_issues","arguments":{"targetIssueId":"<target>","linkType":"relates to","issueToLinkId":"<source>"}}}
```
