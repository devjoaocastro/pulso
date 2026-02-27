# AGENTS.md — Context for AI Coding Assistants

## Project Overview

Pulso is an open-source multi-agent AI orchestration platform that actually does things — manages email, calendar, files, code review, research, and more — running in the cloud 24/7 with zero setup.

Two modes:

- **Simple Mode** — Chat interface for everyone (no configuration)
- **Advanced Mode** — Multi-agent DAG pipelines with YAML for developers

## Architecture

- **Monorepo**: pnpm workspaces + Turborepo
- **Language**: TypeScript (ESM)
- **Packages**: `@pulso/core`, `@pulso/providers`, `@pulso/tools`, `@pulso/memory`, `@pulso/protocols`
- **Apps**: `@pulso/cli` (terminal), `@pulso/web` (React 19 + Vite 6), `@pulso/server` (Cloudflare Workers), `@pulso/mobile` (Flutter)
- **Testing**: Vitest (48 tests)
- **Linting**: Prettier

## Build & Test

```bash
pnpm install          # Install all dependencies
pnpm build            # Build all packages
pnpm test             # Run all tests (48 passing)
pnpm typecheck        # Type-check all packages
pnpm lint             # Check formatting
```

## Package Dependencies

```
@pulso/core          — No internal deps (foundation)
@pulso/providers     — Depends on @pulso/core
@pulso/tools         — Depends on @pulso/core
@pulso/memory        — Depends on @pulso/core
@pulso/protocols     — Depends on @pulso/core
@pulso/cli           — Depends on core, providers, tools, memory
@pulso/web           — React 19 + Vite 6 dashboard + chat UI
@pulso/server        — Cloudflare Workers API (Hono)
```

## Supported LLM Providers (Feb 2026)

- **Anthropic** — Claude Opus 4.6, Sonnet 4.5, Haiku 4.5 (1M context)
- **OpenAI** — GPT-5.2, GPT-5, GPT-5 Mini, GPT-5 Nano (400K context)
- **Google** — Gemini 3 Pro, Gemini 3 Flash, Gemini 2.5 Pro (1M context)
- **DeepSeek** — V3.2 (deepseek-chat, deepseek-reasoner, 128K context)
- **Mistral** — Large 3, Magistral, Codestral (open-weight MoE)
- **Meta** — Llama 4 Scout, Llama 4 Maverick (self-hosted)
- **Ollama** — Any local model (offline, zero cost)
- **OpenRouter** — 100+ models, unified API

## Conventions

- All source code in `src/` directories
- All imports use `.js` extension (ESM)
- Types defined in `types.ts` files
- Public API exported from `index.ts`
- Tests in `tests/` directories using Vitest
- Configuration in YAML (Zod validation)

## Key Types

- `Agent` — Single AI entity with role, model, tools, prompt, budget
- `Swarm` — Collection of agents with DAG execution order and shared memory
- `Provider` — LLM adapter (Claude, GPT, Gemini, DeepSeek, Ollama, OpenRouter)
- `ToolDefinition` — MCP-compatible tool interface
- `Orchestrator` — DAG executor with parallel scheduling and budget enforcement
- `MessageBus` — Inter-agent communication (EventEmitter local, CF Queues cloud)
- `BudgetTracker` — Cost tracking with hard limits per agent and per swarm

## Entry Points

- CLI: `apps/cli/src/index.ts`
- Web: `apps/web/src/main.tsx` (landing page → chat)
- Server: `apps/server/src/index.ts` (Hono on Workers)
- Core: `packages/core/src/index.ts`
- Config: `packages/core/src/config.ts` (YAML loader + Zod)

## Security

- API keys encrypted with AES-256-GCM (PBKDF2 100K iterations, unique salt + IV per credential)
- JWT auth (HMAC-SHA256, 7-day expiry, timing-safe comparison)
- Sandboxed agent execution with explicit tool permissions
- Budget enforcement per agent and per swarm
- Zero-knowledge architecture — server cannot read API keys at rest

## Standards

- MCP (Model Context Protocol) — tool interface compatibility with Claude Code, Cursor
- A2A (Agent-to-Agent) — Google's protocol for agent discovery and communication
