---
name: quarterly-taxes
description: The household's federal tax position for the year and what to pay or withhold next: the quarterly estimated payment, break-even withholding, safe harbor, the set-aside for 1099 and business income. Use for "quarterly taxes", "estimated payment", "will we owe", "withholding".
---

Work the year's taxes from Truenote's projection. Everything here is an estimate from the person's own records, not tax advice; say so once, plainly, and suggest a professional for decisions like filing.

1. `get_tax_projection` for the year (this one unless asked). Read `warnings` first: a missing paystub, a stale year-to-date figure, an income source without figures. Fix inputs before quoting a number: `list_documents` (kind paystub, this year) and `read_document` for the latest paystub, then offer `upsert_income_source` with its year-to-date gross, 401(k) and federal withheld, only after showing the person the figures.
2. From the projection: `outcome` (refund, owe, even), the `statement` line by line only if asked, `estimatedPayments` found in the accounts (a February–April payment may be last year's balance due: ask, and record it with `update_tax_settings` priorYearPayments), `safeHarbor`, `breakEven` per job (alternatives, never added together), `ignores` (state tax, AMT) and `assumptions`.
3. `get_overview` → the next quarterly estimated payment and its date; `list_buckets` for the tax bucket's balance if there is one; `get_context` for each 1099 or business source's set-aside rate.
4. If income changed, re-read the sources (`get_context`) and `upsert_income_source` with the person's new expected total, then project again.

Answer with: the outcome and the number; whether a penalty is likely and why (safe harbor); the two ways to close a gap (extra withholding per paycheck at one job, or an estimated payment by its date) with the figure for each; what the set-aside bucket holds against what's needed. One table, then the caveats from `ignores`. Record the decision as a task (`upsert_task`, with the date and amount) once the person picks one.
