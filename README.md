# Finometr for Claude Code

[Finometr](https://finometr.com/?utm_source=github&utm_medium=readme&utm_campaign=claude-plugin) shows small businesses, freelancers and households where their money is going, across several bank accounts, cash and several businesses at once, and warns before the cash runs short. It brings together bank accounts connected through finAPI (around 2,900 banks in Germany via PSD2), manual accounts and imported statements, keeps business units such as "Studio" and "Personal" apart, and forecasts each unit's balance from its planned payments.

This plugin connects Claude Code to your Finometr account. Ask about balances, transactions, the cash-flow forecast, spending by category, budgets, projects and notifications in your own words, and get a daily brief. When you allow it, Claude can also create manual accounts and business units, record transactions, plan one-off and recurring payments, import bank statements, set categories and notes, log hours on projects, set monthly targets and manage the roles of people in your units. The skills have Claude say what it is about to write and wait for your yes, and Claude Code asks your permission before it calls a tool.

## What the Finometr tools cover

- **85 tools**: 32 that read and 53 that write, plus three prompts (`daily_briefing`, `get_started`, `weekly_review`). The write tools work only when you tick Write at sign-in.
- **Periods**: `search_transactions` and `set_category` take a period of up to 366 days. A longer one is clipped to its last 366 days, and the answer's note says so. Spending by category and budget targets cover one calendar month per call; the cash-flow forecast looks 30, 60 or 90 days ahead.
- **Custom categories**: on Pro and higher (the plan of the unit's owner), a unit can have custom categories inside the standard ones, for spending a standard category lumps together. Finometr's AI sorts new transactions into them by name and description. `set_category` moves earlier rows, up to 200 a call; with a dry run it only counts the rows a filter finds and shows a sample. A unit has up to 25 active custom categories on Pro and 50 on Team. Category names and descriptions go to Finometr's AI provider.
- **Removing and restoring**: removing is soft. Manual and planned transactions, manual accounts (with their rows, recurring payments and plans), empty projects, recurring payments, time entries and shared copies can be removed and brought back: `list_removed_transactions`, `list_removed_accounts` and `list_removed_projects` list what can come back, and a `restore_*` tool brings each back. Custom categories are archived, not deleted. Bank transactions are never removed or edited; only their category and note change. Taking a person out of a unit has no restore: coming back takes a new invitation from the Finometr app.
- **Projects, hours and people**: projects with planned and actual income, costs and hours, time entries, and the people of your units with their roles (owner, admin, editor, viewer). Bank connections and new invitations are made in the Finometr app.
- **Duplicates**: a statement import is a dry run by default, and rows already imported count as duplicates. A manual or planned transaction identical to a live one is not added twice unless you confirm a second one.

## What's inside

- **MCP server** `finometr` at `https://finometr.com/mcp`, the same server as the Finometr connector in the Claude connectors directory.
- **Skills**
  - `finometr-daily-brief`: the morning brief in one call.
  - `finometr-setup`: sets Finometr up with you. First what it needs (an account, transactions in it, a bank connection that works), then optional steps such as a unit of its own for your business, a monthly target or a custom category, each one to accept or skip. Say "Set up Finometr".
  - `finometr-import-statement`: reads a CSV, XLSX or PDF statement, previews the import with a dry run, then imports after you confirm.
- **Command** `/finometr:finometr-brief`: the daily brief.

## Install

Install Finometr from `/plugin` in Claude Code. Then run `/mcp`, pick `plugin:finometr:finometr` and sign in on the Finometr page that opens: check that it shows your account, tick Read, Write or both, and click Allow. With Read alone, the write tools are refused.

Without the plugin, you can add the server alone:

```bash
claude mcp add --transport http finometr https://finometr.com/mcp
```

Run it before starting Claude Code, or inside a running session prefixed with `!`, then restart the session, type `/mcp`, pick `finometr` and sign in.

## Your Finometr account

No Finometr account yet? Create one on the sign-in page that opens when you connect, or on [finometr.com](https://finometr.com/?utm_source=github&utm_medium=readme&utm_campaign=claude-plugin). Every new account starts with 30 days of Pro, no credit card required. The connection to an assistant is part of Pro and higher plans.

Sign-in uses OAuth 2.1 with PKCE on Finometr's own page; Claude never receives your Finometr password or your bank login. Each client gets its own connection (the Claude app and Claude Code are connected separately), and every connection is listed in Finometr under Settings → Connected assistants, where you can revoke it.

## What the plugin sends and where

The plugin has no code of its own: no scripts, hooks or local servers. It points Claude Code at `https://finometr.com/mcp`. When Claude uses a Finometr tool, the request goes to that server, and what the tool returns goes to Claude under your agreement with Anthropic. What Finometr stores about the connection, and for how long, is in the [Privacy Policy](https://finometr.com/privacy?utm_source=github&utm_medium=readme&utm_campaign=claude-plugin), section "Connecting an AI assistant".

## Links

- Finometr: https://finometr.com/?utm_source=github&utm_medium=readme&utm_campaign=claude-plugin
- Connecting an AI assistant: https://finometr.com/docs/assistants?utm_source=github&utm_medium=readme&utm_campaign=claude-plugin
- Privacy Policy: https://finometr.com/privacy?utm_source=github&utm_medium=readme&utm_campaign=claude-plugin
- Terms of Service: https://finometr.com/terms?utm_source=github&utm_medium=readme&utm_campaign=claude-plugin
- Support: https://finometr.com/support?utm_source=github&utm_medium=readme&utm_campaign=claude-plugin (or support@finometr.com)

## License

MIT, see [LICENSE](LICENSE).
