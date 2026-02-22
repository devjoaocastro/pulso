<p align="center">
  <a href="https://app.runpulso.com">
    <img src="docs/header.png" alt="Pulso" width="200" />
  </a>
</p>

<h1 align="center">Pulso</h1>

<p align="center">
  The cloud-native AI agent platform that actually does things.<br />
  <em>ChatGPT tells you how. Pulso does it for you.</em>
</p>

<p align="center">
  <a href="https://github.com/usepulso/pulso/releases"><img src="https://img.shields.io/github/v/release/usepulso/pulso?include_prereleases&style=for-the-badge" alt="GitHub release"></a>
  <a href="https://www.npmjs.com/package/@pulso/companion"><img src="https://img.shields.io/npm/v/@pulso/companion?style=for-the-badge&logo=npm&logoColor=white&color=cb3837" alt="npm"></a>
  <a href="https://github.com/usepulso/pulso/discussions"><img src="https://img.shields.io/github/discussions/usepulso/pulso?style=for-the-badge&logo=github" alt="Discussions"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-Proprietary-blue.svg?style=for-the-badge" alt="License"></a>
</p>

<p align="center">
  <a href="https://app.runpulso.com">Try the App</a> ·
  <a href="#quick-start">Quick Start</a> ·
  <a href="https://github.com/usepulso/pulso/releases">Downloads</a> ·
  <a href="https://github.com/usepulso/pulso/discussions">Discussions</a> ·
  <a href="https://x.com/usepulso">Twitter</a>
</p>

---

## The Problem

Every AI tool in 2026 is the same: you ask a question, it gives you an answer.

_"How do I unsubscribe from marketing emails?"_ — here are 5 steps.
_"When is my next meeting?"_ — I don't have access to your calendar.

You end up doing everything yourself anyway.

## What Pulso Does

Pulso is a cloud-native multi-agent orchestration platform that connects to your services and executes tasks. Not instructions. Not suggestions. **Actions.**

```
You:    "Check my email, summarize anything urgent, and block my calendar
         for the contract review"

Pulso:  Done. 3 agents worked on this:

        Email Agent (Claude Sonnet 4.6):
           Found 3 urgent emails out of 47 unread.
           1. Client contract — needs signature by Friday
           2. Server alert — CPU spike on prod (resolved)
           3. Team lead asking for Q1 report

        Calendar Agent (GPT-4o):
           Blocked 2h tomorrow at 10am for "Contract Review"
           No conflicts found.

        Draft Agent (Gemini Flash):
           Drafted reply for the contract email.
           Marked the server alert as read.

        Total cost: $0.003 | Duration: 4.2s
        Want me to send the draft?
```

Three different AI models. Working in parallel. Costing less than a penny.

## How Pulso Compares

| | **OpenClaw** | **CrewAI** | **Claude Code** | **Pulso** |
|---|:---:|:---:|:---:|:---:|
| **Built for** | Developers | Python devs | Terminal users | Everyone |
| **Runtime** | Local Node.js | Python scripts | Terminal sessions | Cloud edge (zero infra) |
| **Always on?** | Needs laptop/VPS 24/7 | No — runs then stops | No — terminal session | Yes — always running |
| **Setup time** | 10-20 min | 15 min | 5 min | 30 seconds (browser) |
| **Multi-agent** | Basic routing | Python DAG | Single agent | Visual DAG builder + parallel |
| **Mobile app** | Push-to-talk only | None | None | Full native app (iOS/Android) |
| **Channels** | 15 | None | None | 12 (WhatsApp, Telegram, Slack...) |
| **Computer control** | Limited | None | Sandboxed | Full (screenshot, mouse, keyboard, OCR) |
| **Knowledge graph** | Text files | None | Project memory | Entity-relation graph + vectors |
| **Image generation** | Via tools | Via tools | None | Native (Gemini, GPT, FLUX, Seedream) |
| **Cost control** | Manual | Manual | Subscription | Hard budgets per agent + swarm |

## Quick Start

### Use the cloud (recommended)

1. Go to [app.runpulso.com](https://app.runpulso.com)
2. Sign up (free)
3. Add your LLM API key (AES-256 encrypted)
4. Start chatting — or build visual workflows

### Want computer control? Install the Companion:

```bash
npm install -g @pulso/companion
pulso-companion login
```

The `login` command opens your browser for secure device authorization ([RFC 8628](https://datatracker.ietf.org/doc/html/rfc8628)). Once approved, the daemon connects and your agents gain full computer control.

## Downloads

| Platform | Download |
|:--|:--|
| **macOS** | [Apple Silicon `.dmg`](https://github.com/usepulso/pulso/releases/latest) · [Intel `.dmg`](https://github.com/usepulso/pulso/releases/latest) |
| **Windows** | [`.msi`](https://github.com/usepulso/pulso/releases/latest) |
| **Linux** | [`.AppImage`](https://github.com/usepulso/pulso/releases/latest) · [`.deb`](https://github.com/usepulso/pulso/releases/latest) |
| **Android** | [Google Play](https://play.google.com/store/apps/details?id=com.runpulso.app) · [`.apk`](https://github.com/usepulso/pulso/releases/latest) |
| **iOS** | Coming soon |
| **Web** | [app.runpulso.com](https://app.runpulso.com) |
| **Companion CLI** | `npm install -g @pulso/companion` |

## Multi-Agent Orchestration

Agents work together. Pulso uses a DAG (Directed Acyclic Graph) to schedule agent execution. Agents with no dependencies run in parallel. Results flow through the graph automatically.

```
                         ┌─────────────────┐
                    ┌───▶│  Luna (Security) │───┐
                    │    └─────────────────┘    │
┌──────────┐       │    ┌─────────────────┐    │    ┌─────────────────┐
│   Task   │───────┼───▶│ Atlas (Reviewer) │───┼───▶│ Nova (Reporter) │
│  Input   │       │    └─────────────────┘    │    └─────────────────┘
└──────────┘       │    ┌─────────────────┐    │
                    └───▶│Hermes (Notifier) │    │
                         └─────────────────┘    │
                                                │
                         Parallel agents ───────┘
```

Luna + Atlas + Hermes run simultaneously. Nova waits for Luna and Atlas to finish, then synthesizes their results. All with budget enforcement — if any agent hits its spending limit, execution stops gracefully.

**Smart model routing** — Set `model: auto` and Pulso picks the right model for the job. Fast tasks get a fast model (~$0.001). Complex reasoning gets a powerful model (~$0.10). You get top-tier quality when you need it, speed when you don't.

## Channel Adapters

Talk to Pulso from wherever you already are:

| Channel | Status | Features |
|:--|:--|:--|
| **Web Chat** | Production | Full-featured chat UI with streaming |
| **Telegram** | Production | Auto webhook, QR pairing, full agent loop |
| **WhatsApp** | Production | Meta Business API, verified webhooks |
| **Slack** | Production | Thread replies, rich formatting |
| **Discord** | Functional | Bot integration, slash commands |
| **Signal** | Functional | Privacy-first messaging |
| **Teams** | Functional | Microsoft Teams integration |
| **Google Chat** | Functional | Google Workspace integration |
| **Matrix** | Functional | Decentralized protocol support |
| **Instagram** | Functional | Meta API integration |
| **Messenger** | Functional | Meta API integration |
| **LINE** | Functional | LINE messaging API |

Plus: **iMessage** via the Companion daemon, **Webhook API** for custom integrations.

## Supported Providers

Use any LLM. Mix different models in the same workflow:

| Provider | Models | Best For |
|:--|:--|:--|
| **Anthropic** | Claude Opus 4.6, Sonnet 4.6, Haiku 4.5 | Deep reasoning, coding, 200K context |
| **OpenAI** | GPT-4o, GPT-4o Mini, o1, o1-mini | General purpose, vision, function calling |
| **Google** | Gemini 2.5 Pro, Gemini 2.5 Flash | Multimodal, fast, 1M context, image gen |
| **DeepSeek** | V3 (chat + reasoner) | Cost-effective reasoning, 128K context |
| **Mistral** | Large, Codestral, Small | Open-weight, coding |
| **Meta** | Llama 3.3 70B, Llama 3.1 405B | Free, private, self-hosted |
| **Ollama** | Any local model | Fully offline, zero API cost |
| **OpenRouter** | 200+ models from all providers | Maximum flexibility, unified API |

**Native image generation** — Pulso auto-detects which image models you have access to: Gemini Flash Image, GPT Image, FLUX 1.1 Pro, Seedream 4.5, FLUX Schnell (free via Workers AI).

## Companion Daemon

[`@pulso/companion`](https://www.npmjs.com/package/@pulso/companion) — a local daemon that bridges your machine to Pulso.

```bash
npm install -g @pulso/companion
pulso-companion login
```

**55+ commands** including:

- **Computer vision** — Screenshot, OCR, mouse, keyboard, drag, scroll
- **Shell execution** — Run any command, environment-aware (nvm/volta/homebrew)
- **File management** — Read, write, move, copy, delete, search, zip/unzip
- **Browser automation** — Open URLs, navigate, screenshot pages. No extensions
- **App control** — Launch, quit, window management, focus
- **Smart home** — Philips Hue, Sonos, Spotify, Home Assistant
- **Communication** — iMessage send/receive, Contacts, FaceTime
- **macOS Shortcuts** — Trigger any Shortcut by name
- **System** — Notifications, clipboard, dark mode, Do Not Disturb, lock screen

**Cross-platform:** macOS, Windows, Linux. Also available as a **native menu bar app** ([download](https://github.com/usepulso/pulso/releases)).

## Memory System

Three-tier memory architecture:

| Tier | Lifetime | Use Case |
|:--|:--|:--|
| **Session** | Single conversation | Context, intermediate results |
| **Persistent** | Forever | Preferences, learned patterns, task history |
| **Semantic** | Forever | Similarity search, knowledge retrieval |

**Knowledge graph** — Beyond flat memory, Pulso maintains entities and relationships extracted from conversations. When you mention "John is my CTO" and later "John prefers async standups", Pulso connects these facts into a queryable graph with importance scoring and automatic decay.

## Security

| Feature | Details |
|:--|:--|
| **Encryption** | AES-256-GCM for all stored credentials with unique salt + IV |
| **Transport** | TLS 1.3 for all API communication |
| **Isolation** | V8 isolates — each request in its own sandbox |
| **Authentication** | 2FA (TOTP), device authorization (RFC 8628) |
| **Token management** | JTI-based instant revocation, 0600 file permissions |
| **Audit** | All authentication events logged |
| **Hardened** | 21 vulnerabilities found and fixed (3 critical, 5 high) |
| **BYOK** | Your API keys, your models, your data. Zero shared credentials |

Found a vulnerability? Please report it responsibly. See [SECURITY.md](SECURITY.md).

## Architecture

```
  Mobile / Web / Companion / Cloud API
                    │
                    ▼
  ┌─────────────────────────────────────┐
  │       Orchestration Engine          │
  │                                     │
  │  ├─ DAG Scheduler                   │
  │  ├─ Model Router                    │
  │  ├─ Budget Enforcement              │
  │  └─ Agent Sandbox                   │
  └──────────┬──────────────────────────┘
             │
     ┌───────┼───────┬──────────┐
     ▼       ▼       ▼          ▼
 Providers  Tools  Memory   Protocols
 Claude     350+   Session  MCP Server
 GPT        Web    Graph    MCP Client
 Gemini     Shell  Vectors
 +200       ...
```

## Pricing

| | **Solo** | **Swarm** | **Fleet** |
|---|:---:|:---:|:---:|
| | Free | **$19**/mo | **$49**/mo |
| Channels | 1 | 12 | Unlimited |
| Agent Teams | — | Up to 10 | Up to 20 |
| Memory | 100 items | 10,000 | 100,000 |
| Companion | — | Included | Included |
| Automations | — | 10 triggers | 100 triggers |
| MCP Servers | — | 5 | 50 |
| Credits included | — | $5/mo | $20/mo |

All plans include **BYOK** (Bring Your Own Key) — your keys, your models, your data.

## Community

- [GitHub Issues](https://github.com/usepulso/pulso/issues) — Bug reports and feature requests
- [GitHub Discussions](https://github.com/usepulso/pulso/discussions) — Questions, ideas, feedback
- [@usepulso](https://x.com/usepulso) — Updates and announcements

## License

Proprietary. See [LICENSE](LICENSE).

---

<p align="center">
  <strong>Pulso</strong> — The AI agent platform that works for you, not the other way around.
</p>

<p align="center">
  <sub>Built by <a href="https://codeahead.pt">CodeAhead</a> in Portugal · © 2026 CodeAhead Lda</sub>
</p>

<p align="center">
  <sub>
    <a href="https://app.runpulso.com">Website</a> ·
    <a href="https://github.com/usepulso/pulso">GitHub</a> ·
    <a href="https://x.com/usepulso">Twitter</a>
  </sub>
</p>
