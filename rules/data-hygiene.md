# Data Hygiene Rules (always-on)

Paste this file's rules into your project's `CLAUDE.md` / `AGENTS.md`, or keep it loaded as a standing rule set. They apply to **every** operations analysis, regardless of which skill is active. Short forms live in `skills/using-ops-method/SKILL.md`.

1. **Report every dropped row.**
   Rows removed by filters, deduplication, date-range cuts or parse failures are part of the finding. State the count and the reason next to the result they affect. An analysis that silently discards 8% of its input is reporting on a different dataset than the one it claims.

2. **Denominators and date anchors are stated, never implied.**
   "94% on-time" is meaningless until the reader knows: on-time against which date, measured at order or line level, with which orders excluded. Every ratio ships with its definition footnote.

3. **Never average ratios — recompute them.**
   The mean of per-group percentages weights a 10-order group like a 10,000-order group. Always recompute from summed numerators and denominators. If someone hands you an "average of the monthly rates", treat it as unverified.

4. **Check units before comparing.**
   Occurrences vs minutes vs cost; orders vs lines vs units; calendar days vs business days. A ranking that mixes units is a coin flip with a chart.

5. **Normalize by exposure before comparing entities.**
   Lines, shifts, regions and periods with different volumes cannot be compared raw. Divide by machine-hours, orders or units first, and state the exposure base.

6. **Benchmark against doing nothing.**
   Forecasts are judged by value added over naive; initiatives by delta over baseline; tools by delta over the spreadsheet they replace. No benchmark, no claim.

7. **Distinguish week-over-week noise from trend.**
   Compare against a trailing baseline (e.g. 8-week average), not only the previous period. One unusual week manufactures a fake trend in a two-point comparison.

8. **Reconcile before presenting.**
   Recompute one headline number straight from raw rows and match it to the report. If automation produces the report, the reconciliation runs inside the pipeline. A mismatch is a stop-ship, not a footnote.
