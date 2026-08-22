# Lever (lever-co)

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

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/lever-co/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/lever-co/refs/heads/main/apis.yml)

## Scope

- **Access:** 3rd-Party

## Tags

- Applicant Tracking
- ATS
- CRM
- Recruiting
- Hiring
- Talent Acquisition
- Human Resources
- HR Tech
- Postings
- Webhooks
- OAuth

## APIs

### Lever Data API

The Lever Data API exposes the full recruiting workflow — Opportunities (candidates), Postings, Applications, Interviews, Feedback, Notes, Offers, Requisitions, Stages, Files, Tags, Sources, Users, Audit Events, EEO Responses, and Webhooks — over a JSON REST surface at api.lever.co/v1. Supports OAuth 2.0 Authorization Code Grant and HTTP Basic with a personal API key, with fine-grained scopes per resource and per read/write action.

- **Human URL:** [https://hire.lever.co/developer/documentation](https://hire.lever.co/developer/documentation)
- **Base URL:** `https://api.lever.co/v1`

#### Tags

- Applicant Tracking
- ATS
- CRM
- Recruiting
- Hiring
- Opportunities
- Candidates

#### Properties

- [Documentation](https://hire.lever.co/developer/documentation)
- [OpenAPI](openapi/lever-data-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/lever-data-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/lever-data-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/lever-opportunity-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/lever-posting-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON-LD](json-ld/lever-co-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

### Lever Postings API

The public Lever Postings API lets anyone build a custom careers site by listing a company's published jobs at /v0/postings/{site}, fetching a single posting, and submitting applications. Supports JSON, HTML, and iframe response modes, query filters by location/team/department/commitment, and a multipart application submission endpoint. Available globally and in the EU region.

- **Human URL:** [https://github.com/lever/postings-api](https://github.com/lever/postings-api)
- **Base URL:** `https://api.lever.co/v0/postings`

#### Tags

- Postings
- Jobs
- Careers
- Recruiting

#### Properties

- [Documentation](https://github.com/lever/postings-api)
- [Documentation](https://github.com/lever/postings-api/blob/master/README.md)
- [OpenAPI](openapi/lever-postings-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/lever-postings-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/lever-postings-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/lever-posting-schema.json) — [JSON Schema](https://json-schema.org/specification)

### Lever Postings XML Feed

XML feed of all published job postings for a Lever site, designed for distribution to third-party job boards. Returned by appending `?mode=xml` to the Postings API list endpoint. Fields include position, description, location, and commitment type.

- **Human URL:** [https://hire.lever.co/developer/documentation](https://hire.lever.co/developer/documentation)
- **Base URL:** `https://api.lever.co/v0/postings`

#### Tags

- Postings
- Jobs
- XML
- Job Boards
- Feeds

#### Properties

- [Documentation](https://hire.lever.co/developer/documentation)
- [Sample](https://api.lever.co/v0/postings/xmlexample?mode=xml)
- [Postman Collection](collections/lever-data-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/lever-data-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/lever-postings-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/lever-postings-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Lever Webhooks

Lever publishes ten webhook events covering the application and candidate lifecycle — applicationCreated, candidateHired, candidateStageChange, candidateArchiveChange, candidateDeleted, interviewCreated, interviewUpdated, interviewDeleted, contactCreated, contactUpdated. Endpoints must be HTTPS and verify the HMAC-SHA256 signature on every delivery.

- **Human URL:** [https://hire.lever.co/developer/documentation](https://hire.lever.co/developer/documentation)

#### Tags

- Webhooks
- Events
- Integrations

#### Properties

- [Documentation](https://hire.lever.co/developer/documentation)
- [AsyncAPI](openapi/lever-webhooks-asyncapi.yml) — [AsyncAPI Specification](https://www.asyncapi.com/docs/reference/specification/latest)
- [Postman Collection](collections/lever-data-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/lever-data-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/lever-postings-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/lever-postings-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Portal](https://www.lever.co/)
- [Portal](https://hire.lever.co/developer)
- [Documentation](https://hire.lever.co/developer/documentation)
- [Documentation](https://hire.lever.co/developer/usecases)
- [Documentation](https://hire.lever.co/developer/partner)
- [Source Code](https://github.com/lever)
- [Source Code](https://github.com/lever/postings-api)
- [Partners](https://leverpartner.com)
- [Support](https://help.lever.co/)
- [Status Page](https://status.lever.co/)
- [Blog](https://www.lever.co/blog)
- [Pricing](https://www.lever.co/pricing)
- [Terms of Service](https://www.lever.co/legal/terms-of-service)
- [Privacy Policy](https://www.employinc.com/privacy/)
- [Security](https://www.employinc.com/legal/)
- [LinkedIn](https://www.linkedin.com/company/lever-co)
- [Documentation](https://www.employinc.com/)
- [Plans](https://www.lever.co/pricing)
- [Rate Limits](rate-limits/lever-co-rate-limits.yml)
- [Plans](plans/lever-co-plans-pricing.yml)
- [Fin Ops](finops/lever-co-finops.yml)
- [Authentication](https://hire.lever.co/developer/documentation)

## Maintainers

**FN:** Kin Lane
**Email:** info@apievangelist.com
**URL:** https://kinlane.com
