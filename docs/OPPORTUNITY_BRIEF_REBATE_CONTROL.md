# Opportunity Brief — Wholesale Distributor Rebate Control

**Date:** 2026-10-16  
**Business Manager Disposition:** ADVANCE TO G0  
**Current Rank:** #1  
**Working Product Name:** Rebate Control (working name only)

## 1. Target Buyer

Primary ICP:

- U.S. wholesale distributors, initially concentrated in HVACR, electrical, plumbing/PVF, industrial/MRO, and adjacent sectors.
- Rough target size: $20M–$200M annual revenue.
- Especially attractive where the company manages dozens of supplier rebate agreements, SPAs, buying-group programs, co-op/MDF programs, or tiered purchase incentives.
- Prefer companies using common distribution ERPs such as Epicor Prophet 21, Eclipse, Infor, NetSuite, Sage, or Microsoft Dynamics and able to export purchase history without a custom integration.

Primary buyers:

- CFO
- Corporate Controller
- VP Finance
- Rebate Finance Manager
- Director of Procurement / VP Procurement

Primary users:

- Finance/rebate analyst
- Controller team
- Procurement operations

## 2. Core Recurring Problem

Distributor finance teams must reconcile:

1. supplier agreement terms,
2. actual purchases / qualifying transactions,
3. expected rebate or SPA economics,
4. supplier or buying-group statements,
5. cash/credits actually received.

The process is commonly spreadsheet-heavy, dependent on a small number of people, and error-prone.

The economically important question is:

> Did we receive every dollar of supplier incentive we earned?

## 3. Current Workaround

Typical current state:

- Excel workbooks
- ERP exports
- PDF/Word supplier agreements
- supplier statements
- manual accrual calculations
- email follow-up
- spot checking
- broader rebate-management platforms for larger organizations

## 4. Economic Consequence

Failure can create:

- missed supplier rebate revenue
- understated or overstated accruals
- margin leakage
- quarter-end close uncertainty
- missed thresholds
- unclaimed discrepancies
- key-person dependency
- audit/reconciliation labor

The product should be sold primarily as a margin-control system, not a productivity app.

## 5. Proposed Value Proposition

> Know what you earned, what the supplier paid, and exactly where the difference is.

The product should convert supplier agreements + purchase data + supplier/buying-group statements into an auditable exception report.

Every monetary result must be traceable to source evidence.

## 6. Minimum Sellable Product Thesis

Input:

- one supplier agreement
- purchase/export data for the relevant period
- one supplier or buying-group statement

Output:

- normalized agreement terms
- qualifying purchases
- expected rebate / SPA amount
- amount paid/credited
- discrepancy
- source evidence
- exception reason
- claim/review packet

The calculation engine must be deterministic and tested.

AI may assist with agreement extraction and mapping, but AI must not be the authoritative calculator of money.

## 7. Market Evidence

The current wholesale-distribution market is large and fragmented. MDM's 2026 Top Distributors directory alone lists more than 220 major North American distributors across 20 verticals.

Current buyer pain is validated by established rebate-management products and distributor case studies showing spreadsheet-heavy processes, large reconciliation workloads, and high-value rebate operations.

## 8. Competitive Landscape

Important competitors include:

- Enable
- Band
- Speedy Labs
- Spreadjust
- other rebate-management platforms and ERP-specific solutions

### Critical Phase 3 finding

Spreadjust is a very recent and unusually direct competitor.

Its current positioning already includes:

- U.S. distributors roughly $20M–$200M
- agreement + purchase export + supplier statement
- no ERP integration required
- Prophet 21 / Eclipse / Infor / NetSuite exports
- statement reconciliation
- claim packets
- buying-group statements
- $299 / $599 / $1,199 monthly pricing
- a first-pass/free-audit entry motion

This materially reduces feature-level whitespace.

We must not build a clone.

## 9. Differentiation Thesis to Test

The strongest defensible direction appears to be a narrow financial-control layer rather than a general rebate platform.

Potential differentiation areas for G0/G1 investigation:

1. Deep specialization in one distribution vertical and ERP combination.
2. Deterministic, explainable agreement-rule engine.
3. Rebate + SPA + buying-group reconciliation with a unified exception model.
4. Quarter-end accrual confidence / financial-close controls, not only statement checking.
5. Exceptional auditability and source traceability.
6. Security and data-handling posture suitable for controllers.
7. Configurable reusable rules that reduce per-customer setup over time.
8. ERP-consultant / association channel distribution rather than competing primarily on SEO.

The business should not proceed to G1 if the only differentiation is nicer UI or generic AI extraction.

## 10. Customer Acquisition Hypothesis

### Customer #1

Build a list from:

- MDM Top Distributors
- HARDI membership / HVACR ecosystem
- NAED / electrical distribution ecosystem
- public distributor websites
- ERP consultant client ecosystems

Target CFOs, Controllers, Rebate Finance Managers, and VP Procurement.

Initial offer:

> Send one supplier agreement, one statement, and the matching purchase export. We will produce a reconciliation showing what was expected, what was paid, and any supported differences.

The entry offer must not require an ERP integration.

### Customer #10

Add:

- ERP consultants serving P21/Eclipse/Infor/NetSuite distributors
- HARDI/NAED-style industry communities
- webinar or educational content around rebate controls and quarter-end reconciliation
- referrals from existing customers and fractional finance professionals

### Customer #100

Potential scalable channels:

- distribution-industry associations
- ERP implementation partners
- relevant ERP marketplaces/ecosystems
- SEO around rebate reconciliation, SPA reconciliation, buying-group statements, and rebate accrual
- vertical-specific benchmark/control content
- partner/referral network

## 11. First-100-Prospect Feasibility

PASS.

A high-quality initial account list is feasible without a large paid data stack.

MDM alone publishes more than 220 large distributors across 20 sectors. Trade associations and ERP ecosystems provide additional concentrated pools.

The challenge is not finding companies. It is identifying companies where rebate complexity is sufficiently painful and finding the correct finance/procurement buyer.

## 12. Pricing Hypothesis

Do not finalize pricing until G1, but current working range:

- Starter: $399–$499/month
- Growth: $699–$899/month
- Scale: $1,299+/month

Pricing should ultimately reflect:

- annual purchasing volume
- number of active supplier programs
- entities/branches
- reconciliation volume
- value recovered / controlled

Avoid percentage-of-recovery pricing unless management explicitly revisits this. Fixed SaaS pricing better fits the low-touch portfolio model.

## 13. Planning Economics

Illustrative, not forecast:

- $10K MRR at ~$650 blended ARPU: ~16 customers
- $25K MRR: ~39 customers
- $50K MRR: ~77 customers

This customer-count profile is highly attractive for a solo-founder portfolio if onboarding and support can be standardized.

## 14. Expected Sales Friction

Medium.

Likely friction:

- sensitive supplier agreements
- purchase-level financial data
- controller/security questions
- requirement to prove calculation accuracy
- initial rules/configuration
- possible NDA/security questionnaire

Mitigations:

- file-export MSP
- no ERP write access
- deterministic calculations
- source-backed results
- documented data deletion/retention
- strong tenant isolation
- minimize sensitive fields

## 15. Founder-Attention Risk

Primary risk:

> Each agreement becomes a bespoke consulting project.

The business only works for the portfolio if agreement structures can be normalized into reusable configurable rule types.

Human review during early onboarding is acceptable.

Permanent manual interpretation of every agreement is not.

## 16. Defensibility Thesis

Potential moat comes from:

- normalized rebate/SPA rule library
- ERP export mappings
- supplier/buying-group statement mappings
- exception taxonomy
- historical agreement versions
- deterministic calculation engine
- domain-specific reconciliation knowledge
- channel relationships
- accumulated configuration data

The dashboard itself is not a moat.

## 17. Kill / Pivot Conditions

Strongly reconsider or kill if G0/G1 finds:

1. Each customer needs substantial custom engineering.
2. Each supplier agreement requires ongoing human interpretation rather than reusable configuration.
3. Reliable calculations cannot be deterministic and auditable.
4. Data normalization requires deep ERP integrations before first value.
5. Expected onboarding remains above roughly 4–6 founder hours per new customer after the initial learning period.
6. Security requirements force enterprise-grade compliance before early revenue.
7. We cannot define a differentiated wedge versus Spreadjust / Enable / Band / Speedy beyond UI or price.
8. Expected steady-state support materially undermines Return on Founder Attention.

## 18. Questions for Claude at G0

Claude should specifically red-team:

1. Can a useful MSP work from flat-file exports and uploaded agreements/statements?
2. What agreement structures can be represented by a reusable deterministic rule model?
3. What percentage of likely rebate/SPA structures would require custom logic?
4. How should AI extraction be separated from authoritative calculations?
5. Can every output amount be source-traceable?
6. What data normalization strategy minimizes customer-specific engineering?
7. What security controls are necessary for supplier agreements and purchase data?
8. What is the expected variable compute/AI cost per reconciliation?
9. What manual steps would remain for the owner?
10. What technical decisions could make this product difficult to operate as a solo-founder SaaS?
11. Is there a technically meaningful moat available through mappings/rules without building a full rebate-management suite?
12. Recommend GO / GO WITH CHANGES / HOLD / PIVOT / KILL for G1.

## 19. Business Manager G0 Instruction

G0 only.

Do not write production application code.

Create the private product repository, store this Opportunity Brief, perform technical/business-feasibility red teaming required by the governance documents, produce the G0 management-review package, and stop for management approval.
