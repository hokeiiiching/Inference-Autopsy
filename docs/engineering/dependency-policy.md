# Dependency Policy

## Purpose

Control dependency growth and reduce supply-chain risk.

## Reference When

Use before adding, replacing, or upgrading dependencies.

## AI Agents Must Obey

Add dependencies only when they remove meaningful complexity and fit the stack.

## Preferred Stack

- Typer for CLI.
- httpx for async HTTP.
- Pydantic for schemas.
- orjson for fast JSON when needed.
- Rich for terminal output.
- Polars or plain Python for metrics depending on complexity.
- Jinja2 for HTML reports.
- Plotly for static interactive charts when justified.
- pytest, ruff, and mypy for quality.

## Approval Criteria

New dependencies require:

- Clear problem statement.
- Alternatives considered.
- Maintenance and license check.
- Impact on install size and startup time.
- Test coverage for integration.

## DO NOT

- Add a framework for a single helper.
- Add hosted-service dependencies to the core CLI.
- Add browser-only libraries to core metrics.
- Add dependencies with incompatible licenses.

