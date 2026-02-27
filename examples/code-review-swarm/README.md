# Code Review Swarm

A multi-agent pipeline that reviews your code for security, testing, and quality.

## Architecture

```
┌──────────────────┐     ┌──────────────────┐
│ security-scanner │     │   test-checker   │
│  (Sonnet 4.5)    │     │   (Haiku 4.5)    │
└────────┬─────────┘     └────────┬─────────┘
         │                        │
         └────────┬───────────────┘
                  ▼
         ┌──────────────────┐
         │  code-reviewer   │
         │  (Sonnet 4.5)    │
         └──────────────────┘
```

## How It Works

1. **Security Scanner** and **Test Checker** run in parallel
2. Both analyze the codebase from different angles
3. **Code Reviewer** runs after both complete, producing a final summary

## Run

```bash
cd examples/code-review-swarm
pulso swarm "Review the src/ directory for bugs and improvements"
```

## Cost

Approximately $0.50-$1.50 per review depending on codebase size.
