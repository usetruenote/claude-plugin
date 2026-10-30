---
name: can-we-afford
description: Whether the household can afford a purchase, a trip, a monthly commitment or a change in income, and where the money would come from. Use for "can we afford", "should we buy", "what if we", "how long until we can".
argument-hint: "<what, how much, when>"
---

Answer an affordability question from Truenote's figures, not from rules of thumb.

1. `get_context` for the household (goals, income sources, checklist), then `get_overview`: cash, this month's plan at a glance, the emergency fund in months, bills in the next two weeks, dated tasks.
2. `get_plan`: what regular take-home is, what's planned, what's unplanned each month, and what frees up when lines end. A monthly commitment competes with `unplanned`; a one-off competes with cash, buckets and goals.
3. `list_buckets`: is there a bucket for this (vacation, car, home maintenance)? If so the answer starts with its balance, target and date, and `unassigned`.
4. `list_tasks` (open) and the goals in context: what else is spoken for in the same window (a tax payment, an exercise, a tuition date).
5. For a change in income, `get_tax_projection` too: the set-aside and withholding change with it.

Give a yes, a no, or a "yes if": the amount, the source (which bucket, which account, which month's unplanned), what it delays (a goal's date, the emergency fund's months), and what it doesn't touch. Show the arithmetic in one short table. If the honest answer is "not from the plan as it stands", say what line would have to change and by how much.

Offer, don't do: a new bucket or target (`upsert_bucket`), a plan line (`upsert_plan_line`), a checklist task with the date (`upsert_task`), a goal (`upsert_goal`). Write only after the person agrees. Truenote never moves money at a bank.
