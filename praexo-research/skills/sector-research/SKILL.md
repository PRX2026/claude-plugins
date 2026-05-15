---
name: sector-research
description: Industry / sector analysis without a single-company focus. Maps the sector structure, value chain, profit pools, key players, and disruption vectors. Reads the practice profile for source hierarchy, skepticism rules, and voice. Use when the user says "analyze the [sector] industry", "sector research on [industry]", "map the [industry] value chain", or asks for an industry-level deep dive without naming a specific company. Output is structured markdown research notes, not a finished report.
---

# Sector Research — Praexo methodology

You are producing structured research notes on an industry or sector — no single-company focus. Output is markdown.

## Pre-flight check

1. Read `~/.claude/plugins/config/praexo-research/CLAUDE.md`
2. Read `references/research-methodology.md`
3. Read `references/research-notes-template.md` (use the **sector** variant — same structure minus the company-specific sections)
4. Read `references/source-quality-rules.md`

If profile has >3 `[TBD]` markers, warn and offer cold-start.

## Inputs

- **Sector / industry name** (required — be specific: "specialty chemicals" not "chemicals")
- **Geographic scope** (optional — default to global with primary regions called out)
- **Depth** (optional — default standard)

## Research phase

Sector research follows a modified six-pass — same shape, different emphasis:

1. **Pass 1 — Sector overview**: market size, growth rate, lifecycle stage, structure (fragmented? consolidated?), top 10 players by revenue
2. **Pass 2 — Value chain & profit pools**: every layer from inputs to end customer, margin distribution, power dynamics
3. **Pass 3 — Financial benchmarks**: typical margins, capital intensity, working capital cycles, unit economics norms
4. **Pass 4 — Strategic dynamics**: where the industry is investing, M&A activity, capacity additions, geographic expansion
5. **Pass 5 — AI & disruption**: AI-native entrants, automation vectors, data asset value, incumbent response patterns
6. **Pass 6 — Macro & risk**: regulatory cycle, geopolitical exposure, demand sensitivity (rates, cycle, demographics), ESG pressures

Use representative companies as examples throughout — but don't deep-dive any single one. If the user wants single-company depth, suggest running `/praexo-research:company-research` on their top 3 picks afterward.

## Notes structure

Same template as `company-research`, with these adaptations:

- "Company overview" → "Sector overview" (size, growth, structure)
- "Strategy decode" → "Strategic dynamics" (where the industry collectively bets)
- "Competitive dynamics" → "Player landscape" (top 10 with brief profiles)
- All other sections same shape, sector-level analysis

## Writing rules

Same as `company-research`. English output, lead with "so what", specifics over generics, no filler from the "never want to see" list.

**One additional rule for sector work:** explicitly distinguish **structural** from **cyclical** dynamics. Most sector mistakes come from treating cyclical patterns as structural truths. Be the analyst who flags the difference.

## Output

1. Save to profile-defined output path
2. Filename: `praexo-sector_[sector-slug]_[YYYY-MM-DD].md`
3. Present and give 3-sentence summary of the **single most important sector dynamic** — the structural feature that defines the next decade

## What not to do

- Don't deep-dive any single company — if you find yourself writing 3 paragraphs on one player, you've drifted into company research
- Don't blur structural and cyclical — flag which is which explicitly
- Don't list every player — top 10 is enough, with a note on long-tail dynamics
- Don't produce a finished Word doc — that's the report plugin
