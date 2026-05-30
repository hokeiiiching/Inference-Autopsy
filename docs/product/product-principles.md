# Product Principles

## Purpose

Define the product shape and decision philosophy.

## Reference When

Use when planning features, prioritizing scope, or evaluating tradeoffs.

## AI Agents Must Obey

Protect the core product: local CLI plus reproducible traces and static reports.

## Principles

- The user wants to know what slowed down and why.
- Reproducibility is a feature.
- Local-first beats hosted complexity.
- Reports should be shareable artifacts.
- CI gates should be easy to adopt.
- Diagnosis must be backed by metrics.
- Methodology must be visible.

## MVP Philosophy

Ship thin vertical slices:

1. Record trace.
2. Compute metrics.
3. Explain result.
4. Generate report.
5. Compare baseline and candidate.
6. Fail CI when thresholds are crossed.

## Non-Goals by Default

- Hosted SaaS dashboard.
- Provider-specific backend internals.
- Distributed tracing integration.
- Full observability platform.
- Perfect token counting for every provider.

