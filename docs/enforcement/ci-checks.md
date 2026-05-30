# CI Checks

## Purpose

Define expected automated checks.

## Reference When

Use when creating or modifying CI workflows.

## AI Agents Must Obey

CI should protect correctness, contracts, and user trust.

## Required Checks

- Install package.
- Run unit and integration tests.
- Run lint and formatting checks.
- Run type checks.
- Validate fixture traces.
- Generate a sample report.
- Evaluate sample gate pass and fail cases.

## Future Checks

- Markdown link check.
- Dependency vulnerability scan.
- Package build check.
- CLI help snapshot.
- Provider compatibility matrix.

## Gate Failure Policy

Gate failures in user workflows should exit non-zero and print exact metric
values. CI failures in this repository should identify the failing layer.

