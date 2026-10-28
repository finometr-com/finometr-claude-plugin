# Finometr plugin for ChatGPT

The package for the ChatGPT plugin directory (roadmap#470). It connects ChatGPT
to the same Finometr MCP server as the Claude plugin, at
`https://finometr.com/mcp`, with OAuth: ChatGPT registers through its client
metadata document (CIMD), so no client id or secret lives here.

- `plugin.json`: the manifest with the directory listing under
  `extensions.com.openai`.
- `mcp.json`: the server.
- `skills/`: the Claude plugin's three skills, without the Claude Code parts.
  `finometr-setup` is the onboarding skill.
- `assets/`: the logo and composer icon.

The Claude plugin's `/finometr-brief` command is not here: ChatGPT plugins
have no commands, and the daily brief skill covers it.

## Build the archive

Files go at the root of the ZIP:

```bash
cd chatgpt && zip -r ../finometr-chatgpt.zip plugin.json mcp.json skills assets
```

Check it before submitting in ChatGPT: Plugins → Add → Upload plugin archive.
To try it against staging, change the server URL in `mcp.json` to
`https://finometr-staging.web.app/mcp` in a copy, and `name`/`displayName` so
it does not collide with the production plugin. Never commit that copy.
