# CLAUDE.md — Rebate Control

- **Purpose:** working-name product that reconciles distributor supplier-rebate agreements + ERP purchase exports + supplier statements into an evidence-backed exception report.
- **Current gate:** G0 Opportunity Feasibility (package 2026-10-17). Claude recommended HOLD. **No build is authorized.** Do not write application code until the owner explicitly authorizes G1.
- **Approved scope:** none beyond G0 analysis.
- **Governance:** BUSINESS_REVIEW_PROTOCOL.md, PORTFOLIO_TECHNICAL_STANDARD.md, PORTFOLIO_OPERATIONS_ADDENDUM.md (project shared folder). Packages go in `management-review/<GATE>/<YYYY-MM-DD>/`.
- **Stack (proposed, not built):** portfolio default (Next.js, TS strict, pnpm, Postgres+Prisma, Vercel, Stripe, Sentry).
- **Known hazards:** SPA/ship-and-debit is sales-side and out of proposed scope; AI may only draft terms, never compute money; direct competitors Spreadjust and Band (see `management-review/G0/2026-10-17/assets/competitive-evidence.md`).
