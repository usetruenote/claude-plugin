# Truenote for Claude Code

Truenote keeps a household's whole financial picture in one place: bank, card, loan and investment accounts synced read-only through Plaid, plus the context an account can't tell (a spending plan, savings buckets, goals, income sources and their tax set-aside, notes, plans, uploaded paystubs and tax forms). This plugin connects Claude Code to it and adds four skills for the conversations people have most.

## What it does

- Adds the Truenote MCP server, `https://app.usetruenote.com/mcp` (OAuth; you sign in to Truenote and choose what Claude may see and do). That is the only server it talks to, and the only thing it sends anywhere is your tool calls to it.
- Skills: `/truenote:monthly-review`, `/truenote:can-we-afford`, `/truenote:quarterly-taxes`, `/truenote:setup`.

It runs no code of its own: no hooks, no scripts, nothing fetched from elsewhere.

## Install

```sh
claude plugin marketplace add usetruenote/claude-plugin
claude plugin install truenote@claude-plugin
```

Then in Claude Code run `/mcp`, pick `truenote` and choose **Authenticate**. Truenote opens in the browser: sign in (or try the sample household), choose what Claude may see, and allow it. You need a Truenote account: https://app.usetruenote.com (a 14-day trial, then $12 a month or $100 a year).

## What Claude can and can't do

Truenote never moves money; it has no endpoint that can. With write access Claude keeps Truenote's own records (categories, rules, buckets on Truenote's ledger, the plan, goals, notes). Every call lands in your activity log under Connected agents, where you can change or revoke access any time. Figures, the tax projection above all, are estimates from your own records, not tax, legal or financial advice.

Docs: https://usetruenote.com/connect/claude-code · Privacy: https://usetruenote.com/legal/privacy · Support: hello@usetruenote.com
