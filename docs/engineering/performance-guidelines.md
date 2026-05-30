# Performance Guidelines

## Purpose

Define performance expectations for a profiling tool.

## Reference When

Use when touching workload execution, streaming parsing, JSONL IO, metrics, or
report generation.

## AI Agents Must Obey

The tool must measure endpoint performance without adding avoidable measurement
noise.

## Rules

- Use monotonic clocks for timings.
- Avoid blocking work inside streaming loops.
- Write traces append-first and flush deliberately.
- Keep per-token overhead low.
- Separate measurement from presentation.
- Benchmark internal hot paths before optimizing them.
- Make concurrency limits explicit.

## Measurement Integrity

- Record client-side timing source.
- Record timeout and retry policy.
- Preserve partial request data when safe.
- Avoid hidden background work that changes request timing.

## Report Performance

- Static HTML reports should open quickly for typical trace sizes.
- Large traces should be summarized before rendering.
- Charts should use aggregated data when raw points are excessive.

## Scalability Targets

Initial design should handle:

- Hundreds to low thousands of requests per run.
- Token timing arrays for streaming responses.
- CI-friendly diff checks on small fixture traces.

