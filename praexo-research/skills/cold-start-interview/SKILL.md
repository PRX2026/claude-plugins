---
name: cold-start-interview
description: Interview the user about their analytical practice and write the praexo-research practice profile. Run once when first installing the plugin, or re-run when the practice shifts materially (new sector focus, new output destination, different downstream use case). Captures sectors of focus, source hierarchy preferences, skepticism rules, voice preferences, output format, and downstream consumers. Takes 10-15 minutes. Every other skill in this plugin reads from the profile this writes.
---

# Cold-start interview — Praexo Research

You are interviewing the user to build their research practice profile. The output is a filled `CLAUDE.md` at `~/.claude/plugins/config/praexo-research/CLAUDE.md`.

## How to run

Walk the user through the sections below **one at a time**. Conversational, not form-style.

- If the user gives a thin answer, ask one follow-up.
- If they say "skip" or "later", write `[TBD — user deferred]` and move on.
- If they upload reference material (a prior research note, a style guide, the existing `soul_praexo.md`), read it and propose answers — let them confirm or correct.

**Offer a quick-start option upfront:** a 3-minute version that fills only identity, sectors of focus, default output location, and voice preferences. Tell them they can re-run the interview later for the full version.

## Sections to cover

### 1. Identity and use case

- Their name / firm
- Primary use case for these research notes (BD prep? Coursework? Advisory? M&A?)
- How often they run research (weekly? per-deal? per-class-session?)

### 2. Analytical lens

- Sectors they actually focus on — be specific, "B2B" doesn't count
- Geographic focus (where they operate, where their targets sit)
- Time horizon they care about (12-quarter? 5-year? cycle-aware?)
- Default depth — quick notes or extended deep-dive

### 3. Source hierarchy

- Confirm or modify the default hierarchy (SEC → annual reports → transcripts → investor decks → analyst reports → journalism → trade pubs → press releases → academic)
- Specific sources they trust above the default (e.g. a sector trade publication they read religiously)
- Sources they refuse to cite (e.g. promotional content, specific outlets they distrust)

### 4. Skepticism rules

- What they distrust by default — be concrete. "Management TAM claims" is good, "marketing fluff" is too vague.
- Where they demand triangulation (market share? growth rates? margins?)
- Insiders or signals they weight heavily (ex-employee patterns? competitor commentary? specific analysts?)

### 5. Voice and output preferences

- Tone (direct? consultative? academic?)
- Hedge tolerance (when do they want a stated conclusion vs. balanced view?)
- Style hallmarks they care about (lead with "so what"? mechanisms over conclusions? operator's test?)
- **Phrases they never want to see in output** — this is the most useful field. Ask explicitly. ("It's worth noting", "interestingly", "in conclusion" are common offenders.)

### 6. Output format

- Where notes should be saved (absolute path or directory)
- File naming convention
- Whether they want a frozen template (recommended) or flexible structure per note

### 7. Downstream consumers

- What gets built from these notes? (Praexo reports? BD briefs? Memos?)
- Is there a specific format the downstream consumer expects? (e.g. praexo-report expects a specific section order)

### 8. Custom focus / skip lists

- Topics to **always** include (e.g. AI disruption assessment for every company, even non-tech)
- Topics to **skip** unless explicitly asked (e.g. ESG deep dive, currency hedging)

## Output

When the interview is complete:

1. Show the user a draft of the filled `CLAUDE.md` and ask for confirmation
2. On confirmation, write to `~/.claude/plugins/config/praexo-research/CLAUDE.md`
3. Show a 5-line summary of what was captured
4. List the skills now available:
   - `/praexo-research:company-research` — deep-dive on a named company
   - `/praexo-research:sector-research` — sector / industry analysis
   - `/praexo-research:value-chain-map` — focused value chain mapping
   - `/praexo-research:ai-disruption-scan` — AI disruption assessment for a company or sector
5. Remind them the profile is plain markdown and editable anytime

## What not to do

- Don't ask all questions at once
- Don't write to disk until the user confirms the draft
- Don't invent answers — `[TBD]` is honest, made-up content is not
- Don't push the user to fill every section — quick-start is a legitimate path
