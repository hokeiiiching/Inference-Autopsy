# Error Handling

## Purpose

Define how failures are represented, reported, and tested.

## Reference When

Use when adding network calls, parsing, trace writing, metrics, CLI commands, or
report generation.

## AI Agents Must Obey

Failures must be explicit enough for users to decide whether a benchmark is
valid.

## Rules

- Distinguish user input errors, provider errors, timeouts, parsing errors, and
  internal bugs.
- Preserve original exception context where useful.
- Convert low-level errors into actionable CLI messages at the boundary.
- Do not suppress failed requests in metrics.
- Record failure status in traces when a request reaches execution.
- Avoid hidden retries unless the retry policy is explicit in trace metadata.

## Error Categories

- `ConfigurationError`: invalid flags, missing files, bad profiles.
- `ProviderError`: HTTP status failures, provider response errors.
- `StreamParseError`: malformed streaming chunks.
- `TraceWriteError`: output path or serialization failure.
- `MetricError`: invalid or insufficient trace data.
- `GateError`: invalid regression expression.

## CLI Error Output

Good errors include:

- What failed.
- Which input caused it.
- Whether trace data is trustworthy.
- One next action.

