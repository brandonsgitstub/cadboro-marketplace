---
name: prd-generator
description: Generate a well-structured, ready-to-ship Product Requirements Document (PRD) for any feature or initiative. Use this skill whenever a user asks to write, create, draft, or produce a PRD, product spec, requirements doc, or feature brief — even if they just say something like "help me write up this feature" or "I need to document this initiative." Also trigger when someone shares a rough feature idea and needs it formalized for engineering or design handoff. Works across methodologies (Agile, Shape Up, OKR-driven, etc.) and scales to the complexity of the initiative. Designed for PMs at growth-stage companies who need rigorous docs without bureaucratic bloat.
---

# PRD Generator

A skill for producing clear, actionable Product Requirements Documents that align engineering, design, and stakeholders — fast.

This skill guides Claude through a structured interview to gather just enough context, then produces a complete PRD in a well-organized document (`.docx` by default, Markdown if requested).

---

## Phase 1: Gather Context

Before writing anything, assess the complexity of the initiative and route accordingly.

### Step 1: Classify the initiative

Read the prompt and classify it into one of two tiers:

**Tier 1 — Single-surface feature** (e.g., "add in-app notifications", "build a search bar", "redesign the onboarding flow")
- Primarily affects one product area
- Stakeholders are mainly eng + design
- Business decisions (limits, pricing, tier structure) are not core to the spec

**Tier 2 — Cross-functional or business-model initiative** (e.g., feature gating, pricing changes, billing integration, permissions system, API versioning, multi-team platform work)
- Touches multiple systems or teams
- Involves business decisions that the PM — not Claude — must make (e.g., which features go in which tier, what the limits are, whether to grandfather existing users)
- Getting the assumptions wrong could cause real harm if the doc is shared with stakeholders

### Step 2: Route based on tier

**Tier 1 → Draft-first approach.**
Make reasonable product assumptions, write the full PRD, flag gaps with `[TBD]`, and offer a review loop. Don't block on an interview — a draft is faster.

**Tier 2 → Brief check-in first.**
Before drafting, ask 2–4 targeted questions to nail the decisions that can't be assumed. Keep it tight — only ask what you can't reasonably infer or safely placeholder. Frame it like: *"Before I draft this, a few quick questions — these are decisions that'll shape the whole doc and that only you can answer."*

Questions to prioritize for Tier 2 initiatives:
1. **The core business decisions** — e.g., for feature gating: "What features are you thinking go in each tier, and do you have target limits in mind (seats, contacts, etc.)? I'll draft a matrix from whatever you have — even rough notes."
2. **The stakeholder landscape** — "Who else needs to sign off on this before it goes to eng? (Revenue, CS, Legal?)" — shapes the open questions and dependencies sections.
3. **Existing state** — "What's the current behavior today, and are there existing users/contracts that would be affected by this change?" — shapes the migration/grandfather strategy.
4. **The hard constraint** — "Is there a deadline or release dependency driving this?" — shapes milestones.

If the user says "just draft it" for a Tier 2 initiative, respect that — but add a visible `⚠ Assumptions` callout box at the top of the doc listing every business decision you made that they should verify before sharing.

### Core interview questions (for both tiers, if context is thin)

Ask conversationally — don't dump them all at once:

1. **What's the initiative?** — One sentence: what are we building or changing?
2. **Why now?** — What's the triggering insight, problem, or opportunity?
3. **Who is this for?** — Primary user segment(s). Be specific.
4. **What does success look like?** — What metric(s) move? By how much? In what timeframe?
5. **What's in scope / out of scope?** — What are the known boundaries?
6. **What are the key constraints?** — Timeline, team size, technical limitations, dependencies.
7. **Do you have any existing notes, mocks, or prior research?** — If yes, ask them to paste or attach.

---

## Phase 2: Produce the PRD

Once you have enough context (even if incomplete), write the PRD. Use the template in `references/prd-template.md` as your structural guide.

**Key principles:**
- Write for the reader who wasn't in the room. Assume the audience is a senior engineer or designer picking this up cold.
- Be specific where it matters (metrics, personas, scope) and avoid vague qualifiers ("seamless", "intuitive", "robust").
- Flag unknowns explicitly with `[TBD]` or `[Open Question]` rather than papering over them.
- Keep the doc scannable: clear headers, short paragraphs, bullet lists for requirements.
- Match the depth to the initiative. A 3-week feature doesn't need the same PRD as a 6-month platform change.

**Handling assumed business decisions:**

Some content in a PRD requires real business decisions that Claude cannot make — pricing tiers, feature limits, which customers are grandfathered, contractual constraints. When you've had to invent specific values for these (e.g., "Starter plan: up to 2,500 contacts"), do two things:

1. Mark the individual item inline with `[ASSUMED — confirm with Revenue/CS/Legal]` rather than just `[TBD]`. The distinction matters: `[TBD]` means "we haven't decided yet." `[ASSUMED]` means "Claude made this up and it needs verification before this doc is shared."
2. If the doc contains 3 or more assumed business decisions, add a visible `⚠ Assumptions to Verify` callout box immediately after the metadata table at the top of the document. List every `[ASSUMED]` item in one place so the PM can review them before sharing with stakeholders.

**Output format:**
- Default: `.docx` file (use the docx skill — read `/mnt/skills/public/docx/SKILL.md` before generating)
- If the user asks for Markdown: `.md` file
- Always save to `/mnt/user-data/outputs/` and present with `present_files`

---

## Phase 3: Review Loop

After delivering the first draft:
1. Ask: "Does this capture the initiative accurately? What's missing or off?"
2. Incorporate feedback and revise.
3. If a section is thin (e.g., success metrics are vague), flag it and ask a targeted follow-up rather than leaving it weak.

---

## Reference Files

- `references/prd-template.md` — Full PRD template with section-by-section guidance. Read this before writing.
