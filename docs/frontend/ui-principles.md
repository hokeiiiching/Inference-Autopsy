# UI Principles

## Purpose

Define the experience bar for static HTML reports and any future local UI.

## Reference When

Use when designing or changing reports, tables, charts, interactions, or visual
states.

## AI Agents Must Obey

Reports must make inference performance understandable quickly and accurately.

## Principles

- Clarity beats decoration.
- Every chart must answer a question.
- Important regressions must be visible without scrolling deeply.
- Raw numbers and explanations should support each other.
- Users must be able to share reports without running a server.
- Visual hierarchy should guide attention to reliability, latency, and gates.

## Report Sections

Preferred order:

1. Executive summary.
2. Diagnosis.
3. Gate result.
4. Metric comparison.
5. Percentiles.
6. Concurrency behavior.
7. Token timing and stalls.
8. Worst requests.
9. Error breakdown.
10. Metadata and methodology.

## UI Anti-Patterns

- Decorative charts without decisions attached.
- Tables without units.
- Hidden methodology.
- Color-only status indicators.
- Dense walls of numbers without grouping.

