---
name: fix-slop
description: Strip LLM writing tells from technical prose (PR comments, reviews, design docs, commit messages, chat replies). Use when drafting or editing anything a human will read as your own writing.
metadata:
  trigger: Drafting or editing technical prose; "make this not look AI-generated"; reviewing text before posting to GitHub, Slack, or a mailing list
  sources: stop-slop (Hardik Pandya, MIT), slop-forensics (Sam Paech), jola.dev, session-observed Opus/Fable tics, tautologer shortcut-hint example
---

# Fix Slop

Remove LLM tells from technical prose while keeping the properties technical writing needs. This is calibrated for PR comments, code reviews, design docs, SIMD/RFC discussions, commit messages, and chat. It is not an essay-style guide.

## What technical prose is allowed to do

These are fine. Do not "fix" them:

- Passive voice, when the actor is obvious or irrelevant ("the account is written at the epoch boundary").
- Adverbs that carry information ("atomically", "lazily", "twice").
- Lists and tables that carry data. Structure is suspect only when it decorates instead of informs.
- Domain jargon: footgun, hot path, blast radius, plumbing, shim, happy path. These are how engineers talk.
- Hedges on genuinely uncertain claims ("probably", "as far as I can tell"), when you state what would settle the question.
- First person, short sentences, fragments in chat contexts.

## Hard bans

Mechanical, no judgment required. See [references/phrases.md](references/phrases.md) for the full list and [references/greps.txt](references/greps.txt) for a grep-able version.

1. **Em dashes.** None, ever. Use a comma, a period, parentheses, or a colon. For ranges and arrows use `-` and `->`.
2. **Unicode arrows and symbols in prose.** `→`, `⇒`, `≈`, `×` become `->`, `=>`, `~`, `x` outside code blocks.
3. **Sycophancy openers.** "You're absolutely right", "Great question", "Excellent point", "Good catch!" as a reflex. If the person is right, show it by acting on the correction, or state specifically what they got right.
4. **The negation-contrast.** "That's not X, it's Y." / "This isn't just X. It's Y." / "less about X than Y" / "The real X is Y". State Y. Delete the X clause entirely; if X matters, give it its own sentence.
5. **Fake candor framing.** "Let me be straight with you", "I'll be honest", "honest take", "to be frank". Everything you write is presumed honest; announcing it implies the rest wasn't.
6. **Praise inflation for generated artifacts.** "This is an unusually disciplined implementation", "remarkably clean", "impressively thorough". Describe what the artifact does and where it fails. Praise adjectives about AI output are noise at best.
7. **Load-bearing metaphor kit.** "load-bearing", "seam"/"seams", "scaffolding" (non-literal), "the connective tissue", "north star", "gold mine". One concrete metaphor per document is the ceiling, and never one of these.
8. **Mic-drop closers.** The punchy one-line paragraph ender designed to be quoted. End on the fact or the ask instead.

## Constructions to rewrite

Judgment required. Full catalog with before/after pairs in [references/constructions.md](references/constructions.md).

- Throat-clearing: "It's worth noting that", "Importantly,", "Interestingly,", "Here's the thing". Delete the phrase; keep the sentence.
- Meta-narration: "Let me walk through", "I'll now explain". Just walk through it.
- Tricolon padding: three parallel items where two (or one) carry the content. Cut to the ones that matter.
- Bold-label bullets ("**Value:** ...", "**Risk:** ...") when plain sentences would read fine. Keep labels only in structured artifacts like review checklists or backport templates where a reader scans for the label.
- Intensity hedges: "genuinely", "honestly", "frankly", "quite", "really". Delete; the sentence keeps its meaning.
- Vague amplifiers: "significantly", "dramatically", "massively" with no number attached. Give the number or drop the claim.
- Coinage tics: "X-adjacent", "Y-shaped", "Z-flavored". Name the actual relationship.
- Anthropomorphized rhetoric: "the numbers tell a story", "this code wants to be a library". Fine in speech, slop in writing. (Ordinary technical subjects are exempt: "the function returns", "the parser rejects".)
- User instructions phrased as descriptions of keys or buttons: "Enter opens it", "the Retry button runs the job again". Say what to do: "Enter to open", "Click Retry to run the job again". Keep ordinary descriptions of system behavior. See [the examples and scope](references/constructions.md#user-instructions-phrased-as-behavior-descriptions).
- Summary pivots: "So:", "In short,", "Bottom line:", "The upshot:". If the paragraph needs a summary, the paragraph is too long.
- Both-sides reflex: a "That said," / "To be fair," appended to every judgment. Keep one only when the counterpoint changes what the reader should do.

## Model-specific tics

Curated lists in [references/phrases.md](references/phrases.md), split by family:

- **Opus-era tics**: "You're absolutely right!", "Perfect!", "Certainly!", completion summaries studded with checkmarks, "production-ready", "battle-tested", "This should now work correctly".
- **Fable-era tics**: "load-bearing", "honest take", negation-contrast chains, "on the merits", "directionally right", "the calculus", "cuts the other way", "advocacy-adjacent"-style coinages, bold-topic-sentence paragraphs, "Say the word and I'll...".
- **Cross-model lexical slop** (from slop-forensics essay data): "delve", "crucial role", "pivotal role", "extends beyond", "leverage" (verb), "seamless", "robust", "actionable", "underscores" (verb), "testament to", "landscape" (abstract), "streamline", "foster", "empower".

## The pass

1. Grep pass: run the patterns in [references/greps.txt](references/greps.txt) over the draft (`grep -nEi -f references/greps.txt draft.md`). Fix every hit or consciously keep it (false positives exist; the greps are a linter, not a verdict).
2. Construction pass: read each paragraph asking "which pattern from the catalog is this?" Most paragraphs contain zero; the ones that contain one usually contain three.
3. Read-aloud pass: anywhere your voice drops into reading-a-press-release cadence, that sentence gets rewritten.
4. Done when: no hard-ban hits remain, every kept flag has a reason, and nothing reads as designed-to-be-quoted.

## What this skill does not do

It does not shorten for its own sake, add informality, or inject personality. A dry, precise comment with zero tells is the goal. If the input is already clean, say so and change nothing.
