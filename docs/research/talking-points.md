# Interview Talking Points

## Why did you build this?

Answer:
LLM inference latency is not one number. I wanted a tool that records token-level traces, decomposes latency, diagnoses likely bottlenecks, replays workloads, and fails CI on regressions.

## Why OpenAI-compatible endpoints only?

Answer:
Because many serving systems expose that API shape, including vLLM, Ollama, LiteLLM, and hosted providers. Supporting one protocol let me go deeper on measurement, streaming, replay, and regression gates instead of writing shallow adapters.

## What is the difference between TTFB and TTFT?
## What is ITL?
## Why do p95 and p99 matter?
## How does SSE streaming work?
## How do you handle malformed chunks?
## How does cache-aware benchmarking work if you cannot see backend cache state?
## What is PagedAttention?
## How is this different from GuideLLM or AIPerf?
## How is this different from eval frameworks?
## What would you improve with backend telemetry?
## What are the limits of black-box profiling?