# 06 — Unit Economics and Cost Assumptions (G0)

All figures are **estimates** in USD, using list prices Claude knows as of mid-2026; verify at G1.

## 1. Fixed infrastructure (pre-revenue)

| Item | Monthly |
|---|---|
| Vercel Pro (1 seat) | $20 |
| Managed Postgres (Neon/Supabase paid base tier) | $19–25 |
| Object storage (few GB) | <$5 |
| Sentry, PostHog, Resend | $0 (free tiers) |
| Domain | ~$2 |
| **Total** | **~$50–55/mo** |

Within the $100/mo pre-revenue cap. No vendor over $50/mo. No approval needed.

## 2. Variable cost per reconciliation (Brief Q8)

Assumptions: one agreement of 10–40 pages (~15–60k input tokens), extraction with a mid-tier frontier model at roughly $3 per million input tokens and $15 per million output tokens, two passes (extract + verify quotes), ~5k output tokens.

| Step | Cost per run |
|---|---|
| Agreement extraction (once per agreement version) | $0.10–0.50 |
| Statement PDF parsing (per statement, if PDF) | $0.05–0.40 |
| Column/product mapping suggestions | <$0.05 |
| Deterministic calculation + matching | ~$0 (compute) |
| Storage of files and results | <$0.01/month |
| **Per reconciliation, AI-heavy worst case** | **< $2** |

Per customer per month (Estimate): 10–40 active programs, agreements re-extracted only when they change, monthly statements → **$5–25/month** variable cost.

## 3. Gross margin

At ~$650 ARPU and ~$15 variable + ~$5 allocated fixed per customer at 10 customers: technical COGS ≈ 3% of revenue; gross margin before payment fees ≈ **96–97%**; after Stripe (~3%) ≈ **93%**.

**Technical cost is not a risk for this business.** Target is 80%+, comfortably exceeded.

## 4. The real cost: founder hours

The binding constraint is human onboarding and review time, not compute. Estimates (see 07):

| Phase | Founder hours per new customer |
|---|---|
| First 3 customers (learning) | 10–20 |
| Customers 4–15, same vertical + ERP | 4–8 |
| Steady state, templates mature | 2–4 |
| Ongoing per customer per month | 0.25–1 |

At $650/month and 6 onboarding hours + 0.5 h/month, first-year gross profit per founder hour is roughly $600–650 (Estimate). That is attractive **if** the onboarding estimate holds; it collapses if each agreement needs bespoke interpretation (brief kill condition #2/#5).

## 5. Pricing observations (management decision; Claude comments only)

- The brief's $399–$1,299 range sits directly on top of Spreadjust's published $299/$599/$1,199. Without a clear wedge, the market will compare on price.
- Pricing by number of active supplier programs is the best proxy for both value and our onboarding cost. Recommend that axis.
- Charge an onboarding/setup fee (or require annual) to cover front-loaded founder hours and filter tyre-kickers. Low-touch SaaS logic argues against it; the onboarding-hours reality argues for it. Management call.
