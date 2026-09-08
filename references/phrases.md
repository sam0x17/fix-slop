# Phrase Lists

Three tiers. Tier 1 is banned outright. Tier 2 is banned as framing (the sentence usually survives with the phrase deleted). Tier 3 is lexical slop: each use needs a reason, and two uses in one document is a pattern.

## Tier 1: banned outright

Sycophancy and fake candor:

- "You're absolutely right" (and "You're right!" as a reflexive opener)
- "Great question" / "Excellent question" / "That's a great point"
- "Good catch!" as a standalone reflex (naming what was caught is fine)
- "Let me be straight with you" / "let me be honest" / "let me be direct"
- "I'll be honest" / "to be honest" / "to be frank" / "to be blunt"
- "honest take" / "my honest opinion"
- "Let me be clear" / "make no mistake"

Praise inflation (typically about AI-generated artifacts):

- "This is an unusually disciplined/clean/thorough/thoughtful X"
- "remarkably [praise adjective]"
- "impressively [praise adjective]"
- "chef's kiss" in any form
- "production-ready" / "battle-tested" as a verdict on fresh code
- "This should now work correctly" (say what was verified instead)

Metaphor kit:

- "load-bearing"
- "seam" / "seams" / "at the seams" (non-sewing contexts)
- "scaffolding" (when not literal construction or literal test scaffolding)
- "connective tissue"
- "north star"
- "gold mine" / "treasure trove"
- "secret sauce"
- "the plot thickens"

Drama and emphasis:

- "Full stop." / "Period."
- "Let that sink in."
- "Here's the thing" / "Here's the kicker"
- "game-changer" / "game-changing"
- "mic drop" (and writing sentences designed to be one)
- "*slaps roof*"-style bit humor in technical comments

Summary theater:

- "Bottom line:"
- "In short," / "In essence," / "Simply put,"
- "At the end of the day"
- "boils down to"
- "The upshot:"
- "TL;DR" in formal writing (fine in chat when someone asked for one)

## Tier 2: banned as framing

Delete the phrase, keep the sentence:

- "It's worth noting that" / "worth flagging" / "worth mentioning"
- "Notably," / "Importantly," / "Interestingly," / "Crucially,"
- "Keep in mind that" / "Remember that"
- "Needless to say"
- "Of course,"
- "genuinely" / "honestly" / "frankly" as intensifiers
- "quite" / "really" / "very" when the claim carries numbers anyway
- "As mentioned above" / "As we've seen" (restructure so you don't need it)
- "So:" as a pivot into the conclusion
- "That said," / "To be fair," when appended reflexively
- "arguably" (make the argument or drop the claim)
- "essentially" / "basically" / "fundamentally"

## Tier 3: lexical slop

Cross-model, grounded in the slop-forensics essay lists plus long-standing community catalogs:

- delve / delving
- leverage (verb) -> use
- utilize -> use
- robust (without a failure mode it survives)
- comprehensive (without an enumeration of what it covers)
- seamless / seamlessly
- crucial role / pivotal role / vital role
- extends beyond
- actionable
- holistic
- myriad / plethora
- landscape (abstract: "the security landscape")
- journey (abstract)
- empower / unlock / elevate (abstract)
- streamline / foster / bolster
- underscores (verb) / highlights the importance of
- testament to
- boasts (as "features")
- nuanced (as praise)
- state-of-the-art / cutting-edge
- best practices (without naming one)
- performant (suspect, not banned: common in engineering, but "fast" with a number beats it)

## Model-specific tics

### Opus-era

- "You're absolutely right!" (the canonical one)
- "Perfect!" / "Excellent!" / "Certainly!" as turn openers
- "I apologize for the confusion"
- Completion summaries with checkmark bullets and "Key changes:" headers
- "Let me [verb]" narration before every action
- "comprehensive" as a self-descriptor of its own output
- Reflexive offers of more: "Would you like me to also..."

### Fable-era

Observed directly in Fable output (including the session this skill was written in), plus the jola.dev catalog and user reports. Fable's slop is structural more than lexical; the phrase tells:

- "load-bearing" (applied to claims, tests, comments, anything)
- "honest take" / "the honest answer" / "the honest behavior"
- "on the merits"
- "directionally right" / "directionally correct"
- "the calculus" (non-math)
- "cuts the other way" / "cuts against"
- "does a lot of work" / "doing a lot of unexamined work" (about words/claims)
- "-adjacent" coinages ("advocacy-adjacent")
- "not a close call"
- "costs nothing" / "buys you nothing"
- "Say the word and I'll..."
- "One heads-up:" / "One thing to be aware of:"

Structural tells (see constructions.md for rewrites):

- Negation-contrast chains, often several per document
- Bolded topic-sentence paragraphs ("**The trigger.** ...")
- Two-item numbered lists with bolded heads for what is one paragraph of prose
- Paragraph-final positioning claims ("which positions you to own the follow-up")
- Em dashes at roughly one per three sentences
- Parenthetical asides delivering the actual judgment "(he's right, and conceding it costs nothing)"

### Regenerating these lists

slop-forensics (github.com/sam-paech/slop-forensics) computes over-represented n-grams per model against a human baseline. Its published data covers Claude 3.x in creative writing only; no Opus 4.x or Fable 5 profiles exist there yet. To refresh the Fable list empirically: collect your own Fable transcripts, run the slop_profile pipeline against the human_writing baseline, and merge what clears the frequency bar into the lists above.
