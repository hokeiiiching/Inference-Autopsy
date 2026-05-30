# Source Notes: PagedAttention

## Why This Matters

PagedAttention is important background for understanding why KV cache memory management matters in LLM serving. Even though Inference Autopsy is black-box, this helps me explain possible internal causes behind long-context latency and throughput behavior.

## What To Extract

- What problem PagedAttention solves
- Why KV cache memory is expensive
- How paging helps serving throughput
- Why long prompts and many concurrent requests stress memory
- How this relates to batching and scheduling

## Project Connection

Inference Autopsy must not claim to observe PagedAttention internals. But it can observe symptoms that may be consistent with serving pressure:
- TTFT rising with input length
- tail latency growing under concurrency
- throughput plateauing
- long-context workloads regressing

## My Angle

I can explain that my tool is black-box, but I understand the backend mechanisms that might cause observed symptoms.