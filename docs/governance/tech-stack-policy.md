# Tech Stack Policy

## Purpose

Define the approved technology direction.

## Reference When

Use before adding frameworks, dependencies, or infrastructure.

## AI Agents Must Obey

Stay within the approved stack unless an RFC justifies change.

## Approved Direction

- Python CLI.
- Typer command interface.
- Async HTTP with httpx.
- Typed schemas with Pydantic.
- JSONL trace storage.
- Static HTML reports with Jinja2.
- Optional Plotly charts when justified.
- pytest, ruff, mypy for quality.

## Disallowed by Default

- Hosted SaaS backend.
- Required database.
- Required browser app for core workflow.
- Provider-specific SDK as the core transport.
- Heavy frontend framework for static reports.

