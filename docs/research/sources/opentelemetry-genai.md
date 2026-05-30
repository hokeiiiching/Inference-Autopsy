# Source Notes: OpenTelemetry GenAI Conventions

## Why This Matters

OpenTelemetry GenAI conventions provide vocabulary for representing AI model calls, attributes, and telemetry. This is relevant to optional metrics/span export.

## What To Extract

- relevant span names
- GenAI attributes
- model/provider fields
- request/response token attributes
- error attributes
- latency metric conventions
- what is stable vs experimental

## Project Connection

Inference Autopsy V1 should not depend on OTel. But optional export can map trace data to OTel-shaped spans later.

## Implementation Rule

OTel export must consume canonical trace and metric data. It must not become a second telemetry system.

## My Angle

I can say the project is designed so black-box traces could later be exported into observability systems using GenAI semantic conventions.