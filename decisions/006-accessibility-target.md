# 006 — Accessibility: build to WCAG 2.2 AA despite the ADA exemption

**Decision:** Build and test the store to WCAG 2.2 AA (16px+ text, 24px minimum/44px preferred tap targets, plain language, no overlay widgets) even though the ADA Title III religious-entity exemption likely applies.

**Alternatives considered:**
- Rely on the Title III exemption and skip accessibility work — verified legally available, but only pays off after litigation and fails Section 504 if the school takes federal funds.
- Install an accessibility overlay widget — overlay-equipped sites are increasingly sued (1,416 in 2025); not a defense.

**Why this won:** The exemption is a litigation defense, not a design strategy: Section 504 (federal funds), state laws like California's Unruh Act, a mostly-mobile parent base with wide age range, and the school's mission all point the same direction, and AA compliance is nearly free at design time on a mainstream theme.

**Reverse if:** Nothing foreseeable — this is a one-way-door-cheap decision.
