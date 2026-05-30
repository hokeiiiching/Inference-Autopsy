# Migration Template

## Purpose

Guide schema, config, and persistence migrations.

## Reference When

Use before changing trace schema, profile format, or storage.

## AI Agents Must Obey

Migrations must preserve or explicitly manage compatibility.

## Template

```md
# Migration: <name>

## Current Contract

## New Contract

## Compatibility

Can old data be read?
Can new data be downgraded?

## Migration Path

## Rollback Path

## Tests

- Old fixture:
- New fixture:
- Mixed-version behavior:

## Docs Updates
```

