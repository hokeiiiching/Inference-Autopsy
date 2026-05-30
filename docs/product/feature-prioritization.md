# Feature Prioritization

## Purpose

Define how features are ranked and scoped.

## Reference When

Use when choosing between feature ideas.

## AI Agents Must Obey

Prioritize features that improve reproducibility, diagnosis, or CI usefulness.

## Scoring

Score each from 1 to 5:

- User pain.
- Frequency.
- Fit with local CLI and static reports.
- Implementation simplicity.
- Testability.
- Reversibility.
- Maintenance cost, scored inversely.

## Priority Order

1. Correctness and trust.
2. Core benchmark and trace workflow.
3. Report clarity.
4. CI regression gates.
5. Replay and workload profiles.
6. Advanced analysis.

## Scope Control

- Define non-goals.
- Prefer one provider-compatible path before provider-specific features.
- Avoid adding UI workflows before CLI contracts are solid.

