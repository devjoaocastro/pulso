# Contributing to Pulso

Thank you for your interest in contributing to Pulso! This guide will help you get started.

## Development Setup

```bash
# Fork and clone the repository
git clone https://github.com/YOUR_USERNAME/pulso.git
cd pulso

# Install dependencies (requires pnpm 9+)
pnpm install

# Build all packages
pnpm build

# Run tests
pnpm test

# Type-check
pnpm typecheck
```

## Project Structure

```
packages/
  core/        @pulso/core — Agent runtime, orchestrator
  providers/   @pulso/providers — LLM adapters
  tools/       @pulso/tools — MCP-compatible tools
  memory/      @pulso/memory — Memory system
apps/
  cli/         @pulso/cli — Command-line interface
agents/        Pre-built agent templates
examples/      Example swarm configurations
```

## Making Changes

1. Create a branch: `git checkout -b feature/your-feature`
2. Make your changes
3. Add tests for new functionality
4. Run `pnpm test` and `pnpm typecheck`
5. Run `pnpm format` to ensure consistent formatting
6. Create a changeset: `pnpm changeset`
7. Push and create a Pull Request

## Pull Request Guidelines

- Keep PRs focused — one feature or fix per PR
- Include tests for new functionality
- Update documentation if needed
- Follow the existing code style
- Add a changeset for any user-facing changes

## Code Style

- TypeScript with strict mode
- ESM imports with `.js` extensions
- Prettier for formatting
- Vitest for testing
- JSDoc comments on public APIs

## Reporting Issues

- Use GitHub Issues
- Include reproduction steps
- Include your environment (Node version, OS)
- Include relevant error messages

## Code of Conduct

Be kind, be respectful. We're all here to build something great together.
