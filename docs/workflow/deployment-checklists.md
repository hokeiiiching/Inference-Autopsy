# Deployment Checklists

## Purpose

Define checklists for publishing packages, reports, and CI workflows.

## Reference When

Use before release, CI integration, or artifact publication.

## AI Agents Must Obey

Validate artifacts before asking users or CI to trust them.

## Package Publish Checklist

- Version updated.
- Tests pass.
- Build succeeds.
- License included.
- README examples current.
- Changelog updated.

## CI Integration Checklist

- Secrets are configured.
- Baseline trace exists.
- Candidate trace output path is uploaded or retained.
- Gate expressions are documented.
- Failure output includes metric values.

## Report Artifact Checklist

- Opens without server.
- Includes methodology metadata.
- Redacts sensitive data.
- Shows gate results.
- Links to or embeds necessary assets.

