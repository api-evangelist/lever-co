---
generated: '2026-08-26'
method: generated
name: Subscribe to Lever webhooks and verify deliveries
description: Register outbound event subscriptions programmatically and validate the HMAC signature on every delivery.
api: openapi/lever-co-webhooks-api-openapi.yml
operations: [listWebhooks, createWebhook, updateWebhook, deleteWebhook]
source: >-
  operationIds verified verbatim in openapi/lever-co-webhooks-api-openapi.yml.
  Event catalogue in openapi/lever-webhooks-asyncapi.yml. Signing scheme quoted from
  https://hire.lever.co/developer/documentation (Securing webhooks), fetched 2026-08-26.
---

# Subscribe to Lever webhooks and verify deliveries

## Auth
- OAuth Bearer with `webhooks:write:admin` (`webhooks:read:admin` to list only).
- Programmatic webhooks plus OAuth are available to **all** Lever customers; the older manual webhook
  setup requires the customer to hold the Webhook feature.

## Steps
1. **List existing subscriptions** — `listWebhooks` (`GET /webhooks`) before creating, so you do not
   register a duplicate endpoint.
2. **Create** — `createWebhook` (`POST /webhooks`) with the event type and your HTTPS URL.
3. **Amend** — `updateWebhook` (`PUT /webhooks/{id}`).
4. **Remove** — `deleteWebhook` (`DELETE /webhooks/{id}`).

## Receiver requirements
- **HTTPS only.** Lever verifies the certificate against a CA; self-signed certificates are rejected. Use a
  tunnel with HTTPS termination for local development.
- Deliveries are `POST` with a JSON body carrying `id`, `event`, `triggeredAt`, `token`, `signature` and a
  per-event `data` object.

## Verifying the signature
The signature is in the **body**, not a header:

1. Concatenate `token` + `triggeredAt`.
2. HMAC-SHA256 that string with your account signing token as the key, hex digest.
3. Compare against `body.signature`.

Replay protection is **not** automatic — cache the 48-character `token` and reject a repeat, and bound
`triggeredAt` against clock skew.

## Events
Ten published events: `applicationCreated`, `candidateHired`, `candidateStageChange`,
`candidateArchiveChange`, `candidateDeleted`, `interviewCreated`, `interviewUpdated`, `interviewDeleted`,
`contactCreated`, `contactUpdated`. Full payload shapes in `openapi/lever-webhooks-asyncapi.yml`.

## Gotcha
- `candidateId` on these payloads is **deprecated** and carries an **Opportunity** id, not a Contact id.
  Use `opportunityId`. See `lifecycle/lever-co-lifecycle.yml`.

## Reversibility
- `deleteWebhook` cannot be undone. Re-creating restores delivery but not the prior subscription id or its
  delivery history.
