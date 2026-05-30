# Component Architecture

## Purpose

Define how report UI should be decomposed.

## Reference When

Use when building static report templates or future local UI components.

## AI Agents Must Obey

Separate data preparation from rendering.

## Component Types

- Layout components: page, section, grid.
- Data components: metric table, percentile table, gate table.
- Chart components: latency distribution, token gaps, concurrency sweep.
- State components: empty, error, loading, warning.
- Metadata components: run configuration, methodology, trace details.

## Rules

- Components receive prepared view models.
- Components do not compute canonical metrics.
- Components are accessible by default.
- Components should have stable dimensions for charts and tables.
- Components should degrade gracefully for missing data.

## Expected View Model Shape

```python
ReportViewModel(
    summary=SummaryView(...),
    metrics=list[MetricRow],
    gates=list[GateResult],
    charts=list[ChartSpec],
    metadata=RunMetadata,
)
```

