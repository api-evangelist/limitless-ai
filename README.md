# Limitless (limitless-ai)

Limitless is a personalized AI for meetings with a software assistant and the Limitless Pendant wearable that captures conversations as Lifelogs. The Limitless Developer API gives users programmatic access to their own Lifelogs, Ask AI chat history, and audio downloads, with an MCP endpoint that lets Claude and other MCP-compatible tools query Limitless memory directly. The OpenAPI spec is published and example code is hosted on GitHub.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/limitless-ai/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/limitless-ai/refs/heads/main/apis.yml)

## Tags

- AI
- Wearable
- Pendant
- Meeting Notes
- Lifelogs
- Personal AI
- API
- MCP
- OpenAPI

## Timestamps

- **Created:** 2026-05-23
- **Modified:** 2026-05-23

## APIs

### Limitless Pendant

Wearable AI pendant that captures ambient audio, transcribes it, and stores it as Lifelogs in the user's Limitless account.

- **Human URL:** [https://www.limitless.ai/](https://www.limitless.ai/)
- **Base URL:** `https://www.limitless.ai`

#### Tags

- Hardware
- Wearable
- Pendant
- Lifelogs

#### Properties

- [Product Page](https://www.limitless.ai/)
- [Postman Collection](collections/limitless-ai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/limitless-ai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Limitless Meeting Assistant

Software assistant for meetings — transcripts, summaries, and Ask AI chat over personal memory. Available across desktop and mobile.

- **Human URL:** [https://www.limitless.ai/](https://www.limitless.ai/)
- **Base URL:** `https://www.limitless.ai`

#### Tags

- Meetings
- Assistant
- Transcripts
- Ask AI

#### Properties

- [Product Page](https://www.limitless.ai/)
- [Postman Collection](collections/limitless-ai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/limitless-ai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Limitless Developer API

REST API at https://api.limitless.ai/v1 for the authenticated user's Lifelogs and Ask AI chat history. Authentication is the `X-API-Key` header with a key generated in Developer settings. Endpoints include GET /lifelogs (search, sort, paginate), GET /lifelogs/{id}, DELETE /lifelogs/{id}, GET /download-audio (Ogg Opus, max 2-hour duration), GET /chats, GET /chats/{id}, and DELETE /chats/{id}. Rate limit is 180 requests per minute per API key. OpenAPI spec is published at /openapi.yml and example code lives on GitHub.

- **Human URL:** [https://www.limitless.ai/developers](https://www.limitless.ai/developers)
- **Base URL:** `https://api.limitless.ai/v1`

#### Tags

- REST
- API Key
- Lifelogs
- Audio
- Chats
- OpenAPI

#### Properties

- [Documentation](https://www.limitless.ai/developers)
- [OpenAPI](https://api.limitless.ai/v1/openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Examples](https://github.com/limitless-ai-inc/limitless-api-examples)
- [Git Hub Org](https://github.com/limitless-ai-inc)
- [Postman Collection](collections/limitless-ai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/limitless-ai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Limitless MCP Server

Hosted Model Context Protocol endpoint that connects Claude and other MCP-compatible clients to the user's Limitless memory.

- **Human URL:** [https://www.limitless.ai/developers](https://www.limitless.ai/developers)
- **Base URL:** `https://api.limitless.ai/mcp`

#### Tags

- MCP
- Model Context Protocol
- Claude
- Memory

#### Properties

- [Documentation](https://www.limitless.ai/developers)
- [Endpoint](https://api.limitless.ai/mcp)
- [Postman Collection](collections/limitless-ai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/limitless-ai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/limitless-ai)
- [Website](https://www.limitless.ai/)
- [Developers](https://www.limitless.ai/developers)
- [Git Hub](https://github.com/limitless-ai-inc)
- [OpenAPI](https://api.limitless.ai/v1/openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Plans](plans/limitless-ai-plans-pricing.yml)
- [Rate Limits](rate-limits/limitless-ai-rate-limits.yml)
- [Fin Ops](finops/limitless-ai-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
