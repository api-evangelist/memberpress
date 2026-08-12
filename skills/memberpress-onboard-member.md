---
name: memberpress-onboard-member
description: Create a MemberPress member and grant them access to a membership by recording the
  purchase transaction, then verify the entitlement landed.
api: memberpress:developer-tools-rest-api
generated: '2026-08-12'
method: generated
source: openapi/memberpress-developer-tools-openapi.yml
operations:
- verifyAuthentication
- listMemberships
- listMembers
- createMember
- createTransaction
- getMember
---

# Onboard a member onto a membership

Grants a person access to a MemberPress membership by creating the member and the transaction
that entitles them. Use this when a purchase happened somewhere other than the MemberPress
checkout — an offline sale, a migration, a comp'd account.

## Before you start

- Base URL is the customer's own site: `https://{site}/wp-json/mp/v1`. MemberPress is
  self-hosted; there is no vendor host.
- Send the Developer Tools key in the `MEMBERPRESS-API-KEY` header, or as a **bare** value in
  `Authorization`. Do **not** write `Bearer <key>` — it will fail.
- The Developer Tools add-on is a Scale-plan feature. A 404 on every route usually means the
  add-on is not active on this site, not that the site is down.

## Steps

1. **Confirm the credential works.** `verifyAuthentication` — `GET /me`. A 200 returns
   `{"success": true, "data": {"username": "..."}}`. A 401 means the key is wrong or the
   WordPress user lacks the `remove_users` capability.

2. **Find the membership to grant.** `listMemberships` — `GET /memberships?search[title]=<name>`.
   Take the integer `id`. Memberships are the products; do not confuse the membership id with a
   group id.

3. **Check the person is not already a member.** `listMembers` —
   `GET /members?search[email]=<email>`. If a member comes back, skip step 4 and reuse their id.
   **Do this every time.** There is no idempotency key on this API, so a duplicate run without
   this check creates a duplicate WordPress user.

4. **Create the member.** `createMember` — `POST /members` with at minimum
   `{"email": ..., "username": ...}`. Optional: `first_name`, `last_name`, `address1`,
   `address2`, `city`, `state`, `zip`, `country`, `phone`, `send_password_email`. Omit
   `password` to have MemberPress generate one.

5. **Record the entitling transaction.** `createTransaction` — `POST /transactions` with
   `{"member": <member id>, "membership": <membership id>}` plus `amount`, `status`, `gateway`,
   `expires_at` and `send_welcome_email` as appropriate. This is the step that grants access;
   creating the member alone entitles them to nothing.

   > **No safe retry.** If this call times out, do **not** repeat it. Run
   > `GET /transactions?search[member]=<id>&search[membership]=<id>` first and only re-post if
   > nothing landed. A duplicate here is a duplicate financial record.

6. **Verify the entitlement.** `getMember` — `GET /members/{id}` and confirm the membership id
   appears in the member's `active_memberships` array. That array is the authoritative view of
   what a member can access.

## For a recurring arrangement

Use `createSubscription` — `POST /subscriptions` with `member`, `membership`, `period`,
`period_type` and `gateway` — instead of, or in addition to, the one-off transaction. The same
no-idempotency warning applies: check `GET /subscriptions?search[member]=<id>` before retrying.

## Errors

| Status | Meaning | Do |
|---|---|---|
| 401 | Key missing/invalid, or user lacks `remove_users` | Fix the header; use an admin account |
| 400 | `rest_missing_callback_param` | Supply `email`+`username`, or `member`+`membership` |
| 404 | `rest_no_route` | Developer Tools add-on is not active on this site |
| 500 | PHP/DB failure on the customer's server | Site owner's to diagnose; no vendor status page |

Full catalog: `errors/memberpress-error-codes.yml`.
