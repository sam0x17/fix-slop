# Constructions

Each entry: the shape, why it reads as generated, and a rewrite from a technical context.

## The negation-contrast

Shapes: "That's not X, it's Y." / "This isn't just X. It's Y." / "X isn't the problem. Y is." / "less about X than Y" / "The real X is Y." / "That's worse than X: it's Y."

The tell: the writer invents a wrong position (X) purely to knock it down, which adds a sentence of length and zero information. LLMs emit this at a rate no human matches, and several per document is a signature.

Rewrite: state Y. If X is a position someone actually holds, attribute it and address it as its own point.

Before:
> That's worse than an error: there's no signal to fall back to raw decoding, and "no extensions" is itself a meaningful (wrong) answer.

After:
> The response gives no signal to fall back to raw decoding, and "no extensions" is itself a wrong answer a consumer will act on.

## Praise inflation

Shape: an evaluative adjective stack in front of a thing being reviewed, usually AI-generated. "This is an unusually disciplined implementation of the pattern."

The tell: review language that grades instead of describing. A human reviewer says what the code does, where it breaks, and what to change.

Rewrite: replace the grade with the observation that motivated it.

Before:
> This is an unusually clean migration; the new parser is impressively thorough.

After:
> The migration touches only the parsing layer, and the new parser covers all three instruction variants including the multisig path.

## Throat-clearing

Shapes: "It's worth noting that", "Importantly,", "Interestingly,", "One thing that matters before the numbers:".

Rewrite: delete the opener. If the sentence stops mattering without the opener, delete the sentence.

## Meta-narration

Shapes: "Let me walk through the layers.", "I'll now trace the call path.", "Let's dig into why."

Rewrite: perform the action. The reader sees you tracing the call path by reading a traced call path.

## Bold-label bullets

Shape:

> - **Value:** fixes the parsing bug.
> - **Risk:** none, display-layer only.

The tell: form borrowed from a template when two sentences of prose carry it better. Keep the form only where a reader genuinely scans for the label (checklists, structured review templates, tables of options).

Rewrite:

> Fixes the parsing bug. Risk is minimal: display layer only.

## Bolded topic-sentence paragraphs

Shape: "**The trigger.** Token-2022 added..." repeated for four paragraphs.

The tell: essay scaffolding imported into a comment. One document section heading is structure; a bolded phrase opening every paragraph is decoration.

Rewrite: plain paragraphs, or real headings if the document is long enough to navigate.

## Tricolon padding

Shape: "wallets, explorers, and indexers", "no consensus, runtime, or SVM surface", three parallel clauses closing a paragraph.

The tell: rhythm filling in for content; the third item is usually the weakest. Two items or an honest "e.g." reads as chosen rather than generated. Keep three when all three are load... when all three carry distinct weight the reader needs.

## Mic-drop closers

Shape: final one-sentence paragraph engineered for quotability. "That turns 'change my mind' into 'you don't have to.'"

Rewrite: end on the concrete ask, the number, or the next step. If the last sentence would work as a conference-talk slide, replace it.

## Summary pivots

Shape: "So:", "Bottom line:", "The upshot:" introducing a restatement of the previous two paragraphs.

Rewrite: cut the restatement. In long documents, a real "Summary" heading at the top beats a disguised one at the bottom.

## Rhetorical questions

Shape: "So what does this mean for validators?" followed by the answer.

Rewrite: the answer, as a sentence about validators.

## Both-sides reflex

Shape: every judgment followed by "That said, ..." or "To be fair, ...".

Rewrite: keep the counterpoint only when it changes the reader's decision. One per document is plenty; the reflexive version reads as liability management.

## Anthropomorphized rhetoric

Shape: "the numbers tell a story", "the diff wants to be three commits", "this API is begging for misuse".

Scope: ordinary technical subjects are exempt ("the parser rejects", "the runtime writes"). The tell is abstractions performing human drama.

Rewrite: name the person or state the property. "The diff mixes three unrelated changes; split it."

## User instructions phrased as behavior descriptions

Shape: shortcut hints or instructions that make a key, button, or control the subject: "Enter opens it", "Esc returns to it", "Ctrl+C twice quits".

The tell: the reader needs an action, but the text describes what the control does.

Rewrite: use an imperative in prose or a compact "control to action" phrase in shortcut hints. Preserve modifiers such as "twice" and any context needed to identify the target.

Before:
> Enter opens it, Esc returns to it, Ctrl+C twice quits.

After:
> Enter to open, Esc to return, Ctrl+C twice to quit.

Before:
> The Retry button runs the failed job again.

After:
> Click Retry to run the failed job again.

Scope: apply this when telling the reader how to act. Inanimate subjects are normal in descriptions of behavior: "the parser rejects malformed input", "the cache expires after five minutes", "Ctrl+C sends SIGINT". Keep those. Treat this as an editing preference; it does not establish whether an author used an LLM.

## Coinage tics

Shape: "-adjacent", "-shaped", "-flavored" suffixed onto abstractions ("a consensus-shaped problem", "advocacy-adjacent").

Rewrite: state the actual relationship. "borderline advocacy", "a problem for consensus".

## Offer-reflex endings

Shape: closing every message with "Want me to also...?", "Say the word and I'll...", "Happy to draft that if useful."

Scope: chat only; a real offer at a real decision point is fine. The tell is the reflex, one per message regardless of content.
