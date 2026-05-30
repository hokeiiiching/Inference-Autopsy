I will treat this project as more than “building a CLI tool.”

I will treat **Inference Autopsy** as a guided apprenticeship in LLM inference systems.

My real learning goals are:

1. I will understand how LLM streaming APIs behave.
2. I will understand latency decomposition: TTFB, TTFT, ITL, and total latency.
3. I will understand workload design and why weak benchmarks can be misleading.
4. I will understand trace schemas and reproducibility.
5. I will understand tail latency, percentiles, and regression testing.
6. I will learn to build credible developer tooling: CLI, tests, docs, reports, and CI.

The project will be successful if I can say:

> I built a black-box inference profiler, but more importantly, I learned how to reason about LLM serving behavior from request-level traces.

**What I Need To Learn**
| Area | What I Need To Understand |
| --- | --- |
| Python packaging | I need to understand `pyproject.toml`, editable installs, and CLI entrypoints. |
| Typer / CLI design | I need to understand commands, options, help text, and exit codes. |
| Async Python | I need to understand `asyncio`, tasks, semaphores, timeouts, and concurrency. |
| HTTP APIs | I need to understand request lifecycles, headers, status codes, and retries. |
| SSE streaming | I need to understand `data:` chunks, `[DONE]`, partial JSON, and stream parsing. |
| OpenAI-compatible APIs | I need to understand `/v1/chat/completions`, `stream=true`, messages, and usage. |
| Latency metrics | I need to understand TTFB, TTFT, ITL, request latency, and throughput. |
| Statistics | I need to understand p50, p90, p95, p99, ratios, outliers, and sample size. |
| JSONL tracing | I need to understand append-only traces, schema versioning, and replayability. |
| Workload design | I need to understand prompt length, output length, concurrency, and request rate. |
| Testing | I need to understand unit tests, fixtures, fake servers, and golden traces. |
| Reports | I need to understand Jinja templates, tables, charts, and readable diagnosis. |
| CI gates | I need to understand threshold parsing, exit code `1`, and GitHub Actions. |

**Learning Order**

I will not try to learn everything at once. I will learn just enough for the next milestone.

1. I will learn Python CLI basics.
2. I will learn JSONL schema design.
3. I will learn metrics from fake traces.
4. I will learn async HTTP and streaming.
5. I will learn concurrency control.
6. I will learn diagnosis rules.
7. I will learn reports.
8. I will learn diff and CI gates.
9. I will learn replay.

This order matters because fake traces let me learn metrics before I fight real endpoint weirdness.

**Week 1: Foundations And Fake Traces**

My goal is to learn the project shape without needing a real LLM endpoint.

I will study:

- How Python packages are structured.
- How Typer commands work.
- What JSONL is and why observability tools use it.
- Basic Pydantic models.
- How to write small pytest tests.

I will build:

- `autopsy --help`
- `autopsy generate-fake`
- `autopsy summarize`
- A trace schema with request timing fields.
- Tests that validate fake traces.

By the end, I should be able to explain:

> Each line in the trace represents one request, and every metric should be derivable from saved data.

**Week 2: Streaming Client**

My goal is to make one real OpenAI-compatible streaming request and measure it.

I will study:

- HTTP streaming.
- Server-Sent Events.
- OpenAI chat completion request/response shape.
- Why first byte and first token are not always the same.
- How to use `time.perf_counter()` for measurements.

I will build:

- `autopsy single`
- A tolerant SSE parser.
- Token timestamp capture.
- Error capture for bad status codes and malformed chunks.

The important concept I need to understand is:

```txt
TTFB = when the server first responds
TTFT = when the first generated token arrives
ITL = gaps between generated tokens
```

By the end, I should be able to explain why TTFT can be high even if decode speed is fine.

**Week 3: Workload Runner**

My goal is to move from one request to many realistic requests.

I will study:

- `asyncio.Semaphore`
- concurrency vs request rate
- timeouts
- progress bars
- why benchmark workloads need distributions

I will build:

- `autopsy bench`
- `--concurrency`
- `--max-requests`
- `--profile`
- built-in profiles like `short-chat` and `rag-long`

The key lesson I need to internalize is:

> A benchmark is only as useful as the workload it represents.

Short prompts test overhead. Long prompts test prefill. Long outputs test decode. Concurrent requests test queueing and saturation.

**Week 4: Metrics Engine**

My goal is to turn raw traces into trustworthy numbers.

I will study:

- percentiles
- mean vs median
- p95 vs p99
- error rate
- throughput
- outliers
- grouping metrics by concurrency/profile/model

I will build:

- `autopsy summarize`
- percentile tables
- worst 10 requests
- output tokens per second
- stall count from token gaps

I should know these formulas cold:

```txt
TTFT = first_token_time - request_start_time
Request latency = request_end_time - request_start_time
ITL = token_time[n] - token_time[n-1]
Output TPS = output_tokens / decode_duration
Tail ratio = p99_latency / p50_latency
Error rate = failed_requests / total_requests
```

This is where interview-quality understanding starts.

**Week 5: Diagnosis Engine**

My goal is to convert metrics into explanations.

I will study:

- rule-based classification
- thresholds
- evidence generation
- false positives
- black-box limitations

I will build:

- `autopsy diagnose`
- diagnosis labels
- severity
- evidence
- likely causes
- suggested next tests

Example reasoning I should be able to do:

```txt
High TTFT + normal ITL + long input prompts = likely prefill/context issue
Normal median + huge p99 = tail latency issue
High ITL + normal TTFT = decode slowdown
Many 429s = rate limiting
```

I will not use an LLM for diagnosis in v1. Rule-based diagnosis is more credible because it is testable.

**Week 6: HTML Report**

My goal is to create the artifact people can understand in 30 seconds.

I will study:

- Jinja2 templates
- simple charting
- visual hierarchy
- how to explain technical data to humans

I will build:

- `autopsy report`
- metric tables
- diagnosis section
- latency charts
- worst requests table
- error breakdown

The report should answer:

```txt
What happened?
How bad was it?
What evidence supports that?
What should I test next?
```

I will not overbuild the frontend. Static HTML is enough.

**Week 7: Diff And CI Gates**

My goal is to make the tool useful for regression testing.

I will study:

- baseline vs candidate comparisons
- relative thresholds like `+20%`
- absolute thresholds like `> 1000ms`
- process exit codes
- GitHub Actions basics

I will build:

- `autopsy diff baseline.jsonl candidate.jsonl`
- `--fail-if`
- exit code `1` on failed gates
- Markdown summary for CI

This is one of the strongest parts of the project because it turns benchmarking into engineering control.

**Week 8: Replay And Polish**

My goal is to make the project feel complete and reproducible.

I will study:

- preserving request shape
- replay limitations
- deterministic vs non-deterministic outputs
- benchmark methodology writing

I will build:

- `autopsy replay`
- exact prompt replay
- sample traces
- sample reports
- README polish
- benchmark methodology doc
- limitations doc

My final demo should show:

```txt
Run workload
Generate report
Identify bottleneck
Replay workload
Compare baseline vs candidate
Fail a regression gate
```

**My Daily Study Routine**

Each session, I will use this pattern:

1. I will spend 20 minutes reading docs or source code.
2. I will spend 60 to 90 minutes implementing one small piece.
3. I will spend 20 minutes writing tests.
4. I will spend 10 minutes writing notes explaining what I learned.

I will keep a `LEARNING.md` for myself. After each session, I will write:

```txt
What I built:
What confused me:
What I learned:
What I need to verify:
One thing I can now explain:
```

That file will become interview prep gold.

**What I Will Avoid**

I will avoid these until v1 is done:

- SaaS dashboard
- auth
- teams
- database-backed app
- complex frontend
- OpenTelemetry export
- provider-specific internals
- fancy charts before metrics are correct
- too many workload profiles
- LLM-generated diagnosis

My beginner trap will be scope creep. I will fight it.

**How I Will Know I Am Getting Stronger**

I am progressing well if I can explain:

- Why TTFT and ITL measure different bottlenecks.
- Why p95 matters more than average latency.
- Why long prompts hurt first-token latency.
- Why output length affects total latency.
- Why concurrency can make p99 explode.
- Why replay requires saved prompts and settings.
- Why black-box diagnosis is useful but not definitive.
- Why CI gates need stable baselines and careful thresholds.

**The Real Technical Bar**

By the end, I should be able to draw this from memory:

```txt
CLI command
  -> workload profile
  -> async request scheduler
  -> OpenAI-compatible client
  -> stream parser
  -> token timestamps
  -> JSONL trace
  -> metrics aggregation
  -> diagnosis rules
  -> report / diff / replay
```

If I can explain every arrow in that pipeline, I am no longer just someone who has used LLM APIs. I am learning to think like an AI systems engineer.