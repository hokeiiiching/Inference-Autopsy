# AI Anti-Patterns

## Purpose

List patterns that are forbidden or strongly discouraged in this repository.

## Reference When

Use during design, implementation, review, and refactoring.

## AI Agents Must Obey

If a requested implementation requires one of these patterns, stop and propose a
safer alternative.

## Forbidden Patterns

- Premature abstractions with only one caller.
- Generic `utils` modules containing unrelated functions.
- Metric calculations duplicated in CLI, reports, and diff code.
- UI components that fetch data directly from transport clients.
- Silent fallback behavior that changes benchmark meaning.
- Catch-all exception handling without preserving context.
- Logging secrets, prompts, or raw endpoint URLs by default.
- Unversioned trace schema changes.
- Hidden retries that distort latency measurements.
- Mutable global benchmark state.
- Tests that depend on live external providers by default.
- Report charts that cannot be traced back to source metrics.

## Complexity Smells

- A small feature requires changes across many unrelated modules.
- A function needs more than three levels of nesting.
- A class exists only to group functions without state or polymorphism.
- A configuration option has unclear ownership.
- A dependency is added for a feature that standard library code can handle
  clearly.

## Refactor Triggers

Refactor when:

- The same business rule appears in multiple places.
- A module mixes transport, parsing, metrics, and rendering.
- Tests require excessive setup to cover simple logic.
- A public contract is implicit instead of typed and documented.

