# FA Uniform Store — Planning Repository

**This repository is planning-only. It contains no code, no application scaffolding, and no build artifacts — only research and decision documents.** The client is referred to throughout as "the School"; no school-identifying or family information is committed here.

Produced July 2026 by a research-and-planning session: eight parallel research lanes, an adversarial verification pass, a red-team pass, and decision records, culminating in a validated action plan.

## Read first

- [`ACTION_PLAN.md`](ACTION_PLAN.md) — the validated plan: findings, UX, edge cases, red-team mitigations, options, and the recommendation (Shopify Basic, preorder-first, pickup-default).

## Research (`/research/`)

- [`lane-a.md`](research/lane-a.md) — Parent pain: real complaints about uniform/school-store vendors and portals.
- [`lane-b.md`](research/lane-b.md) — School operations: how small private/parochial schools actually run these stores.
- [`lane-c.md`](research/lane-c.md) — Platform options: hosted e-commerce, site builders, school vendors, custom builds, with costs.
- [`lane-d.md`](research/lane-d.md) — Money: processor fees, nonprofit reality, sales tax, refunds, chargebacks, fraud.
- [`lane-e.md`](research/lane-e.md) — UX & accessibility: mobile checkout evidence and US accessibility law.
- [`lane-f.md`](research/lane-f.md) — Uniform domain: sizing, returns, embroidery, catalog restrictions, SKUs, used uniforms.
- [`lane-g.md`](research/lane-g.md) — Inventory reality: stock handling, preorders, reservation, pickup vs shipping, seasonal spikes.
- [`lane-h.md`](research/lane-h.md) — Edge cases: adversarial cross-cutting scenarios the other lanes missed.
- [`review.md`](research/review.md) — Phase 2 adversarial review: verifications, refutations, contradictions, and UNVERIFIED items.
- [`redteam.md`](research/redteam.md) — Phase 3 red team: pre-mortem, operational, adversarial, load, and financial attacks with mitigations.

## Decisions (`/decisions/`)

- [`001-platform-shopify-basic.md`](decisions/001-platform-shopify-basic.md) — Platform: Shopify Basic.
- [`002-preorder-first-inventory.md`](decisions/002-preorder-first-inventory.md) — Inventory: preorder-first hybrid.
- [`003-pickup-default-fulfillment.md`](decisions/003-pickup-default-fulfillment.md) — Fulfillment: free front-office pickup default.
- [`004-payments-and-pricing.md`](decisions/004-payments-and-pricing.md) — Payments: Shopify Payments, all-in pricing, exchange-first refunds.
- [`005-access-model.md`](decisions/005-access-model.md) — Access: light gate, guest checkout, passwordless accounts, no roster sync.
- [`006-accessibility-target.md`](decisions/006-accessibility-target.md) — Accessibility: WCAG 2.2 AA regardless of exemption.
- [`007-operations-and-expansion.md`](decisions/007-operations-and-expansion.md) — Operations: role-based ownership, discreet aid, anti-lock-in posture.

## Ground rules for this repo

- Keep the repository private.
- Never commit the School's real name, address, staff or family names, or student information.
- Never commit API keys, vendor account details, or confidential pricing quotes.
- Answer the open questions in `ACTION_PLAN.md` §11 before starting any build session.
