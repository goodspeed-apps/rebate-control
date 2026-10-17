# 00 — Executive Summary

**Product:** Rebate Control (working name) · **Date:** 2026-10-17 · **Prepared by:** Claude (development organization) · **For:** Kevin (Owner/CEO), Business Manager review

## Current Gate

**G0 — Opportunity Feasibility.** No application code written. Source: `docs/OPPORTUNITY_BRIEF_REBATE_CONTROL.md` (Business Manager disposition: ADVANCE TO G0).

## Overall Status

**YELLOW** — buildable, cheap to run, high margin. The business thesis has a competitive problem that technology cannot fix.

## Recommendation

# HOLD

Do not authorize G1 yet. Convert to **GO WITH CHANGES** only if the validation in `10_DECISIONS_REQUIRED.md` §D1 produces evidence within ~30 days; otherwise **KILL**.

## What Management Needs to Know

1. **It is technically feasible and cheap.** A flat-file MSP (agreement + purchase export + statement → exception report) works without ERP integration. Variable cost is under $2 per reconciliation and $5–25 per customer per month; fixed infra ~$50–55/mo. Gross margin ~93% after payment fees. (06)
2. **No technical moat survives the competitor check.** Spreadjust already sells the brief's exact pitch to the exact ICP at $299–$1,199/mo, including clause-cited line audits, buying-group rebates and accruals. Band covers rebates **and** SPAs, with SOC 2 Type II and named customers in electrical. Eclipse, Infor CSD and NetSuite already track rebates natively. Of the brief's eight differentiators, only **vertical focus** and **channel** remain open, and both are go-to-market wedges, not engineering ones. This meets the spirit of the brief's own kill condition #7. (assets/competitive-evidence.md)
3. **SPA is a different product.** SPA/ship-and-debit claims are calculated on *sales* lines to end customers, not purchases. Including SPA doubles the data pipeline, adds customer-pricing data, and puts us head-on with Band and Speedy Labs. Recommend excluding SPA from any MSP. (02 §6)
4. **The binding cost is founder hours, not compute.** Estimated 10–20 founder hours per early customer, falling to 2–4 once templates mature. Confirming agreement terms and answering "why does this differ?" needs real rebate-accounting fluency. The brief does not name who supplies it. (07)
5. **Usage cadence risk.** Volume rebates settle quarterly or annually. Combined with a free-audit entry offer, there is a real risk customers treat this as a one-off audit and cancel. (07 §4)
6. **Security is manageable at the low end of the ICP.** No SOC 2 needed before revenue at $20M–$100M; expect it above ~$100M or under PE ownership, where Band already has it. (05)
7. **The pain is real.** Rebates are reported at 20–70% of electrical distributors' profit; 52% of distributors believe they are underpaid. These are trade-press and survey figures, not measured leakage.

## Answers to the Brief's G0 Questions

| # | Question | Answer |
|---|---|---|
| 1 | Flat-file MSP viable? | Yes for purchase rebates. Growth rebates need prior-year data too. SPA needs sales data. |
| 2 | Reusable rule model? | Yes: basis × scope × exclusions × period × rate structure (flat/per-unit/retro tier/incremental tier/bonus) × growth × payment form. (02 §3) |
| 3 | % needing custom logic? | Estimate 10–25%, handled as audited manual adjustments, never custom code. Unvalidated until ≥20 real agreements are tested. |
| 4 | AI vs calculation? | AI drafts terms/mappings with source quotes; humans confirm; a deterministic engine accepts only confirmed, versioned rules. (02 §4) |
| 5 | Every amount source-traceable? | Yes, by design (rule version + clause quote + contributing line IDs + arithmetic). |
| 6 | Normalization strategy? | Differences as data: per-ERP export templates, shared supplier catalogue, per-supplier statement templates. Customer item-code mapping is the residual cost. (02 §7) |
| 7 | Security controls? | Tenant isolation, encryption, MFA, audit log, retention/deletion, LLM zero-retention, no line data to LLMs, no ERP access. (05) |
| 8 | Variable compute/AI cost? | < $2 per reconciliation; $5–25 per customer per month. (06) |
| 9 | Manual steps for owner? | Sales/security Q&A, early term confirmation, new supplier/ERP templates, variance explanations, non-standard clauses. (07 §1) |
| 10 | Decisions that make it hard to run solo? | Live ERP integrations, per-customer code, SPA/EDI/portal work, unconfirmed AI numbers, SOC 2 pre-revenue. (07 §5) |
| 11 | Moat via mappings/rules? | Modest. Supplier catalogues and statement templates compound across customers within one vertical, but Band and Spreadjust build the same assets. A moat here comes from being first and deepest in one vertical, not from technology. |
| 12 | Recommendation | **HOLD** (see above). |

## Decisions Required

See `10_DECISIONS_REQUIRED.md`. In short: (D1) whether to fund a 30-day no-code validation; (D2) choose the wedge; (D3) exclude SPA; (D4) who supplies rebate-domain expertise.

## Business Impact

| Area | Impact |
|---|---|
| Time to launch | 4–6 weeks of build after G1 if scoped to rebates + statements. Not the constraint. |
| Revenue potential | Real pain, but price anchored by Spreadjust at $299–$1,199. Hard to command the brief's $399–$1,299 without a wedge. |
| Pricing | Price per active supplier program; consider setup fee or annual terms. Management call. |
| Gross margin | ~93% after Stripe. Not a risk. |
| Support burden | Medium: variance explanations, statement format changes, timing false positives. |
| Founder attention | **Main risk.** Onboarding hours plus domain expertise plus a consultative sale. |
| Scalability | Technically trivial. Commercially gated by channel access. |
| Risk | Competitive: high. Technical: low–medium (PDF statements, item mapping). Security: medium. |

## Claude's Recommendation and Reasons

**HOLD.** The product can be built well and cheaply. Building it is not the risk. Entering a market where a near-identical, cheaper offer and a SOC 2–certified, SPA-capable incumbent already exist, without a wedge we can name, is the risk. The brief told us not to build a clone, and today Claude cannot describe what we would build that is not one.

- **Cut:** SPA/ship-and-debit, co-op/MDF, ERP integrations, multi-vertical positioning.
- **Delay:** accrual/close projections and buying-group aggregation until a design partner asks for them with data in hand.
- **Simplify:** one vertical, one ERP, purchase-volume rebates, CSV statements first (PDF second).
- **Reprice:** do not sit inside Spreadjust's ladder; price on programs under management, and test a paid setup.
- **Redesign:** lead with a channel (ERP consultant or association partner), not SEO or a free audit.
- **Stop:** if the D1 validation does not produce 3 distributors willing to share real files and a channel partner willing to refer, kill it and move founder attention to the next ranked opportunity.
