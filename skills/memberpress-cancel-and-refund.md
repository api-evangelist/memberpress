---
name: memberpress-cancel-and-refund
description: Handle a MemberPress cancellation or refund request safely — locate the member's
  subscription and transactions, choose between cancel, suspend and refund, and confirm the
  outcome.
api: memberpress:developer-tools-rest-api
generated: '2026-08-12'
method: generated
source: openapi/memberpress-developer-tools-openapi.yml
operations:
- listMembers
- listSubscriptions
- listTransactions
- cancelSubscription
- suspendSubscription
- resumeSubscription
- refundTransaction
- refundTransactionAndCancelSubscription
- getSubscription
---

# Cancel or refund a MemberPress member

Every operation here moves money or revokes access, and **none of them is idempotent**. Read the
guardrails before acting.

## Guardrails

- No idempotency key exists anywhere on this API. A timed-out refund may already have been
  issued. **Never blind-retry a refund** — re-read the transaction first.
- `refundTransaction` and `refundTransactionAndCancelSubscription` are irreversible. Require
  explicit human approval before calling either.
- There is no rate-limit header and no `Retry-After`. Serialize these calls; do not parallelize.
- Auth: `MEMBERPRESS-API-KEY`, or a bare key in `Authorization` — never `Bearer`.

## Steps

1. **Identify the member.** `listMembers` — `GET /members?search[email]=<email>`. Keep the
   integer `id`.

2. **Read the current state before changing anything.**
   - `listSubscriptions` — `GET /subscriptions?search[member]=<id>`
   - `listTransactions` — `GET /transactions?search[member]=<id>`

   Transactions carry a `subscription` field when they are recurring payments; that field is how
   you tell a one-off purchase from a renewal.

3. **Choose the right action.**

   | Request | Operation | Effect |
   |---|---|---|
   | Stop future billing, keep access to term end | `cancelSubscription` — `POST /subscriptions/{id}/cancel` | Ends the agreement |
   | Temporary hold, intending to restart | `suspendSubscription` — `POST /subscriptions/{id}/suspend` | Reversible with `resumeSubscription` |
   | Money back on one payment | `refundTransaction` — `POST /transactions/{id}/refund` | Refunds through the gateway; leaves the subscription running |
   | Money back **and** stop billing | `refundTransactionAndCancelSubscription` — `POST /transactions/{id}/refund_and_cancel` | Both, in one call |

   Prefer `refundTransactionAndCancelSubscription` over calling refund and cancel separately —
   one call is one failure surface instead of two, and there is no transaction wrapper to protect
   you if the second call fails.

   Prefer `suspendSubscription` over `cancelSubscription` whenever the member may return: cancel
   has no documented undo, suspend has `resumeSubscription`.

4. **Confirm.** `getSubscription` — `GET /subscriptions/{id}` and re-read
   `GET /transactions?search[member]=<id>`. Confirm the status changed and the refund appears
   before reporting success. Do not infer success from a 200 alone on a retry.

## Do not use delete

`deleteSubscription`, `deleteTransaction` and `deleteMember` exist but destroy the record rather
than reversing it — they erase the billing history a cancellation needs to leave behind.
MemberPress's own documentation marks member deletion "USE WITH CAUTION!". Reserve deletes for
data-erasure requests, never for cancellations.

## Errors

`401` — bad key or the user lacks `remove_users`. `404` — the id does not exist, or the
Developer Tools add-on is not active. `500` — a failure inside the customer's own WordPress
install; there is no vendor status page to check. Full catalog:
`errors/memberpress-error-codes.yml`.
