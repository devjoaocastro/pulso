# Agent Identity Portability (AIP)
### An Open Standard Proposal by Pulso

> **Status:** Draft v0.1 — February 2026
> **Authors:** Pulso Team ([@usepulso](https://github.com/usepulso))
> **License:** CC0 1.0 Universal (public domain)

---

## The Problem

Your AI agent knows you. It knows your communication style, your projects, your preferences, the context behind every decision. It has learned from months of interaction. It manages your workflows, your businesses, your digital life.

Then you want to switch platforms, or use two platforms simultaneously, or back up your agent before a major update.

**You lose everything.** Your agent's memory. Its personality calibration. Its learned behaviors. The relationship you built.

This is AI lock-in — and it's worse than email lock-in, because what's locked isn't just messages. It's **your agent's understanding of who you are.**

---

## The Proposal

**AIP (Agent Identity Portability)** is an open, vendor-neutral format for exporting and importing a complete AI agent identity across platforms.

Think of it like:
- **Phone number portability** — you own your number, not your carrier
- **Email export (MBOX)** — you own your messages, not your client
- **OAuth** — a standard that every platform agreed to implement, benefiting everyone

AIP is the equivalent for AI agents. **Your agent is yours. Not the platform's.**

Any platform that implements AIP can:
- Export a user's agent to `.aip` format
- Import an agent from any other AIP-compatible platform
- Merge agents (combining memory from two platforms)
- Clone agents (create a new agent with the same base identity)

---

## The Format

An AIP bundle is a **signed, optionally encrypted JSON file** with the `.aip` extension.

```json
{
  "aip_version": "0.1",
  "created_at": "2026-02-27T00:00:00Z",
  "exported_by": {
    "platform": "pulso",
    "version": "1.0.0",
    "instance": "api.runpulso.com"
  },

  "identity": {
    "id": "agt_01jnrx8k4m3p5q7r9s2t",
    "name": "João's Assistant",
    "description": "Personal agent for João Castro — indie founder, developer, Portuguese",
    "language": "pt-PT",
    "timezone": "Europe/Lisbon",
    "personality": "direct, no fluff, technical depth when needed, never uses emojis unless asked",
    "avatar_url": "https://cdn.runpulso.com/avatars/agt_01jnrx8k4m3p5q7r9s2t.svg",
    "avatar_data": "<svg>...</svg>"
  },

  "memory": {
    "version": 1,
    "exported_at": "2026-02-27T00:00:00Z",

    "persistent": [
      {
        "key": "user_context",
        "value": "João Castro, founder of Pulso and Vulk, based in Portugal. Prefers async communication. Builds on Cloudflare Workers.",
        "importance": 0.95,
        "created_at": "2026-01-15T10:00:00Z",
        "last_accessed": "2026-02-26T18:30:00Z",
        "access_count": 47,
        "tags": ["identity", "context"]
      }
    ],

    "entities": [
      {
        "id": "ent_01jnrx8k4m",
        "name": "Pulso",
        "type": "project",
        "description": "AI agent OS for indie operators. Cloud-native, Cloudflare Workers.",
        "importance": 0.98,
        "attributes": {
          "status": "in development",
          "url": "runpulso.com",
          "stack": "Hono + React + React Native + Tauri"
        }
      },
      {
        "id": "ent_01jnrx8k4n",
        "name": "João Castro",
        "type": "person",
        "description": "Owner — indie founder, developer",
        "importance": 1.0
      }
    ],

    "relations": [
      {
        "from": "ent_01jnrx8k4n",
        "to": "ent_01jnrx8k4m",
        "type": "builds",
        "weight": 1.0,
        "created_at": "2026-01-15T10:00:00Z"
      }
    ],

    "semantic_index": {
      "format": "float32",
      "dimensions": 1024,
      "model": "text-embedding-3-large",
      "vectors": "base64_encoded_binary_blob_or_external_url"
    }
  },

  "configuration": {
    "model_preferences": {
      "default": "claude-sonnet-4-6",
      "fast": "claude-haiku-4-5",
      "reasoning": "claude-opus-4-6",
      "image": "google/imagen-3"
    },
    "response_style": {
      "format": "markdown",
      "length": "concise",
      "language": "pt-PT",
      "formality": "informal"
    },
    "budget": {
      "daily_limit_usd": 5.0,
      "per_task_limit_usd": 1.0,
      "alert_threshold": 0.8
    },
    "active_channels": ["web", "telegram", "whatsapp"]
  },

  "learned_behaviors": {
    "communication_style": {
      "preferred_post_length": "short",
      "topics_of_interest": ["AI agents", "indie hacking", "Cloudflare", "Portugal tech"],
      "rejected_topics": ["NFTs", "crypto speculation"],
      "tone": "direct and technical, sometimes provocative"
    },
    "approval_patterns": [
      {
        "context": "social_post",
        "accepted_patterns": ["technical depth", "personal story", "controversial take"],
        "rejected_patterns": ["too formal", "generic AI content", "corporate speak"],
        "sample_count": 124
      }
    ],
    "workflow_preferences": {
      "prefers_confirmation_before": ["sending messages", "deleting files", "publishing content"],
      "auto_approves": ["reading files", "web searches", "calendar lookups"]
    }
  },

  "swarms": [
    {
      "id": "swarm_presence",
      "name": "Presence — Social Media OS",
      "description": "5-agent system managing online presence",
      "yaml": "name: presence\nagents:\n  - name: Scout\n    model: claude-haiku-4-5\n    ..."
    }
  ],

  "forge_businesses": {
    "note": "Encrypted with owner's key. Decryption requires original AIP password.",
    "encrypted_payload": "base64_aes256gcm_encrypted_blob"
  },

  "metadata": {
    "total_conversations": 1247,
    "total_tasks_completed": 389,
    "total_cost_usd": 12.47,
    "member_since": "2026-01-10T00:00:00Z",
    "export_includes": ["identity", "memory", "configuration", "behaviors", "swarms"],
    "export_excludes": ["api_keys", "oauth_tokens", "payment_info"]
  },

  "signature": {
    "algorithm": "Ed25519",
    "public_key": "base64_encoded_public_key",
    "signed_fields": ["identity", "memory", "configuration"],
    "signature": "base64_encoded_signature",
    "signed_at": "2026-02-27T00:00:00Z"
  }
}
```

---

## Privacy & Security

An AIP bundle **never contains:**
- API keys or tokens
- OAuth credentials
- Payment information
- Raw conversation transcripts (only extracted memory)
- Passwords

An AIP bundle **optionally encrypts:**
- Forge business data (revenue, client info)
- Learned behaviors (if user chooses)
- The entire bundle (password-protected `.aip`)

**Signing:** Every AIP export is signed by the exporting platform's key, allowing the importing platform to verify authenticity and detect tampering.

---

## The `.aip` File

An AIP bundle is distributed as a single `.aip` file, which is:

1. **JSON** — for standard, unencrypted exports
2. **Encrypted JSON** — when the user chooses a password
3. **Compressed** — gzipped before base64 encoding for large bundles

```
agent-joao-2026-02-27.aip
```

File size estimates:
- Minimal agent (few memories): ~50KB
- Average user (1 year of use): ~500KB - 2MB
- Power user (knowledge graph + many swarms): ~10MB

---

## Platform Compatibility Matrix

| Feature | Pulso | Dify | n8n | OpenHands | Any AIP platform |
|---------|:-----:|:----:|:---:|:---------:|:----------------:|
| Export AIP | v1.0 | — | — | — | Coming |
| Import AIP | v1.0 | — | — | — | Coming |
| Memory portability | Full | Partial | — | — | — |
| Swarm portability | Full | Workflow | Workflow | — | — |
| Behavior learning | Full | — | — | — | — |

*We're actively working with other platforms to adopt AIP. If you build AI agents and want to implement AIP, see [Implementation Guide](#implementation-guide).*

---

## Implementation Guide

### Exporting (any platform)

```typescript
// Minimum viable AIP export
interface AIPBundle {
  aip_version: string           // "0.1"
  created_at: string            // ISO 8601
  exported_by: ExportedBy
  identity: AgentIdentity       // REQUIRED
  memory: AgentMemory           // REQUIRED
  configuration?: AgentConfig   // optional
  learned_behaviors?: Behaviors // optional
  swarms?: SwarmTemplate[]      // optional
  signature: Signature          // REQUIRED
}
```

The minimum implementation requires: `identity` + `memory` + `signature`.

### Importing (any platform)

1. Verify the signature
2. Check `aip_version` compatibility
3. Merge or replace existing memory (user's choice)
4. Map `configuration` to platform-native settings
5. Import `swarms` as platform-native workflows where possible

### What to do with incompatible fields

If your platform doesn't support a field (e.g., `forge_businesses`), **preserve it** in a `_preserved_fields` block. The user may export again to a platform that does support it.

```json
{
  "_preserved_fields": {
    "forge_businesses": { "...": "..." }
  }
}
```

---

## Why Open Standard?

AI agent lock-in is not a feature — it's a failure mode.

Users should be able to:
- Back up their agent before a platform shuts down
- Use multiple platforms simultaneously
- Give their agent to a trusted person when they can no longer use it
- Migrate without losing the relationship they built

This is not a competitive moat. The platform that gives users the most trust wins. And trust starts with ownership.

**Pulso is proposing this standard and implementing it first. We hope others follow.**

---

## Roadmap

| Milestone | Target |
|-----------|--------|
| AIP v0.1 spec (this document) | Feb 2026 |
| Pulso Export implementation | Q1 2026 |
| Pulso Import implementation | Q1 2026 |
| AIP v1.0 (community feedback incorporated) | Q2 2026 |
| First third-party platform implementation | Q3 2026 |
| AIP working group formation | Q4 2026 |

---

## Contributing

This is a community standard, not a Pulso-owned standard.

- Open issues to propose changes
- Fork and submit PRs for improvements
- Join the discussion at [GitHub Discussions](https://github.com/usepulso/pulso/discussions)

We want this to be the foundation every AI agent platform builds on — like OAuth became for authentication.

---

## Related Work

- [Verifiable Credentials (W3C)](https://www.w3.org/TR/vc-data-model/) — identity standards
- [MBOX format](https://www.rfc-editor.org/rfc/rfc4155) — email portability precedent
- [ActivityPub](https://activitypub.rocks/) — decentralized social protocol
- [GDPR Article 20](https://gdpr-info.eu/art-20-gdpr/) — right to data portability (legal mandate)

---

<p align="center">
  <sub>AIP is proposed by <a href="https://runpulso.com">Pulso</a> and released under CC0 (public domain).<br/>
  Anyone can implement it. No permission needed. No royalties. No strings.</sub>
</p>
