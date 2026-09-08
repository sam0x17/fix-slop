# fix-slop

A Claude Code skill that strips LLM writing tells from technical prose: PR comments, code reviews, design docs, RFC/SIMD discussion replies, commit messages, chat.

Heavily modified fork of [stop-slop](https://github.com/hardikpandya/stop-slop) by Hardik Pandya (MIT). The essay-oriented rules are recalibrated for technical writing:

- Passive voice is allowed. So are informative adverbs, data-bearing lists, domain jargon, and honest hedges.
- Em dashes are banned. `->` replaces unicode arrows outside code.
- The construction catalog targets the patterns that actually mark text as generated: negation-contrasts ("that's not X, it's Y"), sycophancy openers ("You're absolutely right!"), fake candor ("let me be straight with you"), praise inflation ("an unusually disciplined implementation"), the load-bearing/seams metaphor kit, mic-drop closers, bold-label bullet formalism.
- Model-specific tic lists for Opus-era and Fable-era Claude, with a documented path to regenerate them empirically.
- UI instructions use direct actions: "Enter to open", "Click Retry to run the job again". Ordinary technical subjects such as "the parser rejects invalid input" are fine.

## Layout

- `SKILL.md`: the rules and the editing pass
- `references/phrases.md`: tiered phrase lists, including per-model tics
- `references/constructions.md`: pattern catalog with before/after rewrites
- `references/greps.txt`: ERE patterns for a mechanical lint pass (`grep -nEi -f references/greps.txt draft.md`; expect false positives, it is a linter, not a verdict)

## Install

Symlink into your global skills directory:

```sh
ln -s ~/workspace/fix-slop ~/.claude/skills/fix-slop
```

## Sources

- [stop-slop](https://github.com/hardikpandya/stop-slop): base skill structure and the generic phrase inventory (MIT)
- [slop-forensics](https://github.com/sam-paech/slop-forensics): cross-model lexical slop, from the essays-domain slop lists; also the methodology for regenerating per-model lists (its published data has no Opus/Fable profiles as of Aug 2026)
- [jola.dev: How to stop Claude from saying "load-bearing"](https://jola.dev/posts/how-to-stop-claude-from-saying-load-bearing): the load-bearing/seams/honest-takes catalog
- Direct observation of Fable 5 output, including the session in which this skill was written
- tautologer (@tautologer), screenshot of a post on shortcut hints: "Enter to open" in place of "Enter opens it"

## License

MIT. Portions copyright Hardik Pandya.
