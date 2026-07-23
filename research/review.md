# Phase 2 — Adversarial Review Log

July 2026. Each significant Phase 1 finding was challenged before acceptance; claims that would change the recommendation were re-verified by independent subagents against the most authoritative reachable sources. Status labels: **CONFIRMED**, **CORRECTED**, **REFUTED**, **UNVERIFIED** (kept visible, not silently dropped).

## Verification results — money and legal (Lane D, A, E, F, G claims)

- **REFUTED — "PayPal's 1.99% + $0.49 charity rate is the cheapest card path for the store."** PayPal's fee schedule ties the charity rate to the *Donations* payment type; merchandise sales take standard rates. Consequence: **nonprofit status yields no meaningful card-rate discount for a store**; processor choice should be driven by platform fit, not nonprofit pricing. (https://www.paypal.com/us/business/paypal-business-fees)
- **CONFIRMED — Stripe's nonprofit discount requires >80% donation volume**, so a school store fails eligibility. (https://support.stripe.com/questions/fee-discount-for-nonprofit-organizations)
- **CORRECTED — the MySchoolBucks $18.25M "junk fee" matter was a private class action, not a CFPB enforcement action**: *Story v. Heartland Payment Systems, LLC* (M.D. Fla. 3:19-cv-724), final approval Sept 2025. Lane A's "CFPB found drip pricing" framing is wrong; the lesson (never reveal fees late in checkout) stands. (https://www.msbfeesettlement.com/)
- **CONFIRMED (with caveats) — USPS July 12, 2026 repricing**: Ground Advantage commercial +~11.8%, sub-1-lb ounce tiers collapsed into the 12–15.999 oz tier for published commercial rates; retail keeps ounce tiers and negotiated rates are unaffected. The pickup-first conclusion stands. (https://support.pirateship.com/en/articles/15453569-july-2026-usps-rate-and-rule-changes)
- **CONFIRMED (secondary only) — Lands' End treats school logos as non-personalization**; logo items returnable 90 days for merchandise credit. landsend.com blocks fetches, so live policy text was not read — spot-check before citing to parents. (https://www.landsend.com/us-returns/ via policy trackers)
- **CONFIRMED — no major processor (Stripe/Square/PayPal) returns the original processing fee on refunds**; exchange-first/store-credit policy is the correct response. (https://docs.stripe.com/refunds)
- **CONFIRMED — Square charges $0 per dispute; Stripe $15 (refunded on win).** (https://www.chargeflow.io/blog/chargeback-fees)
- **CONFIRMED — ADA Title III religious-entity exemption (42 U.S.C. §12187) is broad**, covering all activities of religiously controlled entities including public-facing ones; the WCAG 2.2 AA target is kept anyway on Section 504 (if federal funds), state-law, and mission grounds. (https://uscode.house.gov/view.xhtml?req=granuleid%3AUSC-prelim-title42-section12187)

## Verification results — platforms (Lane C, G claims)

- **CONFIRMED — Shopify Basic $29/mo annual / $39 monthly; 2.9% + $0.30 online (3.5% + $0.30 Amex/business); +2% third-party-gateway penalty.** Official pages bot-blocked; 6+ independent 2026 sources converge. (https://help.shopify.com/en/manual/payments/shopify-payments/transactions/credit-card-rates)
- **CONFIRMED — Shopify's storewide password page exists on all plans** (whole-store gating, one shared password). (https://help.shopify.com/en/manual/online-store/themes/password-page)
- **CONFIRMED (nuance) — Shopify native pre-orders require installing a pre-order app to use deferred purchase options**; charge-later works only with Shopify Payments or PayPal Express and disables Shop Pay/Apple Pay/Google Pay on those items. (https://help.shopify.com/en/manual/products/purchase-options/pre-orders)
- **PARTLY REFUTED — "no reservation window at all" (Lane G).** Add-to-cart holds nothing ("first to pay wins" confirmed), but a 2026 Shopify engineering post documents a short inventory reservation created at payment processing specifically to stop concurrent checkouts claiming the last unit. Oversells via external gateways remain **UNVERIFIED** anecdote. Consequence: oversell risk is lower than Lane G implied but the graceful-oversell script stays as cheap insurance. (https://shopify.engineering/scaling-inventory-reservations)
- **CONFIRMED — Shopify "Ready for pickup" email is automatic and customizable.** (https://help.shopify.com/en/manual/fulfillment/setup/delivery-methods/pickup-in-store)
- **CONFIRMED — Square Online free plan online rate rose to 3.3% + $0.30 on Jan 13, 2026** (2.9% on Plus $49/mo), and shop/category pages cannot be password-protected. Weakens the "Square free tier" option materially. (https://squareup.com/help/us/en/article/7047-password-protection; rates via converging third-party sources)
- **REFUTED — "Wix charges new tiered platform transaction fees (4%/2%)."** Multiple independent 2026 sources agree Wix charges 0% platform fee; the tiered-fee claim traces to a single outlier source. (https://cybernews.com/best-website-builders/wix-review/transaction-fees-explained/)
- **UNVERIFIED — exact Ecwid post-March-2026 prices** (best estimate Venture ~$29–30/mo, Business ~$49/mo annual); repricing itself is official. Not recommendation-critical. (https://support.ecwid.com/hc/en-us/articles/25122701806108)

## Cross-lane contradictions and resolutions

- **Lane B vs Lane A — "outsource to a uniform vendor" vs "vendors are the pain."** Lane B shows most small schools outsource new uniforms; Lane A shows contracted vendors are the top source of parent misery (4–8 week delays, chronic stockouts, hostile exchanges). Resolution: not a factual conflict — outsourcing trades parent experience for staff labor; since this project's stated objective is school-managed inventory, Lane A's evidence defines what the in-house store must do better (real-time stock, fast local exchanges, proactive status), and Lane B's evidence defines the labor guardrails (preorder windows, documented roles) that make in-house survivable.
- **Lane C vs Lane D — Shopify subscription cost framing.** Lane D's "~$35/mo" is Lane C's $29 annual/$39 monthly seen mid-blend; resolved to the verified figures above.
- **Lane E (magic-link login) vs Lane H (shared family email, custody weaponization).** Passwordless login concentrates trust in the email inbox that divorcing households fight over. Resolution: keep passwordless (the friction and support evidence is strong) but make notifications per-account rather than per-student, and treat account-recovery/email-change as a manual, verified front-office action.
- **Lane C (vendor-fulfilled stores "free") vs objective.** SquadLocker/1st Place remove labor but cannot carry school-provided inventory, so they are a complement (spirit wear) not a platform answer.

## Vendor-only claims rejected or downgraded

- "Stockouts push ~69% of shoppers to competitors" (Lane G) — vendor-repeated, unaudited; treated as directional color only.
- Apple Pay "10–15% mobile conversion uplift" and address-autocomplete "30–70% fewer delivery failures" (Lane E) — vendor figures; the underlying practices are kept on Baymard's evidence, the numbers are not relied on.
- SquadLocker "6-month any-reason returns," FlynnO'Hara "up to 10% rebate" — vendor marketing; noted, not load-bearing.
- $70-per-password-reset and 20–50%-of-tickets figures (Lane E) — vendor-relayed order-of-magnitude only.

## Remaining UNVERIFIED items (carried, not dropped)

- Oversell frequency with external payment gateways on Shopify (anecdotal community reports only).
- Exact Ecwid Venture/Business prices post-March-2026.
- Live Lands' End return-policy wording (secondary corroboration only).
- Exact Baymard abandonment sub-percentages (26%/22%) — relayed via a roundup; Baymard's aggregate 70.22% figure is primary.
- Lane A's PTA order-window complaints theme — inferred from store mechanics, weak firsthand sourcing (Lane A flagged this itself).
- MySchoolBucks parent-facing program-fee amounts today (settlement-era figures may not reflect current fees).
