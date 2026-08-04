# Transloadit (transloadit)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Transloadit is a file processing and media handling API for encoding video, resizing images, extracting audio, generating thumbnails, and transcribing media via assembly instructions. The platform supports 94 Robots for automated processing workflows, browser-based uploads via the open-source Uppy file uploader, a Smart CDN for URL-driven conversion, and seamless integrations with storage providers including Amazon S3, Google Drive, Backblaze, and FTP. Founded in 2009 and profitable since 2012, Transloadit serves customers including The New York Times and Coursera.

APIs.json: https://raw.githubusercontent.com/api-evangelist/transloadit/refs/heads/main/apis.yml

Naftiko: https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=transloadit-api-evangelist&utm_content=repo

## Tags

- File Processing
- Media Encoding
- Video Transcoding
- Image Resizing
- Audio Extraction
- Thumbnail Generation
- File Uploading
- Media API

## APIs

### Transloadit API

Core REST API for creating and managing Assemblies (processing jobs), Templates, Template Credentials, Webhooks, Billing, and Queue monitoring. Uses bearer token authentication. Supports video encoding, image manipulation, audio processing, document conversion, and AI-based media tasks via 94 Robots.

- **Base URL:** https://api2.transloadit.com
- **Documentation:** https://transloadit.com/docs/api/
- **Rate Limits:** https://transloadit.com/docs/api/rate-limiting/

**API Sections:** Assemblies | Templates | Template Credentials | Webhooks | Billing | Queue

## Plans, Rate Limits, and FinOps

### Plans

Transloadit offers five tiers plus custom Enterprise plans. All plans include every feature and all 94 Robots; differences are volume, throughput, and seats.

| Plan | Price/mo | Included GB | Overage/GB | Seats | Max File Size |
|---|---|---|---|---|---|
| Community | Free | 5 GB | Not allowed | 1 | 0.5 GB |
| Hobbyist | $9 | 5 GB | Not allowed | 2 | 0.5 GB |
| Startup | $69 | 40 GB | $1.80 | 2 | 5 GB |
| Small Business | $139 | 100 GB | $1.50 | 5 | 10 GB |
| Medium Business | $349 | 300 GB | $1.20 | 10 | 20 GB |
| Enterprise | Custom | Custom | Negotiated | Custom | Custom |

Full plans detail: [plans/transloadit-plans-pricing.yml](plans/transloadit-plans-pricing.yml)

### Rate Limits

- 250 Assemblies per minute (HTTP 413 / RATE_LIMIT_REACHED)
- 250 concurrent Assemblies (HTTP 413 / RATE_LIMIT_REACHED)
- 8-hour maximum Assembly duration
- High-frequency TCP connection limits enforced at the proxy layer (HTTP 429)
- Official SDKs include automatic retry with back-off using the retryIn property

Full rate limits detail: [rate-limits/transloadit-rate-limits.yml](rate-limits/transloadit-rate-limits.yml)

### FinOps

Usage is billed as combined input + output GB. Key cost levers include right-sizing the plan tier, leveraging Robot byte-reduction (up to 90%), minimizing redundant output variants, and configuring spending limits on Enterprise plans. The Billing API at `/bills/{month}` supports programmatic cost reporting.

Full FinOps detail: [finops/transloadit-finops.yml](finops/transloadit-finops.yml)

## Timestamps

- **Created:** 2026-06-12
- **Modified:** 2026-06-12

## Common

| Type | URL |
|---|---|
| Website | https://transloadit.com/ |
| Documentation | https://transloadit.com/docs/ |
| GitHub | https://github.com/transloadit |
| LinkedIn | https://www.linkedin.com/company/transloadit |
| Blog | https://transloadit.com/blog/ |
| Pricing | https://transloadit.com/pricing/ |
| Status Page | https://status.transloadit.com/ |
| X | https://x.com/transloadit |

## Maintainers

**Kin Lane** — kin@apievangelist.com
