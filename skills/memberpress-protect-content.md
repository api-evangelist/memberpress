---
name: memberpress-protect-content
description: Put MemberPress content behind a paywall — create the membership, wire a Smart Rule
  that grants it access to specific content, and optionally drip or expire that access.
api: memberpress:developer-tools-rest-api
generated: '2026-08-12'
method: generated
source: openapi/memberpress-developer-tools-openapi.yml
operations:
- listMemberships
- createMembership
- listRules
- createRule
- updateRule
- getRule
- createGroup
- createCoupon
---

# Protect content with a membership and a Smart Rule

In MemberPress the membership is the *product* and the rule is the *lock*. Creating a membership
protects nothing on its own — the rule is what binds an entitlement to content.

## Steps

1. **Reuse or create the membership.** Check first with `listMemberships` —
   `GET /memberships?search[title]=<name>`. If absent, `createMembership` — `POST /memberships`
   with `{"title": ...}` plus pricing: `price`, `period`, `period_type`
   (`days`/`weeks`/`months`/`years`), and trial fields `trial`, `trial_days`, `trial_amount` if
   offering one. Use `limit_cycles` + `limit_cycles_num` for a fixed-term plan.

2. **Check for an existing rule on the same content.** `listRules` — `GET /rules`. Two rules over
   the same content stack rather than replace, which is a common cause of "why can they still see
   it". If one exists, prefer `updateRule` — `PUT /rules/{id}` — over creating a second.

3. **Create the rule.** `createRule` — `POST /rules` with:
   - `title` (required)
   - `rule_type`, `content_type`, `content_id` — what is being protected
   - `memberships` — the array of membership ids granted access. **This array is the grant.** A
     rule with an empty `memberships` array locks the content away from everyone.
   - `unauth_message_type`, `unauth_message`, `unauth_excerpt_type`, `unauth_excerpt_size`,
     `unauth_login` — what a non-member sees

4. **Add dripping, if the content should unlock over time.** On the same rule set
   `drip_enabled: true` with `drip_amount`, `drip_unit`, and either `drip_after` (an event the
   delay is measured from) or `drip_after_fixed` (an absolute date).

5. **Add expiration, if access should lapse.** `expires_enabled: true` with `expires_amount`,
   `expires_unit`, and `expires_after` or `expires_after_fixed`.

6. **Verify.** `getRule` — `GET /rules/{id}` and confirm `memberships` contains the id you
   intended. Then confirm from the member side: `GET /members/{id}` and look at
   `active_memberships`.

## Packaging and promotion

- **Group several memberships** into one pricing page or upgrade path with `createGroup` —
  `POST /groups` (`title`, `is_upgrade_path`, `upgrade_path_text`, `pricing_display`). Then set
  `group_id` on each membership.
- **Discount it** with `createCoupon` — `POST /coupons` (`code`, `discount_type`,
  `discount_amount`, `valid_date`, `expiration_date`, `usage_amount`, and a `memberships` array
  limiting where it applies).

## Known gaps to plan around

MemberPress does not publish the allowed values for `rule_type`, `content_type`, `period_type`,
`discount_type` or `pricing_display`. Read an existing membership or rule back with a GET and
copy the values it returns rather than guessing — this is the workaround MemberPress itself
documents in place of the `/membership_options` endpoint, which is absent from many
installations. See `data-model/memberpress-data-model.yml`.
