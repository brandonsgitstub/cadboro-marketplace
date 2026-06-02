---
name: jtbd-interview-guide
description: "Generate a Jobs-to-be-Done interview guide or synthesize interview findings into job statements, themes, and opportunity areas. Two modes: (1) Guide mode — triggered when a PM wants to run JTBD interviews; produces a ready-to-use interview guide with screener criteria, warm-up questions, and core JTBD question sequences as a .docx. (2) Synthesis mode — triggered when a PM has completed interviews and wants to make sense of the findings; accepts raw transcripts, notes, or a structured per-interview template and produces a synthesized findings doc with job statements, themes, and opportunity areas as a .docx. Uses flexible JTBD principles adapted for modern SaaS PM practice — not strict Christensen/Ulwick orthodoxy. Designed for PMs at growth-stage companies running discovery on a specific product area, user segment, or upcoming initiative."
---

# JTBD Interview Guide

Two modes. Detect which one the PM needs, then follow the appropriate phase flow.

---

## Mode Detection

Read the PM's request and classify:

**→ Guide mode** if the PM is:
- Planning to run interviews (hasn't done them yet)
- Asking for interview questions, a discussion guide, or a screener
- Starting discovery on a new area

**→ Synthesis mode** if the PM is:
- Sharing interview notes, transcripts, or a filled template
- Asking to make sense of what they heard
- Looking for patterns, job statements, themes, or opportunity areas

If it's genuinely ambiguous, ask: *"Are you looking to run interviews, or do you have notes you'd like to synthesize?"*

---

## MODE 1 — Interview Guide

### Phase 1: Understand the research context

Before writing a single question, establish:

1. **What product area or initiative is this research for?**
   - If not stated, ask. Questions need to be anchored to a specific problem space, not generic.

2. **Who is the target user?**
   - Role, company type, maturity stage if relevant. Use this to calibrate screener criteria and question language.

3. **What does the PM already believe? (optional but useful)**
   - Any existing hypotheses about what job users are trying to get done. These should inform question design but never lead the interview — JTBD interviews surface what's true, they don't confirm what the PM already thinks.

If the PM provides enough context upfront, proceed directly. If 2+ of the above are missing, ask for them in a single message before writing.

### Phase 2: Write the guide

Read `references/question-sequences.md` and `references/screener-templates.md` before writing.

Structure the guide in four sections:

**Section 1 — Screener**
Criteria to recruit participants who will give high-signal JTBD data. See `references/screener-templates.md` for patterns by context.

The goal of a JTBD screener is to find people who have *recently made a meaningful decision* in the relevant space — not just anyone who uses the product. Recent decision-makers remember context, emotion, and trade-offs. Users in steady state do not.

**Section 2 — Warm-up (5–10 min)**
3–4 questions to build rapport and establish shared context. Should cover:
- Who they are and what they do (in their own words, not a job title)
- Their team/workflow context
- A recent relevant activity to prime episodic memory

Warm-up questions are open-ended but not yet JTBD. They orient the interview, not gather findings.

**Section 3 — Hiring trigger sequence (15–20 min)**
The core of a JTBD interview. Goal: understand the moment the person decided to look for a new or better solution — what caused it, what they were trying to achieve, and what forces were pushing and pulling on that decision.

See `references/question-sequences.md` → Hiring Trigger section.

Key principles for this section:
- Always anchor to a *specific past event*, not hypotheticals or general habits. "Tell me about the last time you..." beats "What do you typically do when..."
- The trigger moment is the most important data point in the interview. Spend time here. Don't rush to product questions.
- Emotions and social context are as important as functional needs. A user switches tools because a manager criticized their reports, not just because the reports were slow.

**Section 4 — Progress and struggle sequence (15–20 min)**
Once the hiring trigger is established, explore what the user was trying to accomplish and where they got stuck. Goal: map the progress they were trying to make, the struggles along the way, and the trade-offs they accepted.

See `references/question-sequences.md` → Progress and Struggle section.

**Interviewer notes throughout:**
- Mark questions the interviewer can skip if time runs short with `[skip if short on time]`
- Mark moments where silence is productive with `[pause — let them think]`
- Add a 2-sentence framing note at the start of each section explaining its purpose to the interviewer (not read aloud to the participant)

### Phase 3: Output

Generate a `.docx` using the docx skill at `/mnt/skills/public/docx/SKILL.md`. Save to `/mnt/user-data/outputs/`. Filename: `jtbd-guide-[context].docx`

Include a one-page **Interviewer briefing** at the front of the doc covering:
- Purpose of JTBD interviews (2–3 sentences, adapted to this specific research context)
- The single most important thing to remember: *anchor to specific past events, not hypotheticals*
- What success looks like: the interviewer should come away knowing the hiring trigger, what job the person was trying to get done, and the biggest struggle along the way
- ⚠️ **Time-sensitive assumption callout** if any details in the guide (target segment, specific product area, research context) were inferred rather than stated by the PM

---

## MODE 2 — Synthesis

### Phase 1: Receive interview data

Accept either:
- **Raw input:** transcript, notes, or a summary the PM pastes directly into the chat
- **Structured input:** a filled per-interview template (see `references/synthesis-template.md`)

If the PM has raw notes but no template: offer them the template first. *"Before I synthesize, would you like the per-interview template to structure your notes? It takes 5–10 min per interview and makes the synthesis significantly sharper. Or if you'd prefer, paste your notes as-is and I'll work with what you have."*

If they want to proceed with raw notes: accept them and proceed. Don't block on the template.

Accept notes from a minimum of 2 interviews before synthesizing. If only 1 interview is provided, note that patterns from a single interview are directional only and should not drive decisions.

### Phase 2: Extract and code

Before writing the synthesis doc, internally work through the following for each interview:

1. **Hiring trigger** — What specific event or situation caused this person to seek a new or better solution? What changed?
2. **Functional job** — What were they practically trying to accomplish?
3. **Emotional job** — How did they want to feel (or stop feeling) as a result?
4. **Social job** — How did this decision affect how they appeared to others (team, manager, peers)?
5. **Progress blockers** — What got in the way of making progress?
6. **Workarounds** — What did they do instead? What does that reveal about unmet needs?
7. **Switch moment** — If they changed tools or approaches, what pushed them over the line?

Do this extraction silently — don't output it. Use it to inform the synthesis doc.

### Phase 3: Write the synthesis doc

Read `references/synthesis-format.md` before writing.

Structure:
1. **Research context** — What was studied, how many interviews, who was interviewed (roles/segments, anonymized)
2. **Job statements** — 2–5 core jobs-to-be-done surfaced across interviews, written in job statement format: *"When [situation], I want to [motivation], so I can [expected outcome]."*
3. **Key themes** — 3–6 cross-interview patterns. Each theme needs: a clear label, 2–3 sentences of explanation, and at least one anonymized verbatim quote that illustrates it
4. **Struggle map** — Where in the progress journey do users consistently get stuck? Organized by stage, not by feature
5. **Opportunity areas** — 2–4 areas where the gap between what users are trying to accomplish and what currently exists is largest. Written as opportunity statements, not feature ideas: *"Help [persona] [do job] without [current struggle]."*
6. **What we didn't hear** — Notable absences: jobs or struggles the team expected to find but didn't surface in interviews. These are as valuable as what did surface.
7. **Recommended next steps** — 2–3 concrete actions (e.g. run 3 more interviews to validate job X, bring opportunity area Y to the next roadmap review)

### Phase 4: Output

Generate a `.docx` using the docx skill at `/mnt/skills/public/docx/SKILL.md`. Save to `/mnt/user-data/outputs/`. Filename: `jtbd-synthesis-[context].docx`

After delivering: *"Does this match what you heard? Anything that feels misrepresented or missing from the opportunity areas?"*

---

## Reference Files

- `references/jtbd-primer.md` — Core JTBD concepts adapted for SaaS PM practice
- `references/screener-templates.md` — Screener criteria patterns by research context
- `references/question-sequences.md` — Full question bank: hiring trigger, progress, struggle
- `references/synthesis-template.md` — Per-interview fill-in template
- `references/synthesis-format.md` — Synthesis doc structure with quality standards
