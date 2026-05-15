---
name: ai-disruption-scan
description: Focused assessment of AI as both external threat and internal opportunity for a company or sector. Outputs ranked use case list, AI-native disruptor map, incumbent readiness signals, and data asset valuation. Reads the practice profile for sector context and voice preferences. Use when the user says "AI scan on [company]", "AI disruption analysis", "where is AI changing [industry]", or asks specifically about AI exposure without wanting a full research note. Faster than full company research — focused on the AI dimension only.
---

# AI Disruption Scan — Praexo methodology

Targeted analysis of AI as a force on a specific company or sector. Two-sided: external threat (who attacks the incumbent from outside) and internal opportunity (where the incumbent can apply AI to defend or extend).

## Pre-flight check

1. Read `~/.claude/plugins/config/praexo-research/CLAUDE.md`
2. Read `references/source-quality-rules.md`
3. **If the user uploaded an AI value cases reference file** (e.g. `ai-value-cases_praexo.md`), read it — use its taxonomy when ranking use cases

## Inputs

- **Subject** (required — company or sector)
- **Time horizon** (optional — default 24 months for opportunities, 36 months for disruption threat)

## Research focus

```
[subject] AI strategy artificial intelligence
[subject] AI investment machine learning
[subject] AI hiring head of AI chief AI officer
[subject] technology stack data infrastructure
[subject] data strategy
[subject] digital transformation case study
[industry] AI disruption
[industry] AI startups Crunchbase
[industry] AI funding [year]
[industry] AI native companies
AI replacing [industry function]
[industry] automation McKinsey BCG
[subject] partnerships OpenAI Anthropic Google
```

## Output structure

```markdown
# AI Disruption Scan — [Subject]

**Analyst:** [Marc Leon / Praexo]
**Date:** [YYYY-MM-DD]
**Horizon:** [24m opportunity / 36m disruption threat]

## Headline

[One paragraph: the net AI thesis. Is this subject a winner, loser, or stable
under AI pressure over the horizon? What's the single most important reason?]

## External disruption threat

### AI-native attackers

| Company | Funding | Targets which layer | Stage | Threat level |
| --- | --- | --- | --- | --- |
| [name] | [$ raised] | [layer of value chain] | [seed / A / B / scaled] | [low / med / high] |

(3-7 named companies. If you can't find specifics, say so — don't pad.)

### Disruption vectors

For each vector (typically 2-4):
- **What's being unbundled:** [specific process / role / margin pool]
- **Mechanism:** [why AI does this 10x better or cheaper]
- **Time to material impact:** [months / quarters]
- **Incumbent's natural defense:** [scale? data? relationships? regulation?]

## Internal opportunity

### Top use cases ranked

| # | Use case | Process | Impact | Feasibility | ROI window | Priority |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | [name] | [where applied] | [cost % / revenue % / quality bps] | [low / med / high] | [<6m / 6-18m / 18m+] | [P0 / P1 / P2] |

(5-8 use cases. Rank by Impact × Feasibility, not just by enthusiasm. If you have access to a value-cases reference file, use its taxonomy.)

### Data assets

What proprietary data does the subject hold that could power AI applications?

- **Asset:** [what data]
- **Volume / quality:** [rough scale, freshness, structured vs. unstructured]
- **Defensibility:** [is it actually proprietary, or replicable?]
- **Activation status:** [used today? sitting dormant? not yet collected?]

### Organizational readiness signals

- [Specific signals: AI hires, partnerships, internal initiatives, technical infrastructure
   investment, recent product launches with AI in them]

## What most people get wrong

[One paragraph: the popular narrative about AI on this subject vs. the structural reality. Be the contrarian where the evidence supports it.]

## Open questions

[What you couldn't resolve from public sources.]

## Sources

[Every source cited.]
```

## Writing rules

- **Specific capabilities, not "AI"** — name the capability (LLMs for X, computer vision for Y, embeddings for Z)
- **Specific processes, not "the business"** — name the process being changed
- **Specific outcomes, not "value"** — cost %, revenue %, quality bps, cycle-time reduction
- **Be honest about timing** — most AI claims are 3 years late on adoption curve. Use real evidence (deployments, case studies) not announcements.

## Output

1. Save to profile-defined output path
2. Filename: `praexo-aiscan_[subject-slug]_[YYYY-MM-DD].md`
3. Present and give a 2-sentence summary: net AI thesis, and the single use case the subject should run tomorrow

## What not to do

- Don't write generic AI commentary ("AI will transform...") — every claim is specific or it gets cut
- Don't list every AI startup in the space — top 5-7 by relevance is enough
- Don't conflate announcement with deployment — flag the difference
- Don't ignore the data asset question — most AI value lives there, not in the model choice
