# Limitless (limitless-ai)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
