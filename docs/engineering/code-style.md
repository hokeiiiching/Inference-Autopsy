# Code Style

## Purpose

Define code readability and formatting expectations.

## Reference When

Use during all Python, test, template, and script changes.

## AI Agents Must Obey

Follow automated formatters and keep code explicit.

## Python Style

- Use `ruff format` and `ruff check`.
- Use type hints on public functions and core domain logic.
- Prefer dataclasses or Pydantic models for structured data.
- Keep functions small and named by domain behavior.
- Use early returns to reduce nesting.
- Avoid boolean flags that make one function do unrelated jobs.
- Keep comments for why, not what.

## Complexity Limits

- Prefer files under 400 lines.
- Prefer functions under 50 lines.
- Prefer classes with clear state or interface responsibility.
- Split modules when tests become hard to read.

## Async Style

- Use async where concurrency matters: HTTP requests, streaming, workload runs.
- Keep CPU-bound metrics synchronous unless profiling shows a need.
- Make cancellation and timeout behavior explicit.

## Terminal Output

- Use Rich for readable tables and summaries.
- Keep output stable enough for documentation examples.
- Do not print secrets or full sensitive prompts by default.

