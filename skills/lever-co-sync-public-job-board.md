---
generated: '2026-08-26'
method: generated
name: Sync a public Lever job board
description: Mirror a company's published Lever postings onto a careers site or job board, with no credential.
api: openapi/lever-co-postings-api-openapi.yml
operations: [listPublicPostings, getPublicPosting]
source: >-
  operationIds verified verbatim in openapi/lever-co-postings-api-openapi.yml.
  Behaviour confirmed by live probe of https://api.lever.co/v0/postings/leverdemo
  (HTTP 200, application/json) and ?mode=xml (HTTP 200, text/xml) on 2026-08-26.
---

# Sync a public Lever job board

Read a company's live job postings from Lever without any credential. This is the only Lever surface an
agent can call today with no partner approval.

## Auth
- **None.** The public Postings API is unauthenticated. Base `https://api.lever.co/v0/postings`; EU tenants
  are served from `https://api.eu.lever.co/v0/postings`.
- The `{site}` path segment is the company's Lever board handle — the slug in `jobs.lever.co/<site>`.
  `leverdemo` is Lever's own public demo board.

## Steps
1. **List the board** — `listPublicPostings` (`GET /{site}`). Returns an array of posting objects with
   `id`, `text`, `categories`, `descriptionPlain`, `hostedUrl` and `applyUrl`.
2. **Read one posting** — `getPublicPosting` (`GET /{site}/{postingId}`) for the full description of a
   single role.
3. **Or take the XML feed** — append `?mode=xml` to step 1 for the syndication feed. It is a proprietary
   `<jobs><job>` document, **not** `schema.org/JobPosting`, so a consumer needs a Lever-specific mapper.
   See `conformance/lever-co-conformance.yml`.

## Limits
- Rate: `GET` on the public board has no published per-second limit, but application POSTs against the
  same host are capped at 2/second per site. CORS is restricted to the site's own domain and subdomains,
  so browser-side fetching from a third-party origin will fail — call it server-side.
- No `RateLimit-*` headers are returned. See `rate-limits/lever-co-rate-limits.yml`.

## Errors
- `{"code": "...", "message": "..."}` as `application/json`. A bad `{site}` returns 404 `ResourceNotFound`.
  See `errors/lever-co-problem-types.yml`.

## Notes
- Confidential postings never appear on a public board.
- Postings deleted since your last sync are only discoverable through the authenticated
  `GET /postings/deleted` endpoint (max 30-day query window) — the public feed just stops listing them.
