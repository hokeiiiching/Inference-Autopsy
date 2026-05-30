# AI Agent Rules

## Purpose

Define how AI coding agents must behave in this repository.

## Reference When

Read this at the start of every task and whenever a request is ambiguous,
large, risky, or architecture-touching.

## AI Agents Must Obey

- Treat existing code, docs, and user edits as the source of truth.
- Make the smallest change that solves the stated problem.
- Prefer simple, explicit code over clever abstractions.
- Keep CLI behavior, trace format, and report output stable unless explicitly
  changing them.
- Verify changes with tests, type checks, linting, or focused manual checks.
- Update docs when behavior, architecture, workflow, or public contracts change.
- Preserve reproducibility: benchmark inputs, trace output, and diff logic must
  be inspectable.

## Operating Principles

1. Read before editing.
2. Understand boundaries before adding dependencies.
3. Design for local-first usage and static artifacts.
4. Keep data contracts versioned and migration-aware.
5. Make failure states visible and actionable.
6. Prefer deterministic tests for metrics and diagnosis logic.

## Required Reasoning Before Implementation

Before coding, identify:

- The user-facing behavior being changed.
- The module or document that owns the behavior.
- Inputs, outputs, and persistence contracts.
- Risks to backwards compatibility.
- The narrowest verification command.
- Whether docs or templates must change.

## DO NOT

- Do not invent architecture that is not represented in the repo.
- Do not add dependencies because they are convenient for a tiny task.
- Do not duplicate metric calculations across modules.
- Do not mix transport, parsing, metrics, diagnosis, and presentation logic.
- Do not silently change trace schema fields or CLI flags.
- Do not hide errors that affect benchmark validity.
- Do not optimize before measuring.
- Do not make report visuals beautiful at the expense of interpretability.

