# Architecture Fitness Checks

## Purpose

Define checks that guard architecture boundaries.

## Reference When

Use when designing CI, review scripts, or architecture reviews.

## AI Agents Must Obey

Architecture drift should be detected early.

## Fitness Rules

- `autopsy/core` must not import CLI, report rendering, or HTTP client modules.
- Report rendering must not import HTTP clients.
- Metrics must not import Typer, Rich console instances, or Jinja templates.
- Tests should cover trace schema fixtures.
- Public CLI examples should remain runnable.

## Possible Automation

- Import-linter rules.
- Custom pytest import boundary tests.
- Static checks for forbidden imports.
- CLI snapshot tests.
- Trace schema compatibility tests.

