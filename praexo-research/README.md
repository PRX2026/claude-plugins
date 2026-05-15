# praexo-research

Deep research analysis plugin for Praexo. Produces structured research notes (markdown) on companies and sectors using the Praexo six-pass methodology.

## What this plugin is for

This plugin does **research and analysis**, not finished reports. It outputs structured markdown notes that can be consumed by:

- `praexo-report` plugin (for branded Praexo Word docs)
- BD discovery briefs
- M&A memos
- Columbia coursework
- Any downstream synthesis

If you want a finished 60-page Word report, run `praexo-research` first, then feed its output to `praexo-report`.

## Skills

| Command | What it does |
| --- | --- |
| `/praexo-research:cold-start-interview` | One-time setup — captures your analytical practice |
| `/praexo-research:company-research` | Six-pass deep research on a named company |
| `/praexo-research:sector-research` | Industry / sector analysis without single-company focus |
| `/praexo-research:value-chain-map` | Focused value chain + profit pool analysis |
| `/praexo-research:ai-disruption-scan` | Focused AI threat + opportunity assessment |

## Install (Claude Code)

```bash
cd /path/to/praexo-plugins
/plugin marketplace add ./
/plugin install praexo-research@praexo
/praexo-research:cold-start-interview
```

## Install (Cowork)

Open Cowork → Customize → Browse plugins → Upload custom plugin → zip the `praexo-research/` folder.

Or: push the `praexo-plugins/` repo to GitHub and add the marketplace via the GitHub source.

## Reference files

- `references/research-methodology.md` — the six-pass methodology
- `references/research-notes-template.md` — frozen output structure
- `references/source-quality-rules.md` — what to cite, what to skip

## Notes

- All research output is in **English** regardless of input language. This is intentional.
- The plugin defaults to a primary-source bias. If you want a faster / lighter pass, use `value-chain-map` or `ai-disruption-scan` rather than full company research.
- The "soul" / persona is intentionally NOT in this plugin. Bring your own (e.g. `soul_praexo.md`) at the prompt level or via context.

## License

MIT
