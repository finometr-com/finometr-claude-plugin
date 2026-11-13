# Finometr for Claude Code

[Finometr](https://finometr.com/?utm_source=github&utm_medium=readme&utm_campaign=claude-plugin) shows small businesses, freelancers and households where their money is going, across several bank accounts, cash and several businesses at once, and warns before the cash runs short. It brings together bank accounts connected through finAPI (around 2,900 banks in Germany via PSD2), manual accounts and imported statements, keeps business units such as "Studio" and "Personal" apart, and forecasts each unit's balance from its planned payments.

This plugin connects Claude Code to your Finometr account. Ask about balances, transactions, the cash-flow forecast, spending by category, budgets and notifications in your own words, get a daily brief, and — when you allow it — let Claude create manual accounts and business units, record transactions, plan payments, import bank statements, set categories and monthly targets. The skills have Claude say what it is about to write and wait for your yes, and Claude Code asks your permission before it calls a tool. Finometr's tools can remove only what was added by hand, and it can be restored; bank transactions are never removed.

## What's inside

- **MCP server** `finometr` → `https://finometr.com/mcp`, the same server as the Finometr connector in the Claude connectors directory.
- **Skills**
  - `finometr-daily-brief` — the morning brief in one call.
  - `finometr-setup` — sets Finometr up with you: what it needs first (an account, transactions in it, a bank connection that works), then optional steps such as a unit of its own for your business or a monthly target, each one to accept or skip. Say "Set up Finometr".
  - `finometr-import-statement` — reads a CSV, XLSX or PDF statement, previews the import with a dry run, then imports after you confirm.
- **Command** `/finometr:finometr-brief` — the daily brief.

## Install

Install Finometr from `/plugin` in Claude Code. Then run `/mcp`, pick `plugin:finometr:finometr` and sign in on the Finometr page that opens: check that it shows your account, choose Read, Write or both, and click Allow.

Without the plugin, you can add the server alone:

```bash
claude mcp add --transport http finometr https://finometr.com/mcp
```

Run it before starting Claude Code, or inside a running session prefixed with `!`, then restart the session, type `/mcp`, pick `finometr` and sign in.

## Your Finometr account

No Finometr account yet? Create one on the sign-in page that opens when you connect, or on [finometr.com](https://finometr.com/?utm_source=github&utm_medium=readme&utm_campaign=claude-plugin). Every new account starts with 30 days of Pro, no credit card required.

Sign-in uses OAuth on Finometr's own page; Claude never receives your Finometr password or your bank login. Each client gets its own connection — the Claude app and Claude Code are connected separately — and every connection is listed in Finometr under Settings → Connected assistants, where you can revoke it.

## What the plugin sends and where

The plugin has no code of its own: no scripts, hooks or local servers. It points Claude Code at `https://finometr.com/mcp`. When Claude uses a Finometr tool, the request goes to that server, and what the tool returns goes to Claude under your agreement with Anthropic. What Finometr stores about the connection, and for how long, is in the [Privacy Policy](https://finometr.com/privacy?utm_source=github&utm_medium=readme&utm_campaign=claude-plugin), section "Connecting an AI assistant".

## Links

- Finometr: https://finometr.com/?utm_source=github&utm_medium=readme&utm_campaign=claude-plugin
- Connecting an AI assistant: https://finometr.com/docs/assistants?utm_source=github&utm_medium=readme&utm_campaign=claude-plugin
- Privacy Policy: https://finometr.com/privacy?utm_source=github&utm_medium=readme&utm_campaign=claude-plugin
- Terms of Service: https://finometr.com/terms?utm_source=github&utm_medium=readme&utm_campaign=claude-plugin
- Support: https://finometr.com/support?utm_source=github&utm_medium=readme&utm_campaign=claude-plugin (or support@finometr.com)

## License

MIT — see [LICENSE](LICENSE).
