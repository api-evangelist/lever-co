# Lever (lever-co)

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
