# 04 — Test Report (G0)

N/A — not applicable at this gate. No code was written.

Test approach proposed for G1 (calculation engine is the business-critical logic):
- Golden-file tests: real (anonymized) agreements + exports with hand-calculated expected results, signed off by a rebate practitioner.
- Property tests: tier boundaries, retroactive vs incremental, returns crossing periods, decimal rounding.
- Determinism test: identical inputs produce byte-identical outputs.
- Extraction eval set: ≥20 real agreements with labelled terms; track field-level accuracy of AI drafts.
