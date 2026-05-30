# Development Lifecycle

## Purpose

Define how work moves from idea to release.

## Reference When

Use for all feature, bug, refactor, and release work.

## AI Agents Must Obey

Keep work small, reviewable, tested, and documented.

## Lifecycle

1. Intake: clarify goal and task type.
2. Spec: write or update feature spec for user-facing work.
3. Design: identify boundaries, risks, and tests.
4. Implement: make focused changes.
5. Verify: run tests and inspect artifacts.
6. Review: use `docs/ai/pr-review-checklist.md`.
7. Document: update docs and examples.
8. Release: follow release process.

## Change Size

Prefer small vertical slices. A slice should include CLI behavior, domain logic,
tests, and docs when applicable.

