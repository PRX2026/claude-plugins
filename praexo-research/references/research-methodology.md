# Research Methodology — Six-Pass

Every skill in this plugin that does multi-section research follows this methodology. Single-section skills (value-chain-map, ai-disruption-scan) use a focused subset.

## Why six passes

Each pass builds context for the next. Searching for everything at once produces shallow results because you don't yet know what to ask. Sequential passes let later searches build on earlier findings.

Budget roughly 50-75 web searches total for a standard-depth research note. Adjust based on the practice profile's "default depth" setting.

## Pass 1 — Foundational context (10-15 searches)

**Goal:** Establish what the subject does, key facts, recent trajectory.

```
[subject] business overview
[subject] revenue [latest year]
[subject] annual report [latest year]
[subject] 10-K filing
[subject] earnings Q[latest] transcript
[subject] market cap employees
[subject] CEO leadership
[subject] recent news
[industry] market size growth rate
[industry] lifecycle stage
```

**What to extract:**
- Revenue, margins, employee count, market cap (last 3-5 years)
- Business segment breakdown
- Key products/services and customer types
- Major events in last 12 months
- Industry growth rate and lifecycle stage

## Pass 2 — Value chain & competitive landscape (10-15 searches)

**Goal:** Map the industry structure and where the subject sits in it.

```
[industry] value chain structure
[industry] supply chain
[industry] profit pool distribution
[industry] barriers to entry
[industry] switching costs
[industry] regulatory requirements
[subject] competitors
[subject] market share
[subject] vs [competitor]
[industry] consolidation trends
```

**What to extract:**
- Full value chain layers (inputs → end customer)
- Margin distribution across layers
- Lock-in mechanisms
- Market share data and concentration ratios
- Top 3-5 competitors with their relative positioning

## Pass 3 — Financial deep-dive (8-12 searches)

**Goal:** Understand the financial engine in detail.

```
[subject] revenue growth drivers
[subject] segment revenue breakdown
[subject] gross margin trend
[subject] operating expenses breakdown
[subject] unit economics
[subject] customer acquisition cost
[subject] net revenue retention
[subject] capex R&D spending
[subject] capital allocation
[subject] M&A history
```

**What to extract:**
- Revenue decomposition: volume, price, mix, new products, geography
- Margin trends (gross, operating, FCF) over 3-5 years
- Unit economics (CAC, LTV, payback, retention)
- Capital allocation history: M&A, R&D, capex, buybacks, dividends
- Balance sheet structure

**Use `web_fetch` on:** latest 10-K, latest earnings call transcript, investor day deck

## Pass 4 — Strategy & forward-looking (8-12 searches)

**Goal:** Stated strategy, observable strategy, and the gap between them.

```
[subject] strategy investor day
[subject] CEO interview strategy
[subject] capital allocation priorities
[subject] R&D focus areas
[subject] expansion plans
[subject] insider ownership
[subject] executive compensation
[subject] proxy statement
[subject] board directors
```

**What to extract:**
- Stated strategy from management
- Where money actually goes (M&A + R&D + capex pattern)
- The say-do ratio: targets set 3-5 years ago vs. outcomes
- Executive comp structure (reveals what behavior is rewarded)
- Insider ownership and management tenure

**Use `web_fetch` on:** latest proxy statement, latest investor day transcript, archived investor day from 3-5 years ago for say-do comparison

## Pass 5 — AI & disruption (6-10 searches)

**Goal:** AI as external threat and internal opportunity.

```
[subject] AI strategy artificial intelligence
[subject] AI investment
[subject] technology stack
[subject] data strategy
[industry] AI disruption
[industry] AI startups
[industry] AI funding
[industry] AI native companies
AI replacing [industry function]
[industry] automation case study
```

**What to extract:**
- Subject's stated AI strategy and investments
- AI-native disruptors targeting this value chain (named, with funding)
- Most-amenable processes for AI automation
- Data assets that could power AI applications
- Industry-specific AI case studies (deployments, not announcements)
- Organizational readiness signals (hires, partnerships)

## Pass 6 — Macro & risk (6-10 searches)

**Goal:** Identify risks across economic, geopolitical, regulatory, and secular categories.

```
[subject] risk factors 10-K
[industry] regulatory changes [latest year]
[industry] tariffs trade policy
[subject] supply chain risk
[subject] geographic exposure
[subject] FX currency exposure
[subject] interest rate sensitivity
[industry] demographic trends
[industry] ESG sustainability regulation
[country where operates] political risk
```

**What to extract:**
- Company's own risk factor disclosures (10-K Item 1A)
- Regulatory changes pending or recently enacted
- Supply chain concentration
- Currency mismatches between revenue and cost
- Interest rate sensitivity
- Geopolitical exposure
- Demographic / behavioral trend impact

**Don't stop at the 10-K** — the most interesting risks are usually the ones management hasn't yet identified. Cross-reference with macro research and industry trend analysis.

## When to stop researching

You're done with the research phase when:

- You can answer the five core questions (see `research-notes-template.md`)
- Every major section has at least one primary-source citation
- Every major numerical claim has triangulation across at least two sources
- The "Open questions" list is short and specific

If those conditions aren't met after the six passes, do targeted follow-up searches on the gaps. Don't move to writing with structural holes.
