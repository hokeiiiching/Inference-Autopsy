# Change Management

## Purpose

Define how changes to public contracts and architecture are controlled.

## Reference When

Use when changing CLI, trace schemas, profiles, reports, dependencies, or
release workflows.

## AI Agents Must Obey

Public contract changes must be intentional and documented.

## Change Types

- Patch: bug fix, docs, internal refactor.
- Minor: additive CLI flags, new report sections, new metrics.
- Major: breaking CLI, trace schema, or profile changes.

## Required Steps for Breaking Changes

- Write ADR or RFC.
- Provide migration notes.
- Add compatibility tests.
- Update README and docs.
- Consider deprecation period.

## Backward Compatibility

Default stance: preserve compatibility for trace files and documented CLI
examples.

