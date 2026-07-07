# AGENTS.md

Guidance for AI coding agents (Claude Code, Codex, Warp, etc.) working in this repository.

## What this repo is

**Plainspeak**, a fork of [blader/humanizer](https://github.com/blader/humanizer) retuned as "humanizer meets Orwell": it removes AI tells and makes prose plain and honest, with a tolerance layer for scientific and technical writing. A **Claude Code / OpenCode skill** implemented entirely as Markdown. The runtime artifact is `SKILL.md`: the agent reads its YAML frontmatter (metadata + allowed tools) followed by the editor prompt. There is no build step and no code to run.

## Key files

- `SKILL.md` — the skill itself. YAML frontmatter (`name`, `version`, `description`, `allowed-tools`), then ORWELL'S LENS, PERSONALITY AND SOUL, SCIENTIFIC AND TECHNICAL WRITING, and the canonical numbered pattern list with before/after examples. **This is the source of truth.**
- `README.md` — for humans: installation, usage, a summary table of the patterns, and a version history.

## The maintenance contract

`SKILL.md` and `README.md` must stay in sync. When you change behavior or content:

- **Patterns:** the skill currently defines **34 numbered patterns** (inherited from humanizer, kept stable). If you add, remove, or renumber any, update the README pattern table, its "N Patterns Detected" heading, and every cross-reference in the same change. Keep numbering stable unless you are deliberately renumbering.
- **The non-pattern sections** (ORWELL'S LENS, PERSONALITY AND SOUL, SCIENTIFIC AND TECHNICAL WRITING) carry the Plainspeak character. Keep them consistent with each other: plain and honest is the default, voice is the marked exception, and the scientific tolerance layer (domain terms, methods passive voice, numbers, citations) overrides a pattern only via rule 6.
- **Version:** `SKILL.md` frontmatter has a `version:` field and `README.md` has a "Version History" section. Bump both together.
- **Non-obvious fixes:** if you change the prompt to handle a tricky failure mode (a repeated mis-edit, an unexpected tone shift), add a short note to the README version history explaining what was fixed and why.

## Editing SKILL.md

- Preserve valid YAML frontmatter (formatting and indentation).
- The prompt below the frontmatter is the product. Edit it like a careful instruction document, not code.
