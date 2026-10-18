# Finometr for Claude Code

[Finometr](https://finometr.com) shows small businesses and freelancers where their money is going — across several bank accounts, cash and several businesses at once — and warns before the cash runs short. It brings together bank accounts connected through Open Banking (Europe), manual accounts and imported statements, keeps business units such as "Studio" and "Personal" apart, and forecasts each unit's balance from its planned payments.

This plugin connects Claude Code to your Finometr account. Ask about balances, transactions, the cash-flow forecast, spending by category, budgets and notifications in your own words, get a daily brief, and — when you allow it — let Claude create manual accounts, record transactions, plan payments, import bank statements, set categories and monthly targets. The skills have Claude say what it is about to write and wait for your yes, and Claude Code asks your permission before it calls a tool. Finometr's tools never delete anything.

## What's inside

- **MCP server** `finometr` → `https://finometr.com/mcp`, the same server as the Finometr connector in the Claude connectors directory.
- **Skills**
  - `finometr-daily-brief` — the morning brief in one call.
  - `finometr-setup` — finds what is missing (no accounts, an empty manual account, a bank connection that needs attention) and offers to fix it.
  - `finometr-import-statement` — reads a CSV, XLSX or PDF statement, previews the import with a dry run, then imports after you confirm.
- **Command** `/finometr:finometr-brief` — the daily brief.

## Install

Once Finometr is listed in Anthropic's plugin directory, install it from `/plugin` in Claude Code. Until then, clone this repository and start Claude Code with the plugin loaded:

```bash
git clone https://github.com/finometr-com/finometr-claude-plugin
claude --plugin-dir ./finometr-claude-plugin
```

Then run `/mcp`, pick `plugin:finometr:finometr` and sign in on the Finometr page that opens: check that it shows your account, choose Read, Write or both, and click Allow.

Without the plugin, you can add the server alone:

```bash
claude mcp add --transport http finometr https://finometr.com/mcp
```

Run it before starting Claude Code, or inside a running session prefixed with `!`, then restart the session, type `/mcp`, pick `finometr` and sign in.

## Your Finometr account

Finometr is in closed beta: your account has to be approved before you can allow access. Sign-in uses OAuth on Finometr's own page; Claude never receives your Finometr password or your bank login. Each client gets its own connection — the Claude app and Claude Code are connected separately — and every connection is listed in Finometr under Settings → Connected assistants, where you can revoke it.

## What the plugin sends and where

The plugin has no code of its own: no scripts, hooks or local servers. It points Claude Code at `https://finometr.com/mcp`. When Claude uses a Finometr tool, the request goes to that server, and what the tool returns goes to Claude under your agreement with Anthropic. What Finometr stores about the connection, and for how long, is in the [Privacy Policy](https://finometr.com/privacy), section "Connecting an AI assistant".

## Links

- Finometr: https://finometr.com
- Connecting an AI assistant: https://finometr.com/docs/assistants
- Privacy Policy: https://finometr.com/privacy
- Terms of Service: https://finometr.com/terms
- Support: support@finometr.com

## License

MIT — see [LICENSE](LICENSE).
