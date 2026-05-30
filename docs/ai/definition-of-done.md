# Definition of Done

## Purpose

Define when work is actually complete.

## Reference When

Use before final handoff, merge, release, or closing an issue.

## AI Agents Must Obey

Do not mark work done unless each relevant item is satisfied or explicitly
called out.

## Done Means

- The requested behavior works.
- The smallest reasonable verification has passed.
- Tests cover new or changed logic.
- Public contracts are documented.
- Error paths are handled.
- Security and privacy implications are considered.
- No unrelated user changes were overwritten.
- Generated artifacts are inspected when relevant.
- Remaining risk is named.

## Required Verification by Task Type

- CLI: command invocation, output shape, exit codes.
- Trace schema: validation tests and compatibility notes.
- Metrics: deterministic numeric tests including edge cases.
- Reports: generated sample report reviewed for content and layout.
- Diff gates: pass and fail cases covered.
- Replay: request preservation and redaction behavior covered.
- Docs: links, headings, and examples checked.

## Not Done

Work is not done when:

- It only works for the happy path.
- Tests were skipped without a reason.
- Documentation contradicts behavior.
- A new dependency was added without approval.
- Error output hides why a benchmark cannot be trusted.

