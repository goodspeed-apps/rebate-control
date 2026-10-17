# 07 — Operations, Support, Founder Burden (G0)

## 1. Manual steps that would remain for the owner (Brief Q9)

| Step | Who | Automatable? |
|---|---|---|
| Sales call + security questionnaire | Owner | Partly (standard answer pack) |
| Confirm AI-drafted agreement terms | **Customer** analyst ideally; owner for first customers | No — human confirmation is the control |
| Map customer item codes to supplier product lines | Customer with assistant; owner on first customers | Partly (auto-match) |
| Set up a new ERP export template | Owner/Claude, once per ERP | Becomes reusable |
| Set up a new supplier statement template | Owner/Claude, once per supplier | Becomes reusable |
| Answer "why does this number differ?" questions | Owner | Reduced by evidence trail; never zero |
| Interpret non-standard agreement clauses | Owner (needs rebate-domain fluency) | No |

**Critical dependency:** the last two rows require someone who understands distributor rebate accounting. The brief does not say who that is. If it is the owner, the owner must climb that learning curve; if no one, early customers will get slow or wrong answers. This is the largest founder-attention risk and is not a technical problem Claude can engineer away.

## 2. Who confirms the terms?

Two operating models; the choice drives founder hours more than any technical decision:

- **A. Self-serve confirmation:** customer's analyst confirms the extracted terms in the product. Low founder hours; requires excellent UX and a customer who is willing and able. Liability for wrong terms sits with the customer.
- **B. Done-for-you setup:** owner (or a contractor) confirms terms. Higher win rate early; founder hours scale with customers; drifts toward a service business.

Recommendation: A by default, B only as a paid, time-boxed onboarding package.

## 3. Support load drivers (Estimate)

- False exceptions from timing (supplier statement uses ship date, distributor export uses receipt date; period boundaries). Mitigation: configurable date basis and tolerance windows per supplier.
- Statement layout changes by suppliers (PDF). Mitigation: CSV preferred; template versioning; parse-failure alerts to the owner.
- ERP export column changes after customer upgrades. Mitigation: header validation on every upload with a clear error.

## 4. Usage cadence risk

Volume rebates settle quarterly or annually. If the product is only opened when a statement arrives, usage is 4–12 times a year, and the customer may treat it as a one-off audit ("we found $40k, thanks, cancel"). The free-audit entry motion (also used by Spreadjust) amplifies this.

Mitigation options, all needing management judgement: monthly accrual/close report as the recurring value event; annual contracts; programme-count pricing.

## 5. Technical decisions that would make this hard to run solo (Brief Q10)

Avoid:
1. Any live ERP integration in the MSP (each ERP version is a maintenance stream).
2. Per-customer code branches or custom calculation scripts.
3. Supplier-portal scraping or EDI 844/849 for SPA.
4. Letting AI output reach financial results without confirmation (one wrong number destroys controller trust).
5. Promising "we reconcile everything" (co-op/MDF, freight, price protection, SPA) in v1.
6. On-prem or customer-hosted deployments.
7. SOC 2 before revenue.
