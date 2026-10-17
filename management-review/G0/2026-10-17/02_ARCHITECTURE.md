# 02 — Proposed Technical Approach (G0)

Gate: G0 Opportunity Feasibility. Nothing here is built. This is the approach Claude would carry into G1 if authorized.

Legend: **Fact** = verified or definitional. **Estimate** = Claude's engineering judgment, to be validated with real customer files. **Unknown** = cannot be answered without customer data.

## 1. Minimum technically viable workflow

```
 Upload (3 files)            Confirm (human)               Compute (deterministic)        Output
 ─────────────────           ────────────────              ───────────────────────        ──────────────────
 Agreement PDF/DOCX  ──AI──▶ Draft rule (typed form) ──▶   Rule engine (pure TS)    ──▶   Exception report
 ERP export CSV/XLSX ──map─▶ Column + product mapping ──▶  Qualifying lines         ──▶   Expected vs paid
 Supplier statement  ──AI──▶ Statement lines (review) ──▶  Match + variance         ──▶   Claim packet (PDF/XLSX)
```

Every arrow labelled AI produces a **draft** that a person confirms before it can affect money. The compute stage never calls an AI model.

## 2. Can a useful MSP work from flat-file exports? (Brief Q1)

**Yes, for purchase-volume rebates — with conditions.** (Estimate, high confidence.)

- Every ERP named in the brief (P21, Eclipse, Infor CSD/SX.e, NetSuite, Sage, Dynamics) can export purchase-order receipt or AP invoice lines to CSV/XLSX through standard reporting. **Fact** (standard reporting capability); exact column sets vary by customer configuration. **Unknown** until we see real exports.
- Minimum fields needed per line: supplier ID, item/SKU, supplier product line or category, quantity, extended cost, transaction date (receipt or invoice), branch, document number. Returns/credits must be present as negative lines or a separate file.
- Two conditions that break the flat-file assumption:
  1. **SPA / ship-and-debit claims are calculated on the distributor's *sales* to specific end customers, not on purchases.** They need sales-invoice lines with customer, job/SPA number, sell price, into-stock cost and SPA cost. That is a second, larger, more sensitive dataset. See §6.
  2. **Growth rebates need prior-year purchases** in the same mapped form, so first value needs two periods of data, not one.

## 3. Reusable deterministic rule model (Brief Q2, Q3)

A rebate rule is a composition of a small number of typed parameters. Proposed model (Estimate):

| Parameter | Values |
|---|---|
| Basis | purchase $, purchase units, sales $ (SPA), sales units |
| Scope filter | supplier(s), product lines, SKU include/exclude lists, branches, date window |
| Exclusions | returns, freight, drop-ship, buying-group-billed purchases, promo/net-price items |
| Measurement period | month, quarter, half, year, custom; calendar or program year |
| Rate structure | flat %, per-unit, tiered **retroactive** (all dollars at achieved tier), tiered **incremental** (marginal), fixed bonus at threshold |
| Growth condition | vs prior period (absolute or %), with optional base-year adjustment |
| Payment form | check, credit memo, AP offset, buying-group pass-through; payment lag |
| Combination | sum of multiple rules; cap/floor |

**Estimated coverage:** 75–90% of purchase-volume rebate programs a $20M–$200M distributor holds should fit these parameters without code. (Estimate; based on common program structures. Must be validated against ≥20 real agreements before G1 exit.)

**Likely to need custom logic or human judgement (10–25%, Estimate):**
- Multi-supplier or multi-program combined thresholds (e.g., buying-group aggregate volume).
- Conditional earnings: fill-rate, payment-timeliness, marketing-plan compliance, "growth excluding new stores".
- Prior-year base restatements after acquisitions or SKU reclassification.
- Retroactive mid-year amendments.
- Co-op/MDF: usually claim-against-spend with proof of performance. **Not a calculation problem**; recommend excluding from MSP.

Design rule: anything outside the model is held as a **manual adjustment line** with a reason and attachment, never as custom code per customer. That keeps "custom engineering per customer" at zero by construction; the cost moves to human review time, which is measurable (see 07).

## 4. AI vs. authoritative calculation (Brief Q4)

| Stage | Who decides | AI role |
|---|---|---|
| Agreement → rule draft | Human confirms each parameter | Extract fields + quote the source clause and page |
| Export → column mapping | Human confirms once per ERP template | Suggest mapping from headers/sample rows |
| Product line mapping | Human confirms once per supplier | Suggest matches from descriptions |
| Statement → lines | Human reviews flagged lines | Parse PDF tables when no CSV exists |
| **Money calculation** | **Deterministic engine only** | **None** |
| Exception reason text | Deterministic codes | Optional plain-language summary, clearly labelled |

Enforcement: the engine accepts only a *confirmed* rule version (immutable, hashed). An unconfirmed AI draft cannot be passed to it. Tested with property-based and golden-file tests (decimal arithmetic, no floats).

## 5. Source traceability (Brief Q5)

**Yes, every output amount can be traceable** (Estimate, high confidence), because the engine is a pure function of:
`(confirmed rule version, mapped transaction lines, statement lines) → result`.

Each result row stores: rule version ID, the clause quote/page it came from, the list of contributing transaction line IDs (file + row number), tier reached, and the arithmetic. Re-running the same inputs must give byte-identical output (tested). This is the single strongest technical differentiator available and is cheap to build if designed in from day one; it is expensive to retrofit.

## 6. SPA / ship-and-debit: a scope fork

**Fact:** SPA (special pricing agreement / ship-and-debit) claims in electrical and HVACR distribution are generated per *sales* line: the distributor sells to a contractor at a supplier-agreed price, then claims back the difference between its into-stock cost and the SPA cost. Volume rebates are earned on *purchases*.

Implications (Estimate):
- Different data source (sales invoices, customer names, job references), higher volume (thousands of lines per month vs. purchase totals), higher sensitivity (customer pricing).
- Different cadence: SPA claims are weekly/monthly and transactional; volume rebates settle quarterly/annually. SPA is the **more recurring** pain; rebates are the **larger single-dollar** pain.
- Different counterparties: SPA reconciliation is matching claim submissions to supplier credits, often through supplier portals or EDI 844/849.

**Recommendation:** MSP covers **one**, not both. Default proposed for G1: purchase-volume rebates + buying-group statements (fits the brief's "one agreement + purchase export + one statement" input). SPA is a separate product decision for management (see 10).

## 7. Data normalization strategy (Brief Q6)

Minimize customer-specific engineering by making every customer difference **data, not code**:

1. **ERP export templates** — a stored column-mapping per ERP + report type, reused across customers on the same ERP. First customer on an ERP: ~1–2 hours. Subsequent: minutes, if they use the standard report. (Estimate)
2. **Supplier catalogue** — supplier identity and product-line taxonomy stored once per supplier, shared across customers in the same vertical (Carrier/Lennox/Trane in HVACR; Eaton/Schneider/Siemens in electrical). This is the reusable asset.
3. **Statement templates** — per supplier/buying-group statement layout, reused across customers.
4. **Customer item → supplier product-line mapping** — unavoidably per customer (their item codes). Mitigate with auto-match on supplier part number and description; human resolves residue.

Item 4 is the most likely onboarding-time sink. **Unknown** how clean distributor item masters are; must be measured on real data.

## 8. Proposed stack (portfolio default, no overrides proposed at G0)

Next.js + TypeScript strict, pnpm, Postgres (Neon or Supabase) + Prisma, Vercel, Stripe, Sentry, Resend, managed object storage, Clerk or Auth.js with organizations. Calculation engine as a pure TypeScript module with no I/O, using a decimal library.

Possible G1 overrides to evaluate (not proposed yet):
- Large file parsing (100k–1M rows) may exceed Vercel function limits → background job on a managed worker. Decide at G1 after measuring real export sizes.
- PDF table extraction may need a document-AI service if LLM extraction proves unreliable on scanned statements.

## 9. Essential integrations and external dependencies

| Dependency | Needed for MSP? | Notes / lock-in |
|---|---|---|
| ERP integration | **No** — flat-file upload only | Avoids the largest maintenance burden in this category |
| LLM provider (Anthropic/OpenAI) | Yes, for extraction drafts | Must use zero-data-retention / no-training terms. Swappable; small surface |
| PDF parsing library / document AI | Yes | Open-source first; paid only if needed |
| Supplier portals / EDI 844/849 | **No** | Needed only for SPA automation; high burden |
| Stripe, auth, email, monitoring | Yes | Portfolio defaults |

No platform dependency gives a third party control of distribution or pricing. Lock-in risk is low.

## 10. Implementation complexity by component (Estimate)

| Component | Complexity | Notes |
|---|---|---|
| Auth, orgs, billing, uploads | Low | Portfolio patterns |
| File ingest + column mapping UI | Medium | Large files, many formats, encoding issues |
| Product-line mapping UI | Medium-High | Main onboarding-time lever |
| Rule model + confirmation UI | Medium | Typed form; most UX effort |
| Deterministic engine + tests | Medium | Small code, high test burden; must be exact |
| AI agreement extraction | Medium | Prompting + evidence quoting + eval set |
| Statement parsing (CSV) | Low | |
| Statement parsing (PDF) | High / variable | Per-layout; biggest technical uncertainty |
| Matching + exception model | Medium | Timing differences cause false exceptions |
| Evidence/claim packet export | Low-Medium | |
| Accrual projection (tier forecast) | Medium | Optional wedge; see 10 |

Rough MSP build effort if scoped to rebates + statements only: **4–6 weeks of Claude build time** plus founder review time. (Estimate, low confidence until G1 scoping.)
