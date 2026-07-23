# Action Plan — Parent Uniform & Supply Portal for the School

Planning-only deliverable, July 2026; evidence lives in `/research/`, reasoning in `/decisions/`.

## 1. What we learned

- Late delivery and back-to-school stockouts are the industry's defining failures, so timing is the product.
- Most small schools outsource new uniforms to vendors and keep only used-uniform/spirit sales in-house, because labor is the binding constraint.
- The preorder window (open ~2 weeks, close, bulk-order, batch-distribute) is the proven model that removes inventory risk from small school stores.
- Nonprofit status gets the school almost nothing on payments: no processor discount applies to merchandise, and sales-tax exemption on purchases does not cover sales.
- No processor returns its fee when you refund, which makes casual refunds a permanent leak.
- The ADA religious-entity exemption likely shields the school, but Section 504, state law, and the parent base make WCAG 2.2 AA the right target anyway.
- Everything peaks in a compressed July–August window, exactly when school staffing is thinnest.

## 2. What parents hate

- Uniforms arriving weeks late, including kids starting school without them.
- Contracted vendors being out of stock despite knowing the school's enrollment.
- Wrong sizes compounded by slow shipping and hostile exchange policies.
- No order tracking or status updates, forcing calls to unreachable customer service.
- Fees revealed at the last checkout screen (an $18.25M class-action lesson at MySchoolBucks).
- Refunds issued as expiring gift cards instead of real money.
- School-code lookups and login hoops so confusing that schools publish how-to PDFs.

## 3. What the school staff will hate

- Being the fulfillment warehouse: unclaimed orders piling up at the front office with no chain of custody.
- Password resets and "I can't log in" calls, which dominate small-org support load.
- Cash handling and refunds without controls, a documented theft and audit risk.
- The whole store depending on one person who might leave in June.
- Manual workarounds ("just bill my account") that create untracked debt.
- A July–August workload spike landing on summer skeleton staffing.

## 4. Recommended UI/UX

- Mobile-first storefront on a mainstream accessible theme, tested on real phones.
- Guest checkout always; optional passwordless account (email code) for saved sizes and reorders.
- One parent account with per-child profiles; one payment for all siblings.
- Apple Pay/Google Pay buttons above the card form; address autocomplete; ≤8 form fields.
- Catalog organized by grade band and gender per the dress code, with plain-language size/fit guidance and a printable fit chart.
- Product pages show real-time stock, keep sold-out pages visible with "notify me," and state order-by cutoff dates prominently.
- Status emails at ordered, ready-for-pickup, and picked-up; SMS for pickup notices if budget allows.
- All-in prices with no checkout-revealed fees, and a clear statement descriptor like "SCHOOL UNIFORM STORE."
- 16px+ text, 44px primary tap targets, ~6th-grade reading level, fast on cellular.

## 5. Edge cases

- New/mid-year family not in any roster: no roster gate exists, so they shop like everyone else on day one.
- Divorced parents, duplicate accounts: notifications are per-account, and email changes are a verified front-office action.
- Pickup by the "wrong" adult: policy states the order confirmation (not identity) authorizes pickup, logged by signature/scan.
- Financial-aid family: subsidy arrives as a discreet pre-issued store credit, invisible on receipts and pickup sheets.
- Order never picked up: aging policy reminds at 2 and 4 weeks, then converts to shipment, credit, or donation per published terms.
- Duplicate double-tap orders: same-day duplicate orders to one address are flagged for review before fulfillment.
- Wrong child on an embroidered item: the review screen restates child name and size before payment on personalized goods.
- Family withdraws with an open order: published policy is refund to store credit, offset only by explicit business-office decision.
- Mid-year dress-code change: existing purchases are grandfathered for the school year and a swap window is announced.
- Weather closure during pickup week: pickup days carry built-in slack and a broadcast reschedule channel.
- Out-of-stock ≠ discipline: a published grace policy protects students when the store causes the uniform gap.

## 6. Red team findings

- August access lockout: no roster gate, plus a same-day manual path for anything the office must grant.
- Order emails land in spam: authenticate the school domain (SPF/DKIM/DMARC) before launch and test deliverability to Gmail/Yahoo/Outlook.
- Card-testing attack suspends the account mid-peak: CAPTCHA, CVC+ZIP required, velocity limits, and minimum order enabled from day one.
- Coordinator leaves or gets sick: two admins, a one-page runbook, and credentials in school-controlled storage, verified each spring.
- Pickup chaos at volume: staggered published windows, pre-bagged orders, and a scan/signature at handoff.
- Oversold last unit in the rush: written apologize-refund-or-backorder script plus buffer stock on high-velocity sizes.
- Refunds erode margin: exchange-first policy with store credit default and honest size guidance up front.
- Phishing rides the launch: one canonical URL announced repeatedly, and a standing rule that the school never emails payment links.
- Embroidery misses the first day: preorder windows close 6+ weeks before school starts, with the buffer stated publicly.
- Dead decorated stock: logo items are preorder-only until sell-through data proves otherwise.

## 7. Options

- **Option A — Shopify Basic store (recommended):** pros: best verified fit for inventory, gating, pickup, and preorders with platform-managed security; cons: ~$350/yr forever and it will never do tuition/forms; cost: ~$350–470/yr plus 2.9% + 30¢ per sale.
- **Option B — Square Online free tier:** pros: $0 subscription and a growth path into front-office POS/invoices; cons: 3.3% + 30¢ online, no shop-page password gating, no back-in-stock alerts, preorders require the $49/mo tier; cost: $0–588/yr plus processing.
- **Option C — Outsource new uniforms to a vendor storefront and keep only used/spirit sales in-house:** pros: near-zero school labor and a small rebate; cons: parents inherit the delay/stockout/exchange misery this project exists to fix, and the school loses control of the experience; cost: $0 direct, paid for in parent experience.

## 8. Recommendation

- Build Option A: Shopify Basic, configured per decisions 001–007, with Option C's vendor channel retained only as an optional overflow for odd sizes.

## 9. Foundation

- The entire system stands on a hosted commerce platform (Shopify Basic) plus school-owned, authenticated email and domain — hosted because a school with no IT staff must rent uptime, security, and PCI compliance rather than own them, and email/domain because every order, notification, and login in the design depends on messages that arrive and an address the school controls.

## 10. Disputed or unverified

- PayPal's charity rate for merchandise: REFUTED — donations only, so no processor discount applies to the store.
- MySchoolBucks "CFPB action": CORRECTED — it was a private class action (*Story v. Heartland*, $18.25M, final approval Sept 2025).
- Shopify oversell frequency via external gateways: UNVERIFIED — Shopify holds a short reservation at payment, and community oversell reports remain anecdotal.
- Exact Ecwid post-March-2026 prices: UNVERIFIED but not recommendation-critical.
- Lands' End logo-return policy wording: confirmed via secondary sources only; spot-check before quoting to parents.
- Precise Baymard sub-statistics (26% forced-account abandonment): relayed via roundups; the practice conclusions don't depend on the exact figure.
- Sales-tax treatment in the school's specific state: undetermined until the state is confirmed (see open questions).

## 11. Open questions

- What state is the school in, for sales tax, surcharge law, and any state accessibility exposure?
- Does the school currently use FACTS, TADS, or another tuition system we should integrate with or deliberately avoid?
- Does the school receive any federal funds (lunch program, E-Rate), which would trigger Section 504?
- Is there an existing uniform vendor contract or exclusivity agreement we must work around?
- Who are the two named people (owner + backup) who will run the store, and what hours can they commit in July–August?
- What is the approximate family count and expected order volume, to sanity-check costs and pickup logistics?
- Does the school already own a domain and Google Workspace/Microsoft 365 tenant we can send email from?
- Is embroidery done by a local decorator today, and what are their real minimums and summer lead times?
- What is the financial-aid mechanism today, so subsidy-as-store-credit can match it discreetly?
- Do we want spirit wear sold to the broader community (grandparents, alumni), which affects gating and tax?
