# Industrial Engineering AI Skills

> Your AI assistant is a brilliant analyst with no methodology. Left alone, it will happily compute a MAPE that silently drops a quarter of your data, rank a Pareto by the wrong unit, and report an on-time KPI your customers wouldn't recognize.
>
> These skills install the industrial engineer's discipline — the definitions, the pitfalls, and the validation habits — so the analysis your agent produces is one you can defend in a management meeting.

Agent skills are plain-markdown instruction folders (an [open standard](https://agentskills.io) supported by Claude Code, Codex, Cursor and 40+ agent tools). Each skill here is a **process primitive**: it doesn't add code, it adds judgment — what to compute, in which order, which traps to check, and how to validate before presenting.

## The skills

| Skill | What it disciplines | Fires when you say things like |
|-------|---------------------|-------------------------------|
| [`otif-analysis`](skills/otif-analysis/SKILL.md) | Delivery performance: the 5-rung metric ladder, driver decomposition, tail analysis | "OTIF", "on-time delivery", "why do customers complain at 95%?" |
| [`forecast-accuracy-review`](skills/forecast-accuracy-review/SKILL.md) | Forecast evaluation: WMAPE + bias + FVA vs naive, rolling-origin backtests | "forecast accuracy", "is our demand planning working?" |
| [`abc-xyz-segmentation`](skills/abc-xyz-segmentation/SKILL.md) | Portfolio segmentation: value × variability 9-box with a policy per cell | "ABC analysis", "which SKUs deserve attention?" |
| [`safety-stock-review`](skills/safety-stock-review/SKILL.md) | Buffer sizing: the formula **plus** an empirical stress test of what it delivers | "safety stock", "service level", "reorder point" |
| [`root-cause-pareto`](skills/root-cause-pareto/SKILL.md) | Pareto discipline: unit choice, category hygiene, exposure normalization, follow-up metric | "downtime pareto", "defect ranking", "80/20" |
| [`weekly-ops-report`](skills/weekly-ops-report/SKILL.md) | Reporting contract: what changed / where concentrated / what needs a decision | "weekly report", "summarize our KPIs for management" |

## Why these are different

Every skill encodes **the pitfalls, not just the steps** — the measurement traps I keep meeting in real operations: MAPE's silent zero-dropping, tolerance windows that buy free KPI points, cycle-service numbers quoted where contracts say fill rate, "Other" as the tallest Pareto bar. Each one ends with a validation loop (reconcile against raw data before presenting) and a defined output contract.

The methodology behind these skills is demonstrated, with numbers and charts, in the *measurement honesty* series: [otif-analytics](https://github.com/gulmezeren2-byte/otif-analytics) · [forecast-accuracy-lab](https://github.com/gulmezeren2-byte/forecast-accuracy-lab) · [abc-xyz-inventory](https://github.com/gulmezeren2-byte/abc-xyz-inventory) · [auto-report-pipeline](https://github.com/gulmezeren2-byte/auto-report-pipeline).

## Install

**Claude Code** — copy the skill folders into your project or user skills directory:

```bash
git clone https://github.com/gulmezeren2-byte/industrial-engineering-ai-skills
cp -r industrial-engineering-ai-skills/skills/* ~/.claude/skills/        # user-wide
# or: cp -r industrial-engineering-ai-skills/skills/* .claude/skills/    # this project only
```

**Other agents** (Codex, Cursor, Gemini CLI, ...) — same folders, per the [Agent Skills standard](https://agentskills.io); check your tool's skills directory.

**Any LLM, no agent** — open a SKILL.md and paste it as context before your question. They are written to work as standalone methodology briefs.

## Roadmap — one new skill per week

- [ ] `smed-changeover-analysis` — changeover time reduction, internal/external split discipline
- [ ] `line-balancing` — takt, precedence, balance-loss accounting
- [ ] `demand-pattern-classification` — smooth/erratic/intermittent/lumpy routing to the right method
- [ ] `mrp-sanity-check` — parameter audit: lot sizes, lead times, safety settings vs reality
- [ ] `kpi-tree-design` — from strategic goal to measurable driver tree without vanity metrics
- [ ] `inventory-health-audit` — excess/obsolete detection and cash-release sizing

Suggestions welcome — open an issue with the messiest analysis you keep repeating.

## 🇹🇷 Türkçe özet

Bu depo, endüstri mühendisliği metodolojisini yapay zeka ajanlarının kullanabileceği becerilere (skill) dönüştürür: OTIF denetimi, tahmin doğruluğu değerlendirmesi, ABC-XYZ segmentasyonu, emniyet stoğu kontrolü, Pareto disiplini ve haftalık rapor sözleşmesi. Her beceri yalnızca adımları değil, ölçüm tuzaklarını ve doğrulama alışkanlıklarını da kodlar. Claude Code ile klasörü kopyalayarak, diğer araçlarla Agent Skills standardı üzerinden, ya da herhangi bir LLM'e bağlam olarak yapıştırarak kullanabilirsiniz.

## About

Curated and written by **[Eren Gülmez](https://www.linkedin.com/in/erengulmez)** — industrial engineer, İstanbul. I design measurement systems and direct modern tooling to ship them; these skills are the judgment layer of that work, packaged for reuse.

Part of an open industrial-engineering toolkit → **[awesome-industrial-engineering](https://github.com/gulmezeren2-byte/awesome-industrial-engineering)**

## License

[MIT](LICENSE)
