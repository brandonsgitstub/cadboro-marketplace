# Synthesis Doc Format

Structure and quality standards for the JTBD synthesis output.

---

## Document structure

### 1. Research context (½ page)

Cover:
- What was studied and why (1–2 sentences)
- How many interviews were conducted and over what period
- Who was interviewed — roles, company sizes, segments (anonymized — no names)
- Screener criteria used (what made someone qualify)
- Any important caveats (e.g. "5 of 6 participants were from mid-market companies — enterprise perspective is underrepresented")

Do NOT include: participant names, company names, or any identifying information.

---

### 2. Job statements (core section)

Present 2–5 job statements surfaced across the interviews.

**Format:** *"When [situation], I want to [motivation], so I can [expected outcome]."*

For each job statement include:
- The statement itself
- How many interviews surfaced this job (e.g. "Heard across 4 of 6 interviews")
- 1–2 sentences of context explaining what makes this job significant
- One supporting quote (anonymized, verbatim)

**Quality bar for job statements:**
- No product or feature language — only situation, motivation, outcome
- The situation must be specific enough to be recognizable to a PM who knows the user
- The motivation must be stated in the user's terms, not the PM's terms
- Different jobs must be genuinely distinct — not variations of the same job with different wording

**Common mistakes to avoid:**
- ❌ "Users want a faster dashboard" — this is a feature request, not a job
- ❌ "Users want to feel confident" — too vague; confident about what, in what situation?
- ✅ "When I'm preparing for a quarterly review with my VP, I want to pull together a clean performance summary quickly, so I can walk in focused on the conversation instead of the data"

---

### 3. Key themes (2–3 pages)

3–6 cross-interview patterns. Each theme is a recurring observation — not a job statement, not a feature idea.

**For each theme:**
- **Label** — 3–5 words, active voice (e.g. "Trust breaks before features fail", "Switching cost is social, not technical")
- **Explanation** — 2–3 sentences describing the pattern and why it matters
- **Evidence** — how many interviews surfaced it, in what form
- **One illustrative quote** — verbatim, anonymized (e.g. "P3, mid-market SaaS, 45 employees")
- **What this means for the product** — 1 sentence only; resist the urge to solve here

**Quality bar for themes:**
- Themes must be grounded in the data — not the PM's prior beliefs
- A theme that appeared in only 1 interview should be noted as "early signal" rather than a confirmed pattern
- Themes should be surprising or at least non-obvious — if every PM on the team already knows it, it's not a finding, it's confirmation

---

### 4. Contradictions & Tensions *(conditional — include when triggered)*

**When to add this section:**

Scan the interview data for direct contradictions before writing the synthesis. Add this section — inserted between Key Themes and the Struggle Map — whenever **two or more** of the following are true:

- Two participants directly contradict each other on a dimension that would affect a product decision (e.g. speed vs. accuracy, self-serve vs. specialist, tools vs. process)
- The same product or approach produced materially different outcomes for different participants
- Participants in different roles or segments have incompatible definitions of the same concept (e.g. "accurate," "useful," "done")
- A minority view (1–2 participants) is strong enough that flattening it into the majority would misrepresent the data

**When NOT to add this section:**

- Variation in emphasis or phrasing that doesn't represent a genuine disagreement
- One participant is clearly an outlier with an unusual context that explains the divergence (flag in Research Context caveats instead)
- The contradiction resolves cleanly on a known segmentation variable (e.g. company size, role) — note the segmentation in the theme, don't create a tension entry

**The critical rule: never flatten a real contradiction into false consensus.** A synthesis doc that papers over genuine disagreement misleads product teams into building for a user who doesn't exist. Tensions left visible are more useful than themes made artificially tidy.

**What each tension entry must include:**

- **Label** — name the tension in 5–8 words. Make it specific enough that two people reading it would agree on what's being disputed. Bad: "Different views on data." Good: "Speed vs. accuracy — which failure mode is worse?"
- **View A** — the position, who holds it (anonymized role/company type), and a verbatim quote
- **View B** — the opposing position, who holds it, and a verbatim quote
- **Why both views are valid** — 1–2 sentences explaining that this isn't a misunderstanding. Both participants are rational actors responding to their real context. Don't dismiss either side.
- **Implication** — what this tension means for the product team. Frame it as a question or a decision that needs to be made, not a conclusion. Examples:
  - *"A single product trying to serve both views may be doing neither well. This may be a segmentation decision."*
  - *"The divergence may be explained by pre-existing data quality. If so, there may be a product intervention that changes the outcome."*
  - *"Both participants may be right given their company stage. The product question is whether to optimize for one stage or serve both differently."*

**Format note:** In the output document, use a two-column side-by-side layout for View A and View B where possible — the visual contrast reinforces that these are genuinely different positions, not variations on a theme.

**Cover page note:** When a Tensions section is present, add a callout to the document cover or executive summary: *"This synthesis contains genuine contradictions between participants. Section [N] documents them explicitly. Do not flatten the contradictions into false consensus — the disagreements are findings."*

---

### 5. Struggle map

Where in the progress journey do users consistently get stuck? This section is organized by stage, not by feature or product area.

**Format:**

| Stage | What users are trying to do | Where they get stuck | Workaround used |
|-------|----------------------------|---------------------|-----------------|
| [Stage name] | [Job at this stage] | [Specific friction] | [What they do instead] |

Stages should reflect the user's journey, not the product's IA. Examples:
- "Getting data in" / "Making sense of it" / "Communicating findings" / "Acting on it"
- "Realizing there's a problem" / "Diagnosing the cause" / "Deciding what to fix" / "Measuring the fix"

The workaround column is often the most valuable. It reveals what users do when the product doesn't serve the job — and those workarounds are usually the clearest product opportunity signal.

---

### 6. Opportunity areas

2–4 opportunity areas where the gap between what users are trying to accomplish and what currently exists is largest.

**Format:** *"Help [persona] [do job] without [current struggle]."*

Each opportunity area should include:
- The opportunity statement
- Which job(s) it connects to (by reference to Section 2)
- Why the current solution fails here — in 2–3 sentences
- A rough indication of how broadly this applies (e.g. "surfaced in 5 of 6 interviews" vs. "specific to the mid-market segment")

**Quality bar:**
- Opportunity areas are not features. Do not name a specific UI element, workflow, or solution.
- An opportunity area should be solvable in multiple ways — that's the point. The PM's job is to find the best solution; the research's job is to define the job clearly.
- If an opportunity area could be directly copy-pasted into a JIRA ticket, it's too specific.

---

### 7. What we didn't hear

Notable absences — jobs or struggles the team expected to find but didn't surface in interviews.

This section is short (3–5 bullet points) but often the most provocative.

Format: *"We expected to hear [X]. We didn't. This may mean [possible interpretation]."*

Examples:
- "We expected to hear that users were frustrated by slow load times. This wasn't mentioned unprompted in any interview. Speed may not be a meaningful differentiator for this segment."
- "We expected the integration pain point to be a primary trigger. It appeared only as a secondary frustration after the core job was established. The job is not 'connect my tools' — it's something more upstream."

Possible interpretations should be offered with appropriate uncertainty — these are hypotheses, not conclusions.

---

### 8. Recommended next steps

2–3 concrete, actionable next steps. Not a feature roadmap. Not a backlog.

Examples of good next steps:
- "Run 3 more interviews specifically with [segment] to validate whether job X generalizes beyond mid-market"
- "Bring opportunity area 2 to the next roadmap review for prioritization against the current backlog"
- "Share the struggle map with the design team before the next discovery sprint on [feature area]"
- "Test job statement 1 with a broader audience via a survey to assess prevalence"

---

## Quality standards for the synthesis doc overall

**Conflict-aware:** Before writing, scan the data for direct contradictions. If two participants hold genuinely opposing views on a dimension that would affect a product decision, do not average them — document both in a Tensions section. A synthesis that papers over real disagreement is worse than no synthesis. The disagreements are findings.

**Grounded:** Every claim traces back to specific interview data. No editorializing about what users "probably" think.

**Quotable:** The synthesis doc should contain 6–10 verbatim quotes distributed across sections. Quotes are the evidence. They also make the doc readable to stakeholders who weren't in the interviews.

**Actionable:** A PM should be able to walk out of a synthesis doc review knowing what to do next. If the doc produces shrugs, it's too abstract.

**Honest about limits:** Sample size, segment coverage, and interview quality all affect confidence. Flag limitations clearly rather than overstating certainty.

**Written for a skeptic:** Assume the reader didn't do the interviews and is looking for reasons to dismiss the findings. Pre-empt objections with evidence.
