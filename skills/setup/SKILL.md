---
name: setup
description: Set up a new Truenote household in conversation: bank, household, income, bills, a goal, buckets. Use right after connecting, or whenever get_overview or get_context carry a setup section.
---

Set the person up with them, not for them.

1. `get_overview`. If it has no `setup` section, say Truenote is set up and offer `/truenote:monthly-review` instead. Otherwise take `setup.items` in order; each carries `ask` (what to find out) and `tools` (what to write with).
2. Before each item, read what the bank data already shows (`list_accounts`, `get_recurring`, `spending_summary` for the last three months) and propose from it: the paychecks it sees are the income sources, the recurring charges are the bills, the savings account is where buckets go. Ask one or two questions at a time, in plain words, and only for what the data can't tell (who's in the household, the business, the tax set-aside rate, a goal).
3. Say what you're about to save before saving it, save with the item's tools (`update_profile`, `upsert_entity`, `upsert_income_source`, `upsert_plan_line`, `upsert_goal`, `upsert_bucket`), and tell them what you saved. If a write is refused for scope, ask them to allow writing for this connection in Truenote under Connected agents.
4. A bank is the one thing you can't do: connecting one happens in Truenote's app (Accounts → Connect). Say so and continue with what's there.
5. When `setup` is gone, read the overview back in a few lines and suggest three things to ask next.
