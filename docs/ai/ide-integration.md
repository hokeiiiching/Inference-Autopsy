# AI IDE Integration

## Purpose

Explain how to connect this documentation system to AI coding tools.

## Reference When

Use when configuring Cursor, Claude, Copilot, Codex, or other AI-assisted IDEs.

## AI Agents Must Obey

Keep IDE-specific instructions short and point them back to these docs instead
of duplicating policy in many places.

## Recommended Shared Instruction

```txt
Before editing this repository, read docs/README.md and the relevant files under
docs/ai, docs/engineering, docs/context, and docs/templates. Treat the docs as
project law. Prefer small, tested, architecture-preserving changes.
```

## Cursor Rules

Create `.cursor/rules/project.mdc` with:

```txt
Always follow docs/ai/agent-rules.md and docs/ai/task-execution-protocol.md.
For task-specific work, use the matching template in docs/templates/.
Do not change trace schema, CLI flags, or metric definitions without docs.
```

## Claude Memory

Store:

```txt
Inference Autopsy is a local-first Python CLI for profiling OpenAI-compatible
LLM inference endpoints. The docs/ directory is the source of truth. Keep
changes scoped, tested, and trace-schema aware.
```

## Copilot Instructions

Create `.github/copilot-instructions.md` with:

```txt
Follow docs/engineering/* for code style and architecture. Follow
docs/frontend/* for static HTML reports. Avoid unapproved dependencies and
unversioned public contract changes.
```

## Codex Usage

For substantial tasks, start with:

```txt
Use docs/ai/task-execution-protocol.md and the relevant docs/templates file.
Implement the change, verify it, and update docs if public behavior changes.
```

