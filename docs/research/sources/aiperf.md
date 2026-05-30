# Source Notes: AIPerf

## Why This Matters

AIPerf is relevant because Inference Autopsy is also concerned with LLM inference performance measurement. I should understand what metrics and benchmark methodology it emphasizes so my project can position itself clearly.

## What To Extract

- What workloads it supports
- What metrics it reports
- How it treats TTFT, ITL, throughput, and latency
- Whether it supports concurrency or request-rate sweeps
- How it presents results
- What it does not solve for replay, diagnosis, or CI gates

## Project Connection

Inference Autopsy should not merely duplicate benchmark numbers. It should focus on:
- trace-level reproducibility
- diagnosis
- static reports
- replay
- regression gates
- cache/saturation symptoms

## My Angle

I can say I studied existing inference benchmark tools and designed Inference Autopsy around trace reproducibility and regression workflows rather than only one-off performance numbers.