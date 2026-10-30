# MemberPress

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

MemberPress is a WordPress membership, course and subscription-commerce plugin built by Caseproof. It turns a self-hosted WordPress site into a paid membership business — content protection through Smart Rules, memberships and groups as products, coupons, transactions, recurring subscriptions across Stripe, PayPal, Square and Authorize.net, courses and quizzes, ClubSuite communities and CoachKit coaching. Its developer surface is the Developer Tools add-on, which exposes a REST API under the WordPress namespace /wp-json/mp/v1 on the site owner's own installation, plus a webhook subscription surface for fourteen membership and billing events. The AI Foundation add-on ships a WordPress MCP server that lets Claude, Cursor and VS Code read and act on membership data directly.

**Areas:** Company · Membership · Subscription · WordPress · Payments · E-Commerce · Courses · Content Management · Webhook · MCP

## MemberPress on APIs.io

Everything profiled for MemberPress is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/memberpress/](https://apis.io/providers/memberpress/)** — or go straight to one of the APIs or properties below.

### APIs (12)

- [MemberPress AI Foundation MCP Server](https://apis.io/apis/memberpress/ai-foundation-mcp/) — WordPress MCP server shipped by the MemberPress AI Foundation add-on. It exposes membership, subscription, transaction, coupon, access-rule and reporting…
- [MemberPress Authentication API](https://apis.io/apis/memberpress/memberpress-authentication-api/) — Verify the API key and inspect permissions.
- [MemberPress Coupons API](https://apis.io/apis/memberpress/memberpress-coupons-api/) — Discount codes applied at checkout.
- [MemberPress Events API](https://apis.io/apis/memberpress/memberpress-events-api/) — The MemberPress event log.
- [MemberPress Groups API](https://apis.io/apis/memberpress/memberpress-groups-api/) — Groups of memberships, used for pricing pages and upgrade paths.
- [MemberPress Members API](https://apis.io/apis/memberpress/memberpress-members-api/) — Members are the WordPress users MemberPress tracks.
- [MemberPress Memberships API](https://apis.io/apis/memberpress/memberpress-memberships-api/) — Memberships are the products members buy.
- [MemberPress Reminders API](https://apis.io/apis/memberpress/memberpress-reminders-api/) — Scheduled member emails triggered by events.
- [MemberPress Rules API](https://apis.io/apis/memberpress/memberpress-rules-api/) — Smart Rules that protect content and drip access.
- [MemberPress Subscriptions API](https://apis.io/apis/memberpress/memberpress-subscriptions-api/) — Recurring billing agreements.
- [MemberPress Transactions API](https://apis.io/apis/memberpress/memberpress-transactions-api/) — One-time and recurring payment records.
- [MemberPress Webhooks API](https://apis.io/apis/memberpress/memberpress-webhooks-api/) — Subscribe callback URLs to MemberPress events.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Memberpress Webhooks](https://apis.io/asyncapis/memberpress/memberpress-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [MemberPress AI Foundation](https://apis.io/servers/memberpress/memberpress-ai-foundation/)

#### Collections (1)

Postman and Open Collection request collections.

- [MemberPress Developer Tools REST API](https://apis.io/collections/memberpress/open-memberpress-developer-tools/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Memberpress Developer Tools Overlay](https://apis.io/overlays/memberpress/memberpress-developer-tools-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Memberpress Authentication](https://apis.io/security/memberpress/memberpress-authentication/)
- [Memberpress Domain Security](https://apis.io/security/memberpress/memberpress-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Memberpress Plans Pricing](https://apis.io/plans/memberpress/memberpress-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Memberpress Rate Limits](https://apis.io/rate-limits/memberpress/memberpress-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://memberpress.com/)
- [Documentation](https://memberpress.com/docs/)
- [Getting started](https://memberpress.com/docs/overview-of-using-the-developer-tools/)
- [API reference](https://github.com/caseproof/memberpress-rest-api-documentation#core-resources-and-endpoints)
- [Pricing](https://memberpress.com/pricing/)
- [Sign up](https://memberpress.com/pricing/)
- [Support](https://memberpress.com/support/)
- [Changelog](https://memberpress.com/changelog/)
- [Blog](https://memberpress.com/blog/)
- [Terms of service](https://memberpress.com/terms/)
- [Privacy policy](https://memberpress.com/privacy/)
- [GitHub](https://github.com/caseproof)

## API Evangelist rating

**Kin Score 46.4** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 71.7 |
| Contract quality | 25.0 |
| Contract governance | 4.5 |
| Operational transparency | 26.3 |
| Developer ergonomics | 70.4 |
| Access clarity | 76.3 |

**Agent readiness 37.7** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | documented (partial credit) |
| MCP Server | documented (partial credit) |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | paginated |
| Operation Distinctiveness | distinct |

**Regulatory alignment 22.3** — Payments

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/memberpress/](https://apis.io/providers/memberpress/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for MemberPress: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/memberpress/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
