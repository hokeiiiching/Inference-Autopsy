# Inference Autopsy

**Who killed my TTFT?**

Inference Autopsy is an open-source black-box profiler, workload replayer, and
regression tester for OpenAI-compatible LLM inference endpoints.

It records request-level and token-level traces, measures TTFT, ITL, tail
latency, throughput, streaming stalls, and error rates, then turns those
measurements into reproducible reports, baseline diffs, and CI regression
gates.

> Your LLM endpoint got slow. We found the body in the token stream.

The goal is a polished local CLI plus static HTML reports, not a hosted SaaS
dashboard.

## Why This Exists

LLM inference latency is not just one number.

A request can be slow because of first-token delay, slow decode, long prompts,
tail latency, rate limits, stream stalls, output bloat, or concurrency collapse.
Aggregate benchmark numbers can tell you that something changed. Inference
Autopsy is designed to help answer:

1. How fast is this endpoint?
2. Why is it slow?
3. Can I reproduce the workload?
4. Did my model or deployment regress?
5. Can I explain the failure in one memorable line?

The wedge is:

```txt
benchmark -> trace -> diagnose -> report -> replay -> regression gate
```

Existing tools such as
[NVIDIA GenAI-Perf](https://docs.nvidia.com/deeplearning/triton-inference-server/user-guide/docs/perf_analyzer/genai-perf/README.html),
[GuideLLM](https://github.com/vllm-project/guidellm), and
[LLMPerf](https://github.com/ray-project/llmperf) measure important LLM serving
metrics. Inference Autopsy focuses on trace-level reproducibility, diagnosis,
human-readable reports, and CI gates for OpenAI-compatible endpoints.

## What It Measures

Inference Autopsy focuses on externally visible inference behavior:

| Metric | Meaning |
| --- | --- |
| TTFT | Time from request start to first generated token |
| TTFB | Time from request start to first response byte |
| ITL | Inter-token latency between generated output tokens |
| Request latency | Time from request start to final token or response end |
| Output TPS | Generated output tokens per second |
| Stream stalls | Token gaps above a configurable threshold |
| Error rate | Failed requests divided by total requests |
| Timeout rate | Timed-out requests divided by total requests |
| Tail ratio | p99 latency divided by p50 latency |

Percentiles are first-class:

```txt
p50, p90, p95, p99
```

Because median latency is where demos look good. Tail latency is where systems
start telling the truth.

## Target CLI

### Run a benchmark

```bash
autopsy bench \
  --base-url http://localhost:8000/v1 \
  --model meta-llama/Llama-3.1-8B-Instruct \
  --profile rag-long \
  --concurrency 1,4,8,16 \
  --max-requests 200 \
  --output runs/rag_long_v1.jsonl
```

### Generate a report

```bash
autopsy report \
  runs/rag_long_v1.jsonl \
  --html reports/rag_long_v1.html
```

### Compare two runs

```bash
autopsy diff \
  runs/baseline.jsonl \
  runs/candidate.jsonl
```

### Fail CI on regression

```bash
autopsy diff \
  runs/baseline.jsonl \
  runs/candidate.jsonl \
  --fail-if "ttft_p95 > +20%" \
  --fail-if "itl_p95 > +15%" \
  --fail-if "error_rate > 1%"
```

### Replay a captured workload

```bash
autopsy replay \
  runs/baseline.jsonl \
  --base-url http://localhost:11434/v1 \
  --model qwen3:8b \
  --output runs/replay_ollama.jsonl
```

## Example Output

```txt
Regression detected.

Metric                 Baseline     Candidate    Change
TTFT p95              840ms        1210ms       +44.0%
ITL p95               39ms         47ms         +20.5%
Request p99           6.2s         9.8s         +58.1%
Error rate            0.1%         1.8%         +1.7pp
Output TPS            41.2         35.7         -13.3%

Failed gates:
- ttft_p95 > +20%
- error_rate > 1%

Cause of death:
Tail Hydra + Rate Limit Police
```

## Failure Zoo

Each bad run gets a memorable diagnosis backed by hard metrics.

| Cause of death | Serious meaning |
| --- | --- |
| TTFT Whale | First-token latency dominates request time |
| Decode Goblin | Inter-token latency is high |
| Tail Hydra | p99 latency explodes while median looks fine |
| Context Blobfish | Long prompts crush prefill performance |
| Stream Stutter Gremlin | Streaming has large token gaps |
| Rate Limit Police | 429s, throttling, or retries dominate |
| Output Hydra | Output length inflated unexpectedly |
| JSON Skeleton | Structured output mode causes failures or latency |
| Retry Zombie | Hidden retries inflate latency |
| Concurrency Kraken | Endpoint collapses under parallel load |

Example diagnosis:

```txt
Cause of death: Context Blobfish
Severity: High

Evidence:
- TTFT p95 rises from 620ms at 512-token prompts to 3120ms at 8192-token prompts.
- ITL stays mostly flat.
- Request latency increase is concentrated before the first token.

Likely driver:
Long prompt prefill dominates latency.

Suggested next tests:
- Bucket prompts by input length.
- Compare with prefix caching if the backend supports it.
- Test prompt compression.
```

## Workload Profiles

Inference Autopsy uses workload profiles instead of one toy prompt. Different
workloads expose different bottlenecks.

Planned built-in profiles:

| Profile | Purpose |
| --- | --- |
| short-chat | Basic latency and endpoint overhead |
| rag-long | Long-context RAG-style TTFT sensitivity |
| code-completion | Long decode and output throughput |
| agent-json | JSON reliability and structured-output latency |
| long-context | Context-window and prefill stress |
| mixed-realistic | Blended production-like workload |

Example profile shape:

```yaml
name: rag-long
description: Long-context RAG-style prompts with moderate outputs.

input_tokens:
  distribution: bucket
  values: [2000, 4000, 8000]
  weights: [0.4, 0.4, 0.2]

output_tokens:
  distribution: normal
  mean: 256
  std: 64
  min: 64
  max: 512

sampling:
  temperature: 0.2
  max_tokens: 512

messages:
  system: "You answer questions using the provided context."
  user_template: |
    Context:
    {{ generated_context }}

    Question:
    {{ generated_question }}
```

## Trace Format

Each request is saved as one JSONL line.

```json
{
  "schema_version": "0.1",
  "run_id": "run_2026_05_23_001",
  "request_id": "req_00042",
  "profile": "rag-long",
  "model": "llama-3.1-8b",
  "base_url_hash": "endpoint_a",
  "input_tokens_estimated": 4096,
  "output_tokens": 261,
  "status": "success",
  "timings_ms": {
    "request_start": 0,
    "first_byte": 817,
    "first_token": 942,
    "request_end": 7610
  },
  "token_times_ms": [942, 971, 1001, 1033, 1208],
  "metrics": {
    "ttft_ms": 942,
    "request_latency_ms": 7610,
    "itl_mean_ms": 28.4,
    "itl_p95_ms": 71.2,
    "output_tps": 38.6,
    "stall_count": 2
  },
  "error": null
}
```

JSONL is append-friendly, easy to inspect, easy to upload as a CI artifact, and
simple to process with Python, DuckDB, Polars, or shell tools.

## HTML Reports

The static report is the main demo artifact.

Planned sections:

- Executive summary
- Cause of death
- Metric table
- Latency percentiles
- Concurrency sweep
- TTFT by input length
- ITL distribution
- Token-gap histogram
- Worst 10 requests
- Error breakdown
- Baseline comparison
- Recommendations
- Raw trace metadata

The report is designed to be shareable without running a server.

## CI Usage

Planned GitHub Actions workflow:

```yaml
name: LLM Inference Regression Test

on:
  pull_request:

jobs:
  inference-autopsy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Install Inference Autopsy
        run: pip install inference-autopsy

      - name: Run benchmark
        run: |
          autopsy bench \
            --base-url ${{ secrets.LLM_BASE_URL }} \
            --api-key ${{ secrets.LLM_API_KEY }} \
            --model ${{ vars.LLM_MODEL }} \
            --profile short-chat \
            --max-requests 50 \
            --output candidate.jsonl

      - name: Check regression
        run: |
          autopsy diff baseline.jsonl candidate.jsonl \
            --fail-if "ttft_p95 > +20%" \
            --fail-if "itl_p95 > +15%" \
            --fail-if "error_rate > 1%"
```

## Compatibility Goal

Inference Autopsy targets OpenAI-compatible chat completion endpoints,
especially:

- vLLM OpenAI-compatible server
- Ollama OpenAI-compatible API
- LiteLLM proxy
- hosted OpenAI-compatible inference providers
- internal company deployments using OpenAI-style APIs


Focus;
- `/v1/chat/completions`
- `stream=true`
- `stream=false`
- request-level JSONL traces
- exact replay from saved prompts

## Architecture

```txt
Typer CLI
  -> async workload runner
  -> OpenAI-compatible HTTP client
  -> streaming parser
  -> JSONL trace recorder
  -> metrics engine
  -> diagnosis engine
  -> report generator
  -> diff and CI gate engine
  -> replay engine
```

Planned Python stack:

- Typer for the CLI
- httpx for async HTTP
- Pydantic for schemas
- orjson for fast JSON
- Rich for terminal output
- Polars or plain Python for metrics
- Jinja2 for HTML reports
- Plotly for static interactive charts
- pytest for tests


## Limitations

Inference Autopsy is a black-box endpoint profiler. It identifies externally
visible symptoms and likely bottlenecks, not definitive backend internals.

It does not directly observe GPU kernel time, scheduler state, KV-cache pressure,
batching internals, or prefill/decode implementation details unless a backend
exposes those signals.

Other known limitations:

- Token counting may be approximate when providers do not return usage metadata.
- OpenAI-compatible streaming formats vary across servers.
- Hosted endpoint measurements include network and provider-side variance.
- Replay preserves workload shape and prompts, but not perfect model determinism.
- Static reports are not a replacement for production observability.

## Benchmark Methodology

Reports should include:

- endpoint and model
- hardware or provider
- concurrency
- request count
- warmup policy
- timeout policy
- streaming mode
- token counting method
- retry policy
- prompt generation method
- percentile calculation method

No trace, no reproducibility.

## Development

```bash
python -m venv .venv
source .venv/bin/activate
pip install -e ".[dev]"
pytest
ruff check .
mypy autopsy
```

## License

MIT License. See [LICENSE](LICENSE).
