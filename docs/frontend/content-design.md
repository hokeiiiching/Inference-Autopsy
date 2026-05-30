# Content Design

## Purpose

Define writing standards for CLI output, reports, errors, and docs examples.

## Reference When

Use when writing user-facing strings.

## AI Agents Must Obey

Use precise, plain language backed by metrics.

## Voice

- Direct.
- Technical but readable.
- Specific about units and thresholds.
- Honest about uncertainty.
- Memorable only when it does not reduce clarity.

## Report Copy Rules

- Lead with the conclusion.
- Tie diagnosis to evidence.
- Include likely drivers and next tests.
- Avoid claiming backend internals that were not observed.
- Distinguish symptoms from causes.

## Error Copy Template

```txt
Could not parse streaming response from endpoint_alias.
Reason: missing delta content field in chunk 42.
Benchmark status: request marked failed; run metrics include this failure.
Next step: rerun with --debug-stream to inspect sanitized chunks.
```

