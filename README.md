# Dacast (dacast)

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
