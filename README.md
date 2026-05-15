# Praexo — Claude plugin marketplace

Praexo's plugin marketplace for Claude Code and Cowork. Vertical-grade research, reporting, and advisory tooling for partners, operators, and consultants.

## What's in the marketplace

| Plugin | What it does |
| --- | --- |
| [`praexo-research`](./praexo-research) | Deep research and analysis — companies, sectors, value chains, AI disruption. Six-pass methodology with primary-source bias. Outputs structured markdown notes. |
| [`praexo-report`](./praexo-report) | Praexo-branded Word report generator. 55-65 page full reports or 8-12 page executive briefs. Branded cover, TOC, data tables, emphasis and summary boxes. |

The two plugins are **independent** — use either alone, or chain them: run research → feed the markdown into the report generator.

## Install

### Add the marketplace

```
/plugin marketplace add praexo/praexo-plugins
```

(Replace `praexo/praexo-plugins` with your actual GitHub path if hosting elsewhere.)

### Install the plugins

```
/plugin install praexo-research@praexo
/plugin install praexo-report@praexo
```

### One-time setup

Each plugin has a cold-start interview that captures your preferences (sectors, voice, brand assets, output paths). Run them once:

```
/praexo-research:cold-start-interview
/praexo-report:cold-start-interview
```

For the report plugin, also drop your Praexo logo at `praexo-report/assets/praexo-logo.png` before the first report run.

## Documentation

See [`GUIDE.md`](./GUIDE.md) for the full architecture explanation, typical workflows, customization paths, and v0.1 limitations.

Per-plugin READMEs:
- [`praexo-research/README.md`](./praexo-research/README.md)
- [`praexo-report/README.md`](./praexo-report/README.md)

## Maintainer

**Marc Leon** — Praexo Management BV / Praexo Consulting LLC
- Email: marc@praexo.com
- Web: https://praexo.com

## License

MIT — see plugin-level `LICENSE` files (when added).
