# Source Notes: vLLM OpenAI-Compatible Server and Prefix Caching

## Why This Matters

vLLM is a practical local target for testing Inference Autopsy. Its OpenAI-compatible server lets the tool use one standard API shape. Prefix caching is relevant to cache-sensitive latency analysis.

## What To Extract

OpenAI-compatible server:
- endpoint path
- request shape
- streaming response shape
- authentication behavior if any
- model naming
- local startup command

Prefix caching:
- how vLLM describes prefix caching
- what workloads benefit
- limitations
- configuration flags
- what behavior is visible from outside

## Project Connection

Inference Autopsy should support vLLM as a primary demo endpoint.

Cache analysis should compare:
- cold prompts
- warm prompts
- repeated-prefix prompts
- repeated-exact prompts

But it should say "cache-sensitive behavior", not definitive cache hits.

## Demo Use

Potential demo:
- run rag-long profile
- run prefix-cache profile
- compare cold vs repeated-prefix TTFT