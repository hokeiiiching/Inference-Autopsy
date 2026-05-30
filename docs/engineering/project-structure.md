# Project Structure

## Purpose

Define the target repository organization as the project grows.

## Reference When

Use before creating new packages, modules, tests, or examples.

## AI Agents Must Obey

Place code by responsibility, not by convenience.

## Target Structure

```txt
autopsy/
  __init__.py
  cli/
    main.py
    commands/
  core/
    profiles.py
    traces.py
    metrics.py
    diagnosis.py
    gates.py
  clients/
    openai_compatible.py
    streaming.py
  runner/
    workload_runner.py
    concurrency.py
  reports/
    view_models.py
    html.py
    templates/
  replay/
    replay_runner.py
  storage/
    jsonl.py
tests/
  unit/
  integration/
  fixtures/
examples/
  profiles/
  traces/
docs/
```

## Placement Rules

- CLI argument parsing belongs under `autopsy/cli`.
- Pure domain logic belongs under `autopsy/core`.
- HTTP and streaming details belong under `autopsy/clients`.
- JSONL read/write belongs under `autopsy/storage`.
- Report templates stay under `autopsy/reports`.
- Tests mirror the package layout.

## Growth Rules

- Do not create a package until there are at least two coherent modules or a
  clear boundary.
- Do not create `shared` or `common` packages without an ownership comment.
- Keep examples runnable and small.

