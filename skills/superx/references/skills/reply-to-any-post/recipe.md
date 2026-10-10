# Reply to Any Post

Any post's context, what its top replies already said, and one strong reply draft.

```bash
superx x:post <post-url-or-id>
superx x:replies <post-url-or-id> --limit 20
superx engage:reply-draft --post <post-id> --thoughts "<what to convey>" --tone engaging
```

`x:replies` is a sample of the best-liked direct replies, not every reply, and it does not exclude the author's own.

MCP: `lookup_x_post` -> `get_x_post_replies` -> `draft_reply`

**Variant: small accounts worth replying to.** When the person wants to start conversations rather than add to the top of a busy thread, run `superx x:replies <post-url-or-id> --worth-replying` instead. It returns up to 3 replies from accounts with 100 to 3,000 followers that have at most one reply so far, each with `person.why` (say it in one line per reply) and `person.author_bio`. Once they pick one, draft a reply TO that reply with `superx engage:reply-draft --text "<the reply's text>" --author "<name>" --handle <username> --thoughts "<what to convey; mention what the original post said>"`, so the draft knows the parent post too and no extra lookup is spent. It costs 5 enrichment units (MCP: `get_x_post_replies` with `worth_replying: true`). An empty list is a real answer, and `503 feature_unavailable` means the option is not enabled yet: use the plain flow above.

Stops at: reply TEXT. **The person posts the reply.** The lookups draw on the shared 300-a-day `x:*` allowance: `x:replies` spends 3 enrichment units and moves that daily counter once per page it fetches, up to 3. A reply draft named by `--post` spends one more lookup, plus typically 2 AI credits (measured).
