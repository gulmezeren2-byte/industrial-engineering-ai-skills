# Copilot instructions — industrial-engineering-ai-skills

An operations-analysis *method pack* for AI agents — agent **skills**, role **agents**, always-on **rules**, and artifact **templates** — packaged as a Claude Code plugin and built on the [Agent Skills](https://agentskills.io) open standard; it is not a conventional code project (no build, test, or runtime — every component is Markdown).

## Structure
- `skills/<skill-name>/SKILL.md` (7) — methodology briefs loaded on demand ("how to do the work"); one folder per skill, folder name equals the frontmatter `name`. `using-ops-method` is the entry/router skill.
- `agents/<name>.md` (4) — role definitions / subagent system prompts ("who does the work"): `delivery-analyst`, `demand-planner`, `inventory-analyst`, `ops-reviewer` (the adversarial gate).
- `rules/data-hygiene.md` (1) — 8 numbered always-on data-hygiene constraints applied in every analysis ("what is never allowed").
- `templates/*.md` (3) — output scaffolds with HTML-comment prompts: `analysis-brief`, `data-contract`, `decision-memo`.
- `.claude-plugin/plugin.json` + `marketplace.json` — plugin manifests (`/plugin marketplace add gulmezeren2-byte/...`); `plugin.json` registers `./skills/` and `./agents/` only — rules and templates are copied/pasted manually. `README.tr.md` mirrors `README.md` — keep both in sync.

## Adding a skill / agent
A skill is a new folder `skills/<kebab-name>/SKILL.md` with YAML frontmatter (only `name` + `description`) followed by a Markdown body. `name` must equal the folder name. The `description` is the trigger contract and follows a three-part convention: what it does · `Use when...` trigger phrases (include Turkish keywords) · a single `Differentiator -` clause. Note the ` - ` separator (spaced hyphen), not an em dash.

```yaml
---
name: otif-analysis
description: Audit delivery performance from order-level data - compute the OTIF metric ladder (tolerant to strict), find where lateness concentrates, and quantify the gap between the reported KPI and what customers experience. Use when the user mentions OTIF, on-time delivery, delivery performance, late orders, teslimat performansı, zamanında teslimat, or asks why customers complain despite a high on-time score. Differentiator - exposes measurement choices before optimizing operations.
---
```

An agent is a flat `agents/<name>.md` with the same `name`/`description` frontmatter, then a second-person role prompt that points back to the relevant skill(s).

## Conventions
- Skill bodies follow a fixed shape: intro on failure modes -> `Required data` / `Workflow` / `Pitfalls to check` -> `Output format`, ending in a validation/reconcile loop and a defined output contract; link a worked-example repo where one exists.
- Encode the pitfalls, not just the steps — every component states the measurement traps it guards against.
- Cross-reference other components by bare name (e.g. "see the `using-ops-method` skill", `templates/decision-memo.md`, `rules/data-hygiene.md`), not by URL or path outside the repo.
- Prose is English; keep the bilingual (English + Turkish) trigger keywords inside `description` fields. MIT-licensed; update the README count badges when adding a component.
