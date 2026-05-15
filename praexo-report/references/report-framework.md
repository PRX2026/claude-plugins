# Report Framework — Section-by-Section Specification

This is the canonical structure for `/praexo-report:full-report`. The `executive-brief` skill uses a compressed variant defined in its SKILL.md.

## Full report — 12 sections, 55-65 pages target

### 1. Cover page (1 page)

**No header/footer on this page.**

- Title: company / sector name in 48pt Praexo Green (#02AD84)
- Subtitle: from profile (default "Deep Research Report — Praexo Research") in 24pt gray
- Metadata table at bottom (2 columns):
  - Date | Prepared by [author from profile]
  - Format: simple table, no visible borders, 11pt body
- Page break after

### 2. Table of Contents (1 page)

**Header/footer start here and continue through the document.**

- Manual H1 "Table of Contents" (do not number this one)
- TOC field with `headingStyleRange "1-2"`, hyperlinks enabled
- Page break after

### 3. Executive Summary (2-3 pages)

Maps directly from the 5-question summary in research notes.

- H1 "1. Executive Summary"
- Five H2 subsections, one per question:
  - 1.1 What the subject actually is
  - 1.2 Where economic value concentrates
  - 1.3 The 2-3 variables driving 80% of outcomes
  - 1.4 How AI changes the picture
  - 1.5 What most analysts get wrong
- **End with one Summary Box:** "The view in one paragraph"

### 4. Company / Sector Overview (2-3 pages)

- H1 "2. [Company/Sector] Overview"
- H2 "2.1 What the business is" (1 page body text)
- H2 "2.2 Financial snapshot" — includes Financial Snapshot table
- H2 "2.3 Recent material events" (last 12 months)
- H2 "2.4 Industry context"

### 5. Value Chain Analysis (8-10 pages)

Largest section in the report. This is where Praexo's structural analysis lives.

- H1 "3. Value Chain Analysis"
- H2 "3.1 Overview and headline thesis"
- H2 "3.2 Layer-by-layer map" — includes Value Chain Map table
- H2 "3.3 Profit pool distribution" — includes profit pool table (which layers capture what % of revenue and profit)
- H2 "3.4 Power dynamics and bottlenecks"
- H2 "3.5 Where the map is moving"
- **End with one Summary Box:** key value chain insight
- **At least one Emphasis Box** for the contrarian observation

### 6. Growth & Margin Levers (8-10 pages)

- H1 "4. Growth & Margin Levers"
- H2 "4.1 The financial engine in plain language"
- H2 "4.2 Revenue decomposition"
- H2 "4.3 Margin trends and bridge" — includes Margin Bridge table
- H2 "4.4 Unit economics" (where applicable)
- H2 "4.5 Leading indicators" — includes Leading Indicators table
- H2 "4.6 What management is managing the business against"
- **End with one Summary Box**

### 7. Strategy Decode (6-8 pages)

- H1 "5. Strategy Decode"
- H2 "5.1 Stated strategy"
- H2 "5.2 Observable strategy"
- H2 "5.3 The say-do ratio"
- H2 "5.4 Management quality signals"
- H2 "5.5 12-quarter forward roadmap" — includes 12-Quarter Roadmap table
- **End with one Summary Box**
- **At least one Emphasis Box** for management quality contrarian view

### 8. Competitive Dynamics (5-7 pages)

- H1 "6. Competitive Dynamics"
- H2 "6.1 Positioning" — includes Competitive Positioning table
- H2 "6.2 Recent competitive moves (last 12-18 months)"
- H2 "6.3 New entrants and adjacent threats"
- H2 "6.4 Where the competitive landscape is moving"
- **End with one Summary Box**

### 9. AI Disruption & Transformation (10-12 pages)

Second-largest section. This is where Praexo's forward view lives.

- H1 "7. AI Disruption & Transformation"
- H2 "7.1 Net AI thesis"
- H2 "7.2 External disruption threat"
  - Named AI-native attackers with funding and target layer
- H2 "7.3 Internal opportunity — ranked use cases" — includes AI Use Case Ranking table
- H2 "7.4 Data assets"
- H2 "7.5 Organizational readiness"
- H2 "7.6 What most people get wrong about AI on this subject"
- **End with one Summary Box**
- **At least one Emphasis Box** in section 7.6

### 10. Integrated Risk Assessment (8-10 pages)

- H1 "8. Integrated Risk Assessment"
- H2 "8.1 Master risk matrix" — includes Master Risk Matrix table
- H2 "8.2 Economic risks"
- H2 "8.3 Geopolitical risks"
- H2 "8.4 Regulatory risks"
- H2 "8.5 Secular / structural risks"
- H2 "8.6 The underwriting view" — the risk(s) that would actually change the thesis
- **End with one Summary Box**

### 11. Investment Thesis & Scenarios (3-4 pages)

Synthesis section. Pulls from all prior sections.

- H1 "9. Investment Thesis & Scenarios"
- H2 "9.1 Bull case" — what has to be true, key triggers, checkpoint metrics
- H2 "9.2 Base case" — what's already priced in
- H2 "9.3 Bear case" — what has to go wrong, key triggers, checkpoint metrics
- H2 "9.4 What I'd watch over the next 4 quarters"
- **End with one Summary Box:** the thesis in one paragraph
- **At least one Emphasis Box:** the single highest-conviction view

### 12. Appendices (2-4 pages)

- H1 "10. Appendices"
- H2 "10.1 KPI Dashboard" — includes KPI Dashboard table
- H2 "10.2 Methodology"
- H2 "10.3 Sources" — full source log from input research notes, grouped by primary / secondary / tertiary
- H2 "10.4 Open questions" — from input research notes

---

## Required tables (default 9)

| # | Table | Section | Columns |
| --- | --- | --- | --- |
| 1 | Financial Snapshot | 4.2 | Metric / Latest / Y-1 / Y-2 / Y-3 / Y-5 |
| 2 | Value Chain Map | 5.2 | Layer / Player Type / Revenue Model / Moat / Power Trend |
| 3 | Profit Pool | 5.3 | Layer / % Revenue / % Profit / Trend |
| 4 | Margin Bridge | 6.3 | Component / Latest year / Bridge to FCF |
| 5 | Leading Indicators | 6.5 | Indicator / Current / Watch / Alert / Why it matters |
| 6 | 12-Quarter Roadmap | 7.5 | Quarter / Milestone / Pass criteria / Fail signal |
| 7 | Competitive Positioning | 8.1 | Dimension / Subject / Comp A / Comp B / Comp C |
| 8 | AI Use Case Ranking | 9.3 | # / Use case / Process / Impact / Feasibility / ROI window / Priority |
| 9 | Master Risk Matrix | 10.1 | Risk / Category / Likelihood / Impact / Trend / Hedge |
| 10 | KPI Dashboard | 12.1 | Category / KPI / Current / Watch / Alert / Frequency / Source |

(Profit Pool can be inline with Value Chain Map if compact, in which case minimum is 9 tables. The minimum quality gate is 7.)

## Required special boxes

- **Summary Boxes:** one per analytical section (5, 6, 7, 8, 9, 10, 11) = 7 minimum
- **Emphasis Boxes:** 4-6 across the report. Required placements: Section 5 (value chain), Section 7 (strategy), Section 9 (AI), Section 11 (thesis). Others at the writer's discretion.

## Sections that must always start on a new page

Every H1. Use `pageBreakBefore: true` on H1 style.

## Page numbering

- Cover page: no number
- TOC: no number, but counts toward physical page count
- Section 1 (Executive Summary): starts as page 3 in displayed numbering
- All subsequent pages: footer shows "Praexo Management BV   |   [page number]" right-aligned, 9pt, Praexo Green
