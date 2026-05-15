# Source Quality Rules

Every skill in this plugin enforces these rules. They override the practice profile only when the profile is missing a relevant rule.

## Source hierarchy (default)

In order of authority:

1. **SEC filings** (10-K, 10-Q, proxy, 8-K) for US public companies
2. **Annual reports and regulatory filings** for non-US public companies (EDGAR equivalents: SEDAR for Canada, AFM/AMF for NL/FR, BaFin for Germany, JFSA for Japan, etc.)
3. **Earnings call transcripts** — management commentary and analyst Q&A
4. **Investor presentations / investor days** — management's framing (skepticism warranted)
5. **Industry analyst reports** — Gartner, Forrester, IDC for tech; IBISWorld, Euromonitor for sector data; McKinsey, BCG, Bain for strategic frameworks
6. **Quality business journalism** — FT, WSJ, Bloomberg, Reuters, The Economist, Nikkei
7. **Trade publications** — sector-specific expertise
8. **Company press releases** — factual data only, filter the spin
9. **Academic research** — for structural / macro context

## What to fetch vs. what to skim

**Use `web_fetch` (full page) on:**
- 10-K / annual report (the latest filing)
- Most recent earnings call transcript
- Investor day deck or transcript (latest)
- Long-form analyst report when the snippet shows it has the data point you need
- Specific articles where the snippet promises a number or quote you need to verify

**Skim search snippets only when:**
- The snippet already gives you the data point
- The source is obviously low-quality (listicle, SEO content)
- You're triangulating a fact you already have from a better source

## Triangulation rule

No single source anchors a major conclusion. Specifically:

- **Market size / TAM:** require at least 2 independent estimates, ideally one analyst report + one regulator/industry body
- **Market share:** require 2 sources, with at least one not derived from the company's own disclosure
- **Growth rates:** require historical (3-5y) confirmation from filings + forward estimate from analyst or industry body
- **Margin claims:** must reconcile to filing-level financials, not just analyst commentary
- **Competitive positioning:** require triangulation from at least 2 of: filings, competitor filings, analyst reports, customer reviews

## What never to cite

- SEO listicles ("Top 10 Companies in X")
- AI-generated content farms
- Promotional / marketing pieces (when used analytically, not as evidence of positioning)
- Press releases as evidence of strategic intent (cite the action, not the announcement)
- Forum posts / Reddit / unverified commentary
- Wikipedia as a primary source (fine as a starting point to find the real source)

## Recency rules

- **Strategic / competitive dynamics:** prioritize sources from the last 12 months. Older sources for strategy are usually misleading.
- **Financial data:** use the latest filings. If the latest filing is older than 6 months, search for the most recent interim report.
- **Structural industry analysis:** older authoritative sources are fine — Porter's Five Forces analysis of an industry from 5 years ago may still be valid.
- **AI / technology positioning:** absolute recency required. 12-month-old AI coverage is stale.

## Source tracking

Maintain a running source list throughout research. Every source that informs a claim in the final notes goes in the source log with:

- Author / publisher
- Title
- URL
- Access date (today's date in YYYY-MM-DD)
- Source tier (primary / secondary / tertiary)

If you cite a fact, the source must be in the log. If a source is in the log, it must be cited in the notes. No orphan sources, no orphan claims.

## Skepticism defaults

Apply these by default unless the practice profile overrides:

- **Management TAM claims:** ignore. Recompute from bottom-up if it matters.
- **"AI-first" branding without engineering evidence:** treat as marketing
- **Sell-side price targets:** note them, don't anchor on them
- **Analyst day targets > 3 years out:** track them, but they rarely survive a CEO change
- **Customer testimonials in vendor case studies:** discount heavily

## When sources conflict

If two credible sources disagree on a fact:

1. Flag the disagreement explicitly in the notes
2. Identify which source is closer to the underlying record (filing > analyst summary)
3. State your own view and the reasoning
4. Add the discrepancy to "Open questions" if it matters and can't be resolved
