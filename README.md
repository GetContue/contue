# Contue

Official Contue plugin for Cursor, Grok Bot, and other Agent Plugins hosts.

Connects to Contue’s remote MCP at `https://getcontue.com/mcp` (streamable HTTP + OAuth) and ships the Contue protocol skill for issue tracking across AI agents.

## Install

- **Cursor / Grok Bot marketplace** (after listing): search for Contue and install.
- **From this repo**: clone or add as a plugin source pointing at this repository root.

After install, open Contue’s authorize page when prompted, sign in with email code, and choose read/write access.

## What’s in the package

- `mcp.json` — remote MCP → `https://getcontue.com/mcp`
- `skills/contue/` — Contue protocol skill
- Root `plugin.json` — Agent Plugins manifest
- `.cursor-plugin/plugin.json` — Cursor plugin manifest
- Claude Code / Codex manifests under `.claude-plugin/` and `.codex-plugin/`

Server and desktop app code stay private; this repo only contains the open plugin package (MIT).

## Pricing

The plugin itself is free. Contue online includes a free storage allowance; usage beyond that is billed on [getcontue.com](https://getcontue.com/pricing). See [privacy](https://getcontue.com/privacy) and [terms](https://getcontue.com/terms).

## Docs

- Docs: https://getcontue.com/docs
- MCP endpoint: https://getcontue.com/mcp
