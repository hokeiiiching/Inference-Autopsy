# Naming Conventions

## Purpose

Create predictable names across code, docs, CLI, traces, and reports.

## Reference When

Use when adding modules, commands, functions, metrics, schemas, or UI labels.

## AI Agents Must Obey

Use domain language consistently and avoid vague names.

## Domain Terms

- `run`: one benchmark execution.
- `request`: one model API request.
- `trace`: recorded request-level and token-level data.
- `profile`: workload definition.
- `metric`: computed measurement.
- `diagnosis`: explanation backed by metrics.
- `gate`: pass/fail rule for regression checks.
- `report`: static human-readable artifact.
- `replay`: execution of a captured workload against another endpoint.

## File and Module Names

- Use lowercase snake_case for Python modules.
- Name modules by responsibility: `metrics`, `traces`, `reports`, `gates`.
- Avoid vague names: `helpers`, `misc`, `common`, `stuff`.

## CLI Names

- Commands use short verbs: `bench`, `report`, `diff`, `replay`.
- Flags use kebab case: `--base-url`, `--max-requests`.
- Metric names in gates use snake case: `ttft_p95`, `error_rate`.

## Schema Names

- JSON fields use snake case.
- Time values include units: `ttft_ms`, `request_latency_ms`.
- Percentile names include percentile: `itl_p95_ms`.
- Schema versions are strings: `"0.1"`.

