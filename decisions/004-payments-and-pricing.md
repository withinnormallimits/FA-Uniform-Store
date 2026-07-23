# 004 — Payments: Shopify Payments, all-in pricing, exchange-first refunds

**Decision:** Use Shopify Payments at standard rates, bake processing costs into item prices with no checkout-revealed fees or surcharges, and make exchanges/store credit the default remedy instead of refunds.

**Alternatives considered:**
- PayPal charity rate (1.99% + 49¢) — REFUTED in review: applies to donations only, not merchandise sales.
- Stripe nonprofit rate — confirmed unavailable (requires >80% donation volume).
- Card surcharging / convenience fees — banned in CT/MA/ME, capped by Visa, prohibited on debit, and the MySchoolBucks $18.25M class action shows late-revealed fees are a litigation magnet.
- Third-party gateway on Shopify — adds a 2% penalty on Basic.
- FACTS-style bill-to-family-account — deferred; entangles store orders with tuition delinquency (Lane H) and requires the school's tuition system.

**Why this won:** Verification killed every nonprofit discount path, so standard rates are the floor everywhere and Shopify Payments avoids the gateway penalty while enabling express wallets; all-in pricing is the only fee posture that is legal in every state and immune to the MySchoolBucks failure mode; exchange-first policy responds to the verified fact that no processor returns fees on refunds.

**Reverse if:** The school adopts FACTS/TADS incidental billing and wants store charges on family accounts (revisit with a current-account-only rule), or a processor introduces a genuine nonprofit merchandise rate.
