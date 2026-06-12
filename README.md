# Transloadit (transloadit)

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
