# 01 — Scope and Status (G0)

## Status

- Private repo `goodspeed-apps/rebate-control` (created by the owner) holds the Opportunity Brief and this package only. No application code.
- Analysis is desk-based: governance documents, the brief, public web sources (assets/competitive-evidence.md), and Claude's engineering estimates. **No real customer agreements, exports or statements were examined.** That is the largest gap in this package.

## Scope the brief proposes

One supplier agreement + one period of purchase export + one supplier or buying-group statement → normalized terms, qualifying purchases, expected vs paid, variance with evidence, exception reason, claim packet.

## Scope Claude would carry into G1 (if authorized)

In:
- Purchase-volume rebates (flat, per-unit, retroactive and incremental tiers, growth vs prior year).
- Buying-group statements where the program is purchase-based.
- CSV/XLSX exports from **one** ERP; CSV/XLSX statements first, PDF statements second.
- Manual adjustment lines (with reason and attachment) for anything outside the rule model.
- Evidence-backed exception report and claim packet export.

Out (recommended):
- SPA / ship-and-debit (sales-side; separate product decision).
- Co-op / MDF (proof-of-performance claims, not calculation).
- Any live ERP integration, supplier portal or EDI 844/849.
- Customer-side (sell-side) rebates.
- Multi-entity consolidation.

Open (management):
- Accrual / quarter-end close projection as the recurring value event (competitively contested; see 10 D2).

## Facts vs assumptions

| Item | Type |
|---|---|
| SPA is calculated on sales lines | Fact (sourced) |
| Spreadjust and Band capabilities | Fact as published by the vendors; traction not verified |
| ERPs export the needed fields | Fact in general; customer-specific columns Unknown |
| 75–90% of agreements fit the rule model | Estimate |
| Onboarding hours | Estimate |
| AI and infra costs | Estimate from list prices |
| Rebate leakage magnitude | Unknown (only surveys of belief) |
