# ditto.audio MCP server

Text-to-speech for AI agents. Connect [ditto.audio](https://ditto.audio) to Claude, ChatGPT, Cursor,
VS Code, Codex or any Model Context Protocol client. Your agent can then browse voices and
synthesize speech that comes back as short-lived download links, never as audio bytes in the chat.

**Endpoint:** `https://mcp.ditto.audio` (Streamable HTTP)

You sign in with your ditto.audio account the first time your client connects. There is no key to
paste. Each connection appears under [Account -> API keys](https://ditto.audio/account/api-keys) as
a connected app, draws on the same monthly allowance as your keys, and can be disconnected there.

## Install

| Client | How |
| --- | --- |
| Claude (web, desktop, mobile, and Claude Code signed in with a Claude plan) | [Add to Claude](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=ditto.audio&connectorUrl=https%3A%2F%2Fmcp.ditto.audio), then Connect and sign in |
| Cursor | [Add to Cursor](https://cursor.com/install-mcp?name=ditto&config=eyJ1cmwiOiJodHRwczovL21jcC5kaXR0by5hdWRpbyJ9) |
| VS Code | [Install in VS Code](https://insiders.vscode.dev/redirect/mcp/install?name=ditto&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.ditto.audio%22%7D) |
| Claude Code (API key or Console login) | `claude mcp add --transport http --scope user ditto https://mcp.ditto.audio`, then `/mcp` -> Authenticate |
| Claude Code (plugin) | `/plugin marketplace add ditto-audio/ditto-mcp` then `/plugin install ditto@ditto-audio` |
| ChatGPT | Settings -> Security and login -> Developer mode on, then [chatgpt.com/plugins](https://chatgpt.com/plugins) -> + -> `https://mcp.ditto.audio` |
| Codex | `codex mcp add ditto --url https://mcp.ditto.audio` then `codex mcp login ditto` |

Headless (CI, servers): skip the sign-in and send an API key from
[your API keys page](https://ditto.audio/account/api-keys) as `Authorization: Bearer ditto_sk_live_...`.

## Tools

| Tool | What it does |
| --- | --- |
| `list_voices` | Browse the voice catalogue, and your own cloned or trained voices (marked `owned`) |
| `list_languages` | Every language code and which engines speak it |
| `text_to_speech` | Synthesize text and get a download URL (MP3 by default; FLAC/WAV and more on request) |
| `create_speech_batch` | Queue up to 1000 texts at once |
| `get_speech_batch` | Progress of a batch |
| `get_speech_batch_results` | Download URLs for a batch's items |
| `cancel_speech_batch` | Stop a batch; finished items keep their audio |

Full reference, generated from the live server: https://ditto.audio/docs/mcp

## What is in this repository

| Path | For |
| --- | --- |
| `server.json` | The official MCP Registry entry (`audio.ditto/tts`) |
| `.claude-plugin/marketplace.json`, `plugins/ditto/` | Claude Code plugin marketplace |
| `.cursor-plugin/plugin.json`, `mcp.json` | Cursor Marketplace plugin |

## Support

Email [support@ditto.audio](mailto:support@ditto.audio) or see [ditto.audio/support](https://ditto.audio/support).
Using the server is subject to the [terms](https://ditto.audio/terms) and the
[privacy policy](https://ditto.audio/privacy).

Copyright (c) 2026 ditto.audio. All rights reserved (see `LICENSE`).
