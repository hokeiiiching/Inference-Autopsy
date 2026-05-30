# Testing Strategy

## Purpose

Define how confidence is built across CLI, metrics, streaming, replay, and
reports.

## Reference When

Use before adding or changing behavior.

## AI Agents Must Obey

Prefer deterministic tests and fake endpoints over live provider tests.

## Test Layers

- Unit tests for metrics, gates, diagnosis, parsing helpers, and schema models.
- Contract tests for trace JSONL schema and CLI output.
- Integration tests with a local fake OpenAI-compatible server.
- Report tests that assert key content and generated assets exist.
- Regression tests using fixture traces.

## Required Edge Cases

- Empty trace file.
- Single-token response.
- Non-streaming response.
- Streaming chunks with missing fields.
- Timeout before first byte.
- Timeout after partial stream.
- Provider 429 and 500 responses.
- Missing usage metadata.
- Outlier request latency.
- Zero successful requests.

## Test Data Rules

- Keep fixture traces small.
- Make percentile expectations explicit.
- Do not depend on wall-clock timing except in isolated integration tests.
- Avoid live API calls in default test suite.

## Commands

Expected local verification:

```bash
pytest
ruff check .
ruff format --check .
mypy autopsy
```

