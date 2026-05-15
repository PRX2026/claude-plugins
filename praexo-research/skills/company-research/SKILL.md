---
name: company-research
description: Deep research on a named company using the six-pass Praexo methodology. Outputs structured research notes (markdown) covering company overview, value chain, growth/margin levers, strategy decode, competitive dynamics, AI disruption, and risk assessment. Reads the practice profile for sectors of focus, source hierarchy, skepticism rules, and voice preferences. Use when the user says "research [company]", "analyze [company]", "deep dive on [company]", "Praexo notes on [company]", or names a company and asks for analytical understanding. Output is research notes, not a finished report — for the Praexo Word doc, run /praexo-report:full-report on the notes afterward.
---

# Company Research — Praexo methodology

You are producing structured research notes on a named company. Output is markdown — research notes that downstream skills (or humans) consume. **Not a finished report.**

## Pre-flight check

1. Read `~/.claude/plugins/config/praexo-research/CLAUDE.md` — the practice profile
2. Read `references/research-methodology.md` in this plugin — the six-pass research strategy
3. Read `references/research-notes-template.md` — the output structure (frozen)
4. Read `references/source-quality-rules.md` — what to cite, what to skip

If the practice profile has more than 3 `[TBD]` markers, stop and tell the user:

> "Your research profile is mostly empty. Notes I produce without it will use default settings (English output, standard source hierarchy, balanced voice). Want to run `/praexo-research:cold-start-interview` first? Takes 10-15 min."

Let them choose: proceed with defaults, or run the interview first.

## Inputs

- **Company name** (required)
- **Sector** (optional — infer if not given)
- **Specific focus** (optional — e.g. "focus on AI disruption", "skip M&A history", "deep on competitive dynamics")
- **Depth** (optional — quick (4-6 pages of notes), standard (8-12), extended (15-25). Default to standard unless profile says otherwise.)

If only the company name is given, that's enough. Don't interrogate.

## Research phase

Follow the six-pass methodology in `references/research-methodology.md`. Summary:

1. **Pass 1 — Foundational context** (10-15 searches): business overview, latest 10-K / annual report, recent news, industry overview
2. **Pass 2 — Value chain & competitive** (10-15 searches): value chain structure, profit pools, competitors, regulatory environment
3. **Pass 3 — Financial deep-dive** (8-12 searches): revenue breakdown, margin trends, unit economics, capital allocation
4. **Pass 4 — Strategy & forward-looking** (8-12 searches): earnings call commentary, strategic initiatives, M&A, analyst consensus
5. **Pass 5 — AI & disruption** (6-10 searches): company AI strategy, AI-native disruptors, automation opportunities, data assets
6. **Pass 6 — Macro & risk** (6-10 searches): regulatory changes, geopolitical exposure, macro sensitivity, ESG pressures

**Research quality rules** (from `references/source-quality-rules.md`):

- Primary sources first — filings, transcripts, investor presentations
- Triangulate every major claim — no single source anchors a major conclusion
- Use `web_fetch` for full filings, transcripts, long-form articles — never rely only on snippets
- Recency for strategy/competitive (last 12 months); older OK for structural analysis
- Track every source you use — the notes must cite specifics, not vague references

**Adapt to the practice profile:**
- Add searches for any topics in the profile's "always include" list
- Skip topics in the "skip unless asked" list (unless the user asked)
- Respect the user's source skepticism rules

## Notes structure

Use the frozen template in `references/research-notes-template.md`. The structure:

1. **Header block** — company, date, analyst, depth, focus areas
2. **One-page summary** — the 5 things the reader needs to know
3. **Company / sector overview** — factual baseline
4. **Value chain analysis** — money flows, power dynamics
5. **Growth & margin levers** — what drives the financial engine
6. **Strategy decode** — stated vs. actual, say-do ratio
7. **Competitive dynamics** — positioning, competitor moves
8. **AI disruption & transformation** — external threat, internal opportunity
9. **Risk assessment** — economic, geopolitical, regulatory, secular
10. **Open questions** — what you couldn't answer, what needs more digging
11. **Source log** — every source cited, with URL and access date

## Writing rules

- **English output, always** — even if the user wrote in Dutch / French / etc.
- **Lead each section with the "so what"** — the key insight, not the background
- **Mechanisms over conclusions** — explain *why*, not just *what*
- **Specific over generic** — replace every "significant" or "strong" with a number
- **Distinguish facts, analysis, judgment** — flag which register you're in
- **No filler phrases** — strip anything from the profile's "never want to see" list

## Output

1. Save the notes to the path defined in the practice profile (default: `/mnt/user-data/outputs/`)
2. Filename: `praexo-research_[company]_[YYYY-MM-DD].md`
3. Present the file to the user
4. Give a 3-sentence summary of the **single most important finding** — the thing most people get wrong about this company

## What not to do

- Don't produce a finished Praexo Word doc — that's `/praexo-report:full-report`
- Don't restate what the company says about itself — analyze mechanisms
- Don't include sections with `[TBD]` markers — if you don't have the data, say so explicitly in "Open questions"
- Don't pad — 8 pages of substance beats 15 pages of filler
- Don't quote management without flagging it as a quote and adding your own assessment
