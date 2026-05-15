# Praexo Plugins — Architecture & Usage Guide

**Version:** v0.1
**Status:** Reference implementation ready to install and refine
**Author:** Marc Leon / Praexo

This guide explains the two-plugin architecture, why it's split the way it is, how to install and run both plugins, and how to evolve them as you use them.

---

## The architecture

You have two plugins in one marketplace folder:

```
praexo-plugins/
├── .claude-plugin/
│   └── marketplace.json          ← lists both plugins
├── praexo-research/               ← analysis plugin
│   ├── .claude-plugin/plugin.json
│   ├── CLAUDE.md                  ← practice profile template
│   ├── skills/
│   │   ├── cold-start-interview/
│   │   ├── company-research/
│   │   ├── sector-research/
│   │   ├── value-chain-map/
│   │   └── ai-disruption-scan/
│   └── references/
│       ├── research-methodology.md
│       ├── research-notes-template.md
│       └── source-quality-rules.md
└── praexo-report/                 ← document generation plugin
    ├── .claude-plugin/plugin.json
    ├── CLAUDE.md
    ├── skills/
    │   ├── cold-start-interview/
    │   ├── full-report/
    │   └── executive-brief/
    ├── references/
    │   ├── report-framework.md
    │   └── praexo-brand-spec.md
    └── assets/
        └── (praexo-logo.png — you provide)
```

### Why two plugins, not one

**The old `Research-Report-Skill_willie.md`** is a single monolithic skill that does everything: research methodology, voice, report structure, brand styling, .docx generation. That works for a Cowork file system, but it has three problems as a plugin:

1. **Can't reuse the research.** If you want to run Praexo research and then feed it into a BD discovery brief (not a 60-page Word doc), the monolithic skill doesn't let you. The research output is locked inside the report.

2. **Can't reuse the report shell.** If a junior analyst gives you research notes they wrote by hand, you can't easily produce a Praexo-branded report from them. The brand styling is locked inside the research.

3. **One cold-start can't capture both.** Research preferences (sectors, source hierarchy, skepticism rules) are different from report preferences (logo path, voice intensity, page count). One interview becomes long and confused.

**Splitting them solves all three.** The research plugin outputs structured markdown notes that can feed any downstream consumer. The report plugin accepts any well-structured markdown input. Each has its own focused cold-start.

### The trade-off you accept

The cost of splitting: you run two commands instead of one for the full Praexo workflow.

```
/praexo-research:company-research [Company]
   → produces praexo-research_[Company]_[date].md

/praexo-report:full-report
   → consumes the markdown, produces .docx
```

In practice this is a feature, not a bug. The research output is usable by itself — you'll often want to read or share the markdown notes without bothering to render a Word doc. And when you do render the doc, you can re-run the report skill with different voice intensity or length without re-doing the research.

---

## What's in each plugin

### `praexo-research`

**Five skills:**

| Skill | Purpose |
| --- | --- |
| `cold-start-interview` | Captures analytical practice — sectors, source hierarchy, skepticism rules, voice preferences, output format, downstream consumers |
| `company-research` | Full six-pass deep research on a named company. Output is structured markdown notes. |
| `sector-research` | Industry analysis without single-company focus. Same six-pass shape, sector-level. |
| `value-chain-map` | Focused value chain mapping — tighter than full research, just the structure and profit pool |
| `ai-disruption-scan` | Focused AI threat + opportunity assessment. Faster than full research, AI-only |

**Three reference files** (read by every skill):

- `research-methodology.md` — the six-pass methodology, search queries by pass
- `research-notes-template.md` — frozen output structure (downstream consumers depend on it)
- `source-quality-rules.md` — what to cite, what to skip, triangulation rules

### `praexo-report`

**Three skills:**

| Skill | Purpose |
| --- | --- |
| `cold-start-interview` | Captures report preferences — firm identity, logo path, voice intensity, special box preferences, quality gates |
| `full-report` | 55-65 page Praexo report with 12 sections, 9 required tables, Emphasis + Summary boxes |
| `executive-brief` | 8-12 page compressed brief, same brand, sharper voice |

**Two reference files:**

- `report-framework.md` — section-by-section spec for the full report
- `praexo-brand-spec.md` — colors, fonts, headings, tables, special boxes

**One asset:**

- `assets/praexo-logo.png` — you provide this before running any report skill

---

## Marketplace metadata

The marketplace catalog at `.claude-plugin/marketplace.json` is what users browse when they add your repo. It's worth filling out properly — the difference between sparse and rich metadata is the difference between "install one of these I guess" and "install the one I actually need."

### Required fields

Minimum viable `marketplace.json`:

```json
{
  "name": "praexo",
  "owner": { "name": "Marc Leon", "email": "marc@praexo.com" },
  "plugins": [
    { "name": "praexo-research", "source": "./praexo-research" }
  ]
}
```

- **`name`** — kebab-case identifier for the marketplace itself. Becomes the `@scope` in install commands (`/plugin install praexo-research@praexo`). Reserved names include `claude-code-marketplace`, `claude-plugins-official`, `anthropic-marketplace` — anything that impersonates Anthropic gets blocked.
- **`owner`** — at minimum a `name`. Email and URL are optional but appear when users browse.
- **`plugins`** — array of at least one plugin entry with `name` and `source`.

### Recommended fields

What this marketplace uses (see `.claude-plugin/marketplace.json`):

```json
{
  "$schema": "https://json.schemastore.org/claude-code-marketplace.json",
  "name": "praexo",
  "owner": { "name": "Marc Leon", "email": "marc@praexo.com", "url": "https://praexo.com" },
  "metadata": {
    "description": "Praexo — research, reporting, and advisory plugins for Claude...",
    "version": "0.1.0",
    "pluginRoot": "./"
  },
  "homepage": "https://praexo.com",
  "repository": "https://github.com/praexo/praexo-plugins",
  "keywords": ["research", "advisory", "private-equity", ...],
  "plugins": [ ... ]
}
```

Notable fields:

- **`$schema`** — points to the public schema. Lets VS Code and other editors validate as you type.
- **`metadata.description`** — top-level marketing description. Shown when users browse marketplaces.
- **`metadata.version`** — track changes to the catalog itself (separate from individual plugin versions).
- **`metadata.pluginRoot`** — base path for plugin sources. Set to `"./"` if plugins sit at the repo root; set to `"./plugins"` if you nest them. Lets you shorten `"source": "./praexo-research"` to `"source": "praexo-research"`.
- **`homepage` / `repository`** — project URLs. Shown in browse view.
- **`keywords`** — discoverability terms.

### Per-plugin entry — full schema

Each entry in the `plugins` array can include any field from the plugin manifest schema plus four marketplace-specific fields:

```json
{
  "name": "praexo-research",
  "source": "./praexo-research",
  "description": "Deep research and analysis...",
  "version": "0.1.0",
  "author": { "name": "Marc Leon", "email": "marc@praexo.com" },
  "homepage": "https://praexo.com/plugins/research",
  "license": "MIT",
  "category": "research",
  "tags": ["research", "company-analysis", "sector-analysis"],
  "keywords": ["deep-research", "industry-analysis", "due-diligence"],
  "strict": true
}
```

The four marketplace-specific fields:

- **`source`** — where to fetch the plugin. Can be a relative path (`./praexo-research`), a GitHub object (`{ "source": "github", "repo": "owner/repo" }`), or a URL.
- **`category`** — high-level grouping. Common values: `development`, `productivity`, `research`, `security`, `data`.
- **`tags`** — fine-grained labels for filtering and discovery.
- **`strict`** — defaults to `true`. When `true`, the plugin's own `plugin.json` is the source of truth and the marketplace entry only adds extras. When `false`, the marketplace entry can fully define the plugin (useful if you're curating someone else's repo with custom config). Leave at `true` for first-party plugins.

The remaining fields (`description`, `version`, `author`, `homepage`, `license`, `keywords`) duplicate what's in the plugin's own `plugin.json`. **They override the plugin's version when shown in the browse view** — so keeping them in sync matters. Easiest path: bump both `marketplace.json` and the plugin's `plugin.json` version when you ship a change.

### Source types

```json
// Relative path (same repo)
"source": "./praexo-research"

// Different GitHub repo
"source": { "source": "github", "repo": "praexo/research-plugin" }

// Pinned to a specific commit (for production reproducibility)
"source": { "source": "github", "repo": "praexo/research-plugin", "ref": "v0.1.0", "sha": "abc123..." }

// Arbitrary git URL
"source": { "source": "url", "url": "https://gitlab.com/team/plugin.git" }
```

For your case (both plugins in one repo) relative paths are the right choice.

### Validation

Run `claude plugin validate .` or `/plugin validate .` from the marketplace root. The validator checks:

- JSON syntax
- Required fields (`name`, `owner`, `plugins`, and per-plugin `name`+`source`)
- Plugin name kebab-case (uppercase / spaces / underscores fail)
- Skill frontmatter syntax across all plugins
- Hook configuration syntax

Common errors:

- `"No marketplace description provided"` — add `metadata.description`
- `"Plugin name X is not kebab-case"` — rename to lowercase + hyphens only
- `"Source path does not exist"` — typo in the `source` field or wrong `pluginRoot`

### What users see when they browse

When someone runs `/plugin marketplace add praexo/praexo-plugins`, Claude Code fetches `marketplace.json` and displays:

- The marketplace `name` and `metadata.description` in the header
- Each plugin's `name`, `description`, `category`, and `tags` in the browse list
- The owner's `name` and contact info

If `metadata.description` is missing, the browse view feels generic. If per-plugin `description` is missing or vague, users skim past. Treat these as marketing copy, not documentation.

---

## Install

### From local folder (testing)

Both plugins live in one marketplace folder. Install both from one command sequence:

```bash
cd /path/to/praexo-plugins
```

In Claude Code:

```
/plugin marketplace add ./
/plugin install praexo-research@praexo
/plugin install praexo-report@praexo
```

Then run the cold-start interviews in either order:

```
/praexo-research:cold-start-interview
/praexo-report:cold-start-interview
```

Before running any report skill, copy your Praexo logo to:

```
/path/to/praexo-plugins/praexo-report/assets/praexo-logo.png
```

### From GitHub (sharing across machines)

Push the `praexo-plugins/` folder to a private GitHub repo:

```bash
cd /path/to/praexo-plugins
git init
git add .
git commit -m "Initial praexo-plugins v0.1"
gh repo create praexo/praexo-plugins --private --source=. --push
```

Then on any machine:

```
/plugin marketplace add praexo/praexo-plugins
/plugin install praexo-research@praexo
/plugin install praexo-report@praexo
```

The plugin cache lives at `~/.claude/plugins/cache/`. The practice profiles (filled-in CLAUDE.md) live at `~/.claude/plugins/config/`.

### In Cowork

Open Claude Desktop → Cowork tab → Customize → Browse plugins → Upload custom plugin → zip the relevant plugin folder.

Same source files, same skills, same slash commands. Cold-start interviews work the same way.

---

## Typical workflows

### Full Praexo report on a company

```
/praexo-research:company-research Schneider Electric
   → ~30 min of research, ~15 pages of notes
   → output: praexo-research_schneider-electric_2026-05-15.md

/praexo-report:full-report
   → consumes the markdown above
   → ~15-20 min to render
   → output: Praexo_Schneider_Electric_2026-05-15.docx
```

### Quick value chain map only

```
/praexo-research:value-chain-map "specialty chemicals — paints and coatings"
   → ~5-10 min, 2-3 pages of focused mapping
   → output: praexo-valuechain_specialty-chemicals_2026-05-15.md
```

You can stop here, or feed it into something downstream — a BD prep brief, a strategy memo, a client conversation.

### AI disruption scan as input to AnswerRocket BD

```
/praexo-research:ai-disruption-scan Coca-Cola
   → ~10 min, focused on AI exposure
   → output: praexo-aiscan_coca-cola_2026-05-15.md
```

Pass that into your AnswerRocket discovery prep (via Cowork or directly). You haven't produced a Praexo report — you've produced focused intel for a BD conversation.

### Executive brief instead of full report

```
/praexo-research:company-research [Company]
/praexo-report:executive-brief
   → same research input, shorter output
   → 8-12 pages, sharper voice, 3 required tables instead of 9
```

### Report from hand-curated notes

You don't have to use `praexo-research`. If you (or someone else) has already done the analysis in markdown:

```
/praexo-report:full-report
   → point it at your existing markdown file
   → it maps your content to the 12-section framework as best it can
   → flags anything that doesn't have a natural home
```

---

## How to customize as you use them

The plugins are markdown and JSON. No build step. You can edit anything in place.

### Adjusting your practice profile

Your CLAUDE.md files live at:

```
~/.claude/plugins/config/praexo-research/CLAUDE.md
~/.claude/plugins/config/praexo-report/CLAUDE.md
```

Edit them directly for small changes — adding a sector to your focus list, changing voice intensity, updating output path. Re-run the cold-start interview only when your practice shifts materially.

### Adjusting a skill

Skills live at:

```
~/.claude/plugins/cache/praexo-plugins/praexo-research/skills/<skill>/SKILL.md
~/.claude/plugins/cache/praexo-plugins/praexo-report/skills/<skill>/SKILL.md
```

Edit the `SKILL.md` directly. The change takes effect next time the skill runs.

For changes you want to keep, edit the original files in your `praexo-plugins/` source repo, commit, push, and run `/plugin marketplace update` on other machines.

### Adding a new skill

Same shape as the existing ones:

```bash
mkdir -p praexo-research/skills/<new-skill-name>
```

Create `SKILL.md` with the frontmatter:

```markdown
---
name: <new-skill-name>
description: [The trigger signal. Specific. Under 1024 chars.]
---

# [Skill name]

## Pre-flight check
[What to read first — usually CLAUDE.md and any references]

## Inputs
[What the user provides]

## [The work]
[Step by step]

## Output
[Format, location, what to present to the user]

## What not to do
[Failure modes]
```

Bump the plugin's `version` in `.claude-plugin/plugin.json`. Run `/plugin update` to install the new skill.

### Adding the soul / persona

You explicitly chose to keep the soul out of v0.1. When you're ready to integrate, three options:

1. **Reference at runtime.** Add a line to each skill's pre-flight: "If `soul_praexo.md` is attached or in the project context, read it first and adopt that voice throughout." No plugin change needed beyond the line — the user attaches the soul file when they want it.

2. **Bundle as a reference file.** Drop `soul_praexo.md` into `praexo-research/references/`. Add a line to relevant skills: "Read `references/soul_praexo.md` for the Praexo persona. Adopt that voice." Voice becomes the default, no attachment needed.

3. **Soul as a third plugin.** A `praexo-persona` plugin that does nothing but install the soul as a reference both other plugins read. Overkill for now — only worth it if you build multiple personas (Jonas, Ellie Voss, etc.).

Recommendation: option 2 for v0.2 once you've used v0.1 for a couple of real reports and seen where voice gaps emerge.

---

## v0.1 limitations to know about

These are intentional v0.1 simplifications. Address as you use the plugins:

1. **No persona file.** Skills produce competent analysis but not Praexo's distinctive voice. Add soul integration in v0.2 (see above).

2. **Brand spec covers Praexo only.** If you ever produce reports under a different brand (a client's brand, AnswerRocket's brand), you'll need a different brand spec. The `praexo-brand-spec.md` file is meant to be forked, not multiplied — for v0.2, consider parameterizing the brand spec by a `brand:` field in the profile.

3. **No MCP connectors.** Skills use Claude's built-in web search. For higher-leverage research you'd want connectors to: Bloomberg Terminal data, internal Praexo Google Drive (prior research), Granola call notes, your YPO IQ database. v0.3 territory.

4. **No scheduled agents.** A "watch this company for material events and trigger a research refresh" agent would be valuable for active deals. v0.3 territory — see the `claude-for-legal` repo for the pattern.

5. **Quality gates are run by Claude, not by code.** The skills tell Claude to check the gates, but a malicious or sloppy session could skip them. For v0.2, consider adding a `scripts/validate-report.py` that runs structurally — table count, box presence, no `[TBD]` markers.

6. **No usage analytics.** You won't know how often each skill runs, which ones produce reports you actually keep vs. discard, where quality is highest. Add light usage logging in v0.2 if you decide to share the plugins beyond yourself.

7. **The two `cold-start-interview` skills share a name.** Claude Code will namespace them correctly (`/praexo-research:cold-start-interview` vs. `/praexo-report:cold-start-interview`), but in conversation they're easy to confuse. Watch for it.

---

## Validation before you ship to GitHub

Before pushing to a private repo:

```bash
cd /path/to/praexo-plugins
claude plugin validate .
```

This checks `plugin.json`, `marketplace.json`, and skill frontmatter for syntax and schema errors. Common failures and fixes are in the `claude-for-legal` repo README and the Claude Code plugin docs.

You should see no errors. Warnings about missing description fields are non-blocking but worth fixing.

---

## A note on the v0.1 maturity level

What I've built here is a **working v0.1 that will produce real output** — not a stub, not a sketch. Every skill has explicit inputs, structured outputs, quality gates, and failure modes. Every reference file is content-complete.

But it's still v0.1. The first 3-5 reports you generate will reveal:

- Sections where the skill prompts produce thin output and need a sharper pre-flight read
- Quality gates that fire too often or too rarely
- Brand styling details that the docx skill renders differently than you expected
- Voice drift between research notes and final report

Plan to spend 30-60 minutes after each of the first few reports refining the prompts. By report 5, the plugins will be solid. By report 10, they'll be better than anything you could write from scratch.

The pattern matters more than the v0.1 content. You can rewrite every word of every skill in this folder — what stays is the structure: cold-start writes profile, profile feeds skills, skills produce structured output, output feeds downstream consumers. That's the reusable architecture.
