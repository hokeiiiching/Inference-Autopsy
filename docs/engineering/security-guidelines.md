# Security Guidelines

## Purpose

Protect user credentials, prompts, endpoint details, and generated artifacts.

## Reference When

Use when handling API keys, URLs, traces, reports, logs, config, or CI.

## AI Agents Must Obey

Never expose secrets or sensitive trace content by default.

## Rules

- Read API keys from environment variables or explicit secret providers.
- Do not print authorization headers.
- Redact secrets in logs and errors.
- Hash or alias endpoint URLs in shareable traces and reports.
- Document when prompts are stored in traces.
- Provide opt-in controls for saving full prompts if needed.
- Keep file permissions reasonable for local artifacts.

## CI Rules

- Use GitHub Actions secrets for provider credentials.
- Do not upload raw traces containing sensitive prompts unless explicitly
  configured.
- Prefer sanitized report artifacts.

## Dependency Security

- Avoid dependencies with unclear maintenance.
- Pin release dependencies appropriately.
- Review transitive dependencies before adding report or browser tooling.

