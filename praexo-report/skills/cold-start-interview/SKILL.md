---
name: cold-start-interview
description: Interview the user about their report preferences and write the praexo-report practice profile. Run once when first installing, or re-run when brand or report defaults change. Captures firm identity, brand template path, report length defaults, voice intensity, special box preferences, output paths, and quality gates. Takes 5-10 minutes. Every other skill in this plugin reads from the profile this writes.
---

# Cold-start interview — Praexo Report

You are interviewing the user to build their report practice profile. The output is a filled `CLAUDE.md` at `~/.claude/plugins/config/praexo-report/CLAUDE.md`.

This interview is **shorter** than the praexo-research one — most decisions here are about brand and format, not analytical method.

## How to run

Walk through the sections one at a time. Conversational, not form-style. Offer a quick-start option that fills only firm identity, logo path, output path, and filename convention.

## Sections to cover

### 1. Identity

- Firm name (legal entity that publishes the reports)
- Default author name and title

### 2. Brand

- Path to logo PNG (must be accessible from the plugin's assets/ folder)
- Cover page subtitle convention
- Whether to use the default Praexo brand spec (`references/praexo-brand-spec.md`) or upload a different one

If they upload a different brand spec, read it and adapt the references file. If they confirm Praexo defaults, no further action needed.

### 3. Report defaults

- Target length for full reports (default 55-65 pages)
- Default section structure (confirm or modify the 12-section framework)
- Required table count (default minimum 7)
- Output path (where the .docx lands)
- Filename convention (default `Praexo_[Subject]_[YYYY-MM-DD].docx`)

### 4. Voice intensity

The research notes have an inherent voice — how should the report treat it?

- **Preserve:** voice in the report matches the notes' voice exactly
- **Amplify:** report turns up the directness, adds more contrarian framing in Emphasis Boxes
- **Soften:** report tones down hedge-stripping, adds more balanced framing for external readers

Ask about hedge tolerance for the final published document — same as notes, or different?

Ask where Praexo should "show teeth" — usually Section 9 (AI disruption), Section 11 (thesis), and Emphasis Boxes.

### 5. Special boxes

- Target count for Emphasis Boxes (default 4-6 across full report)
- Placement preference for Summary Boxes (default 1 per major analytical section)

### 6. Input expectations

- Primary input format — praexo-research notes, or other markdown structure?
- Required input sections — confirm the default (all 8 analytical sections)
- Behavior when input is incomplete — warn and ask, or generate placeholders?

### 7. Quality gates

Explain that quality gates are pre-output checks the skill runs before saving the .docx. If a gate fails, the user gets a warning and can choose to override or fix.

Default gates:
- Minimum 7 data tables
- At least 1 Emphasis Box in Sections 7, 9, 11
- No `[TBD]` markers anywhere in the output
- Minimum 3 cited sources per analytical section

Ask if they want to modify any of these.

## Output

1. Show the draft `CLAUDE.md` for confirmation
2. On confirmation, write to `~/.claude/plugins/config/praexo-report/CLAUDE.md`
3. Show a 5-line summary
4. List the skills now available:
   - `/praexo-report:full-report` — full 55-65 page Praexo report
   - `/praexo-report:executive-brief` — 8-12 page executive brief
5. **Important reminder:** the brand logo PNG must exist at the path specified in the profile. If it's not yet in place, prompt the user to copy it to the plugin's `assets/` folder before running any report skill.

## What not to do

- Don't ask about analytical methodology — that's the research plugin's concern
- Don't push the user to override defaults unless they have a clear reason
- Don't write to disk before user confirms the draft
- Don't list every option in the brand spec — only the ones that affect the cold-start decision
