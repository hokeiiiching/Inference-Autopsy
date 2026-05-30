# Code Review Process

## Purpose

Define review expectations for humans and AI agents.

## Reference When

Use before opening, reviewing, or merging a PR.

## AI Agents Must Obey

Review for bugs, contracts, maintainability, and tests before style nits.

## Review Priorities

1. Correctness.
2. Public contract compatibility.
3. Security and privacy.
4. Architecture boundaries.
5. Test coverage.
6. Error handling.
7. Readability.
8. Style.

## Required Review Questions

- Can a user trust the benchmark output?
- Are failures visible and actionable?
- Are secrets and prompts handled safely?
- Does the change preserve trace reproducibility?
- Are docs and examples updated?

