# Clearspeak

**Writing that means what it says, in a human voice.**

Good writing says what it means and sounds like a person. AI writing usually fails on both: it hides thin thinking behind fog, and it reads machine-made. Clearspeak fixes both, in that order. Its primary job is Orwell's test: unfog the prose until the meaning shows, cutting vagueness, inflation, and euphemism. Its second job restores a human voice, clearing the patterns that read as machine-made; removing those surface tells is a side effect of the first job, not the goal. It is safe for scientific and technical work: it keeps domain terms, numbers, units, and citations exactly as written, and preserves lists of steps, options, or parameters rather than flattening them into prose.

## What it catches

It catches the tells below (see [SKILL.md](SKILL.md) for the full catalog):

- **Inflated content:** significance inflation, notability name-dropping, promotional language, superficial -ing analyses, formulaic "challenges" sections.
- **Padded language:** AI vocabulary, copula avoidance ("serves as" for "is"), stale metaphors and padded verbs ("give rise to" for "cause"), filler phrases, excessive hedging, generic positive conclusions.
- **Formulaic structure:** negative parallelism, rule of three, false ranges, synonym cycling, manufactured punchlines, aphorism formulas, rhetorical openers.
- **Hidden actors:** passive voice and subjectless fragments, vague attributions ("experts believe").
- **Formatting tells:** em and en dashes, boldface overuse, redundant bold-label bullets (headers that restate their own item), title-case headings, emojis, curly quotes.
- **Chatbot residue:** collaborative artifacts ("I hope this helps"), knowledge-cutoff disclaimers, sycophantic tone.

## How it differs from humanizer

Clearspeak is a fork of [blader/humanizer](https://github.com/blader/humanizer) and keeps its pattern catalog. The difference is register: humanizer was built for blog and essay voice and tends to add a conversational lift, while Clearspeak keeps reference prose direct, natural, and precise.

Two AI-generated sentences, each run through both skills (Claude Opus 4.8, clean sessions).


| Original (AI) | humanizer | Clearspeak |
|---|---|---|
| Beyond coordination, small teams benefit from stronger ownership and fewer process constraints. | Coordination isn't the whole story, though. Small teams also tend to have stronger ownership and a lot less process. | Small teams also tend to have stronger ownership and lighter process. |

Humanizer adds a conversational hook ("isn't the whole story, though"), appropriate for essays and opinion writing. Clearspeak just states the point.

| Original (AI) | humanizer | Clearspeak |
|---|---|---|
| ...speed comes not from working harder but from removing the friction that size inevitably introduces. | The speed doesn't come from working harder. It comes from not having to deal with the friction that size brings. | ...the speed comes from cutting friction rather than working harder. |

Humanizer breaks the "not X but Y" into a two-sentence reveal, appropriate for essays and opinion writing. Clearspeak folds it into one plain clause.


## Installation

### Claude Code

Clone directly into Claude Code's skills directory:

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/saraya209/clearspeak.git ~/.claude/skills/clearspeak
```

Or copy the skill file manually if you already have this repo cloned:

```bash
mkdir -p ~/.claude/skills/clearspeak
cp SKILL.md ~/.claude/skills/clearspeak/
```

### OpenCode

Clone directly into OpenCode's skills directory:

```bash
mkdir -p ~/.config/opencode/skills
git clone https://github.com/saraya209/clearspeak.git ~/.config/opencode/skills/clearspeak
```

Or copy the skill file manually if you already have this repo cloned:

```bash
mkdir -p ~/.config/opencode/skills/clearspeak
cp SKILL.md ~/.config/opencode/skills/clearspeak/
```

> **Note:** OpenCode also scans `~/.claude/skills/` for compatibility, so if you use both tools, a single clone into `~/.claude/skills/clearspeak/` is enough.

## Usage

### Claude Code

```
/clearspeak

[paste your text here]
```

### OpenCode

```
/clearspeak

[paste your text here]
```

Or ask the model to clearspeak text directly in either tool:

```
Please clearspeak this text: [your text]
```

### Voice Calibration

To match your personal writing style, provide a sample of your own writing:

```
/clearspeak

Here's a sample of my writing for voice matching:
[paste 2-3 paragraphs of your own writing]

Now clearspeak this text:
[paste AI text to clean up]
```

The skill will analyze your sentence rhythm, word choices, and quirks, then apply them to the rewrite instead of producing generic "clean" output.

## Credits

Clearspeak is a fork of [blader/humanizer](https://github.com/blader/humanizer) (Siqi Chen, MIT), whose pattern catalog is built on [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), maintained by [WikiProject AI Cleanup](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_AI_Cleanup). The plainness and honesty come from George Orwell's "Politics and the English Language" (1946), used as paraphrased principles.

## Version History

- **2.1.0** - Rebalanced toward meaning-first. Defog (Orwell's clear, honest prose) is the primary job and surface-tell removal serves it, stated in the opening, the task steps, and the change-note the skill models when reporting back. Meaning is the one mandatory pre-return scan; surface tells are cleared as part of that pass, not headlined, and change notes name a surface-tell edit only on request or when a formatting change needs explaining. Demoted em dashes from a privileged "cut on sight" rule with a mandatory glyph scan to an ordinary tell, cut only when clustered. Added a "lists are structure, not padding" rule so lists of steps, options, or parameters in technical, scientific, and how-to prose are preserved rather than flattened; reframed the style-cleanup default to protect scannable structure; retargeted the inline-header-list pattern onto redundant bold-label restatement rather than the list format itself; reworked the pattern examples so a named source, date, or figure in an "after" is seeded in its "before" (extraction, never fabrication); reorganized the worked examples into one "Examples" section with expressive-prose and technical-procedure cases; and narrowed the "don't copy Orwell" caveat to his dated voice and word-lists rather than a blanket ban on his examples.
- **2.0.0** - Renamed from Plainspeak to **Clearspeak** (trigger is now `/clearspeak`). "Plainspeak" read as "plain = flat," and its `-speak` suffix echoed Newspeak, the wrong Orwell register. Clearspeak keeps Orwell but names the goal: clear, honest prose. Doubleplusgood. The pitch now leads with what the skill is for, not what it removes. No pattern or behavior changes.
- **1.1.0** - Deepened the Orwell layer: added a pattern for stale metaphors and padded verbs (taught as a recognizable move, not a banned-phrase list, to avoid overfitting), wired Orwell's six rules into the audit step as a final gate, drew an explicit line in the personality section between adding voice and inventing facts (with a corrected example), and relabeled the full-example stages for clarity.
- **1.0.1** - Minimal prompt cleanup to reduce overfitting while keeping the 33-pattern catalog: internalized the draft/audit loop, replaced the opinionated fallback with a plain, natural, varied default, preserved coverage instead of paragraph count, blocked invented specificity, added warning-list caveats, tightened passive-voice and hyphenated-compound handling, and clarified punctuation/formatting cleanup.
- **1.0.0** - Initial Plainspeak release, forked from humanizer 2.8.0. Renamed and refocused as "humanizer meets Orwell": added an Orwell lens (six rules plus a positive plain-prose model), softened the personality section so plain and honest is the default, and added a scientific and technical tolerance layer (keep domain terms, methods-section passive voice, numbers, units, and citations). The 33-pattern catalog is unchanged.

## License

MIT
