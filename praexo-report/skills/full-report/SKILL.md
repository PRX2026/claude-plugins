---
name: full-report
description: Generate the full 55-65 page Praexo-branded Word report (.docx) from research notes. Reads the practice profile for firm identity, brand template, length defaults, voice intensity, and quality gates. Input is either praexo-research markdown notes or hand-curated research content. Use when the user says "produce the full report", "build the Praexo report", "Praexo report on [subject]", "generate the .docx", or asks for a deliverable Word document from research. Output is a single .docx file in the user's configured output path.
---

# Full Report — Praexo branded .docx

You are producing a 55-65 page Praexo-branded Word document from research notes.

## Pre-flight check

1. Read `~/.claude/plugins/config/praexo-report/CLAUDE.md` — the report practice profile
2. Read `references/praexo-brand-spec.md` — full brand specification (colors, fonts, headings, tables, boxes)
3. Read `references/report-framework.md` — section-by-section structure
4. Read `/mnt/skills/public/docx/SKILL.md` — docx-js mechanics
5. **Check that the logo PNG exists** at the path defined in the profile. If not, stop and ask the user to provide it.

If profile has >3 `[TBD]` markers, warn and offer cold-start. If the user proceeds, use sensible defaults from the references.

## Inputs

Required:
- **Research input** — either:
  - Path to a praexo-research markdown notes file (`praexo-research_[subject]_[date].md`)
  - Markdown content pasted inline
  - Reference to attached document(s)

Optional:
- **Subject name override** (if filename should differ from input subject)
- **Length override** (default from profile, usually 55-65 pages)
- **Voice intensity override** (default from profile)

If only a subject name is given without research input, stop and tell the user:

> "I need research notes to build the report. Either:
> - Run `/praexo-research:company-research [subject]` first, or
> - Paste / attach your research content, or
> - Tell me to use placeholder content for layout testing only"

## Input parsing

If the input is a praexo-research notes file, expect this structure (from `research-notes-template.md`):

1. Header block
2. One-page summary (5 questions)
3. Company / sector overview
4. Value chain analysis
5. Growth & margin levers
6. Strategy decode
7. Competitive dynamics
8. AI disruption & transformation
9. Risk assessment
10. Open questions
11. Source log

Map each notes section to its report section per `references/report-framework.md`.

If the input is non-standard markdown, map content to report sections by best fit and flag anything that doesn't have a natural home.

## Report structure

Follow `references/report-framework.md` exactly. Summary:

| # | Section | Target pages | From notes section |
| --- | --- | --- | --- |
| 1 | Cover page | 1 | Header block |
| 2 | Table of contents | 1 | (auto-generated) |
| 3 | Executive summary | 2-3 | One-page summary |
| 4 | Company / sector overview | 2-3 | Section 3 of notes |
| 5 | Value chain analysis | 8-10 | Section 4 of notes |
| 6 | Growth & margin levers | 8-10 | Section 5 of notes |
| 7 | Strategy decode | 6-8 | Section 6 of notes |
| 8 | Competitive dynamics | 5-7 | Section 7 of notes |
| 9 | AI disruption & transformation | 10-12 | Section 8 of notes |
| 10 | Integrated risk assessment | 8-10 | Section 9 of notes |
| 11 | Investment thesis & scenarios | 3-4 | (synthesized from all) |
| 12 | Appendices | 2-4 | Section 11 (sources) + KPI dashboard |

## Build sequence

Build the document incrementally — do NOT try to hold the entire report in working memory before writing:

1. Create the docx structure (cover, TOC field, section headings only — no body yet)
2. Generate Section 3 (Executive Summary) — this anchors the rest
3. Generate Sections 4-10 one at a time, saving progress between sections
4. Generate Section 11 (Investment Thesis) — uses all preceding sections
5. Generate Section 12 (Appendices) — including source log from input notes
6. Run quality gate checks
7. Save final .docx and present

## Praexo brand application

Apply the brand spec consistently (see `references/praexo-brand-spec.md` for full detail):

- **Font:** Aptos throughout
- **H1:** 14pt bold, black, Praexo Green (#02AD84) bottom border, starts on new page, numbered "1.", "2.", etc.
- **H2:** 13pt bold, Dark Teal (#0E3C48), sub-numbered "1.1", "1.2"
- **H3:** 11pt bold, Dark Gray (#4D4D4D), not numbered
- **Body:** 11pt, justified, 1.1 line spacing
- **Tables:** Dark Teal header (#0E3C48), white bold header text, alternating body rows (white / #F5F5F5)
- **Emphasis Box:** Amber background (#FFF3E0), Emphasis Amber title (#92671D, bold italic)
- **Summary Box:** Light Teal background (#E6F7F4), Praexo Green title (#02AD84, bold)
- **Header (page 2+):** Praexo logo right-aligned
- **Footer (page 2+):** "Praexo Management BV   |   [page number]" right-aligned in Praexo Green

## Required tables

Minimum 7. Default 9 per `references/report-framework.md`:

1. Financial Snapshot (Sec 4)
2. Value Chain Map (Sec 5)
3. Margin Bridge (Sec 6)
4. Leading Indicators (Sec 6)
5. Competitive Positioning (Sec 8)
6. AI Use Case Ranking (Sec 9)
7. Master Risk Matrix (Sec 10)
8. 12-Quarter Roadmap (Sec 7)
9. KPI Dashboard (Appendix)

## Special boxes

- Summary Box at the end of every major analytical section (after content, before next H1)
- Emphasis Box where the input notes flag a contrarian observation or "what most people get wrong" — target 4-6 across the report

## Voice intensity

Apply the profile's voice intensity setting to the writing:

- **Preserve:** match the notes' voice exactly. Don't rewrite phrasing.
- **Amplify:** strip residual hedges, sharpen contrarian framing in Emphasis Boxes, lead each section with a stronger directional statement
- **Soften:** add balance where notes are highly directional, frame contrarian observations as "alternative interpretations", add more "may" and "could" where notes use "will"

## Quality gates

Before saving, check:

- [ ] At least 7 data tables present
- [ ] At least 1 Emphasis Box in each of Sections 7, 9, 11
- [ ] No `[TBD]` markers anywhere
- [ ] Each analytical section cites at least 3 sources
- [ ] Cover page has correct firm name, author, date
- [ ] TOC field is present and will refresh on Word open
- [ ] Footer page numbers configured correctly
- [ ] Logo image inserted in header

If any gate fails, warn the user with specifics. Let them choose to fix or override.

## Output

1. Save to the profile-defined output path
2. Filename per profile convention (default `Praexo_[Subject]_[YYYY-MM-DD].docx`)
3. Present the file
4. Give a 3-sentence summary: most important finding, where Praexo shows the most teeth, any quality gates that needed override

## What not to do

- Don't fabricate research content. If input is thin, surface the gap — don't pad
- Don't reorganize the section structure unless the profile says to
- Don't deviate from the brand spec without explicit user instruction
- Don't produce both .docx and .pdf unless asked — Word is the deliverable
- Don't generate the entire report in one pass — build incrementally
