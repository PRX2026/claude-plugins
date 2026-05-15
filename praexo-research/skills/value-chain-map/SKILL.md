---
name: value-chain-map
description: Focused value chain analysis for a company or sector. Maps every layer from inputs to end customer, identifies where margin and power concentrate, flags structural bottlenecks. Standalone skill — use when the user only needs the value chain, not a full company / sector research note. Reads the practice profile for source preferences. Use when the user says "map the value chain", "where does the money flow", "profit pool analysis", or asks specifically about industry structure without wanting a full research note.
---

# Value Chain Map — Praexo methodology

You are producing a focused value chain map. Tighter than a full research note — just the structure of the industry / company supply chain and where economic value sits.

## Pre-flight check

1. Read `~/.claude/plugins/config/praexo-research/CLAUDE.md`
2. Read `references/source-quality-rules.md`

No template file needed — output structure is defined below.

## Inputs

- **Subject** (required — a company OR a sector)
- **Specific question** (optional — e.g. "where will margin compress in the next 3 years", "which layer is most vulnerable to AI")

## Research focus

Targeted searches, not the full six-pass:

```
[subject] value chain structure
[subject] supply chain overview
[subject] profit pool distribution
[subject] gross margin by segment
[subject] barriers to entry
[subject] switching costs
[subject] contract terms typical
[subject] regulatory requirements licenses
[subject] supplier relationships
[subject] customer concentration
[subject] consolidation trends
[subject] market share leaders
```

Use industry analyst reports, trade association publications, and 10-K supplier/customer disclosures.

## Output structure

```markdown
# Value Chain Map — [Subject]

**Analyst:** [Marc Leon / Praexo]
**Date:** [YYYY-MM-DD]

## The headline

[One paragraph. Where does economic value concentrate today, and what's
the directional thesis on where it moves in the next 3-5 years. Operator's test.]

## Layer-by-layer map

For each layer (typically 5-8):

### [Layer name — e.g. "Raw material suppliers"]

- **What they do:** [one sentence]
- **Who plays:** [3-5 named examples + concentration level]
- **Typical gross margin:** [range, with source]
- **Revenue model:** [transactional / contract / subscription / commodity / etc.]
- **Power dynamics:** [who has pricing power vs. whom, and why]
- **Moat type:** [scale / regulation / IP / network effects / switching costs / none]
- **Trend:** [strengthening / stable / weakening — with the mechanism]

## Profit pool distribution

| Layer | % of total industry revenue | % of total industry profit | Trend |
| --- | --- | --- | --- |
| [layer 1] | [%] | [%] | [↑ / → / ↓] |
| [layer 2] | [%] | [%] | [↑ / → / ↓] |

**Insight:** [Where does profit concentrate vs. where revenue sits, and what does that reveal about power?]

## Bottlenecks and single points of failure

[2-4 specific structural features that create risk or opportunity — supplier concentration, regulatory chokepoints, capacity constraints, data monopolies, etc.]

## Where AI changes the map

[For each layer, what AI does to it. Be specific — which capability, applied to which process, with what effect on margin or power.]

## Open questions

[Things you couldn't resolve from public sources. Be honest.]

## Sources

[Every source cited, with URL and access date.]
```

## Writing rules

- One layer = one diagnosis. Don't restate the layer name across multiple bullets.
- Margins need numbers. "High margin" without a range is useless.
- Power dynamics need a mechanism. "X has power over Y" isn't enough — *why* and *how durable*.
- Lead the headline with the directional thesis, not the structural description.

## Output

1. Save to profile-defined output path
2. Filename: `praexo-valuechain_[subject-slug]_[YYYY-MM-DD].md`
3. Present and give a 2-sentence summary: where profit concentrates today, and the one layer where the map will look most different in 3 years

## What not to do

- Don't produce a full company research note — that's `/praexo-research:company-research`
- Don't list players without margin data — names without numbers is industry trivia
- Don't treat the value chain as static — every map should have a directional vector
