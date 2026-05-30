# API Design

## Purpose

Define CLI, trace, profile, and internal API contracts.

## Reference When

Use when adding commands, flags, schema fields, profiles, gates, or library
entry points.

## AI Agents Must Obey

Public contracts must be stable, documented, and versioned.

## CLI Design

- Commands should map to user jobs: `bench`, `report`, `diff`, `replay`.
- Flags should be explicit and composable.
- Defaults must be safe for local use.
- Exit codes must distinguish success, user error, and gate failure.

## Trace Schema

- Use JSONL with one request per line.
- Include `schema_version`.
- Include timings in milliseconds with explicit field names.
- Preserve request status.
- Store errors as structured objects when possible.
- Version breaking changes.

## Gate Expressions

- Keep gate syntax readable in CI.
- Fail closed for invalid expressions.
- Report exact metric values used.

## Internal APIs

- Prefer typed inputs and outputs.
- Avoid passing raw dicts beyond schema boundaries.
- Keep pure metric APIs independent of CLI and report libraries.

