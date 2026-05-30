# ADR Guidelines

## Purpose

Define how architecture decision records are written and maintained.

## Reference When

Use before creating or updating ADRs.

## AI Agents Must Obey

Do not rewrite decision history; supersede it.

## Rules

- ADRs are immutable after acceptance except for typo fixes and supersession
  links.
- Use sequential numbering.
- Keep each ADR focused on one decision.
- Include alternatives considered.
- Include consequences and follow-up.
- Mark superseded ADRs clearly.

## Storage

Future ADRs should live under:

```txt
docs/adr/
```

Use `docs/templates/adr-template.md`.

