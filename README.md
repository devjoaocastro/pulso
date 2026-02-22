<p align="center">
  <img src="https://app.runpulso.com/icon.png" alt="Pulso" width="120" />
</p>

<h1 align="center">Pulso</h1>

<h3 align="center">AI agents that actually do things.</h3>

<p align="center">
  <a href="https://app.runpulso.com"><strong>Get Started Free</strong></a>
</p>

<br />

<p align="center">
  <a href="https://app.runpulso.com"><img src="https://img.shields.io/badge/Try_Pulso-Free-FF512F?style=for-the-badge&logoColor=white" alt="Try Pulso" /></a>
  &nbsp;
  <a href="https://www.npmjs.com/package/@pulso/companion"><img src="https://img.shields.io/badge/npm-@pulso/companion-cb3837?style=for-the-badge&logo=npm&logoColor=white" alt="npm" /></a>
  &nbsp;
  <a href="https://x.com/usepulso"><img src="https://img.shields.io/badge/@usepulso-000000?style=for-the-badge&logo=x&logoColor=white" alt="Twitter" /></a>
</p>

<br />

<p align="center">
  <img src="https://img.shields.io/badge/channels-12-22c55e.svg?style=flat-square" alt="12 Channels" />
  <img src="https://img.shields.io/badge/tools-350+-3b82f6.svg?style=flat-square" alt="350+ Tools" />
  <img src="https://img.shields.io/badge/platforms-6-8b5cf6.svg?style=flat-square" alt="6 Platforms" />
  <img src="https://img.shields.io/badge/models-200+-f59e0b.svg?style=flat-square" alt="200+ Models" />
  <img src="https://img.shields.io/badge/uptime-99.9%25-10b981.svg?style=flat-square" alt="99.9% Uptime" />
</p>

---

<br />

> **Tired of AI assistants that just talk?**
>
> Every AI tool in 2026 does the same thing — you ask, it answers, you do the work yourself. Chatbots that can't send an email. Agents that can't click a button. Workflows that break when you need them most.
>
> We built something different.

<br />

## Your AI team. Always on.

Pulso agents don't just answer questions — they **execute**. They check your email, manage your calendar, message your team, control your computer, deploy your code, and work together in parallel. From any device. Through any channel. 24/7.

```
You (from Telegram, 2:13 AM):

    "Check my inbox. Anything urgent from the client?
     If yes, draft a reply and block time on my calendar."

Pulso (3 agents, 4.2 seconds, $0.003):

    ✓  Scanned 47 emails — found 3 urgent from Acme Corp
    ✓  Drafted 3 replies matching your tone (saved as drafts)
    ✓  Blocked 2h tomorrow at 10 AM for "Contract Review"
    ✓  Summary sent to your Slack #urgent channel
```

Three AI models. Working in parallel. While you sleep.

<br />

---

<br />

## What makes Pulso different

<br />

### Talk to your agents from anywhere

Not just another web chat. Pulso connects to **12 messaging channels** natively — Telegram, WhatsApp, Slack, Discord, Signal, iMessage, Teams, Google Chat, Matrix, Instagram, Messenger, LINE.

Your agents have full capabilities on every channel. Tool execution, multi-step reasoning, image generation, memory — not just text forwarding.

<br />

### Your computer, their hands

Install the **Companion daemon** and your agents can control your machine:

```bash
npm install -g @pulso/companion
```

Shell commands. File management. App control. Browser automation. System monitoring. Smart home. iMessage. Native on **macOS, Windows, and Linux**.

Also available as a **native macOS menu bar app**.

> *"My staging server is slow."*
>
> Agent checks CPU usage, finds a stuck process eating 94% CPU, kills it, verifies the server recovered, and reports back — all from a Telegram message.

<br />

### Multiple agents, one task

Define teams of specialized agents that work together. Agents without dependencies run **in parallel** — a research agent and a data agent can work simultaneously, then feed their results to a writing agent.

Build with YAML, a visual drag-and-drop builder, or plain English. **140+ ready-made templates** across 15 categories.

Smart routing automatically picks the right model for each task — fast models for simple lookups, powerful models for complex reasoning. You set the budget, Pulso optimizes the cost.

<br />

### Your AI remembers

Pulso builds a **knowledge graph** from your conversations — entities, relationships, preferences, context. Agents find relevant memories by meaning, not keywords. Old memories naturally fade. New ones strengthen.

Up to **100,000 memory items** that make every interaction smarter than the last.

<br />

### Any model. Your keys. Your data.

Connect your existing API keys from **Anthropic, OpenAI, Google, DeepSeek, Mistral, Ollama**, or access **200+ models through OpenRouter**. Your keys, your billing, your control.

Or use **Pulso Credits** — prepaid credit packs with transparent per-request cost tracking. No surprises.

**We never train on your data. Your conversations are yours.**

<br />

### Image generation built in

Your agents generate images using the latest multimodal models — Gemini Imagen, GPT Image, FLUX, Seedream. Auto-detects your available providers.

<br />

### Event-driven automations

Set triggers that run 24/7. New email from an important client? Agent summarizes it, checks your calendar, drafts a reply, and notifies you on Slack. Automatically. Up to **100 triggers** on the Fleet plan.

<br />

### Standards-first

- **MCP** (Model Context Protocol) — Connect any MCP-compatible tool server
- **A2A** (Agent-to-Agent) — Google's agent interoperability protocol

<br />

---

<br />

## Platform

| | |
|---|---|
| **Web** | Full dashboard — chat, visual workflow builder, analytics, memory explorer |
| **iOS & Android** | Native mobile app with voice, push notifications, full agent access |
| **Companion** | Cross-platform daemon for computer control — [npm](https://www.npmjs.com/package/@pulso/companion) |
| **Menu Bar** | Native macOS app — always one click away |
| **API** | REST + SSE + WebSocket on a global edge network — sub-50ms worldwide |

<br />

---

<br />

## Security

| | |
|---|---|
| **Encryption** | AES-256-GCM for all stored credentials. TLS 1.3 everywhere. |
| **Isolation** | Every request runs in its own V8 isolate. No shared memory. No container escapes. |
| **Auth** | JWT + refresh tokens, 2FA (TOTP), secure device code flow for Companion |
| **BYOK** | Your API keys stay under your control. We proxy, not store. |
| **Data** | Conversations never used for training. Period. |
| **Infrastructure** | Runs on Cloudflare — SOC 2 Type II, ISO 27001, PCI DSS certified |
| **Audit** | Full security audit completed. All findings resolved. |

No exposed ports. No self-hosted attack surface. No servers to patch.

<br />

---

<br />

## Pricing

| | **Solo** | **Swarm** | **Fleet** |
|---|:---:|:---:|:---:|
| | Free | **$19**/mo | **$49**/mo |
| Channels | 1 | 12 | Unlimited |
| Agent Teams | — | Up to 10 agents | Up to 20 agents |
| Memory | 100 | 10,000 | 100,000 |
| Companion | — | Included | Included |
| Automations | — | 10 triggers | 100 triggers |
| MCP Servers | — | 5 | 50 |
| Credits | — | $5/mo included | $20/mo included |

All plans include BYOK at zero cost.

<br />

---

<br />

## Quick start

**1.** Sign up at [app.runpulso.com](https://app.runpulso.com)

**2.** Add your API keys (Settings → Providers)

**3.** Start chatting — your agent is ready with 350+ tools

**4.** *(Optional)* Install the Companion:
```bash
npm install -g @pulso/companion
pulso-companion login
```

<br />

---

<br />

## Community

- [Report a bug](https://github.com/usepulso/pulso/issues/new?template=bug_report.md)
- [Request a feature](https://github.com/usepulso/pulso/issues/new?template=feature_request.md)
- [Discussions](https://github.com/usepulso/pulso/discussions)
- [Security](SECURITY.md)

<br />

---

<br />

<p align="center">
  <a href="https://app.runpulso.com"><strong>Get started free →</strong></a>
</p>

<p align="center">
  <sub>
    <a href="https://app.runpulso.com/terms">Terms</a> ·
    <a href="https://app.runpulso.com/privacy">Privacy</a> ·
    <a href="https://app.runpulso.com/cookies">Cookies</a> ·
    <a href="https://app.runpulso.com/acceptable-use">Acceptable Use</a>
  </sub>
</p>

<p align="center">
  <sub>Built by <a href="https://codeahead.pt">CodeAhead</a> in Portugal · © 2026 CodeAhead Lda · All rights reserved</sub>
</p>
