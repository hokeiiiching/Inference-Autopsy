# Database Guidelines

## Purpose

Define persistence policy for a project that currently uses local files.

## Reference When

Use before adding SQLite, DuckDB, caches, indexes, or external storage.

## AI Agents Must Obey

Do not introduce a database unless file-based JSONL artifacts are insufficient
for a measured use case.

## Current Policy

- JSONL is the canonical trace format.
- Static HTML is the canonical report artifact.
- Local files are preferred over hosted services.

## Acceptable Local Storage

- JSONL for append-friendly traces.
- YAML or TOML for profiles and config.
- HTML for reports.
- Optional DuckDB or Parquet may be considered for large trace analysis after
  an RFC.

## Migration Requirements

Any new persistence layer needs:

- Clear user problem.
- Data ownership model.
- Export path back to open formats.
- Migration and rollback plan.
- Tests for schema evolution.

