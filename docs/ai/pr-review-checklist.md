# AI PR Review Checklist

## Purpose

Provide a mandatory self-review checklist before submitting or handing off work.

## Reference When

Use after implementation and before the final response, pull request, or merge.

## AI Agents Must Obey

Do not claim completion until the relevant checklist items are satisfied or
explicitly reported as not run.

## Checklist

### Correctness

- The change solves the requested problem.
- Existing behavior remains unchanged unless intentionally changed.
- Edge cases are handled: empty traces, failed requests, timeouts, partial
  streams, missing usage metadata, malformed provider responses.
- Error messages are actionable.

### Architecture

- Logic is placed in the owning layer.
- No circular dependencies were introduced.
- No shared utility bucket was created for unrelated functions.
- Public contracts are versioned or documented.

### Testing

- New logic has focused tests.
- Changed CLI behavior has command-level coverage.
- Metrics and percentile calculations use deterministic inputs.
- Snapshot updates are intentional and reviewed.

### UX and DX

- CLI output is readable in terminals.
- Static reports are understandable without a server.
- Failure output explains what happened and what to try next.
- Developer setup remains simple.

### Security and Privacy

- API keys are never logged, stored, or included in reports.
- Endpoint URLs are redacted or hashed when appropriate.
- Trace files do not unexpectedly persist sensitive prompt content without a
  documented option.

### Documentation

- Relevant docs were updated.
- Examples still work.
- Any new limitations are documented.

