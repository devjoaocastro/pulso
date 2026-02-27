# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability in Pulso, please report it responsibly.

**Do NOT open a public GitHub issue for security vulnerabilities.**

Instead, please email: **security@runpulso.com**

We will respond within 48 hours and work with you to resolve the issue.

## Supported Versions

| Version | Supported |
| ------- | --------- |
| 0.1.x   | Yes       |

## How We Handle Your Data

### Credential Encryption

- All API keys are encrypted with **AES-256-GCM** before storage
- Encryption keys are derived using **PBKDF2** with 100,000 iterations
- Unique salt and IV per credential
- Zero-knowledge architecture — the server cannot read your API keys at rest

### Authentication

- Passwords hashed with PBKDF2 (100K iterations, SHA-256)
- JWT tokens with HMAC-SHA256, 7-day expiry
- Timing-safe comparison to prevent timing attacks

### Agent Execution

Pulso agents can execute actions on your behalf. Security controls include:

- **Sandboxed execution** — each agent runs in isolation
- **Explicit tool permissions** — agents only access tools you authorize
- **Budget enforcement** — hard spending limits prevent runaway costs
- **Audit logging** — all agent actions are logged

### Self-Hosting

When self-hosting Pulso, ensure:

- `JWT_SECRET` is a strong random value (32+ characters)
- `ENCRYPTION_KEY` is generated securely
- D1/KV stores are not publicly accessible
- HTTPS is enforced in production

## Security Considerations

In Advanced Mode, agents can:

- Read and write files on the filesystem
- Execute shell commands
- Make network requests

Always review your `pulso.yaml` configuration and agent prompts carefully.
Use the `permissions` field to restrict agent capabilities.
