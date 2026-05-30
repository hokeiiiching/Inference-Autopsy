# Source Notes: GuideLLM

## Why This Matters

GuideLLM is a close neighboring project because it benchmarks LLM serving behavior. It is useful for understanding common metrics, workload design, and serving-performance terminology.

## What To Extract

- Supported endpoint types
- Metrics collected
- Workload profile ideas
- Concurrency behavior
- Output report format
- Methodology choices
- CLI design patterns

## Project Connection

Inference Autopsy should learn from GuideLLM but differentiate through:
- JSONL request-level traces
- replay workflows
- diagnosis labels
- CI regression gates
- cache-sensitive analysis
- static autopsy report narrative

## Questions To Answer

- Does GuideLLM store per-request token timing traces?
- Does it support replay?
- Does it generate diagnosis text?
- Does it support CI gates?
- How does it define TTFT and ITL?