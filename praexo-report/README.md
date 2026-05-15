# praexo-report

Praexo-branded Word report generator. Takes research notes and produces deliverable .docx files in Praexo brand style.

## What this plugin is for

This plugin does **document generation**, not research. It takes structured research content (markdown notes from `praexo-research`, or any well-organized markdown) and produces a polished Word document with full Praexo branding: cover page, TOC, branded headings, data tables, Emphasis Boxes, Summary Boxes, header logo, footer pagination.

If you want to do the analysis itself, use the `praexo-research` plugin first.

## Skills

| Command | What it does |
| --- | --- |
| `/praexo-report:cold-start-interview` | One-time setup — captures firm identity, brand path, voice intensity, output preferences |
| `/praexo-report:full-report` | 55-65 page Praexo report with 12 sections, 9 tables, special boxes |
| `/praexo-report:executive-brief` | 8-12 page compressed brief, same brand, sharper voice |

## Install (Claude Code)

```bash
cd /path/to/praexo-plugins
/plugin marketplace add ./
/plugin install praexo-report@praexo
# Copy your logo to praexo-report/assets/praexo-logo.png
/praexo-report:cold-start-interview
```

## Install (Cowork)

Cowork → Customize → Browse plugins → Upload custom plugin → zip the `praexo-report/` folder. Or add via GitHub source.

**Important:** before running any report skill, copy your Praexo logo PNG to `praexo-report/assets/praexo-logo.png`. The skills will refuse to run without it.

## Reference files

- `references/report-framework.md` — section-by-section spec for full reports
- `references/praexo-brand-spec.md` — colors, fonts, headings, tables, boxes

## Typical workflow

```
# 1. Run research
/praexo-research:company-research [Company]
   → produces praexo-research_[Company]_[date].md

# 2. Build report from research
/praexo-report:full-report
   → consumes the markdown notes
   → produces Praexo_[Company]_[date].docx
```

The two plugins are **independent** — you can run `praexo-report` on any well-structured markdown research, not just `praexo-research` output. And `praexo-research` can feed into other downstream uses, not just this report.

## Quality gates

Each report skill runs pre-output checks:

- Minimum table count
- Required Emphasis Box and Summary Box placements
- No `[TBD]` markers
- Source citation minimums

If a gate fails, the skill warns you with specifics before saving. You can fix or override.

## License

MIT
