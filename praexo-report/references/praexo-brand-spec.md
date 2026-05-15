# Praexo Brand Specification

This is the canonical brand spec for `praexo-report` skills. Refer to this for every styling decision.

## Font

**Aptos** throughout. No exceptions. If Aptos is unavailable, fall back to **Calibri** (Word's default).

## Color palette

| Token | Hex | Usage |
| --- | --- | --- |
| Praexo Green | `#02AD84` | Cover title, H1 bottom border, footer text, Summary Box title |
| Dark Teal | `#0E3C48` | H2 text, Table header background |
| Emphasis Amber | `#92671D` | Emphasis Box title (bold italic) |
| Emphasis Box BG | `#FFF3E0` | Emphasis Box background |
| Summary Box BG | `#E6F7F4` | Summary Box background |
| Row Stripe | `#F5F5F5` | Alternating table body rows |
| Dark Gray | `#4D4D4D` | H3 text |
| Black | `#000000` | H1 text, body text |
| White | `#FFFFFF` | Table header text, alternating table body rows |

## Heading styles

### H1 (section heading — e.g. "1. Executive Summary")

- Font: Aptos
- Size: 14pt
- Weight: Bold
- Color: Black (`#000000`)
- Border: Bottom border 1pt, color Praexo Green (`#02AD84`)
- Spacing: 18pt before, 10pt after
- Numbering: "1.", "2.", "3.", etc.
- **Always starts on new page** (`pageBreakBefore: true`)

### H2 (subsection — e.g. "1.1 What the business is")

- Font: Aptos
- Size: 13pt
- Weight: Bold
- Color: Dark Teal (`#0E3C48`)
- Spacing: 14pt before, 8pt after
- Numbering: "1.1", "1.2", "2.1", etc.

### H3 (tertiary heading)

- Font: Aptos
- Size: 11pt
- Weight: Bold
- Color: Dark Gray (`#4D4D4D`)
- Spacing: 10pt before, 6pt after
- Numbering: none

### Body text

- Font: Aptos
- Size: 11pt
- Alignment: Justified
- Line spacing: 1.1
- Spacing: 6pt before

## Cover page

- Title: 48pt, Bold, Praexo Green (`#02AD84`)
- Subtitle: 24pt, regular weight, gray (`#4D4D4D`)
- Metadata table at bottom:
  - 2 columns: "Date" | "Prepared by"
  - 11pt body text
  - No visible borders
  - Compact

## Tables (data tables)

### Header row
- Background: Dark Teal (`#0E3C48`)
- Text color: White (`#FFFFFF`)
- Weight: Bold
- Padding: 80 DXA top/bottom, 120 DXA left/right

### Body rows
- Alternating: row 1 White (`#FFFFFF`), row 2 Row Stripe (`#F5F5F5`), row 3 White, etc.
- Text color: Black
- Weight: Regular
- Padding: 60 DXA top/bottom, 120 DXA left/right

### Borders
- All sides: single, size 4, auto color

### Width
- Full text width: 9360 DXA
- Column widths must sum to 9360
- **Always DXA** — never use `WidthType.PERCENTAGE`

## Special boxes

### Emphasis Box (contrarian / risk / "what most people miss")

- Structure: full-width single-cell table
- Background: Emphasis Box BG (`#FFF3E0`)
- Borders: no visible borders (all sides set to "none" or width 0)
- Padding: 160 DXA all sides
- Title (first line of cell, bold italic, Emphasis Amber `#92671D`): the box's claim
- Body (subsequent paragraphs, regular body style): the supporting analysis

Use sparingly — 4-6 across a full report. Required placements per `report-framework.md`.

### Summary Box (section takeaway / key insight)

- Structure: full-width single-cell table
- Background: Summary Box BG (`#E6F7F4`)
- Borders: no visible borders
- Padding: 160 DXA all sides
- Title (first line of cell, bold, Praexo Green `#02AD84`): the takeaway
- Body (subsequent paragraphs, regular body style): the supporting context

Use one per major analytical section, placed after the analysis and before the next H1.

## Header (page 2 onward)

- Praexo logo PNG, right-aligned
- Logo height: ~0.4 inch (adjust to fit gracefully in standard Word header area)
- Logo path from practice profile (e.g. `assets/praexo-logo.png`)

## Footer (page 2 onward)

- Right-aligned
- Text: "Praexo Management BV   |   [page number]"
- Use 3 spaces between firm name and pipe, and pipe and page number
- Font: Aptos, 9pt, Praexo Green (`#02AD84`)
- Page number is a Word field, not literal text — it auto-updates

## Spacing and margins

- Page margins: 1 inch all sides (default Word)
- Line spacing: 1.1 body, 1.0 in tables
- Paragraph spacing: defined per style above

## What never to deviate from

- Font (Aptos)
- Praexo Green for headers/borders/footer
- Dark Teal for table headers and H2
- Emphasis vs. Summary box color distinction (amber = contrarian, green = takeaway)
- H1 always starts on new page
- Footer always shows page number

If the user requests a deviation in voice or content, that's fine — voice is on the writer side. If they request a deviation in brand styling, surface it as an exception: "I can do that, but it's outside the Praexo brand spec. Confirm?"
