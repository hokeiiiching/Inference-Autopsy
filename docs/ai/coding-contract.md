# AI Coding Contract

## Purpose

This contract defines the minimum quality bar for every AI-generated code
change.

## Reference When

Use before editing files, during implementation, and before final handoff.

## AI Agents Must Obey

- Keep changes scoped to the task.
- Respect user changes in the working tree.
- Prefer repo patterns over personal preference.
- Add or update tests for changed behavior.
- Make public contracts explicit.
- Leave the project easier to understand than you found it.

## Contract

### Architecture

- CLI commands delegate to application services.
- HTTP transport is isolated from metrics and reporting.
- Trace schemas are validated with typed models.
- Metrics logic is pure where possible.
- Report rendering consumes prepared view models, not raw transport objects.

### Code Quality

- Functions should have one reason to change.
- Keep domain names precise: request, trace, run, profile, metric, gate,
  diagnosis, report.
- Prefer composition over inheritance.
- Avoid global mutable state.
- Make async boundaries explicit.
- Handle cancellation, timeouts, and partial failures deliberately.

### Tests

Every behavior change should include at least one of:

- Unit test for pure logic.
- Contract test for schema or CLI output.
- Integration test with a fake OpenAI-compatible endpoint.
- Snapshot or semantic assertion for report output.

### Documentation

Update docs when changing:

- CLI commands or flags.
- Trace schema.
- Workload profile format.
- Metrics definitions.
- Diagnosis rules.
- Report sections.
- CI gate syntax.

