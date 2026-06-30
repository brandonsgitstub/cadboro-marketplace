---
name: positioning-generator
description: Generate sharp, defensible product positioning using a Dunford-style frame (competitive alternatives, unique attributes, value, target segment, market category). Use this skill whenever someone wants to position or reposition a product, figure out their category, sharpen a value proposition that sounds generic, write a positioning statement, or answer "what are we, exactly, and who is this for." Trigger even on loose phrasing like "we sound like everyone else", "help me explain what we do", "what category are we in", or "nail down our angle." Works from a one-line product description or a full brief, and handles both brand-new products and repositioning existing ones. Designed for founders and product marketers at growth-stage SaaS companies who need positioning they can defend to a skeptic, not a tagline.
---

# Positioning Generator

A skill for producing sharp, defensible product positioning: the strategic choice of what you are, who you're for, and why you win, expressed as a statement a team can rally around.

Positioning is upstream of messaging. This skill makes the *choice*. It does not write the marketing copy. That hand-off goes to the Messaging Framework skill.

Read `references/positioning-frame.md` for the method before you start the work, and `references/positioning-template.md` for the output structure before you write the brief.

---

## Phase 1: Assess input and route

Read what the user gave you and route. Do not run a fixed interview.

### If input is rich
The user described the product, has some sense of competitors, and named or implied a customer. **Draft first.** Work the frame, make reasonable calls on anything missing, flag assumptions inline with `[ASSUMED \u2013 confirm]`, and deliver. A flagged draft they can react to beats a questionnaire.

### If input is thin
You know roughly what the product does and who it's for, but little else. **Draft anyway, with assumptions flagged.** Make explicit calls on competitive alternatives, segment, and category, mark each one, and produce the brief. Then offer the review loop.

### If core facts are missing
You genuinely cannot tell what the product does or who it's even roughly for. **Ask before drafting** — you cannot position a black box. Keep it to the few questions that unblock you:
1. In one line, what does the product do and for whom?
2. What would a customer use instead if you didn't exist? (Include DIY, manual, do-nothing.)
3. Is this new positioning, or are we fixing positioning that isn't working?

Ask only what you can't infer or safely assume. Never dump all three if you only need one.

### Always establish: new vs repositioning
If repositioning an existing product, capture the current positioning and *why* it's failing before proposing the replacement. The old frame is data. Repositioning that ignores why the current frame broke tends to break the same way.

---

## Phase 2: Build the positioning

Work the five components in order, each constraining the next. Full guidance is in `references/positioning-frame.md`; the short version:

1. **Competitive alternatives** — what they'd really use instead. Force DIY / manual / do-nothing onto the list. This is the anchor.
2. **Unique attributes** — concrete, checkable things you have that the alternatives don't. Not benefits, not adjectives.
3. **Value and proof** — map each attribute to a benefit the buyer cares about, and to proof or a path to proof. Drop attributes that map to nothing.
4. **Target market** — the beachhead segment that cares *most*, defined so a marketer could build a list. Pick one primary; name secondaries.
5. **Market category** — the frame that makes the value obvious. Prefer an existing category. Flag a new-category play loudly: high cost, high risk, rarely right.
6. **Relevant trend** (optional) — only if genuinely true and genuinely helpful. When in doubt, leave it out.

Then synthesize into the statement and run the pressure-test checklist in the frame reference. If the one-liner could be said word-for-word by a competitor, it isn't differentiation yet. Go back to attributes.

---

## Phase 3: Produce the brief

Write the brief using `references/positioning-template.md`. Lead with the positioning statement (the thing people quote), then the components, then the rationale.

**Output format:**
- Default: `.docx` via the docx skill. Read `/mnt/skills/public/docx/SKILL.md` before generating.
- `.md` only if the user asks.
- Save to `/mnt/user-data/outputs/` and present with `present_files`.

**Two forms of the statement, always:**
- Classic fill-in: *For [target] who [need], [product] is a [category] that [value]. Unlike [alternative], [product] [differentiator].*
- Short narrative: 2–3 plain sentences for internal alignment.

If three or more components were assumed rather than known, add the `Assumptions to verify` section listing every `[ASSUMED]` item in one place, so the user can confirm before sharing.

---

## Phase 4: Review loop

After the first draft:
1. Ask: "Does this frame feel right, or are we anchored against the wrong alternative?" The competitive-alternative anchor is the most common thing to get wrong, so probe it first.
2. Pressure-test the segment and category with one targeted follow-up if either is thin.
3. Revise. Positioning usually takes one real iteration to land. Expect it.

---

## House voice

Everything this skill writes follows Cadboro house voice: punchy, dry, short sentences, no em dashes. Declarative over decorated. The positioning statement especially must sound like a person wrote it, not a committee.

Banned words in output: "seamless", "robust", "intuitive", "game-changing", "revolutionary", "best-in-class", "cutting-edge", "leverage" (as a verb), "synergy". If one of these is the only word that fits, the thought underneath is too vague. Sharpen the thought, don't reach for the filler.

---

## Edge cases

- **Category creation.** When no existing frame fits, you may recommend a new category, but say plainly what it costs (you now have to teach the market) and what it takes to win. Default against it.
- **Multiple segments.** Pick a beachhead. Positioning for everyone is positioning for no one. Name the secondaries so they're not lost.
- **B2C / prosumer.** The frame still holds, but "competitive alternatives" lean harder on habits and do-nothing, and "proof" leans on experience over ROI math. Adjust tone, keep the structure.
- **Pre-product / pre-revenue.** Proof becomes proof-path. Be honest that value claims are hypotheses, and flag them.
- **Crowded category with a real incumbent.** Position against the category's trained pain ("the anti-[incumbent]") rather than claiming a brand-new space.

---

## Chaining

This skill is the keystone of the Cadboro product-marketing line. Its output feeds the Messaging Framework, Sales Enablement, Launch Content, and Battlecard skills. If those skills are present and the user is heading that way, *offer* to hand the positioning forward — but never auto-run the next skill. Offer, don't auto-chain.

It can also consume a Buyer Persona / ICP brief as input for the target-market component if the user has one.

---

## Reference files

- `references/positioning-frame.md` — the method: the five components, the process, the pressure-test checklist, and failure modes. Read before working the frame.
- `references/positioning-template.md` — the output structure and voice rules for the brief. Read before writing.
