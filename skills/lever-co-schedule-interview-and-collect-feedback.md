---
generated: '2026-08-26'
method: generated
name: Schedule an interview and collect feedback
description: Book an interview on an Opportunity, then read or submit the structured feedback.
api: openapi/lever-co-interviews-api-openapi.yml
operations: [listInterviews, createInterview, updateInterview, deleteInterview, listFeedback, createFeedback, listPanels, createPanel]
source: >-
  operationIds verified verbatim in openapi/lever-co-interviews-api-openapi.yml,
  openapi/lever-co-feedback-api-openapi.yml and openapi/lever-co-panels-api-openapi.yml.
  Semantics from https://hire.lever.co/developer/documentation (fetched 2026-08-26).
---

# Schedule an interview and collect feedback

## Auth
- OAuth Bearer with `interviews:write:admin` and `feedback:write:admin` (add `panels:write:admin` for
  multi-interviewer panels). See `scopes/lever-co-scopes.yml`.

## Steps
1. **Check what is already scheduled** — `listInterviews` (`GET /opportunities/{id}/interviews`). Do this
   first: with no idempotency key, this is your only guard against double-booking after a timeout.
2. **Create the interview** — `createInterview` (`POST /opportunities/{id}/interviews`) with the subject,
   time, duration and `interviewers[]`. Since 2024-06-24 each interviewer may carry their own
   `feedbackTemplate`; omitted, it falls back to the interview's template.
3. **Or create a panel** — `createPanel` (`POST /panels`) when several interviews are scheduled as one
   block. `listPanels` (`GET /panels`) reads them back.
4. **Amend** — `updateInterview` (`PUT /opportunities/{id}/interviews/{interviewId}`).
5. **Read the feedback** — `listFeedback` (`GET /opportunities/{id}/feedback`). Since 2025-03-31 the
   response includes `assignment` and `share` feedback types alongside `interview`.
6. **Submit feedback** — `createFeedback` (`POST /opportunities/{id}/feedback`) against a feedback template.

## Reversibility
- `deleteInterview` (`DELETE /opportunities/{id}/interviews/{interviewId}`) is **final** — no restore, no
  grace period. Deleting a panel removes its constituent interviews.
- Prefer `updateInterview` over delete-and-recreate.

## Errors
- 429 on the shared 10 req/s token bucket. No `Retry-After` is returned; back off exponentially and read
  back with `listInterviews` before re-firing. See `rate-limits/lever-co-rate-limits.yml`.
