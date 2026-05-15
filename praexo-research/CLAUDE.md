# Praexo Research — Practice Profile

This file is read by every skill in the `praexo-research` plugin before producing output.
Edit it directly for small fixes, or re-run `/praexo-research:cold-start-interview` for a full refresh.

## Identity

- **Analyst / firm:** [TBD — e.g. Marc Leon, Praexo]
- **Primary use case:** [TBD — e.g. AnswerRocket BD prep, Columbia coursework, M&A diligence, advisory work]
- **Default output language:** English (Praexo's reports are ALWAYS in English regardless of input language)

## Analytical lens

- **Sectors of focus:** [TBD — e.g. CPG, financial services, life sciences, industrials]
- **Geographic focus:** [TBD — e.g. global with US/EU primary, NL/BE secondary]
- **Time horizon for analysis:** [TBD — e.g. 12-quarter forward view default]
- **Default depth:** [TBD — standard (8-12 pages of notes) or extended (15-25 pages)]

## Source hierarchy

In order of authority — every claim should be backed by a source as high in this list as available:

1. SEC filings (10-K, 10-Q, proxy, 8-K) for US public companies
2. Annual reports and regulatory filings for non-US public companies
3. Earnings call transcripts
4. Investor presentations (treat with healthy skepticism)
5. Industry analyst reports (Gartner, McKinsey, BCG, Bain, IBISWorld)
6. Quality business journalism (FT, WSJ, Bloomberg, Reuters, The Economist)
7. Trade publications
8. Company press releases (facts only, filter the spin)
9. Academic research for structural / macro context

**Skip:** [TBD — e.g. SEO listicles, marketing content, promotional analyst pieces]

## Skepticism rules

- **What I distrust by default:** [TBD — e.g. management TAM claims, "AI-first" branding without evidence, sell-side price targets]
- **Where I demand triangulation:** [TBD — e.g. market share, growth rates, margin claims need ≥2 independent sources]
- **Insiders I weight heavily:** [TBD — e.g. competitor earnings call commentary, ex-employee Glassdoor patterns, customer reviews]

## Voice and output preferences

- **Tone:** [TBD — e.g. direct, confident, operator's-test (every insight must change a decision)]
- **Hedge tolerance:** [TBD — e.g. low — state directional conclusions when evidence supports them]
- **Style hallmarks:** [TBD — e.g. lead with "so what", mechanisms over conclusions, falsify own thesis]
- **What I never want in output:** [TBD — e.g. "it's worth noting", "interestingly", "in conclusion", generic AI commentary]

## Default output format

Research notes are markdown files saved to: `[TBD — e.g. /mnt/user-data/outputs/ or ~/Praexo/Research/]`

File naming: `[TBD — e.g. praexo-research_[company-or-sector]_[YYYY-MM-DD].md]`

Notes structure: see `references/research-notes-template.md` (frozen — do not edit unless re-running cold-start)

## Downstream consumers

These notes feed into:

- [TBD — e.g. `/praexo-report:full-report` for Praexo Word docs]
- [TBD — e.g. AnswerRocket discovery briefs]
- [TBD — e.g. M&A memos, advisory work]

## Custom skip / focus lists

- **Always include in research:** [TBD — e.g. AI strategy assessment, even for non-tech sectors]
- **Skip unless asked:** [TBD — e.g. ESG deep-dive, currency hedging analysis]
