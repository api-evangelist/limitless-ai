---
name: Review Limitless Ask AI chats
description: >-
  List and read a user's Ask AI conversation history, including the tool calls the agent
  made and which lifelog entries it retrieved. Use this to recall a previous Ask AI
  answer, or to audit what the assistant actually looked at before answering.
api: openapi/limitless-developer-openapi-original.yml
operations:
  - getChats
  - getChat
  - deleteChat
---

# Review Limitless Ask AI chats

Ask AI is Limitless's assistant over the user's own recorded history. This skill reads
that conversation history back — including the agent's own reasoning trail.

## Authentication

`X-API-Key: <key>` header on every request against `https://api.limitless.ai`.

## Steps

1. **List conversations.** Call `getChats` (`GET /v1/chats`). Page with `cursor`,
   reading `meta.chats.nextCursor` from each response until it is absent. Each `Chat`
   carries `summary`, `createdAt`, `startedAt`, and `visibility` — the `summary` is
   usually enough to pick the right conversation without opening it.
2. **Open the conversation.** Call `getChat` (`GET /v1/chats/{id}`). This returns
   `data.chat` with the full `messages` array.
3. **Read the trail.** Each `ChatMessage` has `text` plus two parallel arrays:
   - `toolCalls[]` — `{ id, toolName, args }`, what Ask AI decided to invoke.
   - `toolResults[]` — `{ toolCallId, toolName, result, isError, entriesReturned }`,
     what came back. Join a result to its call on `toolResults[].toolCallId ==
     toolCalls[].id`.
   - `entriesReturned` on a tool result names the lifelog entries the agent actually
     retrieved. This is the bridge into the lifelog graph — follow those entries with
     `getLifelog` when the user wants the underlying transcript rather than the
     assistant's summary.
   - Check `isError` before trusting a result. A failed tool call means the answer in
     that turn was produced without the data it was reaching for.
4. **Delete on request.** `deleteChat` (`DELETE /v1/chats/{id}`) permanently removes a
   conversation. Confirm the specific chat with the user first — there is no undo.

## Auditing an answer

When the user asks "why did Ask AI say that?", the honest reconstruction is: the `text`
of the message, the `args` of each `toolCall` (the query the agent actually ran), and
`entriesReturned` (what it actually saw). Report gaps plainly — if `entriesReturned` is
empty or `isError` is true, the assistant answered without grounding.

## Rules

- Rate limit is 180 requests per minute per API key. `429` carries `retryAfter` in
  seconds; wait it out rather than retrying immediately.
- Responses are enveloped: `{ "data": { "chats": [...] }, "meta": { ... } }` for the
  list, `{ "data": { "chat": { ... } } }` for a single chat.
- Errors are plain JSON with no machine-readable code. Branch on HTTP status: `401`
  bad key, `404` no such chat, `429` rate limited.
- Chat history is personal data about the user and, through the recordings, about other
  people in their conversations. Read only what the current question needs.
