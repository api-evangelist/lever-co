---
generated: '2026-08-26'
method: generated
name: Source a candidate into the pipeline
description: Create an Opportunity for a candidate, place them in a stage, and tag their source.
api: openapi/lever-co-opportunities-api-openapi.yml
operations: [listStages, listSources, createOpportunity, getOpportunity, updateOpportunity]
source: >-
  operationIds verified verbatim in openapi/lever-co-opportunities-api-openapi.yml,
  openapi/lever-co-stages-api-openapi.yml and openapi/lever-co-sources-api-openapi.yml.
  Semantics from https://hire.lever.co/developer/documentation (fetched 2026-08-26).
---

# Source a candidate into the pipeline

Add a sourced candidate to Lever as an Opportunity.

## Auth
- OAuth 2.0 Bearer token with `opportunities:write:admin`, plus `stages:read:admin` and
  `sources:read:admin` for the lookups. See `authentication/lever-co-authentication.yml` and
  `scopes/lever-co-scopes.yml`.
- Base `https://api.lever.co/v1`.

## Before you write
- **There is no idempotency key.** A retried `createOpportunity` creates a second candidacy for the same
  person. See `conventions/lever-co-conventions.yml`.
- A **Contact** is the person; an **Opportunity** is one candidacy. If the person already exists, pass the
  `contact` id on create so Lever links rather than duplicates. Without it, Lever falls back to
  de-duplicating on the email in the request (changelog entry 2021-06-02).

## Steps
1. **Resolve the target stage** — `listStages` (`GET /stages`). Capture the stage UUID you want the
   candidate to land in.
2. **Resolve the source** — `listSources` (`GET /sources`) so the candidate's origin is attributed
   correctly in reporting.
3. **Create the Opportunity** — `createOpportunity` (`POST /opportunities`) with `name`, `emails[]`,
   `stage`, `sources[]`, and `contact` when you already know the person's Contact id. A resume file may be
   attached; note that jpg/png upload but are **not** parsed.
4. **Read it back** — `getOpportunity` (`GET /opportunities/{id}`) to confirm the write landed before any
   retry. Use `?expand=stage&expand=owner` to inline references instead of making extra calls.
5. **Advance or archive later** — `updateOpportunity` (`PUT /opportunities/{id}`) changes stage, tags,
   sources, links and archived state.

## Reversibility
- Archiving is the reversible exit: `updateOpportunity` with an archive reason archives, and the same
  operation with the reason set to `null` un-archives. No time window applies.
- Deleting an Opportunity is not reversible. See `conventions/lever-co-conventions.yml`.

## Errors
- 403 when the credential lacks the scope, or when the record is confidential and the credential has no
  confidential grant — an access error, not an empty result. See `errors/lever-co-problem-types.yml`.
