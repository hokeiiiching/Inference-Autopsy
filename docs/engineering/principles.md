# Engineering Principles

## Purpose

Define the engineering values that govern all implementation choices.

## Reference When

Use when making tradeoffs, reviewing code, or designing a feature.

## AI Agents Must Obey

Prefer maintainable, explicit, testable code over cleverness or novelty.

## Principles

- KISS: simple systems scale better than clever systems.
- YAGNI: do not build future flexibility without current evidence.
- DRY: avoid duplicated business logic, not harmless repeated syntax.
- SOLID: apply as a tool for clarity, not ceremony.
- Composition over inheritance.
- Functional core, imperative shell.
- Domain-driven names over technical filler names.
- Explicit dependencies over hidden global state.
- Observable failures over silent degradation.
- Reproducibility over convenience.

## Inference Autopsy Biases

- Trace data is the source of truth.
- Benchmarks must be reproducible and explainable.
- Local artifacts beat hosted complexity.
- Static reports should be useful without a backend.
- Metrics must be defined once and reused everywhere.

## Tradeoff Framework

When choosing between approaches, prefer the one that:

1. Preserves public contracts.
2. Is easiest to test deterministically.
3. Makes invalid benchmark states visible.
4. Uses fewer moving parts.
5. Aligns with existing patterns.

