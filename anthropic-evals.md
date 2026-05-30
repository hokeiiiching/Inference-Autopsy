# Source Notes: Anthropic Eval Writing

## Why This Matters

Anthropic eval writing is useful for understanding how to design good evaluation tasks. It is not core to Inference Autopsy V1, but it can inform workload profile design and future eval integration.

## What To Extract

- what makes an eval useful
- task clarity
- grading criteria
- avoiding ambiguous tests
- dataset construction principles
- failure analysis

## Project Connection

Workload profiles should be purposeful and not arbitrary. Even though they are performance workloads, they should have clear intent:
- short-chat
- rag-long
- code-completion
- agent-json
- prefix-cache
- saturation

## My Angle

I can explain that performance benchmarks also need workload design discipline, similar to eval design.