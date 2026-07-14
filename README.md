# Industrial Engineering AI Skills

![Skills](https://img.shields.io/badge/skills-7-blue) ![Agents](https://img.shields.io/badge/agents-4-blue) ![Templates](https://img.shields.io/badge/templates-3-blue) ![Rules](https://img.shields.io/badge/rules-1-blue) ![License](https://img.shields.io/badge/license-MIT-green)

Works with **Claude Code · Codex · Cursor · Gemini CLI** and any [Agent Skills](https://agentskills.io) client.

🇹🇷 Türkçesi: [README.tr.md](README.tr.md)

> Your AI assistant is a brilliant analyst with no methodology. Left alone, it will happily compute a MAPE that silently drops a quarter of your data, rank a Pareto by the wrong unit, and report an on-time KPI your customers wouldn't recognize.
>
> This pack installs the industrial engineer's discipline — a fixed method, the definitions, the pitfalls, and the validation habits — so the analysis your agent produces is one you can defend in a management meeting.

Not a grab-bag of prompts: **one operations-analysis method, packaged as composable parts.** Skills carry the how, agents carry the roles, rules carry the always-on constraints, templates carry the artifacts. Built on the [Agent Skills open standard](https://agentskills.io) (Claude Code, Codex, Cursor and 40+ tools).

## Components

| Component | What it is | Semantics |
|-----------|-----------|-----------|
| [`skills/`](skills/) (7) | Methodology briefs the agent loads on demand | *How to do the work* |
| [`agents/`](agents/) (4) | Role definitions (Claude Code subagent format; usable as system prompts anywhere) | *Who does the work* |
| [`rules/`](rules/) (1) | Data-hygiene constraints, active in every analysis | *What is never allowed* |
| [`templates/`](templates/) (3) | Analysis brief, data contract, decision memo | *What the work produces* |

## The method

Every analysis runs the same sequence — enforced by the entry skill [`using-ops-method`](skills/using-ops-method/SKILL.md):

```mermaid
flowchart LR
    A["1 · Brief"] --> B["2 · Data contract"] --> C["3 · Honest metrics"] --> D["4 · Driver decomposition"] --> E["5 · Stress test"] --> F["6 · Decision memo"]
```

The constitution underneath (full text in [`rules/data-hygiene.md`](rules/data-hygiene.md)): report every dropped row · state every denominator and date anchor · never average ratios · benchmark against doing nothing · reconcile one headline number to raw data before presenting.

## The skills

| Skill | What it disciplines | Fires when you say things like |
|-------|---------------------|-------------------------------|
| [`using-ops-method`](skills/using-ops-method/SKILL.md) | **The entry point** — sequence, routing and the constitution | any ops/supply-chain analysis request |
| [`otif-analysis`](skills/otif-analysis/SKILL.md) | Delivery performance: the 5-rung metric ladder, driver decomposition, tail analysis | "OTIF", "on-time delivery", "why do customers complain at 95%?" |
| [`forecast-accuracy-review`](skills/forecast-accuracy-review/SKILL.md) | Forecast evaluation: WMAPE + bias + FVA vs naive, rolling-origin backtests | "forecast accuracy", "is our demand planning working?" |
| [`abc-xyz-segmentation`](skills/abc-xyz-segmentation/SKILL.md) | Portfolio segmentation: value × variability 9-box with a policy per cell | "ABC analysis", "which SKUs deserve attention?" |
| [`safety-stock-review`](skills/safety-stock-review/SKILL.md) | Buffer sizing: the formula **plus** an empirical stress test of what it delivers | "safety stock", "service level", "reorder point" |
| [`root-cause-pareto`](skills/root-cause-pareto/SKILL.md) | Pareto discipline: unit choice, category hygiene, exposure normalization, follow-up metric | "downtime pareto", "defect ranking", "80/20" |
| [`weekly-ops-report`](skills/weekly-ops-report/SKILL.md) | Reporting contract: what changed / where concentrated / what needs a decision | "weekly report", "summarize our KPIs for management" |

## The agents

| Agent | Role |
|-------|------|
| [`delivery-analyst`](agents/delivery-analyst.md) | OTIF and service-level analyses, end to end |
| [`demand-planner`](agents/demand-planner.md) | Demand profiling and forecast-value verdicts |
| [`inventory-analyst`](agents/inventory-analyst.md) | Segmentation, safety stock, rationalization |
| [`ops-reviewer`](agents/ops-reviewer.md) | **The gate**: adversarial review of any analysis against the rules, before it ships |

## Why this is different

Every part encodes **the pitfalls, not just the steps** — the measurement traps of real operations: MAPE's silent zero-dropping, tolerance windows that buy free KPI points, cycle-service numbers quoted where contracts say fill rate, "Other" as the tallest Pareto bar. Each skill ends with a validation loop and a defined output contract, and the `ops-reviewer` agent exists to break your analysis in private before someone breaks it in a meeting.

The methodology is demonstrated, with numbers and charts, in the *measurement honesty* series: [otif-analytics](https://github.com/gulmezeren2-byte/otif-analytics) · [forecast-accuracy-lab](https://github.com/gulmezeren2-byte/forecast-accuracy-lab) · [abc-xyz-inventory](https://github.com/gulmezeren2-byte/abc-xyz-inventory) · [auto-report-pipeline](https://github.com/gulmezeren2-byte/auto-report-pipeline)

## Install

**Claude Code — one command (plugin):**

```
/plugin marketplace add gulmezeren2-byte/industrial-engineering-ai-skills
/plugin install industrial-engineering-ai-skills
```

**Claude Code — manual copy** (pick the parts you want):

```bash
git clone https://github.com/gulmezeren2-byte/industrial-engineering-ai-skills
cd industrial-engineering-ai-skills
cp -r skills/* ~/.claude/skills/          # user-wide skills (or .claude/skills/ per project)
cp -r agents/* ~/.claude/agents/          # role subagents (or .claude/agents/ per project)
cat rules/data-hygiene.md >> CLAUDE.md    # always-on rules, per project
cp templates/* your-project/docs/         # artifacts
```

**Other agents** (Codex, Cursor, Gemini CLI, ...) — the `skills/` folders follow the [Agent Skills standard](https://agentskills.io); check your tool's skills directory. Agent files work as plain system prompts.

**Any LLM, no agent** — open a SKILL.md and paste it as context before your question; each one is written to work as a standalone methodology brief.

## Roadmap — next skills

- [x] Entry skill, roles, rules and templates (the pack structure)
- [ ] `smed-changeover-analysis` — changeover time reduction, internal/external split discipline
- [ ] `line-balancing` — takt, precedence, balance-loss accounting
- [ ] `demand-pattern-classification` — smooth/erratic/intermittent/lumpy routing to the right method
- [ ] `mrp-sanity-check` — parameter audit: lot sizes, lead times, safety settings vs reality
- [ ] `kpi-tree-design` — from strategic goal to measurable driver tree without vanity metrics
- [ ] `inventory-health-audit` — excess/obsolete detection and cash-release sizing

Suggestions welcome — open an issue with the messiest analysis you keep repeating.

## About

Curated and written by **[Eren Gülmez](https://www.linkedin.com/in/erengulmez)** — industrial engineer, İstanbul. I design measurement systems and direct modern tooling to ship them; this pack is the judgment layer of that work, packaged for reuse.

Part of an open industrial-engineering toolkit → **[awesome-industrial-engineering](https://github.com/gulmezeren2-byte/awesome-industrial-engineering)**

## License

[MIT](LICENSE)
