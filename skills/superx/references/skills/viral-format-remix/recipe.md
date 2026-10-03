# Viral Format Remix

Proven hooks and structures from a library of 50M+ high-performing posts, rewritten in the account's voice.

```bash
superx inspiration:search "<topic>" --sort outlier --min-likes 500 --limit 10
superx posts:draft --brief "<what this account would say on that topic>" --mirror "<the reference post's text>" --count 2
superx scheduled:create --text "<approved text>" --idempotency-key "remix-<slug>-1"
```

`--mirror` copies the SHAPE of a proven post, not its words. Pick a reference with room for the account's own facts.

MCP: `find_inspiration` (`sort: "outlier"`, optionally `min_outlier_score: 3` for posts with 3x the expected engagement for the author's size) -> `draft_post` -> `schedule_post`

Stops at: reference posts plus drafts, for the person to pick from. 3 AI credits per draft written.
