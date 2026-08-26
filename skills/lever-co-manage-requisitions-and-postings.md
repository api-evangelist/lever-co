---
generated: '2026-08-26'
method: generated
name: Manage requisitions and link them to postings
description: Create headcount requisitions, link them to job postings, and update them without destroying data.
api: openapi/lever-co-requisitions-api-openapi.yml
operations: [listRequisitions, createRequisition, updateRequisition, deleteRequisition, listPostings, getPosting, createPosting, updatePosting]
source: >-
  operationIds verified verbatim in openapi/lever-co-requisitions-api-openapi.yml and
  openapi/lever-co-postings-api-openapi.yml. Linking semantics quoted from the
  2022-09-07 entry on https://hire.lever.co/developer/updates; the irrecoverability
  warning is quoted from the requisition-fields section of
  https://hire.lever.co/developer/documentation (both fetched 2026-08-26).
---

# Manage requisitions and link them to postings

## Entitlement
Requisition endpoints are **not available to every Lever customer** — they require the Lever TRM
Enterprise package or the Advanced HR feature. Expect 403 on accounts without it.

## Auth
- OAuth Bearer with `requisitions:write:admin` and `postings:write:admin`
  (plus `requisition_fields:write:admin` for custom fields).

## Steps
1. **List** — `listRequisitions` (`GET /requisitions`).
2. **Create** — `createRequisition` (`POST /requisitions`) with `name`, `requisitionCode`,
   `headcountTotal`, `hiringManager`, `owner`, `team`, `department`. Pass `postingIds[]` to link postings
   at creation.
3. **Link from the other side** — `updatePosting` (`PUT /postings/{id}`) with `requisitionCodes[]`.
   Confidential postings **cannot** be modified through the API at all.
4. **Update** — `updateRequisition` (`PUT /requisitions/{id}`).

## The one hazard that matters
`updateRequisition` and the requisition-field update are **whole-object PUTs with delete-by-omission
semantics**. Lever's own words: *"Anything that you do not include will be considered deleted and will be
removed. This data cannot be recovered from within Lever or via our API."*

Always **GET, merge, then PUT**. Never send a partial object. There is no restore and no grace period.

Two array fields have a third behaviour worth knowing: omitting `postingIds` (or `requisitionCodes`)
leaves the links unchanged, while passing an **empty array clears every link**.

## Reversibility
- `deleteRequisition` (`DELETE /requisitions/{id}`) is final.
- `updatedAt` on a requisition only moves for a defined set of 17 fields (changelog 2022-11-29), so it is
  not a reliable change-detection signal for everything else.

## Errors
- 403 on accounts without the TRM Enterprise / Advanced HR entitlement, and on confidential postings.
  See `errors/lever-co-problem-types.yml`.
