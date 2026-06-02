# JTBD Primer — SaaS-Adapted

This is not a textbook summary of Jobs-to-be-Done theory. It's a working reference for what JTBD concepts mean in practice when doing discovery on a SaaS product.

---

## The core idea

People don't buy products. They hire them to make progress in a specific situation. When a PM understands what progress a user is trying to make — and what's getting in the way — they can design solutions that actually fit the job, rather than solutions that fit what the PM imagined the job to be.

The job is defined by the situation, not the user. The same person might hire different tools for different jobs. "I need to write a report" and "I need to look credible in front of my board" are different jobs — even if both end up using the same product.

---

## The three job layers

**Functional job** — the practical thing they're trying to get done.
*"Consolidate pipeline data from three sources into one report before the Monday call."*

**Emotional job** — how they want to feel (or stop feeling) as a result.
*"Feel confident walking into that meeting rather than scrambling."*

**Social job** — how this affects how they appear to others.
*"Look like the person who has their act together, not the one who's always chasing data."*

In B2B SaaS, the social job is often underweighted. It drives a lot of switching behaviour, tool adoption, and upgrade decisions. "My manager noticed I was using spreadsheets" is a social trigger that leads to a product purchase. Surface it.

---

## The hiring trigger

The hiring trigger is the specific event or situation that caused someone to seek a new or better solution. It's the most important thing to find in a JTBD interview.

Why: people don't make decisions in the abstract. They make them in response to something that changed — a new job, a team growing, a process breaking down, a manager's comment, a missed deadline. The trigger reveals the situation that made progress feel urgent.

**Good triggers are specific and past-tense:**
- "We grew from 4 to 14 reps and my old system broke"
- "I missed a renewal because I had no visibility into contract dates"
- "My VP asked why our activation rate was lower than the competition"

**Weak triggers are generic and present-tense:**
- "I needed something more scalable"
- "We wanted better reporting"

Generic triggers produce generic insights. Always push toward the specific event.

---

## The progress-making forces

Four forces act on any decision to change how someone does something:

**Push** (away from the old way)
What about the current situation is frustrating, broken, or insufficient? What's the pain?

**Pull** (toward the new way)
What does the new solution promise that makes progress feel possible?

**Anxiety** (about switching)
What are the fears and risks of changing? What might go wrong?

**Habit** (of the old way)
What's the inertia keeping them where they are? What's comfortable or familiar about the current approach?

In practice, a switch happens when push + pull > anxiety + habit. Understanding all four forces explains why someone moved — and why others in the same situation haven't yet.

For SaaS PMs, anxiety and habit are the most underexplored. They explain churn, failed activations, and why a feature that solves a real pain still doesn't get adopted.

---

## Job statements — the format

A job statement captures what a user is trying to accomplish in their language, not product language.

Format: *"When [situation], I want to [motivation], so I can [expected outcome]."*

**Good job statement:**
*"When I'm preparing for a quarterly business review, I want to pull together a clean performance summary without spending half a day on it, so I can show up to the meeting focused on strategy rather than data wrangling."*

**Weak job statement:**
*"Users want a better dashboard."*

The weak version is a solution (dashboard) masquerading as a job. A job statement contains no product or feature language — only situation, motivation, and outcome.

---

## What JTBD is not

- **Not a persona framework.** Personas describe who someone is. JTBD describes what they're trying to do in a specific situation. The same persona might have multiple jobs. Different personas might share the same job.
- **Not a feature request framework.** Users will tell you features during a JTBD interview. That's noise. Your job is to hear the underlying motivation behind the feature request.
- **Not a substitute for usability research.** JTBD answers "are we building the right thing?" Usability research answers "are we building it right?" Both are necessary. Neither replaces the other.

---

## When to use JTBD interviews

Strong signal moments:
- You're entering a new market or user segment
- Activation or retention is underperforming and you don't know why
- You're about to start a new initiative and want to validate the underlying job before scoping
- You've heard conflicting things from customers and need to untangle them
- You want to find expansion opportunities within an existing user base

Weak signal moments:
- You already have high-quality qualitative data and need quantitative validation → use surveys
- You need to test a specific UI flow or copy → use usability testing
- You want to understand churn reasons post-cancellation → use exit interviews (related but distinct)
