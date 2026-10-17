# 05 — Security, Privacy, Compliance (G0)

## 1. Data the product would hold

| Data | Sensitivity | Why it matters |
|---|---|---|
| Supplier rebate agreements | **High (commercial confidential)** | Many supplier programs carry confidentiality clauses. A customer uploading them to a third-party SaaS may need to check those clauses. Sales friction, not our legal liability, but it slows deals. |
| Purchase history (cost, volume by supplier/SKU) | High | Reveals the distributor's buying power and margins |
| Supplier / buying-group statements | High | Same |
| Sales lines with end-customer pricing (only if SPA in scope) | **Very high** | Contractor names and job pricing. Avoid in MSP. |
| User accounts | Low (business contact PII only) | |

No consumer PII, payment card data, health or regulated data. No federal/state regulatory regime applies by default (not legal advice; confirm at G3 per addendum §12).

## 2. Controls required before first paying customer (Brief Q7)

Required (fits portfolio standard, no new vendor):
- Strict tenant isolation: every row tenant-scoped, enforced server-side; tests that cross-tenant reads fail. Consider Postgres row-level security as a second layer.
- Encryption in transit (TLS) and at rest (provider default). Uploaded files in private buckets, signed short-lived URLs.
- MFA available for all users; enforced for admins.
- Audit log of uploads, confirmations, rule edits, exports, and deletions.
- LLM provider under **zero data retention / no training** terms. Send only the agreement text needed for extraction; never send purchase or sales line data to an LLM.
- Documented retention: raw uploads deleted after N days (customer-configurable), derived results kept until account deletion. One-click workspace export and deletion.
- No ERP credentials, no write access to any customer system (flat files only).
- Founder access to customer data only through an audited support view; no direct DB browsing in normal operations.

## 3. The SOC 2 question

**Estimate:** at $20M–$100M revenue most buyers will accept a security questionnaire + written security overview. At $100M–$200M, and anywhere with PE ownership or an internal audit function, expect requests for SOC 2.

- SOC 2 Type I via a compliance platform (Vanta/Drata/Secureframe) plus auditor is typically several thousand to low tens of thousands of dollars per year (Estimate; vendor pricing not verified here). That exceeds the addendum's $600 annual-commitment threshold, so it is a **management decision**.
- Recommendation: do **not** pursue SOC 2 before revenue. Prepare a 2-page security overview and a standard questionnaire answer set (CAIQ-lite) at G3. Revisit SOC 2 if ≥2 qualified deals stall on it. This is kill condition #6 in the brief; Claude's view is that it is **not triggered** at the target size, but it caps the upper end of the ICP.

## 4. Privacy

Business-to-business data. A Privacy Policy, Terms, and a short Data Processing Addendum template will be needed at G3. Sub-processor list: hosting, database, storage, LLM provider, email, monitoring, Stripe.

## 5. Security risks specific to this product

- Malicious or malformed uploads (zip bombs, macro XLSX, huge CSVs): parse in a sandboxed job with size/row limits; never execute macros.
- Prompt injection inside an uploaded agreement steering extraction: low impact because AI output is a draft that a human confirms and cannot reach the engine unconfirmed.
- Wrong-tenant mapping reuse: shared supplier catalogues must contain only public supplier taxonomy, never a customer's terms or prices.
