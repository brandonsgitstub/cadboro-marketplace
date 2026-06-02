# Roadmap & Rationale Template

Use this as the structural guide for the `.md` output. Adapt section depth to the input. The goal is a roadmap a stakeholder can read in a few minutes and a rationale that survives a skeptical question.

---

## Roadmap (Now / Next / Later view)

```markdown
# [Product / Team] Roadmap
**Goal this roadmap serves:** [the OKR, metric, or strategic bet every Now item ladders to]
**View:** Now / Next / Later
**Last updated:** [date]

## Now
*Active or starting imminently. High confidence.*

- **[Initiative]** — [one line: what it is]
  - *Why now:* [the sequencing reason — value, dependency unblock, or strategic call]
  - *Depends on:* [blocker, or "none"]
  - *Success signal:* [what tells us it worked]

- **[Initiative]** — …

## Next
*On deck. Intended, not date-committed. Often gated behind a Now item or a validation step.*

- **[Initiative]** — [what it is] — *Gated by:* [what needs to happen first]

## Later
*Directional. Believed to matter; not yet scoped or sequenced.*

- **[Initiative]** — [what it is] — *Open question:* [what we'd need to learn before committing]
```

For a **theme-based** view, replace the Now/Next/Later headers with theme headers (e.g., `## Activation`, `## Enterprise Readiness`) and, optionally, nest Now/Next/Later inside each theme.

For a **quarterly** view, replace horizons with `## Q3 2026`, `## Q4 2026`, etc., and only date-anchor items that are genuinely understood. Mark speculative later quarters as tentative.

---

## Sequencing Rationale

```markdown
## Why this sequence

**The through-line:** [In 2–3 sentences, the story the order tells. What's the strategy the sequence expresses?]

**Top calls:**
- [Initiative] is first because [reason — often a dependency or de-risking move, not just "highest score"].
- [Initiative] moved ahead of [other] because [explicit override of raw priority, with the business reason].

**What we deprioritized and why:**
- [Initiative] → Later because [specific reason: low confidence pending validation, low reach, blocked by X]. Not "low score" — name the actual cause.

**Risks in this plan:**
- *Capacity:* [does Now imply more than the team can carry? Be honest.]
- *Dependencies:* [any cross-team or technical blockers that could reorder things]

**Assumptions to challenge:**
- [The 1–3 things that, if wrong, would change the sequence. Invite the reader to push on these.]
```

---

## Notes for the writer

- Lead with the **goal**. A roadmap whose first line isn't an outcome is a list.
- Every Now item must connect to the goal. If one doesn't, flag it inline rather than hiding it.
- Prefer specific success signals ("activation rate from 28% → 35%") over vague ones ("better onboarding").
- When the sequence diverges from a prioritization score, say so explicitly with the score reference — that traceability is what makes the roadmap and the prioritization credible as a pair.
- Keep it scannable. Short lines, clear hierarchy, no walls of text.
