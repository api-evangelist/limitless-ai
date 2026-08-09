---
name: Search and read Limitless lifelogs
description: >-
  Find the right Pendant recording in a user's Limitless history using hybrid search or a
  time window, then read its full transcript. Use this whenever the user asks what was
  said, who said it, or when something was discussed.
api: openapi/limitless-developer-openapi-original.yml
operations:
  - getLifelogs
  - getLifelog
---

# Search and read Limitless lifelogs

## Authentication

Send `X-API-Key: <key>` on every request. Base URL `https://api.limitless.ai`. The key
comes from Developer settings in the Limitless web app (https://app.limitless.ai). A
missing or invalid key returns `401`.

## Choose your access pattern first

Limitless gives you two mutually exclusive ways into the lifelog list, and picking the
wrong one wastes calls:

- **You know roughly what was said** → use `search`. This is hybrid keyword + semantic
  search, so natural-language queries ("the restaurant Bob recommended at dinner") work
  as well as boolean keyword queries ("blue OR red"). Capped at 100 results, and you
  **cannot paginate** a search.
- **You know roughly when** → use `date`, or `start` + `end`, with `cursor` pagination.

Never send `cursor` together with `search` — the cursor is ignored.

## Steps

1. **List candidates.** Call `getLifelogs` (`GET /v1/lifelogs`).
   - Always set `timezone` to the user's IANA zone (e.g. `America/New_York`). If you
     omit it, Limitless assumes UTC and day boundaries will be wrong.
   - Datetimes for `start`/`end` use modified ISO-8601: `YYYY-MM-DD` or
     `YYYY-MM-DD HH:mm:SS`. Any offset you embed in the value is **ignored** — only the
     `timezone` parameter counts.
   - Set `limit` (max 100) and `direction` (`desc` is the default, newest first).
   - Set `isStarred=true` to restrict to entries the user flagged.
2. **Keep the first pass cheap.** For a scan, send `includeContents=false` and
   `includeMarkdown=false` so you get titles and time spans without pulling every
   transcript. Note that Limitless drops `contents` automatically whenever more than 25
   results come back, regardless of the flag — so do not rely on contents from a wide
   list call.
3. **Page through** by reading `meta.lifelogs.nextCursor` from the response and passing
   it back as `cursor`. Stop when `nextCursor` is absent. Remember: this does not work
   when you used `search`.
4. **Read the winner.** Call `getLifelog` (`GET /v1/lifelogs/{id}`) with the chosen `id`
   and `includeMarkdown=true` to get the full transcript. Returns `404` if the lifelog
   does not exist.

## Reading the response

Everything is wrapped: `{ "data": { "lifelogs": [...] }, "meta": { "lifelogs": {
"nextCursor": "...", "count": N } } }`. A single fetch returns `data.lifelog`.

Each lifelog has a `markdown` rendering and a `contents` tree of `ContentNode`s. Nodes
nest via `children`, and carry `speakerName`, `speakerIdentifier`, and both absolute
(`startTime`/`endTime`) and relative (`startOffsetMs`/`endOffsetMs`) timing. Use
`speakerName` when the user asks who said something; use the offsets when you need to
point at a moment inside the recording.

## Rules

- **Rate limit: 180 requests per minute per API key.** On `429` the body carries
  `retryAfter` (seconds) — wait that long, then retry. Do not retry blindly.
- Errors are plain JSON (`{ "error": "..." }`), not RFC 9457 problem+json, and carry no
  machine-readable error code. Branch on the HTTP status.
- This is personal recorded-conversation data. Retrieve only what answers the user's
  question, and do not fan out across their whole history to satisfy a narrow ask.
