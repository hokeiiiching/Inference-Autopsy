# Code Ownership

## Purpose

Define ownership expectations as the project grows.

## Reference When

Use when assigning review responsibility or creating CODEOWNERS.

## AI Agents Must Obey

Route sensitive changes to the right owner when ownership exists.

## Suggested Ownership Areas

- CLI and developer experience.
- HTTP client and provider compatibility.
- Trace schema and storage.
- Metrics and gates.
- Diagnosis rules.
- Static reports and UX.
- Security and privacy.
- Release engineering.

## CODEOWNERS Direction

When maintainers are assigned, create `.github/CODEOWNERS` entries for:

```txt
/autopsy/core/traces*       @trace-owner
/autopsy/core/metrics*      @metrics-owner
/autopsy/reports/           @reports-owner
/docs/                      @docs-owner
```

