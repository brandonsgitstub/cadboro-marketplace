# PRD Template — Cadboro Labs

Use this template as your structural guide when generating PRDs. Adapt section depth to initiative complexity. Omit sections that genuinely don't apply (e.g., a pure backend change may not need a UX section). Never leave a section blank without a note explaining why.

---

## [Feature / Initiative Name]
**Status:** Draft / In Review / Approved  
**Author:** [Name]  
**Last Updated:** [Date]  
**Target Release:** [Quarter or Date]  
**PM Owner:** [Name]  
**Eng Lead:** [Name]  
**Design Lead:** [Name]  

---

## 1. Problem Statement

*In 2–4 sentences: what problem exists, for whom, and why it matters to the business now. This is the "why we're doing this" section — it should make a skeptic nod.*

**Example:**
> Growth-stage PMs spend 3–5 hours writing PRDs that still lack the specificity engineers need to begin work. This creates back-and-forth that delays sprint starts by 1–2 days. As teams scale, this overhead compounds — and inconsistent doc quality creates alignment risk across squads.

---

## 2. Goals & Success Metrics

What does success look like? Tie metrics to business outcomes, not activity.

| Goal | Metric | Current Baseline | Target | Timeframe |
|------|--------|-----------------|--------|-----------|
| Example | Example | Example | Example | Example |

**Primary metric:** [The one number that matters most]  
**Counter-metrics:** [What we're watching to make sure we're not trading off something important]

---

## 3. Non-Goals

Explicitly state what this initiative will NOT address. This is as important as what it will address.

- We are not building X in this iteration.
- We are not solving Y (tracked separately as [link]).
- Out of scope: Z.

---

## 4. Background & Context

*Optional but useful for large initiatives.* Summarize prior research, customer feedback themes, data signals, or prior attempts that inform this direction. Keep it tight — link to full docs rather than reproducing them.

---

## 5. Target Users

**Primary persona:** [Specific description — role, company stage, context of use]

**Secondary personas (if any):** [Who else is affected or benefits]

**User needs being addressed:**
- [Job to be done or pain point 1]
- [Job to be done or pain point 2]

---

## 6. Proposed Solution

High-level description of what we're building. This is not a technical spec — it's a clear narrative of the solution that any stakeholder could understand.

Include:
- Core user workflow / experience (what the user does, sees, decides)
- Key product decisions made (and why)
- Any notable alternatives considered and rejected (briefly)

---

## 7. Requirements

### Functional Requirements

Must-haves for this initiative to achieve its goals. Write from the user's perspective where possible.

- [ ] FR-01: [Requirement]
- [ ] FR-02: [Requirement]
- [ ] FR-03: [Requirement]

### Non-Functional Requirements

Performance, reliability, security, accessibility, etc.

- [ ] NFR-01: [Requirement]
- [ ] NFR-02: [Requirement]

### Out of Scope (requirements explicitly deferred)

- [ ] Deferred: [Requirement — link to future ticket or initiative if exists]

---

## 8. UX / Design Considerations

*Skip if purely backend/infra initiative.*

- Link to mocks, wireframes, or Figma: [link]
- Key UX decisions or constraints
- Edge cases the design must handle
- Accessibility requirements

---

## 9. Technical Considerations

High-level technical notes for the eng team. This is not a technical design doc — it's a heads-up on known complexity.

- Key systems / services affected
- Known technical risks or unknowns
- Data model changes (if any)
- API changes (if any)
- Third-party dependencies

---

## 10. Dependencies

| Dependency | Type | Owner | Status | Notes |
|-----------|------|-------|--------|-------|
| [Team / system] | Blocking / Informational | [Name] | [On track / At risk / TBD] | |

---

## 11. Milestones & Timeline

| Milestone | Target Date | Owner | Notes |
|-----------|------------|-------|-------|
| Kickoff | | | |
| Design complete | | | |
| Eng complete | | | |
| QA / staging | | | |
| Launch | | | |

---

## 12. Open Questions

Track unresolved decisions here. Move to resolved or close as the initiative progresses.

| # | Question | Owner | Due | Resolution |
|---|----------|-------|-----|-----------|
| 1 | [Question] | [Name] | [Date] | [Open / Resolved: answer] |

---

## 13. Appendix

Links to supporting materials: customer research, competitive analysis, data deep-dives, prior PRDs, related tickets, etc.
