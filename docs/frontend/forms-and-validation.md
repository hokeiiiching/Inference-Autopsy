# Forms and Validation

## Purpose

Define form and validation behavior for profiles, configs, and any future local
UI.

## Reference When

Use when adding profile validation, config files, UI forms, or CLI input
validation.

## AI Agents Must Obey

Validate early and explain fixes clearly.

## Rules

- Validate profile files before starting a benchmark.
- Show all validation errors when practical.
- Include field paths in validation messages.
- Preserve units in labels and errors.
- Keep defaults visible.
- Reject ambiguous configuration.

## Profile Validation Examples

- Concurrency values must be positive integers.
- `max_tokens` must be positive.
- Distribution weights must sum to a valid non-zero total.
- Prompt templates must include required variables.

