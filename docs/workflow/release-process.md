# Release Process

## Purpose

Define how releases are prepared and validated.

## Reference When

Use before publishing packages or tagging versions.

## AI Agents Must Obey

Do not release without tests, changelog, and compatibility review.

## Release Checklist

- All tests pass.
- Lint and type checks pass.
- README examples are current.
- Docs reflect public behavior.
- Trace schema compatibility is reviewed.
- CLI help output is checked.
- Sample report is generated.
- Changelog entry is written.
- Version is updated consistently.

## Rollback

Every release should have:

- Previous version available.
- Clear migration notes for trace schema changes.
- Known issue notes when relevant.

