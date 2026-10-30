---
name: monthly-review
description: A month of the household's money against its spending plan, with what to change. Use when the person asks how a month went, where the money went, or for a monthly, end-of-month or budget review.
---

Run a monthly review in Truenote. Default to the month that just ended; "this month" means the current one.

1. `get_overview` for where things stand now; `get_context` once, for the household, ids and open checklist.
2. `plan_vs_actual` for the month: bills (paid, due, unpaid), set-asides (met, in progress, short), everyday spending against the plan and the three-month average, `chargedToBuckets`, `left`.
3. Where everyday is over, `spending_summary` for that month grouped by category, then merchant for the top category. Name the two or three places the money went; skip the rest.
4. `list_review_items` (open): anything bucket automation left for the person to decide. Offer to resolve each with `resolve_review_item` after they answer.
5. `get_recurring` only if a bill or subscription looks new, doubled or missing.

Report in this order: the one-line verdict (what was left, or how far over), bills, set-asides, everyday by category with the plan figure beside each, what needs a decision. Say "charged to buckets" spending is paid for, not overspending. Use the plan's own words (the group and line names).

Then propose at most three changes, each as a specific tool call the person can approve: a plan line amount (`upsert_plan_line`), a bucket move (`move_between_buckets`), a rule (`create_rule`), a note (`add_note`). Don't write anything until they say yes. Never move money at a bank; Truenote can't.
