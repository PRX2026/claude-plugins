---
name: executive-brief
description: Generate a shorter 8-12 page Praexo-branded executive brief from research notes. Same brand styling as full-report but compressed to the highest-leverage analysis. Reads the practice profile for brand, voice intensity, and output preferences. Use when the user says "executive brief", "short report", "investor brief", "C-suite brief", or asks for a Praexo Word doc shorter than the full 60-page report.
---

# Executive Brief — Praexo branded .docx (8-12 pages)

A compressed version of the full report. Same brand, same voice, fewer sections, tighter analysis.

## Pre-flight check

Same as `full-report`:

1. Read `~/.claude/plugins/config/praexo-report/CLAUDE.md`
2. Read `references/praexo-brand-spec.md`
3. Read `references/report-framework.md` (use the **brief variant** below)
4. Read `/mnt/skills/public/docx/SKILL.md`
5. Confirm logo PNG exists

## Inputs

Same as `full-report` — research notes (file or inline) plus optional overrides.

## Brief structure (8-12 pages)

| # | Section | Target pages | Notes |
| --- | --- | --- | --- |
| 1 | Cover page | 1 | Same as full-report |
| 2 | Executive summary | 1-2 | Tightest version of the 5-question summary |
| 3 | The thesis in one page | 1 | New section — bull/base/bear in 3 short paragraphs |
| 4 | What the business actually is | 1-2 | Compressed company/sector overview + value chain |
| 5 | Growth & margin engine | 1-2 | Top 2-3 levers only |
| 6 | Competitive positioning | 1 | One table + 2-paragraph diagnosis |
| 7 | AI disruption | 1-2 | Top 3 use cases + top 2 external threats |
| 8 | Risk matrix | 1 | One table + 2-paragraph diagnosis |
| 9 | Bottom line | 0.5-1 | One Emphasis Box with the contrarian view + 1 Summary Box with the action items |

No appendices. No KPI dashboard. No 12-quarter roadmap.

## Required tables (minimum 3)

1. Competitive Positioning
2. AI Use Case Ranking
3. Master Risk Matrix

## Required boxes (minimum 2)

- 1 Emphasis Box: the contrarian view from the notes
- 1 Summary Box: the action items / what to do with this view

## Brand application

Same as `full-report`. Don't simplify the brand — a shorter document gets the same level of polish.

## Voice intensity

Apply the profile setting. For executive briefs, **default to amplify** — short documents reward clear directional voice. The reader has less time, so the analyst has less room to hedge.

## Quality gates

- [ ] At least 3 data tables
- [ ] At least 1 Emphasis Box and 1 Summary Box
- [ ] No `[TBD]` markers
- [ ] Bottom line section present and clear

## Output

Filename: `Praexo_[Subject]_ExecBrief_[YYYY-MM-DD].docx`

Present the file with a 2-sentence summary: the thesis in one sentence, and the action it implies.

## What not to do

- Don't try to fit the full report's content into 12 pages — choose ruthlessly
- Don't drop the brand styling to save space — keep the polish
- Don't soften the voice. Shorter = sharper, not gentler
- Don't add sections not in the brief structure — if the user wants more, route them to `full-report`
