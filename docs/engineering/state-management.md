# State Management

## Purpose

Define how runtime state is represented and controlled.

## Reference When

Use when adding benchmark execution state, report state, config, retries, or UI
interactions.

## AI Agents Must Obey

Keep state explicit, minimal, and close to the owner.

## CLI and Runner State

- Represent run configuration as an immutable object.
- Track request state with request IDs.
- Avoid global mutable state.
- Keep random seeds configurable for reproducible workloads.
- Store timing state per request.

## Report State

- Static reports should not require a backend.
- Client-side interactivity should be derived from embedded report data.
- Avoid storing raw trace data in the browser when aggregated data is enough.

## Configuration

Precedence should be:

1. CLI flags.
2. Environment variables.
3. Config file.
4. Built-in defaults.

Document any exception.

