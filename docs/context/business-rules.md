# Business Rules

## Purpose

Define product rules that should remain consistent across code and docs.

## Reference When

Use when implementing CLI behavior, traces, reports, gates, and replay.

## AI Agents Must Obey

Business rules should be encoded once and tested.

## Rules

- Every benchmark run should have a run ID.
- Every request trace should have a request ID.
- Trace files should be append-friendly JSONL.
- Metrics must include units.
- Percentiles are first-class.
- Failed requests are part of run results.
- Reports must include methodology metadata.
- Gate failures should produce non-zero exit codes.
- Replay should preserve workload shape and prompts unless redaction or
  transformation is explicit.
- Endpoint identity should be redacted or hashed in shareable artifacts.

## Open Questions

- Exact default timeout values.
- Default stall threshold.
- Default warmup policy.
- Whether prompts are stored by default or behind an explicit flag.

