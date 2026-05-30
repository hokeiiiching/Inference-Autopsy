# Feature Spec Template

## Purpose

Standardize product planning for new features.

## Reference When

Use before implementing any user-visible feature.

## AI Agents Must Obey

Do not implement a broad feature without a scoped spec.

## Template

```md
# Feature: <name>

## Problem

What user problem does this solve?

## Users

Who needs it?

## Goals

- <goal>

## Non-Goals

- <explicitly out of scope>

## User Flow

1. <step>
2. <step>

## CLI/API Contract

Commands, flags, trace fields, or report sections.

## Data and Privacy

What is stored, redacted, or displayed?

## Success Metrics

How will we know this worked?

## Risks

Architecture, compatibility, performance, security.

## Rollout

How can this be released or reverted safely?
```

