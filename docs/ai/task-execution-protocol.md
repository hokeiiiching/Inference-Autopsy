# Task Execution Protocol

## Purpose

Define the step-by-step workflow for humans and AI agents implementing changes.

## Reference When

Use at the start of every feature, bug fix, refactor, migration, or report/UI
change.

## AI Agents Must Obey

Follow this protocol unless the user explicitly asks for a different workflow.

## Protocol

### 1. Intake

- Restate the goal internally.
- Identify whether the task is a feature, bug, refactor, migration, UI change,
  performance task, incident, or documentation task.
- Open the matching template from `docs/templates/`.

### 2. Inspect

- Read the relevant files before editing.
- Check current Git status.
- Identify existing patterns, tests, and docs.
- Find the smallest module boundary that owns the change.

### 3. Plan

For non-trivial work, define:

- Scope.
- Non-goals.
- Files likely to change.
- Risks.
- Verification commands.
- Documentation updates.

### 4. Implement

- Make incremental edits.
- Keep behavior and refactors separate when practical.
- Prefer pure functions for metrics, gates, and diagnosis rules.
- Keep side effects at the edges.

### 5. Verify

- Run the narrowest useful tests first.
- Expand verification when shared behavior changed.
- Inspect generated artifacts when output is visual or file-based.

### 6. Handoff

Report:

- What changed.
- How it was verified.
- Any tests not run.
- Any residual risk or follow-up.

