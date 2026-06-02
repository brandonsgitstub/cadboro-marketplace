---
name: roadmap-generator
description: "Turn a backlog, prioritization output, or rough brain dump into a structured, communicable product roadmap. Use this skill whenever a PM asks to build a roadmap, sequence initiatives, plan a quarter, lay out Now/Next/Later, organize work into themes, or turn a prioritized list into a timeline. Trigger even if the input is messy — a pasted backlog, a list of features, customer themes, or the output of a RICE prioritization all work. Chains naturally from feature-prioritization: scores in, sequenced roadmap out. Produces a roadmap artifact (.md) plus a narrative rationale a PM can paste into a stakeholder update, with an optional .xlsx timeline. Designed for PMs at growth-stage SaaS companies who need a defensible roadmap they can share with eng and leadership without starting from a blank canvas."
---

# Roadmap Generator

A skill for turning a messy or prioritized list of initiatives into a structured product roadmap with a clear sequencing rationale stakeholders can actually read.

**Default outputs:**
1. **Roadmap** (`.md`) — the structured roadmap in the chosen view (Now/Next/Later or themed/quarterly), with each item carrying its rationale, dependencies, and target signal of success
2. **Sequencing Rationale** (narrative, in the same `.md` or as a short brief) — why things are ordered the way they are, what got pushed, and the assumptions a reader should challenge

**Optional output:** an `.xlsx` timeline (swimlane-style) when the PM wants a visual or date-anchored view to share.

A roadmap is a communication tool, not a backlog with dates stapled on. The job here is to make the *logic* of the sequence legible — so a skeptical engineer or exec understands not just what's planned, but why this and why now.

---

## Phase 1: Understand the Input and Pick a View

The PM's input could be a clean RICE output from `feature-prioritization`, a pasted backlog, customer feedback themes, or a paragraph-long brain dump. Before sequencing anything, do two things.

### Step 1: Normalize the items

Extract discrete initiatives. Each roadmap item should be one coherent body of work — not a bundle ("billing + notifications") and not a task-level sliver ("add a button"). If the input is a prioritization output, carry forward the scores and buckets; they're your strongest sequencing signal. If an item is too vague to place ("improve performance"), keep it but flag it for a target and a rough size.

### Step 2: Choose the roadmap view

The right view depends on the audience and how much the PM wants to commit to dates. Don't assume — ask one quick question if it isn't obvious from context. The three default views (full detail in `references/roadmap-guide.md`):

| View | When to use | Commits to dates? |
|------|-------------|-------------------|
| **Now / Next / Later** | Default. Internal alignment, fast-moving teams, leadership that wants direction without false precision | No — relative horizons |
| **Theme-based** | When the story is about strategic bets (e.g., "Activation", "Enterprise readiness") more than individual features | Loosely, grouped by theme |
| **Quarterly / time-boxed** | When there's a real deadline, dependency chain, or a board/customer commitment driving dates | Yes — by quarter or month |

If the PM hasn't said, default to **Now/Next/Later** and offer the others: *"I'll lay this out as Now/Next/Later since it keeps us honest about uncertainty — want a themed or quarterly view instead?"*

### Step 3: Anchor to a goal

A roadmap with no goal is just a list. Ask (or infer from the input): *"What's the outcome this roadmap is in service of — the OKR, the metric, or the strategic bet?"* Every Now item should connect to it. If the PM can't name one, that's a finding worth surfacing, not a blocker.

---

## Phase 2: Sequence the Work

Sequencing is where judgment lives. Priority score tells you what matters; it doesn't tell you what comes first. Order using these forces, roughly in this order of weight:

1. **Dependencies.** If A unblocks B, A comes first regardless of score. Surface the dependency explicitly — hidden dependencies are the most common reason roadmaps slip.
2. **Value and confidence.** High-value, high-confidence work earns an early slot. Use the prioritization score if you have one. High-value but *low-confidence* work often belongs in Next behind a validation step, not in Now — note that reasoning.
3. **Effort and team capacity.** Don't stack three large initiatives into the same Now horizon if one team carries them all. Call out when the plan implies more capacity than likely exists.
4. **Strategic sequencing.** Sometimes a lower-scored item goes early because it opens a market, de-risks a later bet, or builds a foundation. When you make this call, say so out loud — it's exactly the kind of decision a reader needs explained.
5. **Quick wins for momentum.** A cheap, visible win early can buy credibility for a longer roadmap. Reasonable to place one in Now even if it isn't top-scored — flag it as a deliberate momentum play.

For each item, capture: the horizon/bucket it lands in, a one-line **why it's here / why now**, its key **dependency** (if any), and the **signal of success** (what tells us it worked). These four things are what make the roadmap defensible.

### Validate the shape

Before generating output, sanity-check the whole thing:
- Is Now overloaded? A Now horizon with ten items isn't a plan, it's a wish. If it's crowded, push the weakest-justified items to Next and say why.
- Does every Now item ladder to the goal? If one doesn't, either it's misplaced or the goal is incomplete — flag it.
- Are there orphaned dependencies (an item in Now that depends on something in Later)? That's a sequencing bug — fix it or surface it.

---

## Phase 3: Generate Outputs

### Output 1: The Roadmap (.md) — always

Use the structure in `references/roadmap-template.md`. The markdown roadmap leads with the goal, then lays out the chosen view. Each item is scannable: name, one-line rationale, dependency, success signal. Keep it paste-ready — a PM should be able to drop it into a Notion doc or stakeholder update unedited.

### Output 2: Sequencing Rationale — always

This is the part that makes the roadmap survive scrutiny. It can live as a section in the same `.md` (default) or a short standalone brief. Cover: the through-line (what story the sequence tells), the top calls and why, what got deprioritized and on what grounds, the capacity/dependency risks, and the assumptions a reader should push on. Template in `references/roadmap-template.md`.

### Output 3 (optional): Timeline (.xlsx)

Generate only if the PM wants a visual or date-anchored view. Read `/mnt/skills/public/xlsx/SKILL.md` first, then build a swimlane-style timeline per `references/timeline-spec.md` (rows = themes or teams, columns = horizons or quarters, cells = initiatives, color-coded by horizon).

If the user came in through Cadboro's `.xlsx`/`.docx` toolkit and expects polished files, offer the timeline proactively. Otherwise lead with the markdown and ask.

---

## Phase 4: Review Loop

A roadmap is a draft for a conversation, not a verdict. After delivering:
1. Ask: *"Does this sequence match how you'd defend it to leadership? Anything ordered wrong given context I don't have?"*
2. When the PM moves an item, dig into why — is it a missing dependency, a capacity reality, or a strategic override of the score? Each implies a different fix. Document deliberate overrides in the rationale so the next reader understands the call wasn't an accident.
3. Re-output the affected sections rather than regenerating everything.

---

## Chaining from feature-prioritization

When the input is a RICE scorecard or prioritization brief, this skill is the natural next step. Carry forward the scores and Now/Next/Later buckets as the *starting* sequence — but don't treat them as final. Prioritization ranks by value; a roadmap re-orders that ranking against dependencies, capacity, and strategy. Where the roadmap diverges from the raw score order, note it: *"Ranked #4 by RICE, but sequenced first because it unblocks three downstream items."* That traceability is what makes the pair credible together.

---

## Reference Files

- `references/roadmap-guide.md` — The three roadmap views explained, with when-to-use guidance, examples, and common anti-patterns (date theater, the everything-is-Now trap, themeless feature dumps).
- `references/roadmap-template.md` — Markdown structure for the roadmap and the sequencing rationale.
- `references/timeline-spec.md` — Layout and formatting spec for the optional .xlsx swimlane timeline.
