# Decision Framework

## Purpose

Define how architectural and product decisions are made.

## Reference When

Use when choices affect public behavior, dependencies, architecture, or
long-term maintenance.

## AI Agents Must Obey

Escalate significant decisions into an RFC or ADR.

## Decision Levels

- Local: small implementation choice inside one module.
- Project: affects multiple modules or user behavior.
- Strategic: changes product direction, architecture, dependencies, or public
  contracts.

## Required ADR/RFC

Create one for:

- Trace schema breaking changes.
- New dependency class.
- Database or hosted service introduction.
- CLI command rename or removal.
- Major report UX change.
- Concurrency model change.

## Evaluation Criteria

- User value.
- Simplicity.
- Reversibility.
- Testability.
- Compatibility.
- Security.
- Maintenance cost.

