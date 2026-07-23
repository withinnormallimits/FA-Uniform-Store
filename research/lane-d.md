# Lane D — Money

Payment processing, tax, and fraud research for a small US private Christian school's online uniform store. Researched July 2026. All rates are US-domestic unless noted. Items marked **[vendor]** are vendor marketing/blog content, not official docs; **[stale]** = source or event older than ~18 months (verify before relying).

---

## 1. Processor fees (online card-not-present, US)

| Processor | Online card rate | ACH | Monthly fee | Notes |
|---|---|---|---|---|
| Stripe | 2.9% + $0.30 | 0.8%, $5 cap | $0 | +1.5% intl cards, +1% currency conversion |
| Square (Free plan) | ~2.9–3.3% + $0.30 (see below) | 1% via invoice, $1 min | $0 | Free plan online rate reported at 3.3% + $0.30 in 2026; 2.9% + $0.30 on paid plans — verify in dashboard |
| PayPal (std business) | ~2.89–3.49% + $0.49 depending on product (PayPal Checkout vs. card fields) | — | $0 | Fixed fee is $0.49, higher than Stripe/Square's $0.30 — hurts on small orders |
| Shopify Payments (Basic) | 2.9% + $0.30 online | — | Basic plan subscription required (~$29–39/mo) | 3.5% + $0.30 for Amex/business cards on Basic; using a third-party gateway instead of Shopify Payments adds a penalty fee |

- Stripe standard 2.9% + $0.30; dispute fee $15; ACH 0.8% capped at $5. Official: https://stripe.com/pricing (page blocks bots; rates corroborated at https://checkoutpage.com/blog/stripe-processing-fees **[vendor]** and https://www.swipesum.com/insights/guide-to-stripe-fees-rates-for-2025 **[vendor]**).
- Square fee schedule: https://squareup.com/help/us/en/article/5068-what-are-square-s-fees (official). 2026 plan-tier reporting (Free plan online 3.3% + $0.30 vs. 2.9% + $0.30 on Plus/Premium): https://www.posusa.com/square-fees-pricing/ **[vendor]** — conflicting third-party numbers, confirm current rate in Square dashboard.
- Square Invoices ACH: 1%, $1 minimum: https://squareup.com/us/en/invoices/pricing and https://squareup.com/us/en/payments/ach-payments (official). Recording cash/check payments is free.
- PayPal merchant fee table (official, bot-blocked but canonical): https://www.paypal.com/us/business/paypal-business-fees
- Shopify Payments rates by plan/card type (official): https://help.shopify.com/en/manual/payments/shopify-payments/transactions/credit-card-rates — Basic 2.9% + $0.30 online; Grow 2.7%; Advanced 2.5%; Amex/business cards 3.5% + $0.30 on Basic.
- Remember Shopify's platform subscription is a real cost on tiny volume: at ~$35/mo that's $420/yr before any processing — often more than total processing fees for a small uniform store.

### School-oriented processors
- **Vanco** (churches/schools): Grow plan $0/mo, cards 2.9% + $0.45, ACH 1% + $0.45; Thrive $54/mo, cards 2.65% + $0.39, ACH 0.9% + $0.39; Amex 3.99%; chargeback $25; PCI non-compliance $23.95/mo. Official pricing: https://www.vancopayments.com/egiving/pricing; fee detail roundup: https://www.nerdwallet.com/business/software/learn/vanco-payment-solutions **[vendor]**. Worse than Stripe/Square for card sales; only compelling if the school already uses Vanco for giving.
- **FACTS** (tuition management): passes a ~2.95% convenience fee to families for cards; ACH free to families; $25 returned-payment fee. It's built for tuition/incidental billing, not a storefront: https://factsmgt.com/features/accounting-billing-payments/ (official, marketing) and school-published FACTS FAQs, e.g. https://resources.finalsite.net/images/v1612361373/divinechildhighschoolorg/kp3wscf0okdvnumgvk8e/FACTSpayement_21-22.pdf **[stale, 2021 school handout — fee % may differ today]**. If the school already bills incidentals through FACTS, uniforms could ride that rail with zero card cost to the school.
- **Blackbaud Merchant Services**: contract-specific pricing, monthly minimums and PCI/chargeback fees possible; not published: https://www.blackbaud.com/info/bbip/nonprofit-credit-card-processing-faqs (official, marketing). Overkill unless the school is already a Blackbaud shop.

---

## 2. Nonprofit status: what it actually gets you

- **Stripe nonprofit discount exists but likely does NOT apply here**: discounted rate (~2.2% + $0.30, by application) requires 501(c)(3) proof AND ≥80% of Stripe volume being tax-deductible **donations**. Uniform sales are commerce, not donations — a uniform store would fail the 80% test unless run on a separate account from a donation account. Official: https://support.stripe.com/questions/fee-discount-for-nonprofit-organizations; explainers: https://www.zeffy.com/blog/stripe-for-nonprofits **[vendor]**, https://www.whitelabel.ai/blog/stripe-nonprofit-discount **[vendor]**.
- **PayPal charity rate 1.99% + $0.49** for confirmed 501(c)(3)s (application + pre-approval required). Official fee page: https://www.paypal.com/us/business/paypal-business-fees; explainer: https://www.zeffy.com/blog/paypal-donation-fees-for-nonprofits **[vendor]**. Important: PayPal's charity rate historically applies to the org's PayPal transactions broadly (not donation-only like Stripe), which can make PayPal the cheapest card option for a 501(c)(3) store on mid-size orders ($50 uniform order: PayPal charity ≈ $1.49 vs. Stripe ≈ $1.75). Confirm scope at application — "subject to eligibility and pre-approval."
- **Square has no published nonprofit rate** (same rates for nonprofits): https://squareup.com/help/us/en/article/5068-what-are-square-s-fees.
- **501(c)(3) ≠ sales tax exemption on your sales** (see §3) and **≠ immunity from income tax on store profits** (UBIT):
  - UBIT basics: income from a trade/business, regularly carried on, not substantially related to exempt purpose is taxable (Form 990-T). IRS Pub 598: https://www.irs.gov/publications/p598.
  - **Convenience exception** (IRC 513(a)(2)): a business run by a 501(c)(3) school "primarily for the convenience of its members, students..." is excluded from UBIT — the classic example is a school cafeteria/bookstore. IRS: https://www.irs.gov/charities-non-profits/charitable-organizations/unrelated-business-income-tax-exceptions-and-exclusions. A required-uniform store selling to enrolled students fits squarely; also arguably "substantially related" since uniforms implement school policy.
  - Caveat: some university tax offices note the IRS position that the convenience exception is shakier for items with useful life >1 year sold to the general public (e.g., https://taxation.unm.edu/tax-ubit.html). Selling only to current families keeps this clean; selling spirit wear to the general public is where UBIT risk creeps in.

---

## 3. Sales tax (the trap: exemption on purchases ≠ exemption on sales)

- **State-by-state; 501(c)(3) does not automatically confer any sales tax exemption.** Overview: https://www.salestaxinstitute.com/resources/which-organizations-are-exempt-from-sales-tax; state matrix: https://wiss.com/state-by-state-nonprofit-sales-tax-exemptions/ **[vendor]**.
- A nonprofit's exemption certificate usually covers what it **buys** for exempt purposes. When it **sells** taxable goods (uniforms = tangible personal property), most states require it to register and collect sales tax unless a specific exemption applies. Examples of the nuance:
  - **Texas**: nonprofit/educational orgs' purchases can be exempt, but their sales are generally taxable except two one-day tax-free sale days per year: https://comptroller.texas.gov/taxes/publications/96-122.php and https://comptroller.texas.gov/taxes/exempt/educational.php (official).
  - **Colorado**: sales TO schools broadly exempt; sales BY schools/school orgs only exempt in limited cases and not always from local taxes: https://tax.colorado.gov/sales-use-tax-topics-school-exemptions (official).
  - **Utah**: sales of required school uniforms sold BY the school are exempt; same uniform from an outside seller is taxable: https://tax.utah.gov/forms-pubs/pub-35/ (official) — shows how school-seller status can matter.
  - **Minnesota**: clothing is exempt statewide, so uniform sales are not taxable there regardless: https://www.revenue.state.mn.us/sites/default/files/2024-06/fs111.pdf (official).
- **Occasional/isolated sale exemptions** exist in many states but usually assume infrequent sales — a year-round online store typically does NOT qualify (Texas's version is explicitly limited to two one-day sales/year, above).
- **Clothing-exempt states**: MN (no cap), PA and NJ (most clothing exempt) — if the school is in one of these, uniform sales are likely non-taxable as clothing. Guides: https://www.taxjar.com/sales-tax/sales-tax-on-clothing **[vendor]**, https://www.avalara.com/blog/en/north-america/2020/02/how-to-handle-sales-tax-on-clothing-a--state-by-state-guide.html **[vendor, 2020 — stale, verify]**.
- **Action**: check the school's own state DOR page for (a) nonprofit-sales exemption, (b) school-fundraiser/occasional-sale carve-outs, (c) clothing taxability. Do not assume the purchase-side exemption certificate covers the store.

---

## 4. Refund mechanics (does the fee come back?)

- **Stripe: NO.** No fee to issue a refund, but the original processing fee is not returned. Official: https://support.stripe.com/questions/understanding-fees-for-refunded-payments and https://docs.stripe.com/refunds.
- **Square: NO** (since April 2023 policy change). Processing fees are kept on full and partial refunds. Official policy-change notice: https://squareup.com/us/en/press/policy-and-pricing-updates; refunds doc: https://squareup.com/help/us/en/article/6116-process-refunds.
- **PayPal: NO** (since 2019 **[stale event, current policy]**): neither the percentage nor the fixed fee is returned on full or partial refunds. Policy-change coverage: https://www.digitaltransactions.net/a-new-refund-policy-from-paypal-will-stop-returning-fees-to-sellers-on-canceled-sales/; current fee page: https://www.paypal.com/us/business/paypal-business-fees.
- **Implication for a uniform store**: sizing exchanges are common. Every refund eats ~3% + $0.30–0.49 of the order with nothing recovered. Prefer **exchanges/store credit over refunds**, publish a fitting guide, and consider a sample-size fitting day to cut refund volume.

---

## 5. Chargebacks & fraud

- **Fees**: Stripe $15/dispute (returned if you win the countered fee under current structure; see https://docs.stripe.com/disputes/how-disputes-work and https://support.stripe.com/questions/dispute-fees-faq). Square: **$0 dispute fee** — Square covers dispute management and doesn't charge per dispute; if you win, funds AND processing fee return: https://squareup.com/help/us/en/article/3882-payment-disputes-walkthrough (official). PayPal: $15 standard dispute fee ($30 high-volume tier at ≥1.5% dispute rate); may be waived/refunded if resolved in your favor or Seller Protection applies: https://www.paypal.com/us/cshelp/article/what-is-the-paypal-dispute-fee-and-why-was-i-charged-one-help349 (official) + https://chargebacks911.com/paypal-chargeback-fee/ **[vendor]**.
- **Process**: bank debits the funds + fee immediately; you submit evidence (receipt, uniform policy, delivery/pickup confirmation, parent's order email); issuer decides in weeks. Stripe: https://docs.stripe.com/disputes/how-disputes-work.
- **Win rates**: vendor stats vary wildly — roughly 20–54% of fought disputes won; fraud-coded disputes much worse (~17–37%) than non-fraud (~57%): https://www.chargeback.io/blog/chargeback-statistics **[vendor]**, https://chargebacks911.com/chargeback-stats/ **[vendor]**. For a school selling to its own families, true chargebacks should be near zero — most "disputes" are a parent not recognizing the statement descriptor. **Set a clear statement descriptor** (e.g., "FA UNIFORM STORE").
- **Card testing**: small nonprofit/school checkout and donation pages are prime targets for validating stolen cards (attacker-controlled amounts, low fraud screening). Mitigations: CAPTCHA on checkout, CVC + ZIP (AVS) verification required, block on failed CVC/ZIP, rate limiting, minimum order amounts, Stripe Radar rules. Official: https://docs.stripe.com/disputes/prevention/card-testing; nonprofit-focused guides: https://donorbox.org/nonprofit-blog/how-to-overcome-credit-card-testing-attacks **[vendor]**, https://www.givelively.org/resources/protect-against-credit-card-testing. Card testing produces waves of $0.30 auth fees and later disputes even on "declined" storms — don't run a checkout without CAPTCHA/Radar-style protection.

---

## 6. Passing fees to customers (surcharging / convenience fees)

- **Network rules**: credit-card surcharge capped at the LOWER of your actual cost or the network cap — Visa cap is 3% (lowered from 4% in April 2023), Mastercard 4%; requires disclosure at entry/checkout and (for Visa) advance notice to your acquirer. **Surcharging debit/prepaid cards is prohibited by network rules regardless of state law** — a problem online since you often can't tell card type without processor tooling. Summary guides: https://www.lawpay.com/about/blog/credit-card-surcharge-rules/ **[vendor]**, https://merchantcostconsulting.com/lower-credit-card-processing-fees/credit-card-surcharge-laws-by-state/ **[vendor, updated 2026]**.
- **State law**: Connecticut, Massachusetts, and Maine ban credit-card surcharges outright; California's and New York's older bans have been narrowed by courts to disclosure regimes (post-*Italian Colors*/*Expressions Hair Design*), and several states (e.g., CO, NJ, NV) cap or condition surcharges — sources conflict on CA's current status, so check the school's own state AG/DOR guidance. Per-state guides: https://staxpayments.com/blog/credit-card-surcharge-guidance/ **[vendor]**, https://allaypay.com/blog/processing/credit-card-surcharge-laws-by-state/ **[vendor]**.
- **"Convenience fee"** is a distinct, narrower concept (flat fee for an alternative payment channel, e.g., what FACTS charges for card vs. free ACH) — networks allow it only in specific configurations; don't DIY-label a surcharge as a convenience fee.
- **Cleanest legal path everywhere**: build ~3% into uniform prices and offer a **cash/check or ACH discount** — cash discounts are legal in all states.

---

## 7. Alternatives / hybrid flows

- **ACH**: Stripe 0.8% capped $5 (https://stripe.com/pricing); Square Invoices 1%, $1 min (https://squareup.com/us/en/invoices/pricing). On a $60 uniform order: ACH ≈ $0.48–0.60 vs. card ≈ $2.04–2.58. ACH downside: disputes/returns take days, R-code returns fee ($5 at Vanco), no instant confirmation.
- **Cash/check at office**: $0 processing. Square (and most platforms) let you record cash/check payments free for inventory/reporting: https://squareup.com/help/us/en/article/5068-what-are-square-s-fees. Hybrid pattern: online order + "pay at front office" option; mark paid on pickup. Costs: staff time, reconciliation, NSF checks (~$25 bank fee), no auto-receipts unless recorded.
- **Ride existing rails**: if the school already uses FACTS incidental billing, adding uniform charges to family accounts means ACH-free (to school) collection and zero new vendor: https://factsmgt.com/features/accounting-billing-payments/ (official, marketing).

---

## Top 5 takeaways

1. **For pure card processing, Stripe/Square/Shopify are all ~2.9% + $0.30; PayPal's approved charity rate (1.99% + $0.49) is likely the cheapest card option for a 501(c)(3)** — Stripe's nonprofit discount won't apply because it requires ≥80% donation volume, which a store fails.
2. **No major processor returns the original processing fee on refunds** (Stripe, Square since 2023, PayPal since 2019). With uniform sizing exchanges, push exchanges/store credit and a fitting guide instead of refunds.
3. **Sales tax exemption on purchases does NOT cover the school's sales.** Uniform sales are generally taxable retail unless the school's state exempts clothing (MN/NJ/PA), has a school-seller uniform carve-out (UT), or a limited fundraiser exemption (TX: two tax-free days/year). Check the state DOR; UBIT is likely a non-issue via the IRS convenience exception if sales are to enrolled students only.
4. **Fee pass-through is legally messy** (CT/MA/ME bans, 3% Visa cap, no surcharging debit). Simplest compliant approach: bake ~3% into prices and discount for cash/check/ACH — ACH costs 0.8–1% capped vs. ~3% for cards.
5. **Protect the checkout from card testing from day one** (CAPTCHA, CVC/ZIP required, rate limits, Radar-style rules) and set a recognizable statement descriptor — friendly-fraud disputes from confused parents plus $15 dispute fees (Stripe/PayPal; Square charges $0) are the main chargeback exposure for a school store.
