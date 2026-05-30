# Roadmap

## Purpose

Track product direction without overcommitting to dates.

## Reference When

Use when choosing what to build next.

## AI Agents Must Obey

Do not treat roadmap ideas as approved implementation scope.

## Near-Term

- Establish Python package skeleton.
- Implement `bench` for OpenAI-compatible chat completions.
- Record request-level JSONL traces.
- Compute TTFT, TTFB, ITL, request latency, output TPS, stalls, and errors.
- Generate static HTML report.
- Implement `diff` with CI gates.

## Mid-Term

- Add replay from captured traces.
- Add built-in workload profiles.
- Add diagnosis rules backed by metrics.
- Improve report charts and methodology sections.
- Add sanitized artifact mode.

## Later

- Large-trace aggregation.
- Optional DuckDB analysis workflow.
- Provider compatibility test matrix.
- Plugin-style custom profiles or diagnosis rules.

