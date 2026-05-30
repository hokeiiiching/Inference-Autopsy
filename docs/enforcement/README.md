# Enforcement System

## Purpose

Turn documentation rules into automated and reviewable checks.

## Reference When

Use when configuring CI, pre-commit hooks, ownership, or AI validation.

## AI Agents Must Obey

Prefer measurable checks over relying on memory.

## Enforcement Layers

- Local: format, lint, type check, unit tests.
- CI: full tests, fixtures, report generation, security checks.
- Review: PR checklist, docs review, architecture review.
- Governance: ADR/RFC for significant changes.
- AI validation: task-specific checklist before handoff.

## Initial Tooling Ideas

- `ruff check .`
- `ruff format --check .`
- `mypy autopsy`
- `pytest`
- Markdown link check.
- Trace schema fixture validation.
- Report generation smoke test.
- Dependency audit.

