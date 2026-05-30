# AI Validation

## Purpose

Define the final validation AI agents must perform before handoff.

## Reference When

Use at the end of every AI-assisted task.

## AI Agents Must Obey

Complete this validation and report any unchecked item.

## Validation Checklist

- I read the relevant docs.
- I inspected existing code before editing.
- I kept the change scoped.
- I preserved user changes.
- I followed architecture boundaries.
- I added or updated tests when behavior changed.
- I ran appropriate verification or explained why not.
- I updated docs when public behavior changed.
- I checked for secrets, sensitive prompts, and unsafe logs.
- I summarized residual risk.

## Task-Specific Additions

- Metrics: deterministic numeric tests.
- Trace schema: old and new fixture behavior.
- Reports: generated artifact inspected.
- CLI: command output and exit code checked.
- Dependencies: approval rationale documented.

