# Logging and Monitoring

## Purpose

Define observability for a local CLI and CI regression tool.

## Reference When

Use when adding logs, progress output, report metadata, or CI diagnostics.

## AI Agents Must Obey

Observability must help users trust or reject a benchmark result.

## Logging Rules

- Default logs are concise and human-readable.
- Debug logs can include structured details, but never secrets.
- Use run IDs and request IDs for correlation.
- Log benchmark configuration at start.
- Log summary metrics at end.
- Redact API keys, authorization headers, and sensitive URLs.

## Report Metadata

Reports should include:

- Model and endpoint alias or hash.
- Run ID.
- Profile.
- Concurrency.
- Request count.
- Warmup policy.
- Timeout policy.
- Streaming mode.
- Token counting method.
- Retry policy.
- Trace schema version.

## CI Diagnostics

When gates fail, output:

- Failed gate expression.
- Baseline value.
- Candidate value.
- Change.
- Link or path to report artifact when available.

