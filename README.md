<p align="center">
  <a href="https://app.runpulso.com">
    <img src="assets/banner.svg" alt="Pulso — AI agents that actually do things" width="100%" />
  </a>
</p>

<p align="center">
  <a href="https://app.runpulso.com"><img src="https://img.shields.io/badge/Launch_Dashboard-FF512F?style=for-the-badge&logoColor=white" alt="Launch" /></a>
  &nbsp;
  <a href="https://www.npmjs.com/package/@pulso/companion"><img src="https://img.shields.io/badge/npm_install-@pulso/companion-cb3837?style=for-the-badge&logo=npm&logoColor=white" alt="npm" /></a>
  &nbsp;
  <a href="https://x.com/usepulso"><img src="https://img.shields.io/badge/Follow-@usepulso-000000?style=for-the-badge&logo=x&logoColor=white" alt="Twitter" /></a>
</p>

<br />

> **Tired of AI that just talks?** Every chatbot in 2026 does the same thing — you type, it types back, you still do everything yourself. Heavy, bloated, insecure apps that promise automation and deliver autocomplete.
>
> **Pulso agents execute.** They check your email, deploy your code, message your team, control your computer, and work together — from any device, any channel, any AI model.

<br />

---

<br />

## See what's possible

<br />

### Your agent sees your screen, clicks, types — like a human

The Companion daemon gives agents **computer vision**. They take screenshots, read text via OCR, move the mouse, click buttons, type text, drag elements, and use keyboard shortcuts. Any app. Any workflow.

```
You (Telegram):
    "Open Photoshop, create a new 1920x1080 canvas, add the
     company logo from my Desktop, center it, add the text
     'Q1 Report 2026' below it in Helvetica Bold, and export as PNG."

Pulso (Companion — screenshot + mouse + keyboard):

    ├─ Launched Photoshop
    ├─ 📸 Screenshot → identified menu bar, tools
    ├─ File → New → 1920x1080 → Create
    ├─ File → Place Embedded → navigated to Desktop/logo.png
    ├─ Centered logo with Cmd+A → align center
    ├─ Selected Type tool → clicked below logo
    ├─ Typed "Q1 Report 2026" → set Helvetica Bold 48pt
    ├─ Aligned text center
    ├─ File → Export → Quick Export as PNG
    └─ Saved to Desktop/q1-report-cover.png

    ✓ "Here's your cover. Want me to adjust anything?"
```

<br />

### Control your entire desktop from WhatsApp

```
You (WhatsApp, from the airport):
    "Close all my open browser tabs, save any unsaved docs,
     put Spotify on my chill playlist, dim the office lights
     to 30%, and lock my Mac."

Pulso (Companion):

    ├─ Listed 34 Chrome tabs → saved 3 with unsaved forms
    ├─ Closed all Chrome tabs
    ├─ Found 2 unsaved TextEdit docs → saved both
    ├─ 🎵 Spotify → playing "Chill Vibes" playlist
    ├─ 💡 Philips Hue → office lights dimmed to 30%
    ├─ 🔒 Screen locked

    ✓ Office secured. Music playing. Lights dimmed.
      Safe travels.
```

<br />

### Deploy from your phone at midnight

```
You (WhatsApp, 11:47 PM):
    "Run tests on the backend, if green deploy to production,
     then verify everything works."

Pulso (3 agents, 38 seconds):

    Test Agent
    ├─ Ran 247 tests via Companion shell
    ├─ 247 passed, 0 failed
    └─ Coverage: 94.2%

    Build Agent
    ├─ Built production bundle (3.2 MB gzipped)
    └─ Deployed to production

    Verification Agent
    ├─ Health check: 200 OK (34ms)
    └─ All endpoints responding

    ✓ Live. Deploy log saved.
```

<br />

### Research report while you sleep — 5 agents in parallel

```
You (Telegram, before bed):
    "Research EU AI regulation 2026. Compare 8+ countries.
     Professional report with executive summary."

Pulso (5 agents, 4 minutes, $0.12):

    3 Research Agents (parallel)
    ├─ Deep web search across 140+ sources
    ├─ 11 EU countries analyzed
    └─ Cross-referenced legal databases

    Analysis Agent
    ├─ 7 key regulatory trends identified
    └─ Compliance timeline mapped

    Writer Agent
    ├─ 22-page report with executive summary
    └─ Saved to Google Drive, sent to your email

    ✓ Notification on Slack #research
```

<br />

### Browse the web, extract data, fill forms — no extensions

```
You (Slack):
    "Go to our competitor's pricing page, screenshot it,
     extract all their plan prices, and put them in a
     spreadsheet on my Desktop."

Pulso (Companion — browser + OCR + files):

    ├─ Opened Chrome → navigated to competitor site
    ├─ 📸 Screenshot of pricing page
    ├─ OCR extracted 4 plans with prices and features
    ├─ Cross-checked with 2 other competitor sites
    ├─ Created competitor-pricing.csv on Desktop
    └─ Formatted with plan name, price, key features

    ✓ "Spreadsheet ready. They raised prices 15% since
       last quarter. Want me to compare with ours?"
```

<br />

### Smart home from any channel

```
You (Telegram, arriving home):
    "I'm home. Movie night setup."

Pulso (Companion — Hue + Sonos + system):

    ├─ 💡 Living room lights → "Movie" scene (10% warm)
    ├─ 💡 Kitchen lights → off
    ├─ 🔊 Sonos → volume 40%, ambient soundtrack
    ├─ 🖥️ Mac → Do Not Disturb on
    ├─ 🖥️ Mac → dark mode enabled
    └─ 📱 Notification: "Movie night ready. Enjoy."
```

<br />

### Set up a new Mac in one command

```
You (Web Chat):
    "Set up this MacBook for full-stack dev."

Pulso (Companion, 6 minutes):

    ├─ Installed Homebrew, Node 22, Python 3.12, Rust, Go
    ├─ Installed VS Code + 14 extensions (from your memory)
    ├─ Cloned 8 pinned GitHub repos
    ├─ Configured git, SSH keys, GPG
    ├─ Installed Docker, Postgres, Redis
    ├─ Applied dotfiles (.zshrc, .gitconfig, .vimrc)
    ├─ Set dark mode, Dock, keyboard shortcuts
    └─ Added apps to login items

    ✓ Ready to code. 47 packages. 14 extensions. 8 repos.
```

<br />

### 24/7 infrastructure monitoring

```
Automation (every 5 min, $0.001/check):

    ├─ api.yourapp.com: 200 OK (23ms)
    ├─ app.yourapp.com: 200 OK (45ms)
    ╰─ cdn.yourapp.com: ⚠️ 503 (timeout)

    → Detected CDN failure
    → Auto-restarted origin server via shell
    → Verified: 200 OK (38ms)
    → Alert → Telegram + Slack with timeline
```

<br />

### Message your contacts via iMessage

```
You (Web Chat):
    "Send Maria a message on iMessage saying I'll be
     15 minutes late for lunch."

Pulso (Companion — iMessage + Contacts):

    ├─ Searched contacts → found Maria Santos
    ├─ 💬 iMessage sent: "Hey Maria, running about
    │   15 minutes late for lunch. Be there soon!"
    └─ ✓ Delivered

    "Done. Message sent to Maria."
```

<br />

### Manage your music from Telegram

```
You (Telegram):
    "Play something chill on Spotify. And put the living
     room Sonos on the same vibe, lower volume."

Pulso (Companion — Spotify + Sonos):

    ├─ 🎵 Spotify → searched "chill lo-fi beats"
    ├─ Playing "Lo-Fi Chill Beats" playlist
    ├─ 🔊 Sonos Living Room → same playlist via Spotify URI
    ├─ Sonos volume → 25%
    └─ Mac Spotify volume → 60%

    ✓ "Vibes set. Want me to queue anything specific?"
```

<br />

### Manage your week from anywhere

```
You (Telegram):
    "Cancel non-essential meetings this week. Book a
     dentist Thursday afternoon."

Pulso (2 agents, 8 seconds):

    Calendar Agent
    ├─ Cancelled 3 low-priority meetings
    ├─ Kept: client call, standup, sprint review
    └─ Booked dentist Thu 2 PM (Dr. Silva)

    Communication Agent
    ├─ Sent cancellation emails with apologies
    └─ Confirmation in your inbox

    ✓ Freed up 4.5 hours this week
```

<br />

### Run any macOS Shortcut

```
You (Discord):
    "Run my 'End of Day' shortcut."

Pulso (Companion — Shortcuts):

    ├─ Triggered "End of Day" Shortcut
    │   ├─ Closed all open apps
    │   ├─ Emptied Downloads folder
    │   ├─ Backed up Desktop to iCloud
    │   └─ Set tomorrow's focus schedule
    └─ ✓ Shortcut completed

    "Done. Tomorrow's schedule is set. Have a good night."
```

<br />

---

<br />

<p align="center">
  <img src="assets/features.svg" alt="Pulso Capabilities" width="100%" />
</p>

<br />

---

<br />

## Download

<table>
  <tr>
    <td align="center" width="180">
      <a href="https://app.runpulso.com">
        <img src="https://img.shields.io/badge/Web-Launch_App-FF512F?style=for-the-badge" alt="Web App" />
      </a>
      <br /><sub>Dashboard · Chat · Builder</sub>
    </td>
    <td align="center" width="180">
      <a href="https://apps.apple.com/app/pulso-ai-agents/id6740000000">
        <img src="https://img.shields.io/badge/iOS-App_Store-000000?style=for-the-badge&logo=apple&logoColor=white" alt="iOS" />
      </a>
      <br /><sub>iPhone · iPad</sub>
    </td>
    <td align="center" width="180">
      <a href="https://play.google.com/store/apps/details?id=com.runpulso.app">
        <img src="https://img.shields.io/badge/Android-Google_Play-3DDC84?style=for-the-badge&logo=googleplay&logoColor=white" alt="Android" />
      </a>
      <br /><sub>Phone · Tablet</sub>
    </td>
  </tr>
  <tr>
    <td align="center">
      <a href="https://www.npmjs.com/package/@pulso/companion">
        <img src="https://img.shields.io/badge/Companion-npm_install-cb3837?style=for-the-badge&logo=npm&logoColor=white" alt="Companion" />
      </a>
      <br /><sub>macOS · Windows · Linux</sub>
    </td>
    <td align="center">
      <a href="https://github.com/usepulso/pulso/releases">
        <img src="https://img.shields.io/badge/Menu_Bar-Download-8b5cf6?style=for-the-badge&logo=apple&logoColor=white" alt="Menu Bar" />
      </a>
      <br /><sub>Native macOS app</sub>
    </td>
    <td align="center">
      <a href="https://api.runpulso.com">
        <img src="https://img.shields.io/badge/API-Documentation-3b82f6?style=for-the-badge" alt="API" />
      </a>
      <br /><sub>REST · SSE · WebSocket</sub>
    </td>
  </tr>
</table>

<br />

---

<br />

<p align="center">
  <img src="assets/platform.svg" alt="Pulso Platform Architecture" width="100%" />
</p>

<br />

---

<br />

## Pricing

| | **Solo** | **Swarm** | **Fleet** |
|---|:---:|:---:|:---:|
| | Free | **$19**/mo | **$49**/mo |
| Channels | 1 | 12 | Unlimited |
| Agent Teams | — | Up to 10 | Up to 20 |
| Memory | 100 | 10,000 | 100,000 |
| Companion | — | Included | Included |
| Automations | — | 10 triggers | 100 triggers |
| MCP Servers | — | 5 | 50 |
| Credits | — | $5/mo included | $20/mo included |

<p align="center"><sub>All plans include BYOK (Bring Your Own Key) at zero cost. Your keys, your models, your data.</sub></p>

<br />

---

<br />

## Get started in 60 seconds

```bash
# 1. Sign up (free)
open https://app.runpulso.com

# 2. Add your API keys → Settings → Providers
#    (Anthropic, OpenAI, Google, DeepSeek, Mistral, Ollama, OpenRouter)

# 3. Start chatting — your agent is ready

# 4. Want computer control? Install the Companion:
npm install -g @pulso/companion
pulso-companion login
```

<br />

---

<br />

<p align="center">
  <a href="https://app.runpulso.com"><img src="https://img.shields.io/badge/Start_Free-FF512F?style=for-the-badge&logoColor=white" alt="Start Free" /></a>
</p>

<p align="center">
  <sub>
    <a href="https://github.com/usepulso/pulso/issues/new?template=bug_report.md">Report Bug</a> ·
    <a href="https://github.com/usepulso/pulso/issues/new?template=feature_request.md">Request Feature</a> ·
    <a href="https://github.com/usepulso/pulso/discussions">Discussions</a> ·
    <a href="SECURITY.md">Security</a>
  </sub>
</p>

<p align="center">
  <sub>
    <a href="https://app.runpulso.com/terms">Terms</a> ·
    <a href="https://app.runpulso.com/privacy">Privacy</a> ·
    <a href="https://app.runpulso.com/cookies">Cookies</a> ·
    <a href="https://app.runpulso.com/acceptable-use">Acceptable Use</a>
  </sub>
</p>

<br />

<p align="center">
  <sub>Built by <a href="https://codeahead.pt">CodeAhead</a> in Portugal · © 2026 CodeAhead Lda · All rights reserved</sub>
</p>
