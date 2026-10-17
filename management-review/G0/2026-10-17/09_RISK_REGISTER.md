# 09 — Risk Register (G0)

Likelihood/Impact: H/M/L. "Kill #" refers to the brief's §17 kill conditions.

| # | Risk | Type | L | I | Mitigation | Kill # |
|---|---|---|---|---|---|---|
| R1 | No differentiated wedge vs Spreadjust (same ICP, pitch, lower price) and Band (SOC 2, SPA, named customers) | Competitive | **H** | **H** | Pick one vertical + ERP + channel partner; validate before G1 | **7** |
| R2 | Founder hours per onboarding stay above 4–6 h | Operational | M-H | H | Self-serve confirmation; templates per ERP/supplier; paid setup; measure on 3 real datasets | 5 |
| R3 | Agreements need human interpretation, not configuration | Technical/Ops | M | H | Rule model + audited manual adjustments; test on ≥20 real agreements | 2 |
| R4 | Nobody on the team has rebate-accounting fluency to confirm terms and explain variances | Founder/Domain | **H** | H | Domain advisor or fractional rebate analyst on contract; or customer-confirmed terms only | 8 |
| R5 | One-off audit usage → churn after first recovery | Commercial | M-H | H | Monthly recurring value event (accrual/close); annual terms | — |
| R6 | Customer item codes don't map cleanly to supplier product lines | Data | M | M-H | Auto-match on supplier part no.; measure match rate on real data | 4 |
| R7 | PDF statement layouts vary and change | Technical | H | M | CSV first; template versioning; parse-failure alerts | — |
| R8 | False exceptions from date-basis and period mismatches erode trust | Product | M | M | Configurable date basis and tolerance windows | — |
| R9 | SOC 2 demanded before purchase | Security/Sales | M (higher above $100M) | M | Target $20M–$100M first; security overview pack; revisit if ≥2 deals stall | 6 |
| R10 | Supplier confidentiality clauses block uploads | Legal/Sales | L-M | M | DPA template, minimal retention, customer-controlled deletion | — |
| R11 | Wrong number shown to a controller | Trust | L (by design) | **H** | Deterministic engine, confirmed rules only, golden-file tests, evidence on every line | 3 |
| R12 | ERP vendors close the gap natively (Epicor add-on, NetSuite SuiteApp) | Platform | M | M | Focus on statement verification, which ERPs don't do | — |
| R13 | Cross-tenant data leak | Security | L | **H** | Server-side tenant scoping, RLS, tests | — |
| R14 | LLM extraction error accepted unchecked | Trust | M | M | Field-level confirmation UI; source quotes; eval set | 3 |

**Kill-condition scorecard (Claude's view at G0):**

| Kill # | Condition | Status |
|---|---|---|
| 1 | Substantial custom engineering per customer | Avoidable by design |
| 2 | Ongoing human interpretation per agreement | Unknown, plausible risk |
| 3 | Calculations can't be deterministic/auditable | Not triggered |
| 4 | Deep ERP integration needed before first value | Not triggered (rebates); triggered-ish for SPA |
| 5 | Onboarding > 4–6 founder hours steady state | Unknown; estimate 2–4 h once mature, 10–20 h early |
| 6 | Enterprise compliance before revenue | Not triggered at $20M–$100M |
| 7 | No wedge beyond UI or price | **Triggered on current evidence** |
| 8 | Support undermines Return on Founder Attention | Unknown; depends on R4 |
