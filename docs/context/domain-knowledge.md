# Domain Knowledge

## Purpose

Capture domain concepts needed to work effectively on LLM inference profiling.

## Reference When

Use when implementing metrics, reports, diagnosis, or docs examples.

## AI Agents Must Obey

Do not claim backend internals unless they are directly observed or clearly
marked as likely.

## Concepts

- TTFT: time from request start to first generated token.
- TTFB: time from request start to first response byte.
- ITL: time between generated output tokens.
- Tail latency: high-percentile latency such as p95 or p99.
- Output TPS: generated output tokens per second.
- Stream stall: token gap above a configured threshold.
- Prefill: backend processing before generation begins.
- Decode: backend token generation phase.
- Concurrency sweep: running the workload at multiple parallelism levels.

## Black-Box Constraint

Inference Autopsy observes external behavior. It can identify symptoms and
likely drivers, but cannot prove internal scheduler, GPU, KV-cache, or batching
behavior unless the backend exposes that data.

