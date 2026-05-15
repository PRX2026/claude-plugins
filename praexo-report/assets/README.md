# Assets

Place the Praexo logo PNG in this folder as `praexo-logo.png` before running any report skill.

The path is referenced from the practice profile (`CLAUDE.md`) and used by `full-report` and `executive-brief` skills to insert the logo in the document header.

**Required:**
- File: `praexo-logo.png`
- Format: PNG with transparency preferred
- Size: anything reasonable — the skill will scale to ~0.4 inch height in the header

**If logo is missing:** the report skills will stop pre-flight and ask you to provide it.
