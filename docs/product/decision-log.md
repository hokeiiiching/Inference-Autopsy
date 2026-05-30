# Product Decision Log

## Purpose

Track product decisions that affect scope, users, or public behavior.

## Reference When

Use when making or reviewing product tradeoffs.

## AI Agents Must Obey

Record decisions that explain why the product does or does not do something.

## Format

```md
## YYYY-MM-DD: <decision>

Status: proposed | accepted | superseded
Owner: <name>

Context:
<why this decision was needed>

Decision:
<what we chose>

Consequences:
<tradeoffs and follow-up>
```

## Initial Decisions

### 2026-05-30: Local CLI and Static Reports First

Status: accepted
Owner: project maintainers

Context: Users need reproducible inference profiling without operating a hosted
service.

Decision: Build a polished local CLI and static HTML reports before any hosted
dashboard.

Consequences: The architecture should avoid server assumptions and keep report
artifacts self-contained.

