# 007 — Operations: role-based ownership, discreet aid, and an anti-lock-in posture

**Decision:** Run the store as a documented role (front office + one trained backup, two admins, a one-page runbook, diocesan-style money controls), apply financial-aid subsidies off-portal as manually issued store credit/gift cards, and keep the school-owned domain and email authentication (SPF/DKIM/DMARC) as the permanent parent-facing identity.

**Alternatives considered:**
- Single volunteer coordinator owns everything — the documented default and the documented failure mode (Lane B).
- Visible discount codes for aid families — outs them at checkout and on pickup sheets; NAIS evidence says subsidy must be invisible and proactive.
- Use the platform's subdomain and email sending as-is — ties parent habits and deliverability reputation to the platform, boxing in the later tuition/forms/events expansion.

**Why this won:** Coordinator departure and knowledge loss is the highest-probability operational failure and a binder-plus-backup is its only known defense; discreet gift-card subsidy keeps aid status out of every UI, receipt, and pickup artifact; owning domain and email means the store, and anything added later (tuition, forms, events), lives at an address the school controls no matter which vendor sits behind it.

**Reverse if:** The school hires dedicated ops/IT staff (role documentation can relax), or a unified school-management platform later absorbs commerce, tuition, and communication under the school's domain.
