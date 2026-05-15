# Praexo Report — Practice Profile

This file is read by every skill in the `praexo-report` plugin before producing output.
Edit it directly for small fixes, or re-run `/praexo-report:cold-start-interview` for a full refresh.

## Identity

- **Firm:** [TBD — e.g. Praexo Management BV / Praexo Consulting LLC]
- **Default author name:** [TBD — e.g. Marc Leon]
- **Default author title:** [TBD — e.g. Managing Partner]

## Brand

- **Template name:** [TBD — e.g. Praexo Standard Research Report]
- **Brand reference file:** `references/praexo-brand-spec.md` (in this plugin)
- **Logo path:** [TBD — e.g. assets/praexo-logo.png — must exist in plugin assets/ folder]
- **Cover page subtitle convention:** [TBD — e.g. "Deep Research Report — Praexo Research"]

## Report defaults

- **Target length:** [TBD — e.g. 55-65 pages for full-report, 8-12 for executive-brief]
- **Section structure:** [TBD — default 12 sections per references/report-framework.md, or override]
- **Required tables:** [TBD — default 9 per framework, or override]
- **Default output path:** [TBD — e.g. /mnt/user-data/outputs/]
- **Filename convention:** [TBD — e.g. Praexo_[Subject]_[YYYY-MM-DD].docx]

## Voice intensity

How aggressive Praexo's voice should be in the final report. The research notes have an inherent voice; the report can amplify or soften it.

- **Default intensity:** [TBD — preserve / amplify / soften]
- **Hedge tolerance in report:** [TBD — low / medium / high]
- **Where Praexo should "show teeth":** [TBD — e.g. Section 9 AI disruption, Section 11 thesis, Emphasis Boxes]

## Special boxes preference

- **Emphasis Boxes** (amber, contrarian observations): [TBD — target count per report, default 4-6]
- **Summary Boxes** (green, section takeaways): [TBD — target placement, default 1 per major section]

## Input expectations

- **Primary input format:** [TBD — e.g. praexo-research markdown notes, or hand-curated outline]
- **Required input sections:** [TBD — default: all 8 analytical sections of research-notes-template.md]
- **Behavior when input is incomplete:** [TBD — warn and ask / generate placeholders / use defaults]

## Quality gates

- [TBD — e.g. minimum 7 data tables in any full-report]
- [TBD — e.g. at least 1 Emphasis Box in Sections 7, 9, 11]
- [TBD — e.g. no section may contain `[TBD]` markers — fail the build if found]
- [TBD — e.g. minimum 3 cited sources per analytical section]
