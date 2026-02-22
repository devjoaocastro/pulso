<p align="center">
  <img src="https://app.runpulso.com/icon.png" alt="Pulso" width="100" />
</p>

<h1 align="center">Pulso</h1>

<p align="center">
  <strong>AI agents that actually do things.</strong><br />
  <sub>Multi-agent orchestration &middot; 12 messaging channels &middot; Full computer control &middot; Knowledge graph memory</sub>
</p>

<p align="center">
  <a href="https://app.runpulso.com">Dashboard</a> &middot;
  <a href="https://www.npmjs.com/package/@pulso/companion">npm</a> &middot;
  <a href="https://app.runpulso.com/privacy">Privacy</a> &middot;
  <a href="https://app.runpulso.com/terms">Terms</a> &middot;
  <a href="https://x.com/usepulso">@usepulso</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/tools-352-22c55e.svg?style=flat-square" alt="352 Tools" />
  <img src="https://img.shields.io/badge/channels-12-3b82f6.svg?style=flat-square" alt="12 Channels" />
  <img src="https://img.shields.io/badge/TypeScript-100%25-3178c6.svg?style=flat-square" alt="TypeScript" />
  <img src="https://img.shields.io/badge/MCP-compatible-f97316.svg?style=flat-square" alt="MCP" />
  <img src="https://img.shields.io/badge/platforms-web%20%7C%20iOS%20%7C%20Android%20%7C%20macOS%20%7C%20Windows%20%7C%20Linux-8b5cf6.svg?style=flat-square" alt="Platforms" />
  <img src="https://img.shields.io/badge/edge_runtime-Cloudflare_Workers-f38020.svg?style=flat-square" alt="Cloudflare Workers" />
</p>

---

## The Problem

Every AI tool does the same thing: you type a question, it types back an answer. Then you go do the actual work yourself.

ChatGPT can't check your email. Gemini can't deploy your code. Claude can't message your team on Slack.

**What if your AI agents had hands?**

---

## What Pulso Does

Pulso is an AI agent platform where agents **execute tasks** — not just generate text. They read your emails, manage your calendar, control your computer, message your team, run shell commands, deploy code, manage files, and work together in parallel across any AI model you choose.

```
You:     "Check my email, summarize anything urgent, draft replies for
          the contract emails, and block my calendar for the review."

Pulso:   Done. 3 agents worked in parallel (4.2 seconds):

         Email Agent (Claude Sonnet 4.6)
         ├─ Scanned 47 unread emails
         ├─ Found 3 urgent (contract review, server alert, client request)
         └─ Summarized each with priority tags

         Calendar Agent (GPT-4o)
         ├─ Found first available 2h slot: tomorrow 10:00 AM
         └─ Created "Contract Review" with context from email

         Draft Agent (Gemini 2.5 Flash)
         ├─ Drafted 3 email replies matching your writing style
         └─ Saved as drafts for your review

         Cost: $0.003 | Models: 3 | Tools used: 7
```

Three different AI providers. Working in parallel. Costing less than a penny.

---

## Architecture

```
┌────────────────────────────────────────────────────────────────────────┐
│                          YOUR DEVICES                                  │
│                                                                        │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌───────────────────────┐  │
│  │ Web App  │  │  Mobile  │  │ Telegram │  │   Companion Daemon    │  │
│  │ React 19 │  │ iOS/And. │  │ WhatsApp │  │ macOS/Windows/Linux   │  │
│  │ Vite 6   │  │ Expo 54  │  │ Slack    │  │ Shell, Files, Apps,   │  │
│  │          │  │          │  │ Discord  │  │ Browser, iMessage     │  │
│  └────┬─────┘  └────┬─────┘  │ +8 more  │  └──────────┬────────────┘  │
│       │              │        └────┬─────┘             │               │
└───────┼──────────────┼─────────────┼───────────────────┼───────────────┘
        │              │             │                   │
        └──────────────┴──────┬──────┴───────────────────┘
                              │
                    ┌─────────▼──────────┐
                    │   Cloudflare Edge  │
                    │   Global Network   │
                    │   (300+ cities)    │
                    └─────────┬──────────┘
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
  ┌─────▼──────┐    ┌────────▼────────┐    ┌───────▼───────┐
  │   Hono     │    │ Durable Objects │    │  Cloudflare   │
  │   API      │    │                 │    │  Services     │
  │            │    │ Chat Sessions   │    │               │
  │ 117 routes │    │ Swarm Sessions  │    │ D1 (SQLite)   │
  │ Auth/Rate  │    │ Companion WS    │    │ R2 (Storage)  │
  │ limit/CORS │    │ Heartbeat       │    │ Vectorize     │
  └─────┬──────┘    └────────┬────────┘    │ AI Gateway    │
        │                    │             └───────────────┘
        │                    │
  ┌─────▼────────────────────▼──────────────────────────┐
  │              352 TOOL DEFINITIONS                    │
  │                                                      │
  │  Web Search  │  Gmail/Calendar  │  GitHub/Notion     │
  │  File Ops    │  Slack/Discord   │  Jira/Linear       │
  │  Shell Exec  │  Browser Auto    │  Smart Home        │
  │  Image Gen   │  Voice/TTS       │  Crypto/Stocks     │
  │  Deep Search │  PDF/Documents   │  144 Swarm Tpls    │
  └──────────────────────────┬──────────────────────────┘
                             │
        ┌────────────────────┼────────────────────┐
        │                    │                    │
  ┌─────▼──────┐    ┌───────▼───────┐    ┌───────▼───────┐
  │ Anthropic  │    │    OpenAI     │    │    Google     │
  │ Claude 4.6 │    │   GPT-4o     │    │  Gemini 2.5  │
  ├────────────┤    ├───────────────┤    ├───────────────┤
  │ DeepSeek   │    │   Mistral    │    │   Ollama     │
  │ OpenRouter │    │   Meta       │    │  Workers AI  │
  └────────────┘    └───────────────┘    └───────────────┘
```

**Everything runs on Cloudflare's edge network** — V8 isolate execution, no cold starts, sub-50ms latency globally. No servers to manage. No Docker containers. No Kubernetes clusters.

---

## Core Capabilities

### Multi-Agent Swarms

Define teams of specialized agents. Pulso uses a **DAG orchestration engine** — agents with no dependencies execute in parallel, results flow through the graph automatically.

```yaml
# research-and-write.yaml — 3 agents, 2 run in parallel
name: Research Report
agents:
  researcher:
    role: "Find the latest data on {topic}"
    model: auto                        # CascadeRouter picks the best model
    tools: [web_search, deep_research]
    budget: $0.10

  analyst:
    role: "Analyze the research data and identify key trends"
    depends_on: [researcher]
    model: auto

  writer:
    role: "Write a professional report with executive summary"
    depends_on: [analyst]
    model: anthropic/claude-sonnet-4-6
    budget: $0.05
```

- **CascadeRouter** scores task complexity (0-100) and picks the cheapest model that can handle it
- YAML config, visual workflow builder, or natural language — your choice
- Hard budget caps per agent and per swarm (never get surprised)
- **144 ready-to-use templates** across 15 categories (business, engineering, marketing, research...)
- Up to 20 concurrent agents on the Fleet plan

### 12 Channel Adapters

Talk to your agents from wherever you already are:

| Channel | Status | Auth Method |
|---|---|---|
| **Web Chat** | Production | JWT |
| **Telegram** | Production | Auto webhook + QR pairing |
| **WhatsApp** | Production | Meta Business API, HMAC-SHA256 |
| **Slack** | Production | HMAC + replay protection |
| Discord | Functional | Bot token |
| Signal | Functional | Signal CLI bridge |
| iMessage | Functional | Companion (macOS) |
| Teams | Functional | Bot Framework |
| Google Chat | Functional | Service account |
| Matrix | Functional | Homeserver API |
| Instagram | Functional | Meta Graph API |
| Messenger | Functional | Meta webhooks |
| LINE | Functional | Messaging API |

Every channel gets the **full ReAct agent loop** — tool use, multi-step reasoning, memory injection, image generation. Not just text forwarding.

### Companion Daemon — Your Agent's Hands

```bash
npm install -g @pulso/companion
pulso-companion login   # Secure device code flow (RFC 8628)
```

The Companion is a daemon that runs on your machine and gives agents **real-world capabilities**:

| Category | Examples |
|---|---|
| **Shell** | Run commands, scripts, manage processes, cron jobs |
| **Files** | Create, read, edit, move, search, compress, decompress |
| **Applications** | Launch, close, focus, resize, list running apps |
| **Browser** | Open URLs, take screenshots, interact with pages |
| **System** | CPU/RAM/disk stats, network info, notifications, clipboard |
| **Audio** | System volume, input/output devices, text-to-speech |
| **iMessage** | Read, send, search messages (macOS) |
| **Smart Home** | HomeAssistant, Philips Hue, Sonos |

**65+ commands** with native implementations for macOS, Windows, and Linux. Also available as a **native macOS menu bar app** built with Tauri.

```
You (from Telegram):  "My server is running slow. Check what's using
                       all the CPU and kill anything unnecessary."

Companion Agent:      Checking system resources...
                      ├─ CPU: 94% usage
                      ├─ Top process: chrome (47 tabs, 3.2 GB RAM)
                      ├─ Second: node (webpack dev server, stuck)
                      ├─ Killed: webpack process (PID 2847)
                      └─ CPU dropped to 23%. Chrome still has 47 tabs
                         though — want me to close inactive ones?
```

### Memory & Knowledge Graph

Your agents don't start from scratch every conversation:

```
┌─────────────────────────────────────────────────────┐
│                  MEMORY SYSTEM                       │
│                                                      │
│  ┌──────────────┐  ┌─────────────┐  ┌────────────┐  │
│  │ Flat Memory  │  │  Knowledge  │  │  Vectorize  │  │
│  │              │  │    Graph    │  │  (Semantic)  │  │
│  │ "Prefers     │  │             │  │             │  │
│  │  dark mode"  │  │ [You]──────▶│  │ Query by    │  │
│  │ "Uses vim"   │  │   works_at  │  │ meaning,    │  │
│  │ "Team lead"  │  │ [Company]   │  │ not keywords│  │
│  └──────────────┘  └─────────────┘  └────────────┘  │
│                                                      │
│  Auto-extraction from conversations (Claude Haiku)   │
│  Memory decay: unused memories fade after 7 days     │
│  Up to 100,000 items on Fleet plan                   │
└─────────────────────────────────────────────────────┘
```

- **Entities & relationships** extracted automatically after each conversation
- **Semantic search** via Cloudflare Vectorize — agents find relevant context by meaning
- **Natural decay** — memories unused for 7+ days gradually fade, keeping context fresh and relevant

### Smart Model Routing (CascadeRouter)

Set `model: auto` and Pulso picks the best model for each task:

```
Complexity 0-30   →  Haiku 4.5        (fast, cheap — simple lookups, formatting)
Complexity 31-70  →  Sonnet 4.6       (balanced — most tasks, tool use, analysis)
Complexity 71-100 →  Opus 4.6         (genius — complex reasoning, long context)
```

Or specify any model directly: `anthropic/claude-sonnet-4-6`, `openai/gpt-4o`, `google/gemini-2.5-flash`, `deepseek/deepseek-chat`, or any of **200+ models through OpenRouter**.

### Event-Driven Automations

```
When:    New email from *@important-client.com
Then:    Summarize → Check calendar availability → Draft reply → Notify on Slack
Budget:  $0.02 per trigger
Runs:    24/7, automatically
```

Up to **100 automation triggers** on the Fleet plan. Each trigger runs a full agent loop with tool access, memory, and multi-model support.

---

## Platform

| Component | Stack | Description |
|---|---|---|
| **Web App** | React 19, Vite 6, Tailwind | Dashboard, chat, workflow builder, analytics, memory explorer |
| **Mobile** | React Native 0.81, Expo 54 | iOS & Android — voice calls, push notifications, full agent access |
| **Companion** | Node.js, TypeScript | Cross-platform daemon (macOS/Windows/Linux) — [npm](https://www.npmjs.com/package/@pulso/companion) |
| **Companion App** | Tauri v2, Rust | Native macOS menu bar app with glassmorphism UI |
| **API** | Hono 4.7, Cloudflare Workers | 117 endpoints, REST + SSE + WebSocket, global edge deployment |
| **Database** | Cloudflare D1 + Vectorize | 29 tables, semantic vector search, sub-10ms queries |

---

## Security

Pulso is built with security as a foundation, not an afterthought:

| Layer | Protection |
|---|---|
| **Credentials** | AES-256-GCM encryption, unique IVs, decrypted only in-memory during requests |
| **Transport** | TLS 1.3 everywhere, HSTS, no mixed content |
| **Auth** | JWT + refresh tokens, 2FA (TOTP), RFC 8628 device code flow for Companion |
| **Execution** | V8 isolate per request — no shared memory, no container escape |
| **API** | Rate limiting on all endpoints, CORS, CSRF protection, replay detection |
| **Data** | Your conversations are never used to train AI models. Period. |
| **BYOK** | Your API keys → your provider billing → your control. We just proxy. |
| **Compliance** | Runs on Cloudflare (SOC 2 Type II, ISO 27001, PCI DSS) |
| **Audit** | Full security audit completed Feb 2026 — 21 findings, all resolved |

No exposed ports. No self-hosted attack surface. No Docker containers to patch. No Kubernetes to misconfigure.

---

## Pricing

| | Solo | Swarm | Fleet |
|---|---|---|---|
| **Price** | Free | $19/mo | $49/mo |
| **Channels** | 1 | 12 | Unlimited |
| **Swarm Agents** | -- | Up to 10 | Up to 20 |
| **Memory** | 100 items | 10,000 | 100,000 |
| **Companion** | -- | Included | Included |
| **Automations** | -- | 10 triggers | 100 triggers |
| **MCP Servers** | -- | 5 | 50 |
| **Credits** | -- | $5/mo included | $20/mo included |

All plans include BYOK (Bring Your Own Key) at zero cost. Connect your Anthropic, OpenAI, Google, DeepSeek, Mistral, or OpenRouter keys and pay only what you use at provider rates.

**Pulso Credits** are available for users who prefer not to manage API keys — $0.01 per credit with transparent per-request cost tracking.

---

## Getting Started

```bash
# 1. Sign up
open https://app.runpulso.com

# 2. Add your API keys (Settings → Providers)
#    Anthropic, OpenAI, Google, DeepSeek, Mistral, Ollama, OpenRouter

# 3. Start chatting — your agent has 352 tools ready

# 4. (Optional) Install the Companion for computer control
npm install -g @pulso/companion
pulso-companion login
```

---

## Comparison

| Capability | Pulso | ChatGPT | Open-source agents | Workflow tools |
|---|---|---|---|---|
| Multi-agent orchestration | DAG engine, parallel execution | Single agent | Varies (CrewAI, AutoGPT) | Sequential only |
| Messaging channels | 12 native adapters | Web only | Usually 0-1 | Webhooks only |
| Computer control | 65+ native commands, 3 platforms | Not available | Plugin-dependent | Not available |
| Model choice | Any provider (BYOK) + auto-routing | OpenAI only | Usually 1-2 providers | N/A |
| Memory | Knowledge graph + semantic + decay | Limited context | Basic RAG | None |
| Security | AES-256, V8 isolates, 2FA, audit | Trust provider | Self-managed | Trust provider |
| Infrastructure | Serverless edge (0 ops) | Hosted | Self-hosted required | Hosted |
| Mobile app | Native iOS & Android | Web wrapper | None | Some |
| Pricing transparency | Per-request cost tracking | Subscription only | Free + compute | Per-task pricing |

---

## Standards

- **MCP** (Model Context Protocol) — Standardized tool interface
- **A2A** (Agent-to-Agent) — Google's agent discovery protocol
- **RFC 8628** — OAuth 2.0 Device Authorization Grant for Companion auth

---

## Links

| | |
|---|---|
| Web App | [app.runpulso.com](https://app.runpulso.com) |
| Companion (npm) | [@pulso/companion](https://www.npmjs.com/package/@pulso/companion) |
| Privacy Policy | [app.runpulso.com/privacy](https://app.runpulso.com/privacy) |
| Terms of Service | [app.runpulso.com/terms](https://app.runpulso.com/terms) |
| Cookie Policy | [app.runpulso.com/cookies](https://app.runpulso.com/cookies) |
| Acceptable Use | [app.runpulso.com/acceptable-use](https://app.runpulso.com/acceptable-use) |
| Twitter / X | [@usepulso](https://x.com/usepulso) |

---

<p align="center">
  Built by <a href="https://codeahead.pt">CodeAhead Lda</a> in Portugal.
  <br /><br />
  <sub>Pulso is proprietary software. &copy; 2026 CodeAhead Lda. All rights reserved.</sub>
</p>
