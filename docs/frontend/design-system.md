# Design System

## Purpose

Define reusable visual foundations for reports.

## Reference When

Use when creating report templates, components, charts, or examples.

## AI Agents Must Obey

Keep visual design restrained, consistent, and suited to technical analysis.

## Foundations

- Use an 8px spacing grid.
- Keep cards and panels at 8px radius or less.
- Use high-contrast text.
- Use color sparingly for status and grouping.
- Pair status color with text or icons.
- Avoid one-note palettes.

## Suggested Tokens

```css
--space-1: 4px;
--space-2: 8px;
--space-3: 12px;
--space-4: 16px;
--space-6: 24px;
--radius-sm: 4px;
--radius-md: 8px;
--color-bg: #ffffff;
--color-panel: #f7f8fa;
--color-text: #16181d;
--color-muted: #5f6877;
--color-border: #d9dee7;
--color-good: #137333;
--color-warn: #b06000;
--color-bad: #b3261e;
```

## Typography

- Use system fonts.
- Use tabular numbers for metric tables.
- Keep headings descriptive.
- Do not scale font size with viewport width.

## Dark Mode

Dark mode must preserve contrast, chart readability, and print/export quality.

