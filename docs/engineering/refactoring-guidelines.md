# Refactoring Guidelines

## Purpose

Define safe refactoring practices.

## Reference When

Use when simplifying code, moving modules, reducing duplication, or preparing
for a feature.

## AI Agents Must Obey

Refactors must preserve behavior unless behavior change is explicitly scoped.

## Rules

- Separate refactors from feature changes when practical.
- Start with tests or characterization checks.
- Move code before rewriting code.
- Keep public imports stable or provide compatibility shims.
- Update docs for architecture or module boundary changes.
- Remove dead code after proving it is unused.

## Good Refactor Targets

- Duplicate metric calculations.
- Long functions with multiple responsibilities.
- Mixed transport and domain logic.
- Report rendering that computes canonical metrics.
- Tests with repeated complex setup.

## Refactor Stop Conditions

Stop and reassess when:

- The refactor changes CLI behavior.
- Fixture outputs change unexpectedly.
- A simple move requires broad unrelated edits.
- The new abstraction is harder to explain than the old code.

