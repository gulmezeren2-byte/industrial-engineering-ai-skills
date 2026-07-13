---
name: using-ops-method
description: Entry point for any operations or supply-chain data analysis - routes the work through a fixed method (brief, data contract, honest metrics, driver decomposition, stress test, decision memo) and calls the specialized skills at the right step. Use when starting any ops analysis, KPI study, delivery/forecast/inventory question, operasyon analizi, veri analizi, or when unsure which ops skill applies. Differentiator - enforces sequence and validation, not just tool choice.
---

# Using the Ops Method

Operations analyses fail in predictable ways: answering a question nobody asked, computing on data nobody validated, reporting a metric nobody defined, and ending without a decision. The method below exists to make those failures impossible by construction. **Follow the sequence; do not skip steps because the task looks small.** Small tasks skip the brief; wrong answers follow.

## The sequence

| Step | Question it answers | Use | Artifact |
|------|--------------------|----- |----------|
| 1. Brief | What decision does this analysis feed? | `templates/analysis-brief.md` | Filled brief, confirmed by the requester |
| 2. Data contract | What data, what columns, what quality? | `templates/data-contract.md` | Contract + quality-gate results |
| 3. Honest metrics | What is the true number, under which definition? | route: delivery → `otif-analysis` · forecasts → `forecast-accuracy-review` · portfolio/stock → `abc-xyz-segmentation`, `safety-stock-review` | Metric ladder / scoreboard |
| 4. Drivers | Where does the problem concentrate? | `root-cause-pareto` | Ranked drivers + sub-analysis of #1 |
| 5. Stress test | Where does the standard answer break? | the stress sections inside the routed skill | Trust statement per segment |
| 6. Decision memo | What should the reader do? | `templates/decision-memo.md` | One-page memo with counter-metric |

For a recurring deliverable (weekly/monthly), wrap steps 3-6 with `weekly-ops-report` instead of a one-off memo.

## The constitution (always-on rules)

These override convenience in every step. The full versions with rationale live in `rules/data-hygiene.md`; the short forms:

1. **Report every dropped row.** Filtered, deduplicated or failed-parse rows are findings, not housekeeping.
2. **Denominators and date anchors are stated, never implied.** An unlabeled percentage is a rumor.
3. **Never average ratios.** Recompute from numerator and denominator sums; a mean of percentages is almost always wrong.
4. **Benchmark against doing nothing.** A forecast beats naive or it subtracts value; an initiative beats the baseline or it is theater.
5. **Reconcile one headline number to raw data before presenting.** Single pass, no intermediate tables; a mismatch stops the delivery.

## Routing notes

- Requests mentioning on-time, OTIF, late orders, teslimat → `otif-analysis`.
- Forecast accuracy, MAPE, demand planning value → `forecast-accuracy-review`.
- Which SKUs matter, segmentation, rationalization → `abc-xyz-segmentation`.
- Buffer, safety stock, service level → `safety-stock-review` (route through `abc-xyz-segmentation` first if classes are unknown).
- Downtime, defects, complaints, "biggest cause" → `root-cause-pareto`.
- "Summarize for management", recurring KPI reporting → `weekly-ops-report`.
- Mixed or unclear → start at step 1; the brief will disambiguate.

## Failure modes this method prevents

- **Skipped brief** → technically correct answer to the wrong question; the requester "clarifies" after you present.
- **Skipped contract** → silent schema drift; last month's numbers no longer reproduce.
- **Skipped stress test** → the recommendation works on average and fails exactly where it matters (volatile SKUs, peak weeks).
- **Skipped memo** → an analysis that everyone praises and nobody acts on.

## Output expectation

Every engagement ends with the decision memo (or the recurring report): finding in one line, evidence with numbers, what the evidence does *not* say, options with trade-offs, a recommendation, and a counter-metric with a re-check date.
