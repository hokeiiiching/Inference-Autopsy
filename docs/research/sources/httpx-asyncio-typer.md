# Source Notes: HTTPX, asyncio, and Typer

## Why This Matters

These are the core implementation tools for the project.

## HTTPX Notes

Extract:
- async client usage
- streaming responses
- timeout configuration
- connection pooling
- error handling
- event hooks if useful

Project use:
- OpenAI-compatible HTTP client
- streaming request handling
- provider error capture

## asyncio Notes

Extract:
- task creation
- cancellation
- semaphores
- timeouts
- queues
- gathering results
- exception handling in concurrent tasks

Project use:
- concurrent benchmark runner
- closed-loop concurrency
- request-rate scheduling
- graceful cancellation

## Typer Notes

Extract:
- command structure
- option parsing
- environment variable support
- help text
- exit codes
- testing CLI commands

Project use:
- `autopsy bench`
- `autopsy report`
- `autopsy diff`
- `autopsy replay`
- `autopsy summarize`

## Interview Angle

I can explain why async IO is appropriate: benchmark workers spend most of their time waiting on network and streaming responses, so asyncio lets one process manage many in-flight requests efficiently.