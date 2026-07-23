# Red Team — Attacking the Plan Before It Exists

Written July 2026, after Phase 1 research and during Phase 2 verification. The target: a parent-facing portal on a hosted commerce platform, school-managed inventory, preorder windows for decorated goods, front-office pickup as default fulfillment, run by limited school staff. No code exists; these attacks are against the design and the operations.

---

## 1. Pre-mortem: it is the first week of August and the portal has failed publicly

Each bullet is a plausible obituary, with the evidence lane that makes it plausible.

- **"Nobody could log in."** The store was gated behind roster-matched accounts; new and re-enrolling families — the heaviest buyers — weren't in the roster export yet, and the one person who could add them was on summer break. (Lane H #2, Lane B staffing)
- **"The emails never arrived."** Order confirmations and pickup notices went out from a new unauthenticated domain and landed in spam; parents assumed orders failed and ordered again or charged back. (Lane H #1 — deliverability is the top-ranked edge case)
- **"The sizes everyone needed were gone in two days."** Stock-on-hand was bought from last year's guesses with no per-size sell-through data; youth M/L polos sold out August 3 and the restock PO had a 60–90 day lead time. (Lane G lead-time math, Lane A stockout rage)
- **"Two hundred orders, one office fridge-sized closet."** Every order chose free pickup; the front office became a fulfillment warehouse with no bin system, no chain of custody, and volunteer sorters. (Lane B storage reality, Lane H lost-order edge)
- **"The checkout was charging twice."** Slow checkout under load + parents double-tapping Pay = duplicate charges on scarce inventory; refunds ate the processing fees on every one. (Lane H #4, Lane D refund mechanics)
- **"Card testers found us the week we launched."** The new checkout had no CAPTCHA or velocity limits; a card-testing storm triggered processor review and the account was suspended during back-to-school week. (Lane D fraud section, Lane H #7)
- **"The embroidered items missed the first day."** Decorated-to-order lead times double in summer; the preorder window closed too late for the decorator's peak-season queue. (Lane F embroidery seasonality)
- **"A parent posted the store password in a public Facebook group."** The single shared storefront password leaked immediately, making the "parents-only" store public and the school's gating claim embarrassing rather than protective. (Lane H identity/access)
- **"The launch email looked exactly like the phishing email."** A scammer registered a lookalike domain and asked parents to "pay uniform fees"; because the school had just trained parents to click new payment links, several paid. (Lane H phishing, NBOA warning)

## 2. Operational attack: the bus-factor test

- **Single-coordinator dependency is the default failure mode**: volunteer/staff-run school stores degrade to whatever the one coordinator can do, and PTO guidance treats knowledge loss on departure as the expected outcome, not the exception. (Lane B failure modes)
- Attack: the coordinator is out sick during pickup week → nobody else knows the platform admin password, the pickup bin system, or the refund policy. Mitigation: **two named admins minimum, a one-page runbook committed to school records, and platform credentials in the school's password manager, not a personal inbox.**
- Attack: the coordinator leaves in June → August launch has no owner. Mitigation: **the store's owner must be a role (front office + one backup), never a person; the annual cycle (catalog update, preorder window, pickup days) is a documented calendar.**
- Attack: refunds and inventory adjustments are done by the same single person who reconciles the money — the classic small-organization embezzlement setup that diocesan finance manuals explicitly forbid. Mitigation: **two-person rule on refunds over a threshold and monthly reconciliation review by the business office, matching existing diocesan/PTO controls.** (Lane B money handling)

## 3. Adversarial attack: who abuses this

- **Card testers**: small school checkouts are documented targets for validating stolen cards; a storm produces fees, disputes, and possible processor suspension. Mitigation: **CAPTCHA on checkout, require CVC+ZIP, block on mismatch, velocity limits, and a minimum order amount — enabled before launch, not after the first attack.** (Lane D, Lane H — sourced incidents)
- **Non-parents in a semi-private store**: link-and-password gating leaks via forwarded emails; outsiders can buy logo apparel that doubles as school-affiliation identification. Mitigation: **decide explicitly what is public (spirit wear) vs gated (roster-priced/subsidized items); treat the gate as a speed bump, not a security control, and keep anything sensitive (aid pricing) out of the storefront entirely.**
- **Refund/chargeback abuse**: a parent disputes a card charge rather than dealing with the exchange policy; fraud-coded disputes are mostly lost. Mitigation: **clear statement descriptor, pickup signature/scan as evidence, exchange-first policy, and treating any chargeback as a relationship conversation before a dispute response.** (Lane D)
- **Withdrawn or delinquent families**: store access outliving enrollment, or store purchases running up an unpaid family account. Mitigation: **store purchases are card-paid at order time by default; any bill-to-account option requires the account be current.** (Lane H money edges)
- **Account takeover**: parent accounts hold home addresses, children's names and sizes — a stalking-grade bundle; K-12 systems are actively targeted (PowerSchool breach). Mitigation: **passwordless magic-link login (nothing to stuff), no stored child birthdates or student IDs, sizes kept on orders rather than persistent child profiles.** (Lane H data/privacy)

## 4. Load attack: the whole school orders in 48 hours

- Reality check on scale: a small school's "spike" is hundreds of orders, not thousands — **hosted platforms will not fall over; the school's people and processes will.** The load risk is operational, not technical.
- **Inventory race**: add-to-cart reserves nothing, and although Shopify holds a short reservation at payment (verified in Phase 2, reducing the risk Lane G described), oversells via external gateways remain unverified-but-plausible on one-unit-deep sizes. Mitigation: **a written oversell script (apologize + refund or backorder with ETA), and buffer stock on the highest-velocity sizes.** (Lane G, review.md)
- **Pickup crush**: 200 orders ready simultaneously with a two-hour office window. Mitigation: **published pickup days with staggered windows, orders pre-bagged and sorted by family name, and a check-off scan at handoff.**
- **Support crush**: every unclear state (is it ready? did it go through?) becomes a front-office call. Mitigation: **proactive status emails at order, ready, and picked-up states — the single biggest deflector of "where's my order" volume.** (Lane A order-opacity findings)
- **Payout timing**: a compressed sales window means the school fronts vendor POs months before parent money arrives; late-window orders may not clear before the vendor invoice is due. Mitigation: **preorder windows close early enough that parent payments fund the bulk PO.**

## 5. Financial attack: where margin quietly dies

- **Refunds eat ~3% + fixed fee every time** because no processor returns fees; a size-exchange-heavy product line refunded casually can turn a break-even store negative. Mitigation: **exchange-first policy, store credit as the default refund vehicle, and honest size guidance to prevent the exchange in the first place.** (Lane D, F)
- **Shipping is a margin trap**: post-July-2026 USPS rates put single-shirt shipping at $5–8+, often 25%+ of item price; flat "cheap" shipping quietly subsidizes every shipped order. Mitigation: **free pickup as the default, real-cost shipping as the priced exception.** (Lane G — pending verification)
- **Sales tax surprise**: "we're a nonprofit" does not exempt the school's *sales* in most states; discovering this after a season of untaxed sales creates back-tax exposure. Mitigation: **one-time state DOR determination before launch, platform tax settings configured accordingly.** (Lane D)
- **Decorated-goods dead stock**: logo items bought to stock and not sold are unreturnable to the vendor and worthless if the dress code changes. Mitigation: **decorated items sold by preorder window only; stock-on-hand limited to blanks and fast-moving basics.** (Lane F, G)
- **Fee pass-through as legal risk**: surcharging is banned or capped in several states and prohibited on debit; the MySchoolBucks fee litigation shows late-revealed fees are also a reputational/legal trap. Mitigation: **all-in pricing with fees baked in; no checkout-revealed fees, ever.** (Lane D, A)

## Top red-team conclusions

1. The portal's real failure modes are operational (access gating in August, email deliverability, pickup chain of custody, single-coordinator dependency) — not technical scale.
2. Fraud controls (card-testing protection, statement descriptor, pickup evidence) must exist at launch because the attack finds the store, not vice versa.
3. Margin survives only if the store is exchange-first, pickup-first, preorder-first, and all-in-priced.
4. Every gate needs a same-day manual override the front office can execute, or August becomes a lockout story.
5. The store must be run as a documented role with two admins and existing diocesan-style money controls, not as one person's project.
