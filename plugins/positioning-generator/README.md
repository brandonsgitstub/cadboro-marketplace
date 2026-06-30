# Positioning Generator

Sharp, defensible product positioning, fast. Part of the [Cadboro Labs](https://cadborolabs.com) product-marketing toolkit.

This skill makes the positioning *choice*: what you are, who you're for, and why you win. It works the Dunford-style frame (competitive alternatives, unique attributes, value, target segment, market category), then writes a positioning brief with a quotable statement on top. It handles brand-new products and repositioning existing ones.

Positioning is upstream of messaging. This skill produces the strategy; the Messaging Framework skill produces the copy.

## Install

```
/plugin marketplace add brandonsgitstub/cadboro-marketplace
/plugin install positioning-generator@cadboro-labs
```

Then invoke it directly:

```
/positioning-generator:positioning-generator
```

…or just describe the task ("help me position this", "what category are we in", "we sound like everyone else") and Claude triggers it.

## What you get

- A positioning statement in two forms: the classic fill-in and a short narrative.
- The five components, filled and pressure-tested.
- Category rationale and a beachhead segment defined so a marketer could build a list.
- A handoff section teeing up messaging, plus any assumptions flagged for you to verify.

Output is a `.docx` brief by default, `.md` on request.

## How it works

- **Rich input** → drafts first, flags assumptions inline.
- **Thin input** → drafts anyway with assumptions marked, then asks only what unblocks it.
- **Black box** → asks the few questions it needs before drafting.
- **Repositioning** → captures why the current frame is failing before proposing the new one.

## License

[GPL-3.0-or-later](https://github.com/brandonsgitstub/cadboro-marketplace/blob/main/LICENSE).

Built by [Brandon Gains](https://www.linkedin.com/in/brandon-gains/) · [Cadboro Labs](https://cadborolabs.com)
