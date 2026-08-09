---
name: Export and erase Limitless data
description: >-
  Export a user's Limitless history — lifelog transcripts plus the raw Ogg Opus audio —
  and permanently delete lifelogs or Ask AI chats on request. Use this for data
  portability, right-to-erasure requests, and wind-down archival before the Limitless
  support window closes.
api: openapi/limitless-developer-openapi-original.yml
operations:
  - getLifelogs
  - getLifelog
  - downloadAudio
  - deleteLifelog
  - deleteChat
---

# Export and erase Limitless data

The Limitless API describes its own purpose as "providing transparency and portability
to user data". This skill covers both halves: getting everything out, and taking it
down.

**Timing matters.** Limitless was acquired by Meta. Pendant sales ended 2025-12-05 and
support is committed only "throughout 2026", with no published commitment beyond that.
If a user wants an archive, treat it as time-sensitive rather than something to defer.

## Authentication

`X-API-Key: <key>` header on every request against `https://api.limitless.ai`.

## Exporting transcripts

1. Walk the full history with `getLifelogs` (`GET /v1/lifelogs`), oldest-first, by
   setting `direction=asc` and `limit=100`.
2. Set `timezone` to the user's IANA zone so day boundaries are correct.
3. Set `includeMarkdown=true` and `includeHeadings=true`. Do **not** rely on
   `includeContents` in a bulk walk — Limitless strips `contents` automatically whenever
   a response exceeds 25 results.
4. Page with `meta.lifelogs.nextCursor` → `cursor` until `nextCursor` is absent.
5. If you need the structured `ContentNode` tree (speaker attribution, millisecond
   offsets) for a given entry, fetch it individually with `getLifelog`
   (`GET /v1/lifelogs/{id}`).

## Exporting audio

Call `downloadAudio` (`GET /v1/download-audio`) for a time range. The response is an Ogg
Opus file.

- **Hard cap: 2 hours of audio per request.** A longer range returns `400`. Chunk long
  spans into ≤2-hour windows and stitch them yourself.
- `404` means there is no audio for that range — expected for gaps when the Pendant was
  off. Treat it as a normal outcome, not a failure.
- Audio is the largest payload in this API. Budget it against the 180 req/min limit and
  pace requests.

## Erasing data

`deleteLifelog` (`DELETE /v1/lifelogs/{id}`) and `deleteChat`
(`DELETE /v1/chats/{id}`) **permanently** remove the record. There is no undelete, no
soft-delete, and no trash.

Before calling either:

1. Confirm the exact target with the user by title and time span — never delete from a
   search result the user has not seen.
2. Offer to export first. Once deleted, the transcript and its audio are unrecoverable.
3. Delete one record per confirmation. Do not loop a delete across a result set on a
   single blanket approval.

`404` means it was already gone — that is a success for an erasure request, not an
error worth retrying.

## Rules

- Rate limit is 180 requests per minute per API key; `429` returns `retryAfter` in
  seconds. Honor it — a bulk export will hit this.
- Every operation here is a `GET` or `DELETE`, both idempotent at the HTTP level.
  Limitless publishes no idempotency-key header, and none is needed: a repeated delete
  simply returns `404`.
- Deletion via this API is scoped to individual records. Full account deletion and the
  bulk export feature live in the Limitless app, not the API — point the user there for
  an all-at-once wipe.
