<h1 align="center">Pulso</h1>

<p align="center">
  <strong>AI agents that actually do things.</strong>
</p>

<p align="center">
  <a href="https://github.com/usepulso/pulso/releases"><img src="https://img.shields.io/github/v/release/usepulso/pulso?include_prereleases&style=for-the-badge" alt="GitHub release"></a>
  <a href="https://www.npmjs.com/package/@pulso/companion"><img src="https://img.shields.io/npm/v/@pulso/companion?style=for-the-badge&logo=npm&logoColor=white&color=cb3837" alt="npm"></a>
  <a href="https://github.com/usepulso/pulso/discussions"><img src="https://img.shields.io/github/discussions/usepulso/pulso?style=for-the-badge&logo=github" alt="Discussions"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-Proprietary-blue.svg?style=for-the-badge" alt="License"></a>
</p>

**Pulso** is a _personal AI agent platform_ that runs on your devices.
It answers you on the channels you already use (WhatsApp, Telegram, Slack, Discord, Signal, iMessage, Microsoft Teams, Google Chat, Matrix, LINE, Instagram, Messenger), controls your computer via the Companion daemon (screenshot, OCR, mouse, keyboard, shell, files, browser, smart home), and coordinates multi-agent teams in parallel — with any AI model you bring.

If you want AI agents that go beyond chat and actually execute tasks on your machine, across your channels, with your own API keys — this is it.

[Website](https://app.runpulso.com) · [Releases](https://github.com/usepulso/pulso/releases) · [Issues](https://github.com/usepulso/pulso/issues) · [Discussions](https://github.com/usepulso/pulso/discussions) · [@usepulso](https://x.com/usepulso)

## Install

Runtime: **Node >= 18**.

```bash
npm install -g @pulso/companion
pulso-companion login
```

The `login` command opens your browser for secure device authorization (RFC 8628 device code flow). Once approved, the Companion daemon connects and your agents gain full computer control.

Desktop app (menu bar): download from [GitHub Releases](https://github.com/usepulso/pulso/releases).

## Quick Start

```bash
# Install the Companion daemon
npm install -g @pulso/companion

# Authenticate via browser
pulso-companion login

# The daemon starts automatically — your agents can now:
#   - Control your computer (screenshot, mouse, keyboard, OCR)
#   - Run shell commands and manage files
#   - Control Spotify, Philips Hue, Sonos, Home Assistant
#   - Send iMessages, run macOS Shortcuts
#   - Browse the web (no extensions needed)

# Or just use the web/mobile app without Companion:
# https://app.runpulso.com
```

## Highlights

- **[Multi-channel inbox](https://app.runpulso.com)** — WhatsApp, Telegram, Slack, Discord, Signal, iMessage, Microsoft Teams, Google Chat, Matrix, LINE, Instagram, Messenger. Full agent loop on every channel — not just text relay.
- **[Companion daemon](https://www.npmjs.com/package/@pulso/companion)** — Screenshot, OCR, mouse, keyboard, shell, files, browser, audio, clipboard. Any app. Any workflow. macOS, Windows, Linux.
- **[Multi-agent teams](https://app.runpulso.com)** — Parallel swarms with DAG orchestration. Smart model routing picks the right model for each task. 140+ templates. Visual builder.
- **[Knowledge graph](https://app.runpulso.com)** — Entities and relationships extracted from conversations. Semantic search by meaning. Natural decay keeps memory fresh. Up to 100K items.
- **[Smart home + media](https://app.runpulso.com)** — Philips Hue lights, Sonos multi-room, Spotify playback, Home Assistant for locks, blinds, climate. Local control.
- **[24/7 automations](https://app.runpulso.com)** — Event-driven triggers that run full agent loops. Email, schedule, webhook, or custom events. Budget caps per trigger.
- **[200+ AI models](https://app.runpulso.com)** — Anthropic, OpenAI, Google, DeepSeek, Mistral, Groq, Ollama, OpenRouter. BYOK — your keys, your data. Optional Pulso Credits if you don't want to manage keys.
- **[MCP servers](https://app.runpulso.com)** — Connect external tool servers via the Model Context Protocol. Up to 50 servers.

## Downloads

| Platform | Download |
|:--|:--|
| **macOS** (menu bar app) | [GitHub Releases](https://github.com/usepulso/pulso/releases) — `.dmg` |
| **Companion CLI** (macOS, Windows, Linux) | `npm install -g @pulso/companion` |
| **Web** | [app.runpulso.com](https://app.runpulso.com) |
| **iOS** | [App Store](https://apps.apple.com/app/pulso-ai-agents/id6740000000) |
| **Android** | [Google Play](https://play.google.com/store/apps/details?id=com.runpulso.app) |

## Everything we built

### Channels

- **WhatsApp** — Meta Business API, HMAC-SHA256 webhook verification, full agent loop with tool use.
- **Telegram** — Auto webhook registration, QR pairing, ReAct loop (10 iterations), inline images.
- **Slack** — HMAC + replay protection, thread replies, rich formatting.
- **Discord** — Full bot integration with slash commands and thread support.
- **Signal** — End-to-end encrypted messaging via signal-cli.
- **iMessage** — Send and receive via Companion daemon on macOS.
- **Microsoft Teams** — Bot Framework integration.
- **Google Chat** — Workspace app integration.
- **Matrix** — Federation-compatible bridge.
- **LINE, Instagram, Messenger** — Platform API integrations.

### Companion daemon

- **Computer vision** — Screenshot capture, OCR text extraction, visual element detection.
- **Input control** — Mouse move/click/drag, keyboard typing, hotkeys, scroll.
- **Shell execution** — Run any command, capture output, environment-aware (nvm/volta/homebrew).
- **File management** — Read, write, move, copy, delete, search, zip/unzip, watch.
- **Browser automation** — Open URLs, navigate, screenshot pages, extract content. No extensions.
- **App control** — Launch, quit, list running apps, window management, focus.
- **Smart home** — Philips Hue (lights, scenes, brightness, color), Sonos (multi-room, queue, volume), Spotify (playback, playlists, search), Home Assistant (any device).
- **Communication** — iMessage send/receive, Contacts search, FaceTime.
- **Audio** — System volume, input/output device selection, text-to-speech.
- **macOS Shortcuts** — Trigger any Shortcut by name.
- **System** — Notifications, clipboard, dark mode, Do Not Disturb, lock screen, battery, Wi-Fi.
- **Cross-platform** — macOS (AppleScript + shell), Windows (PowerShell), Linux (X11/Wayland/GNOME/KDE).

### Agent runtime

- **ReAct loop** — Observe-think-act cycle with tool execution, up to 20 turns per agent.
- **Multi-agent orchestration** — YAML-defined DAG workflows, parallel execution (up to 4 concurrent agents), upstream output injection.
- **Smart model routing** — CascadeRouter scores task complexity and picks the optimal model tier (fast/smart/genius).
- **350+ tools** — Every Companion command, channel action, memory operation, and integration is a callable tool.
- **140+ swarm templates** — Pre-built multi-agent workflows across 16 categories.

### Memory

- **Flat memories** — Key-value facts extracted from conversations.
- **Knowledge graph** — Entities and relationships with importance scoring.
- **Semantic search** — Vectorize-powered similarity search across all memories.
- **Auto-extraction** — Post-chat extraction via fast model.
- **Natural decay** — Importance decays after 7 days stale, pruned at threshold, capped at plan limit.

### Security

- **AES-256-GCM** encryption for stored credentials and TOTP secrets.
- **TLS 1.3** for all API communication.
- **V8 isolates** — Cloudflare Workers runtime isolation.
- **2FA** — TOTP-based two-factor authentication with encrypted backup codes.
- **Device authorization** — RFC 8628 device code flow for Companion login. No tokens in URLs.
- **Token revocation** — JTI-based instant revocation for companion tokens.
- **Audit logging** — All authentication events logged.
- **Security audited** — 21 vulnerabilities found and fixed (3 critical, 5 high).
- **Credential storage** — `~/.pulso/credentials.json` with 0600 permissions.

### Infrastructure

- **Edge runtime** — Cloudflare Workers with D1 (SQLite), Durable Objects (WebSocket sessions), R2 (file storage).
- **Durable Object sessions** — Persistent WebSocket connections for Companion and real-time chat.
- **MCP server** — Model Context Protocol support for external tool servers.
- **Webhook adapters** — Per-channel webhook handlers with platform-specific verification.
- **Rate limiting** — Per-IP and per-user rate limits on all endpoints.

## Community

- [GitHub Issues](https://github.com/usepulso/pulso/issues) — Bug reports and feature requests.
- [GitHub Discussions](https://github.com/usepulso/pulso/discussions) — Questions, ideas, and feedback.
- [@usepulso](https://x.com/usepulso) — Updates and announcements.

## Security

Found a vulnerability? Please report it responsibly. See [SECURITY.md](SECURITY.md) for our disclosure policy and response timelines.

## License

Proprietary. See [LICENSE](LICENSE) for details.

<sub>Built by [CodeAhead](https://codeahead.pt) in Portugal · © 2026 CodeAhead Lda</sub>
