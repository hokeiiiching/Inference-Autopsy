# Debugging Guide

## Purpose

Provide a repeatable approach for diagnosing issues in the tool.

## Reference When

Use when investigating failed tests, bad metrics, provider failures, or report
issues.

## AI Agents Must Obey

Debug from evidence, not guesses.

## Workflow

1. Reproduce with the smallest command or fixture.
2. Capture exact inputs and outputs.
3. Identify the layer: CLI, config, HTTP, stream parsing, trace, metrics,
   diagnosis, report, gate.
4. Add a failing test or fixture.
5. Fix the owning layer.
6. Verify the failure and a nearby edge case.

## Useful Artifacts

- Sanitized trace line.
- Run metadata.
- CLI command and flags.
- Provider status and response shape.
- Generated report section.
- Gate expression and values.

