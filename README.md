# Dacast (dacast)

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

Dacast is a unified live streaming and video hosting (OTT) platform that lets businesses broadcast live channels, host and monetize video on demand (VOD), organize content into playlists, and embed a white-label HTML5 player. Dacast exposes a RESTful JSON API at `https://developer.dacast.com/v2` for programmatically creating live channels, uploading and managing VOD, building playlists, and reading viewer analytics.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/dacast/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/dacast/refs/heads/main/apis.yml)

## Access Model (read this first)

Dacast's API is **plan-gated, not open self-serve**:

- **API access is included only on the Scale plan and Custom (enterprise) plans.** The entry **Starter** and **Event** plans do not include API access.
- Trial accounts can request **temporary API access from Dacast sales** for evaluation.
- API keys are generated in the Dacast dashboard under **Settings > Integrations** and passed as an **`X-Api-Key`** request header (some calls also require an `X-Format` header).

Because the full reference sits behind the developer portal, this catalog grounds the confirmed pieces (base host, `v2` versioning, `X-Api-Key` auth, and the operations `POST /v2/vod`, `POST /v2/channel`, `POST /v2/playlist`, `GET /v2/playlist/{playlistId}`) and **honestly models** the remaining documented capabilities. Modeled operations are flagged with `x-modeled: true` in the OpenAPI and listed under `endpointsModeled` in `review.yml`. Verify exact paths against [docs.dacast.com](https://docs.dacast.com) and [docs.dacast.com/llms.txt](https://docs.dacast.com/llms.txt) before use.

## Tags

- Live Streaming
- Video
- VOD
- OTT
- Video Hosting
- Media
- Analytics

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

### Dacast VOD API

Create, list, look up, and delete video-on-demand assets, and upload source files. Uploads work by requesting a signed upload target (`POST /v2/vod`) and pushing the file to Dacast storage, with multi-part upload and bulk upload flows for large libraries.

- **Human URL:** [https://docs.dacast.com/docs/vod-upload](https://docs.dacast.com/docs/vod-upload)
- **Base URL:** `https://developer.dacast.com/v2`

### Dacast Live Channels API

Create and manage live streaming channels (`POST /v2/channel`), look up a stream, list online streams, switch stream ingest, change channel type, and manage simulcast destinations that restream to third-party targets. Live ingest is RTMP/SRT push, not a Dacast-hosted API transport.

- **Human URL:** [https://docs.dacast.com/docs/create-live-streams-channels](https://docs.dacast.com/docs/create-live-streams-channels)
- **Base URL:** `https://developer.dacast.com/v2`

### Dacast Playlists API

Create playlists (`POST /v2/playlist`), retrieve a playlist (`GET /v2/playlist/{playlistId}`), and set playlist contents by mixing VOD and live channel items. Playlist updates are a replace-in-place operation - the full content array is submitted on each change.

- **Human URL:** [https://docs.dacast.com/docs/playlists](https://docs.dacast.com/docs/playlists)
- **Base URL:** `https://developer.dacast.com/v2`

### Dacast Analytics API

Read raw viewer analytics - views, watch time, bandwidth, and geography per content item and per account - so you can build custom reporting on top of Dacast VOD and live streaming. Dacast documents analytics export via the API, but exact endpoint paths and query parameters are not published; the analytics operations here are honestly modeled.

- **Human URL:** [https://www.dacast.com/support/knowledgebase/walkthrough-to-per-content-video-analytics-on-dacast/](https://www.dacast.com/support/knowledgebase/walkthrough-to-per-content-video-analytics-on-dacast/)
- **Base URL:** `https://developer.dacast.com/v2`

## Pricing (summary)

| Plan | Price (billed annually) | Bandwidth | Storage | API access |
|------|------------------------|-----------|---------|------------|
| Starter | $39/mo ($468/yr) | 2.4 TB/yr | 500 GB | No |
| Event | $63/mo ($750/yr) | 6 TB upfront | 250 GB | No |
| Scale | $165/mo ($1,980/yr); ~$250/mo month-to-month | 24 TB/yr | 2,000 GB | Yes |
| Custom | Contact sales | Custom | Custom | Yes |

Overages: bandwidth ~$0.30/GB (pre-paid as low as $0.09/GB), storage ~$0.15/GB/month. All plans include unlimited concurrent viewers. See [plans/dacast-plans-pricing.yml](plans/dacast-plans-pricing.yml).

## WebSocket Review

Dacast does **not** expose a documented public WebSocket API. Its public developer API is request/response REST over HTTPS, and its real-time video is carried by RTMP/SRT ingest and HLS/DASH delivery - media streaming transports, not a WebSocket message API. No AsyncAPI document was authored. See [review.yml](review.yml).

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/dacast)
- [Website](https://www.dacast.com)
- [Documentation](https://docs.dacast.com)
- [Plans](plans/dacast-plans-pricing.yml)
- [Rate Limits](rate-limits/dacast-rate-limits.yml)
- [Fin Ops](finops/dacast-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
