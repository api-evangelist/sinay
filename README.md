# Sinay (sinay)

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

Sinay is a maritime data and analytics company whose Developers Platform exposes a marketplace of REST APIs for the shipping and ocean-tech industry - vessel and port lookup from combined satellite and terrestrial AIS, metocean (weather and ocean) conditions, per-voyage CO2 emissions modeled on the GLEC Framework, ETA prediction, live port congestion, sailing schedules, and underwater noise.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/sinay/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/sinay/refs/heads/main/apis.yml)

## Access Model (read this first)

- **Marketplace of per-product REST APIs.** Every Sinay API is served over HTTPS from the single host `api.sinay.ai`, with each product mounted under its own versioned base path - e.g. `https://api.sinay.ai/co2/api/v2` and `https://api.sinay.ai/ports-vessels/api/v1`.
- **One auth scheme everywhere.** All endpoints require an API key sent in an `API_KEY` request header. Get a free key from the [Sinay Developers Platform](https://developers.sinay.ai/).
- **Per-API subscriptions / credits.** Usage is metered as monthly API calls / API units (credits). Published tiers: a **Free** plan (~500 calls/month), a **Pro** plan (~10,000 calls/month), and a custom **Enterprise** plan, plus a no-credit-card **free trial** (~100 calls/month). Some endpoints consume more than one API unit per call. Each API reports its own consumption via a `/usages` endpoint (or `/consumption` on Port Congestion). Prices/currency are not reconciled here - confirm on the Developers Platform.
- **REST only.** No public WebSocket API is documented. A separate Webhooks API (container-tracking / Safecube surface) pushes events via HTTP POST to a subscriber endpoint; it is out of scope for the five maritime APIs profiled here.

This entry profiles five of Sinay's maritime-data APIs. The Swagger index at [api.sinay.ai/doc](https://api.sinay.ai/doc/index.html) also lists live specs for underwater noise, sailing schedules, Safecube Ports Intelligence (beta), container tracking, webhooks, and Safecube - not profiled separately here.

## Tags

- Vessel Tracking
- AIS
- Maritime
- Maritime Data
- Weather
- CO2 Emissions
- Port Congestion
- Ship Tracking
- ETA
- Ocean Data

## Timestamps

- **Created:** 2026-07-12
- **Modified:** 2026-07-12

## APIs

### Sinay Ports and Vessels API

Look up vessels by name, MMSI, or IMO and ports by name or UN/LOCODE from Sinay's maritime reference data, built on combined satellite and terrestrial AIS.

- **Human URL:** [https://sinay.ai/en/sinay-hub/ports-and-vessels-api/](https://sinay.ai/en/sinay-hub/ports-and-vessels-api/)
- **Base URL:** `https://api.sinay.ai/ports-vessels/api/v1`
- Endpoints: `GET /vessels`, `GET /ports`, `GET /usages`

### Sinay Metocean API

Retrieve meteorological and oceanographic (weather and ocean) conditions for a geographic area and time window from a chosen model.

- **Human URL:** [https://sinay.ai/en/sinay-hub/metocean-api/](https://sinay.ai/en/sinay-hub/metocean-api/)
- **Base URL:** `https://api.sinay.ai/metocean/api/v1`
- Endpoints: `GET /models`, `POST /stations`, `GET /usages`

### Sinay CO2 Emission API

Compute the CO2 emissions of a container voyage between two ports for a given vessel (IMO or MMSI), returning voyage length and tons of CO2 per TEU via a vessel-model method and a GLEC Framework tradelane method (WTT/TTW/WTW).

- **Human URL:** [https://sinay.ai/en/sinay-hub/co2-api/](https://sinay.ai/en/sinay-hub/co2-api/)
- **Base URL:** `https://api.sinay.ai/co2/api/v2`
- Endpoints: `POST /compute-co2`, `GET /usages`

### Sinay ETA API

Predict a vessel's estimated time of arrival to a destination port, routed from its latest AIS position or from a specified departure port and date.

- **Human URL:** [https://sinay.ai/en/sinay-hub/eta-api/](https://sinay.ai/en/sinay-hub/eta-api/)
- **Base URL:** `https://api.sinay.ai/etac/api/v1`
- Endpoints: `POST /compute-eta`, `GET /usages`

### Sinay Port Congestion API

Retrieve aggregated live port congestion data for a single port by UN/LOCODE or up to ten ports at once, plus credit-consumption reporting.

- **Human URL:** [https://sinay.ai/en/sinay-hub/port-congestion-api/](https://sinay.ai/en/sinay-hub/port-congestion-api/)
- **Base URL:** `https://api.sinay.ai/congestion/api/v1`
- Endpoints: `GET /congestion/{portCode}`, `POST /congestion/batch`, `GET /consumption/current-period`, `GET /consumption/periods`

## Artifacts

- [OpenAPI](openapi/sinay-openapi.yml) - consolidated description of all five APIs
- [Postman Collection](collections/sinay.postman_collection.json)
- [Open Collection](collections/sinay.opencollection.json)
- [Authentication](authentication/sinay-authentication.yml)
- [Plans](plans/sinay-plans-pricing.yml)
- [Rate Limits](rate-limits/sinay-rate-limits.yml)
- [FinOps](finops/sinay-finops.yml)
- [Domain Security](security/sinay-domain-security.yml)
- [Review](review.yml)

## Common Properties

- [Website](https://sinay.ai)
- [Documentation](https://help.sinay.ai/sinay-apis)
- [Sign Up / Developers Platform](https://developers.sinay.ai/)
- [LinkedIn](https://www.linkedin.com/company/sinay)

## Grounding & Honesty Notes

- Endpoints, methods, the `API_KEY` header security scheme, and the CO2 / ETA / congestion request-response shapes were transcribed from the live per-product Swagger files at `https://api.sinay.ai/<product>/api/<version>/swagger.yaml` (confirmed 2026-07-12).
- In the consolidated OpenAPI, some response bodies (vessel/port records, metocean stations, ETA result, congestion aggregate) are represented as generic objects; the authoritative field-level schemas live in the upstream per-product Swagger.
- Pricing (`plans`, `finops`) is modeled from public descriptions of the Developers Platform and marked `reconciled: false`; per-unit prices, currency, and per-endpoint credit weightings are unverified.

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
