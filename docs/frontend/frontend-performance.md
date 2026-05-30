# Frontend Performance

## Purpose

Keep static reports fast and usable.

## Reference When

Use when adding charts, embedded data, scripts, styles, or report sections.

## AI Agents Must Obey

Report performance must scale with realistic trace sizes.

## Rules

- Precompute canonical metrics before rendering.
- Embed only data needed for the report.
- Aggregate large token timing datasets for charts.
- Avoid heavy client-side processing on load.
- Keep CSS and JS minimal.
- Prefer static HTML with optional lightweight interactivity.

## Budgets

Initial budgets:

- Typical report opens in under 2 seconds on a laptop.
- HTML file remains reasonable for CI artifacts.
- Charts do not block the executive summary from rendering.

## Verification

For substantial report changes:

- Generate a sample report.
- Open it locally.
- Check first meaningful content, chart rendering, and table usability.

