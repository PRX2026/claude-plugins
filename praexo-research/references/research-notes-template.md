# Research Notes Template (FROZEN)

This is the output structure for `/praexo-research:company-research` and `/praexo-research:sector-research`. Do not modify unless re-running cold-start with explicit user permission.

The structure is deliberately constrained so that downstream consumers (`praexo-report`, BD briefs, M&A memos) can parse it predictably.

---

## Header block

```markdown
# Praexo Research Notes — [Subject]

**Analyst:** [Marc Leon / Praexo]
**Date:** [YYYY-MM-DD]
**Subject:** [Company or sector]
**Sector:** [if subject is a company]
**Depth:** [quick / standard / extended]
**Focus areas:** [optional — if user requested specific focus]
**Output language:** English
```

## One-page summary

Five questions, answered in 3-5 sentences each. This is the highest-leverage section — many readers won't go further.

```markdown
## Summary

### 1. What does this subject actually do, and how does it make money?
[3-5 sentences. No hedging. Specific revenue model, specific customer type.]

### 2. Where does economic value concentrate in the value chain?
[3-5 sentences. Which layer captures the most margin and why.]

### 3. What are the 2-3 variables that drive 80% of the financial outcome?
[3-5 sentences. The actual operating levers, not the marketing narrative.]

### 4. How does AI change this subject over the next 24-36 months?
[3-5 sentences. External threat AND internal opportunity. Specific, not generic.]

### 5. What is the single most important thing most analysts get wrong about this subject?
[3-5 sentences. The contrarian view, with the evidence that supports it.]
```

## Company / sector overview

(For company subjects)

```markdown
## Company overview

**Business model in one paragraph:** [What they sell, to whom, on what economic model.]

**Financial snapshot:**

| Metric | Latest | Y-1 | Y-2 | Y-3 | Y-5 |
| --- | --- | --- | --- | --- | --- |
| Revenue | | | | | |
| Gross margin % | | | | | |
| Operating margin % | | | | | |
| FCF margin % | | | | | |
| Employees | | | | | |
| Market cap / EV | | | | | |

**Segments:** [breakdown by segment with revenue and margin if available]

**Recent material events** (last 12 months): [bulleted list with date and source]

**Industry context:** [size, growth rate, lifecycle stage, structural features]
```

(For sector subjects, replace with sector size, growth, structure, top 10 players.)

## Value chain analysis

```markdown
## Value chain

[2-paragraph headline: where value concentrates, where it's moving]

### Layer-by-layer

For each of 5-8 layers:

#### [Layer name]
- What they do, who plays, typical margins, power dynamics, moat, trend

### Profit pool distribution

| Layer | % industry revenue | % industry profit | Trend |
| --- | --- | --- | --- |

### Bottlenecks and single points of failure

[2-4 structural features]
```

## Growth & margin levers

```markdown
## Growth & margin levers

[2-paragraph headline: the financial engine in plain language]

### Revenue decomposition

[Volume / price / mix / new products / geography breakdown]

### Margin trends

[Gross, operating, FCF trajectories with the mechanisms behind them]

### Unit economics (where applicable)

[CAC, LTV, payback, retention]

### Leading indicators

| Indicator | Current | Watch | Alert | Why it matters |
| --- | --- | --- | --- | --- |

### What management is managing the business against

[From earnings calls — the 2-3 metrics that get repeated quarter after quarter]
```

## Strategy decode

```markdown
## Strategy decode

[2-paragraph headline: stated strategy, observable strategy, the gap]

### Stated strategy

[From investor day / earnings calls / CEO interviews]

### Observable strategy

[Where money actually goes — M&A, R&D, capex pattern]

### Say-do ratio

[Targets set 3-5 years ago vs. outcomes — be specific]

### Management quality signals

- Insider ownership: [%]
- CEO/CFO tenure: [years]
- Comp structure: [what behavior is rewarded]
- Track record on capital allocation: [hit rate on M&A, R&D returns]
```

## Competitive dynamics

```markdown
## Competitive dynamics

[2-paragraph headline: subject's positioning and the likely competitive moves]

### Positioning

| Dimension | Subject | Comp A | Comp B | Comp C |
| --- | --- | --- | --- | --- |

### Recent competitive moves (last 12-18 months)

[Specific moves by competitors that signal strategic direction]

### New entrants and adjacent threats

[Startups + adjacent players that could expand in]
```

## AI disruption & transformation

```markdown
## AI disruption & transformation

[2-paragraph headline: net AI thesis]

### External disruption threat

[Named AI-native companies with funding and target layer]

### Internal opportunity — ranked use cases

| # | Use case | Process | Impact | Feasibility | ROI window | Priority |

### Data assets

[Proprietary data the subject holds, defensibility, activation status]

### Organizational readiness

[AI hires, partnerships, internal initiatives]
```

## Risk assessment

```markdown
## Risk assessment

[2-paragraph headline: top 3 risks ranked by likelihood × impact]

### Master risk matrix

| Risk | Category | Likelihood | Impact | Trend | Hedge available |
| --- | --- | --- | --- | --- | --- |

Categories: Economic / Geopolitical / Regulatory / Technological / Secular

### Underwriting view

[The risk(s) that would actually change the investment or operating thesis]
```

## Open questions

```markdown
## Open questions

[Specific things you couldn't resolve from public sources. Be honest about gaps.
This list should be short — 3-7 items. If it's longer, the research wasn't deep enough.]
```

## Source log

```markdown
## Sources

[Every source cited, with URL and access date. Group by primary / secondary / tertiary.]

### Primary sources
- [Filing / transcript / company disclosure]

### Secondary sources
- [Analyst reports, business journalism]

### Tertiary sources
- [Trade publications, press releases]
```
