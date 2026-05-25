# Lever

Lever is a modern applicant tracking system (ATS) and recruiting CRM that helps organizations attract,
nurture, and hire talent. The platform unifies candidate relationship management, automation, structured
interview feedback, analytics, and collaborative hiring tools in a single record (the **Opportunity**) that
spans every posting a candidate touches. Lever is owned by **Employ Inc.**, which also operates JazzHR and
Jobvite.

This repository is an [API Evangelist](https://apievangelist.com/) catalog entry for Lever, capturing the
public Lever developer surface as a portable, machine-readable profile (apis.yml + OpenAPI + AsyncAPI +
JSON Schema + JSON-LD + Naftiko capabilities + API Commons Plans / Rate Limits / FinOps).

- **Provider site**: <https://www.lever.co/>
- **Developer portal**: <https://hire.lever.co/developer>
- **API documentation**: <https://hire.lever.co/developer/documentation>
- **Postings API repo & examples**: <https://github.com/lever/postings-api>
- **Status**: <https://status.lever.co/>
- **Pricing**: <https://www.lever.co/pricing> (contact sales)

## APIs Profiled

| API | Base URL | Auth | Spec |
|-----|----------|------|------|
| Lever Data API | `https://api.lever.co/v1` | OAuth 2.0 / API Key (Basic) | [`openapi/lever-data-api-openapi.yml`](openapi/lever-data-api-openapi.yml) |
| Lever Postings API (public) | `https://api.lever.co/v0/postings` (EU: `api.eu.lever.co`) | Public; posting-form key for application POST | [`openapi/lever-postings-api-openapi.yml`](openapi/lever-postings-api-openapi.yml) |
| Lever Postings XML Feed | `https://api.lever.co/v0/postings/{site}?mode=xml` | Public | — |
| Lever Webhooks | Outbound | HMAC-SHA256 signature | [`openapi/lever-webhooks-asyncapi.yml`](openapi/lever-webhooks-asyncapi.yml) |

### Data API resources

Applications, Archive Reasons, Audit Events, Contacts, EEO Responses (with and without PII), Feedback,
Feedback Templates, Files, Form Fields, Forms / Form Templates, Groups, Interviews, Notes, Offers,
Opportunities, Panels, Postings, Posting Forms, Profile Forms, Profile Form Templates, Referrals,
Requisitions, Requisition Fields, Resumes, Roles, Sources, Stages, Surveys, Tags, Tasks, Uploads, Users,
Webhooks.

### Webhook events

`applicationCreated`, `candidateHired`, `candidateStageChange`, `candidateArchiveChange`,
`candidateDeleted`, `interviewCreated`, `interviewUpdated`, `interviewDeleted`, `contactCreated`,
`contactUpdated`. All deliveries are HMAC-SHA256 signed; endpoints must serve HTTPS.

## Authentication

- **HTTP Basic** — Lever API key as username, blank password (use for personal-account integrations).
- **OAuth 2.0 Authorization Code Grant** — `https://auth.lever.co/authorize` (auth) and
  `https://auth.lever.co/oauth/token` (token). Refresh tokens supported via `offline_access`. Access tokens
  expire after 1 hour; refresh tokens after 1 year or 90 days of inactivity.
- **Granular scopes** — `{resource}:{read|write}:admin` pattern across opportunities, postings, interviews,
  feedback, users, requisitions, offers, files, webhooks, audit events, EEO responses (with optional PII
  scope), and a top-level `confidential:access:admin` for restricted records.

## Rate Limits

- Data API: token-bucket, **10 req/s steady-state, 20 req/s burst per API key**.
- Postings API: **2 application POSTs per second per site**.

See [`rate-limits/lever-co-rate-limits.yml`](rate-limits/lever-co-rate-limits.yml).

## Pricing

Lever is contact-sales — no public price list. The single visible plan bundles ATS, CRM, reporting, and
integrations. Optional add-ons: **Candidate Insights**, **AI Screening by VONQ**, **Onboarding**. API access
is included with the platform subscription. See [`plans/lever-co-plans-pricing.yml`](plans/lever-co-plans-pricing.yml).

## Artifacts

```
lever-co/
├── apis.yml                                            # APIs.json provider profile
├── openapi/
│   ├── lever-data-api-openapi.yml                      # Data API (full resource map)
│   ├── lever-postings-api-openapi.yml                  # Public Postings API
│   └── lever-webhooks-asyncapi.yml                     # Webhooks (AsyncAPI 3.0)
├── json-schema/
│   ├── lever-opportunity-schema.json
│   └── lever-posting-schema.json
├── json-ld/
│   └── lever-co-context.jsonld                         # schema.org-aligned semantics
├── capabilities/                                       # Naftiko capability definitions
│   ├── data-opportunities.yaml
│   ├── data-postings.yaml
│   ├── data-interviews.yaml
│   ├── data-feedback.yaml
│   ├── data-notes.yaml
│   ├── data-files.yaml
│   ├── data-users.yaml
│   ├── data-requisitions.yaml
│   ├── data-offers.yaml
│   ├── data-webhooks.yaml
│   └── postings-public.yaml
├── plans/
│   └── lever-co-plans-pricing.yml                      # API Commons Plans 0.1
├── rate-limits/
│   └── lever-co-rate-limits.yml                        # API Commons Rate Limits 0.1
├── finops/
│   └── lever-co-finops.yml                             # FOCUS-aligned FinOps
└── vocabulary/
    └── lever-co-vocabulary.yml
```

## Use Cases Lever Highlights

- **Assessments** — invite candidates to assessment platforms as they reach a stage.
- **Background checks** — trigger when an opportunity reaches the background-check stage.
- **HRIS / onboarding** — fire when an opportunity is archived as `Hired`.
- **Job boards** — distribute via the XML feed.
- **Scheduling** — create / update / delete interviews.
- **Sourcing** — push opportunities into Lever from external sources.

Reference partner integrations include GoodHire, Sapling Onboarding by Kallidus, GoodTime, and Fetcher
(see <https://leverpartner.com>).

## License

Catalog content is published under the API Evangelist conventions. The Lever name, marks, and underlying
APIs are property of Lever / Employ Inc.; this profile is a third-party catalog entry and not affiliated
with Lever.
