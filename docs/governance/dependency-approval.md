# Dependency Approval

## Purpose

Define how dependencies are approved.

## Reference When

Use before adding or replacing packages.

## AI Agents Must Obey

Do not add dependencies without documenting why.

## Approval Template

```md
# Dependency Request: <package>

## Problem

What problem does it solve?

## Alternatives

Standard library or existing dependencies considered.

## Fit

How it fits the architecture.

## Risk

License, maintenance, security, install size, performance.

## Tests

How integration will be verified.
```

## Fast-Path

Dev-only dependencies for testing or linting can be approved with a shorter note
if they are widely used, maintained, and low risk.

