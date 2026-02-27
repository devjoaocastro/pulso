# Pulso Platform Roadmap

> Full-stack plan for shipping Pulso on ALL platforms.
> Last updated: 2026-02-21

---

## Current Platform Status

| Platform | App | Status | Distribution |
|----------|-----|--------|-------------|
| **Web** | `apps/web` (React 19 + Vite 6) | Production | `pulso-web.pages.dev` |
| **API** | `apps/server` (Hono + CF Workers) | Production | `api.runpulso.com` |
| **iOS** | `apps/mobile` (React Native + Expo 54) | Beta | EAS Build (not in App Store) |
| **Android** | `apps/mobile` (React Native + Expo 54) | Beta | EAS Build (not in Play Store) |
| **macOS Desktop** | `apps/companion-app` (Tauri v2) | Beta | DMG (manual build) |
| **Windows Desktop** | `apps/companion-app` (Tauri v2) | Not built | Tauri supports it, needs CI |
| **Linux Desktop** | `apps/companion-app` (Tauri v2) | Not built | Tauri supports it, needs CI |
| **macOS Companion** | `apps/companion` (Node.js) | Production | npm: `@pulso/companion@0.4.1` |
| **Windows Companion** | `apps/companion` (Node.js) | Code exists | `WindowsAdapter` written, untested |
| **Linux Companion** | `apps/companion` (Node.js) | Not started | Needs `LinuxAdapter` implementation |
| **Chrome Extension** | `apps/extension` (MV3) | Production | Manual CRX |
| **Firefox Extension** | `apps/extension` | Not started | Needs manifest adaptation |
| **Safari Extension** | `apps/extension` | Not started | Needs Xcode wrapper |
| **Edge Extension** | `apps/extension` | Not started | Zero code changes (Chromium) |
| **CLI** | `apps/cli` (Commander.js) | Functional | npm: `@pulso/cli` |

---

## Phase 1: Store Submissions (Week 1-2)

### 1.1 iOS App Store

- [ ] Apple Developer Program enrollment ($99/year)
- [ ] Create App ID `com.runpulso.app` in Apple Developer Portal
- [ ] Register app in App Store Connect
- [ ] Update `eas.json` production profile for `"distribution": "store"`
- [ ] Create App Store screenshots (6.7", 6.1", 5.5", 12.9" iPad)
- [ ] Write App Store description + keywords
- [ ] Privacy policy URL (required)
- [ ] App Privacy questionnaire (contacts, calendar, location, microphone)
- [ ] `eas build --platform ios --profile production`
- [ ] `eas submit --platform ios` (TestFlight first, then production)

### 1.2 Google Play Store

- [ ] Google Play Console enrollment ($25 one-time)
- [ ] Update `eas.json` production Android to `"buildType": "app-bundle"` (AAB)
- [ ] Create Play Store screenshots + feature graphic (1024x500)
- [ ] Privacy policy URL
- [ ] Data safety form (contacts, calendar, location, microphone)
- [ ] Content rating questionnaire
- [ ] `eas build --platform android --profile production`
- [ ] `eas submit --platform android` (internal track first)

### 1.3 Install expo-updates for OTA

```bash
cd apps/mobile && npx expo install expo-updates
```

### 1.4 Edge Extension (zero code changes)

- [ ] Microsoft Partner account (free)
- [ ] Upload same Chrome extension ZIP to Edge Add-ons

---

## Phase 2: Web Hardening (Week 2)

### 2.1 Custom Domain

- [ ] Add `app.runpulso.com` as custom domain in Cloudflare Pages
- [ ] Auto SSL certificate provisioning

### 2.2 SEO

- [ ] Add `robots.txt` (`Disallow: /app/`)
- [ ] Add Open Graph meta tags to `index.html`
- [ ] Add JSON-LD structured data
- [ ] Create `_headers` and `_redirects` for Cloudflare Pages

### 2.3 PWA

- [ ] Install `vite-plugin-pwa`
- [ ] Create `manifest.webmanifest` (name, icons, theme)
- [ ] Generate PWA icons (192x192, 512x512)
- [ ] Service worker with Workbox (offline-first for `/app/*`)

---

## Phase 3: Desktop Multi-Platform (Week 3-5)

### 3.1 GitHub Actions for Tauri Builds

Create `.github/workflows/release-desktop.yml`:
- macOS ARM64 + x86_64 (DMG)
- Windows x86_64 (NSIS installer)
- Linux x86_64 (AppImage + .deb)

Uses `tauri-apps/tauri-action@v0`.

### 3.2 Tauri Config Updates

- [ ] Change `"targets": ["dmg", "app"]` to `"targets": "all"`
- [ ] Add NSIS config for Windows
- [ ] Add AppImage/deb config for Linux
- [ ] Conditional UI (no vibrancy on Windows/Linux)

### 3.3 macOS Code Signing + Notarization

- [ ] Apple Developer ID certificate
- [ ] Set `signingIdentity` in tauri.conf.json
- [ ] Notarize via `xcrun notarytool`

### 3.4 Windows Code Signing (optional for now)

- [ ] EV certificate ($200-400/year) or Azure Trusted Signing
- [ ] Without it: SmartScreen warnings (acceptable for beta)

---

## Phase 4: Companion Cross-Platform (Week 4-7)

### 4.1 Extract macOS Code

- [ ] Move implementations from `index.ts` `handleCommand()` → `macos.ts` `MacOSAdapter`
- [ ] Wire `loadPlatformAdapter()` into command dispatch
- [ ] Test all 55+ commands still work on macOS

### 4.2 Test Windows Adapter

- [ ] `WindowsAdapter` already written in `platform/windows.ts`
- [ ] Test on real Windows machine (PowerShell, user32.dll, COM)
- [ ] Fix any broken commands

### 4.3 Implement Linux Adapter

- [ ] Create `platform/linux.ts` implementing `PlatformAdapter`
- [ ] X11 tools: `xdotool`, `xclip`, `wmctrl`, `scrot`
- [ ] Wayland tools: `ydotool`, `wl-paste`, `wl-copy`, `grim`
- [ ] Runtime detection: `XDG_SESSION_TYPE === 'wayland'`
- [ ] TTS: `espeak-ng` or `spd-say`
- [ ] Notifications: `notify-send`
- [ ] OCR: `tesseract` CLI

### 4.4 npm Publish Updates

- [ ] Bump `@pulso/companion` version
- [ ] Publish with cross-platform support

---

## Phase 5: Browser Extensions (Week 6-8)

### 5.1 Firefox Extension

- [ ] Add `browser_specific_settings` to manifest
- [ ] Handle optional `host_permissions` (Firefox default)
- [ ] Build script to generate Firefox ZIP
- [ ] Submit to AMO (addons.mozilla.org)

### 5.2 Safari Extension

- [ ] Run `xcrun safari-web-extension-converter`
- [ ] Xcode project setup + signing
- [ ] Test on macOS + iOS Safari
- [ ] Submit via Mac App Store

---

## Phase 6: Mobile App Completion (Week 5-10)

### Current: 1 screen (ChatScreen). Need 19+ screens.

- [ ] **Onboarding flow** — Welcome, API key setup, channel connect
- [ ] **Dashboard** — Stats, quick actions, recent chats
- [ ] **Chat** — Already built (ChatScreen)
- [ ] **Connections** — OAuth providers, channels, companion pairing
- [ ] **Agents/Swarms** — YAML editor, run history, cost
- [ ] **Skills** — User-created tools
- [ ] **Memory** — Knowledge graph viewer
- [ ] **Automations** — Scheduled tasks, triggers
- [ ] **Settings** — Profile, API keys, theme, notifications, plan
- [ ] **Usage/Billing** — Cost tracking, plan management
- [ ] **Activity** — Real-time agent activity feed

---

## Phase 7: Infrastructure Hardening (Week 8-12)

### 7.1 CI/CD Pipeline

- [ ] GitHub Actions for server deploy (on push to main)
- [ ] GitHub Actions for web deploy (on push to main)
- [ ] GitHub Actions for mobile EAS Build (on tag)
- [ ] GitHub Actions for desktop Tauri build (on tag)

### 7.2 Security

- [ ] Email verification on registration
- [ ] Account lockout after 5 failed login attempts
- [ ] Register social login callback URLs in Google/GitHub OAuth apps
- [ ] Set `OPENROUTER_PLATFORM_KEY` for credits system
- [ ] Set `RESEND_API_KEY` for email delivery

### 7.3 Monitoring

- [ ] Error tracking (Sentry or similar)
- [ ] Uptime monitoring for `api.runpulso.com`
- [ ] Usage alerts for billing thresholds

---

## Phase 8: Public Launch Prep (Week 10-14)

### 8.1 Git Repository — Public Presence Strategy

> **Model**: Closed-source SaaS with a public **product hub** repo (similar to Botpress).
> Zero source code. The repo serves as the single entry point for users to learn about Pulso,
> download apps, install npm packages, file issues, and read documentation.

#### Current State

- **Private monorepo**: `usepulso/pulso` (49 commits, single `main` branch)
- **CRITICAL**: Git history contains leaked secrets (JWT_SECRET, API keys, login credentials)
- **Cannot** be made public — even with cleanup, `git log -p` exposes everything
- **Solution**: Create a fresh public repo under `runpulso` org (no history baggage)

#### Action Plan

1. **Create GitHub org** `runpulso` (matches domain `runpulso.com`)
2. **Create public repo** `runpulso/pulso` — the product hub
3. **Keep private** `usepulso/pulso` — the development monorepo (all source code stays here)
4. **Rotate all leaked secrets** — JWT_SECRET, ELEVENLABS_API_KEY, account passwords
5. **Remove credentials** from CLAUDE.md in private repo
6. **Add `gitleaks` pre-commit hook** to prevent future secret commits

#### Public Repo Content (`runpulso/pulso`)

```
runpulso/pulso/
├── README.md                    # Product overview, features, architecture
├── LICENSE                      # Proprietary — "All rights reserved"
├── SECURITY.md                  # Responsible disclosure policy
├── CHANGELOG.md                 # Public release notes
│
├── docs/
│   ├── getting-started.md       # Account creation, first chat, API key setup
│   ├── companion/
│   │   ├── install.md           # npm install -g @pulso/companion
│   │   ├── login.md             # Device code flow authentication
│   │   ├── commands.md          # 55+ available commands
│   │   └── platforms.md         # macOS, Windows, Linux support
│   ├── channels/
│   │   ├── telegram.md          # Setup guide + screenshots
│   │   ├── whatsapp.md          # Meta Business API setup
│   │   ├── slack.md             # Slack App configuration
│   │   ├── discord.md           # Bot setup
│   │   └── ...                  # All 12 channel adapters
│   ├── agents/
│   │   ├── overview.md          # What are swarms, DAG execution
│   │   ├── yaml-syntax.md       # Agent YAML configuration reference
│   │   ├── gallery.md           # 144 pre-built templates
│   │   └── cascade-router.md    # Auto model selection explained
│   ├── memory/
│   │   ├── overview.md          # Knowledge graph, semantic search, decay
│   │   └── api.md               # Memory API endpoints
│   ├── mcp/
│   │   ├── overview.md          # Model Context Protocol support
│   │   └── setup.md             # How to connect MCP servers
│   ├── api/
│   │   ├── authentication.md    # JWT, refresh tokens, 2FA
│   │   ├── endpoints.md         # Full API reference (206 endpoints)
│   │   └── rate-limits.md       # Rate limiting details
│   └── billing/
│       ├── plans.md             # Solo/Swarm/Fleet comparison
│       └── credits.md           # Pulso Credits system
│
├── downloads/
│   └── README.md                # Links to all platform downloads
│                                # - iOS: App Store link
│                                # - Android: Play Store link
│                                # - macOS: DMG download (GitHub Releases)
│                                # - Windows: NSIS installer (GitHub Releases)
│                                # - Linux: AppImage + .deb (GitHub Releases)
│                                # - Chrome: Web Store link
│                                # - npm: @pulso/companion
│
├── examples/
│   ├── swarm-email-triage.yaml  # Example swarm configs (no proprietary code)
│   ├── swarm-code-review.yaml
│   └── swarm-research.yaml
│
└── .github/
    ├── ISSUE_TEMPLATE/
    │   ├── bug_report.md
    │   ├── feature_request.md
    │   └── channel_issue.md
    └── FUNDING.yml               # Sponsor links if applicable
```

#### What is NOT in the public repo

- No server source code (`apps/server`)
- No web app source code (`apps/web`)
- No mobile app source code (`apps/mobile`)
- No companion source code (`apps/companion`)
- No internal packages (`packages/*`)
- No CI/CD workflows (those stay in private repo)
- No environment variables, secrets, or credentials
- No database schema or migration files

#### Competitor Reference

| Platform | Stars | What's Public | Our Approach |
|----------|-------|--------------|--------------|
| Botpress | 15k | SDK + integrations only | Most similar — docs hub |
| CrewAI | 44k | Framework (MIT) | We don't open-source any runtime |
| n8n | 176k | Full source (fair-code) | We stay fully proprietary |
| Dify | 130k | Full source (anti-SaaS) | We stay fully proprietary |

### 8.2 Documentation

- [ ] Deploy `docs.runpulso.com` (content mirrors public repo docs/)
- [ ] API reference (auto-generated from route types)
- [ ] Getting started guide (with screenshots)
- [ ] Swarm template gallery with live preview
- [ ] Channel setup guides per platform (with video walkthroughs)
- [ ] Companion CLI reference

### 8.3 Marketing

- [ ] Landing page final polish
- [ ] 500+ swarm templates in gallery
- [ ] Demo videos (CEO workflow, code pipeline, financial analysis)
- [ ] Product Hunt launch plan
- [ ] Twitter/X thread showing capabilities
- [ ] GitHub repo README with badges, screenshots, feature comparison

---

## Summary Timeline

| Week | Focus | Deliverable |
|------|-------|------------|
| 1-2 | Store submissions | iOS TestFlight, Android internal track, Edge extension |
| 2 | Web hardening | Custom domain, PWA, SEO |
| 3-5 | Desktop builds | Windows + Linux installers via CI |
| 4-7 | Companion cross-platform | macOS extraction, Windows test, Linux adapter |
| 5-10 | Mobile screens | 19 screens matching web feature parity |
| 6-8 | Browser extensions | Firefox + Safari |
| 8-12 | Infrastructure | CI/CD, security, monitoring |
| 10-14 | Launch prep | Public repo, docs, templates, marketing |
