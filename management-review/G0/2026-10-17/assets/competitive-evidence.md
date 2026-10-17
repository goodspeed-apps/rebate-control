# Competitive and Domain Evidence (G0)

Web research, accessed 2026-10-17. **[Inference]** marks Claude's reading of the facts. Unverified items are named as such.

## Direct competitors in the exact ICP

| Vendor | What it does | Evidence of traction | Pricing |
|---|---|---|---|
| **Spreadjust** (spreadjust.com) | Agreement + statement (PDF/sheet/scan) + purchase export; no ERP connection; P21/Eclipse/Infor/NetSuite named; line-level statement audit **citing the contract clause**; buying-group rebates; claim deadlines; supplier audits; **rebate accruals**; missing-statement alerts; dated audit file | No named customers, no team listed, **states it is not SOC 2 certified**, no third-party mentions found | $299 / $599 / $1,199 per month, month-to-month; free first pass for first 10 distributors |
| **Band** (joinband.com) | SPAs, vendor rebates, customer rebates; SPA claims in each vendor's format; tier alerts; margin waterfall; reconciliation; Eclipse/P21/Infor CSD/NetSuite/SAP/Dynamics **or flat file** | **SOC 2 Type II**; named customers include Global Industrial, Broken Arrow Electric, Wiseway Supply, Revere Electric, buying groups HTSA, BuyQ, PTN | Not published |
| **Speedy Labs** (speedylabs.ai) | AI rebate management, full SPA lifecycle | YC W23, ~8 people | Not published |
| **Enable** (enable.com) | Enterprise rebate management | Established; annual, quote-based on program value | Not published |
| **Epicor Data Analytics Rebates** | Epicor add-on: payable/receivable rebates, near-miss, forecasting | Vendor product | Not published |

Sources: spreadjust.com; joinband.com; altss.com/companies/yc/speedy-labs; erpresearch.com/erp-add-ons/distribution/enable/pricing; platform.softwareone.com (Epicor Data Analytics Rebates). Not verified this session: Vistex, Flintfox, Rebate Pro, Vendortell pricing.

## ERP native capability

- **Eclipse**: Epicor brochure lists Automated Rebates/SPA, electrical-industry SPA support, vendor rebate tracking.
- **Infor CSD/SX.e**: native vendor rebates on purchase and "vendor on sale", with claim response codes (docs.infor.com).
- **NetSuite**: Rebates Management SuiteApp (vendor rebates on purchase or sale, accruals).
- **Prophet 21**: native rebate/SPA not confirmed; partners sell custom P21 rebate tools because users rely on spreadsheets (mindharbor.com).

**[Inference]** ERPs *track* and *accrue*. The open gap is verifying supplier statements and payments against the distributor's own records, and agreement terms too complex to configure in the ERP. P21 shops look like the least-served ERP base.

## SPA mechanics (confirmed)

SPA / ship-and-debit claims are based on the distributor's **sales** to an eligible end customer: claim = into-stock cost − SPA cost, per line, with proof of sale (vendavo.com; blog.speedylabs.ai; ogl.co.uk). HVACR Trends 2019 survey (~130 respondents): 10% say claiming is easy; most deal with 10–30 SPA manufacturers, each with its own portal; mismatched claims that cannot be refiled are written off. EDI 844/849 is the standard claim/response transaction set (use in electrical not confirmed).

## Economic size of the pain

- Rebates are reported at 20–60% of an electrical distributor's net income (David Gordon) and 40–70% of total profit (NAED 2023 PAR as cited by Electrical Trends, Nov 2025; primary report not accessed). Trade-press, not audited.
- 52% of distributors **believe** they do not receive all rebates earned (Enable 2024 survey via MDM). Belief, not measurement.
- "3–5% of rebate value left on the table" (ProfitOptics; no methodology). No independent measured leakage study found.
- ~2 in 3 distributors belong to a buying group; 57% of those do not know what each manufacturer pays them (Enable report via MDM/NAW).

## What this does to the brief's differentiation list (§9)

| Brief differentiator | Status after research |
|---|---|
| 1. One vertical + ERP depth | **Open**, but replicable; only a GTM wedge, not technical |
| 2. Deterministic, explainable rule engine | Claimed by Spreadjust (clause-cited lines) |
| 3. Rebate + SPA + buying group unified | Band does this with SOC 2 and named customers |
| 4. Accrual / close controls | Listed by Spreadjust; Epicor add-on does forecasting |
| 5. Auditability / traceability | Claimed by Spreadjust |
| 6. Security posture for controllers | Band has SOC 2 Type II; we would start without it |
| 7. Reusable configurable rules | Table stakes; every competitor needs this |
| 8. ERP-consultant / association channel | **Open**; not technical; depends on owner relationships |

**[Inference]** No technical differentiator remains that Claude can build and competitors lack. What is left is distribution (channel, vertical focus) and execution quality.
