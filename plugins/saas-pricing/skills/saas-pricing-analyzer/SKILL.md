---
name: saas-pricing-analyzer
description: Analyzes SaaS subscription pricing data to produce tier effectiveness diagnostics, concentration risk assessments, and optimization recommendations with projected revenue impact. Use when the user shares pricing tiers, customer counts, MRR/ARR figures, or billing platform exports (Stripe, Chargebee, Paddle) and asks for a pricing sanity check, pricing strategy review, tier optimization, board/fundraising prep, or a full pricing deep dive.
---

# SaaS Pricing Analyzer

A skill for turning real subscription revenue data into a pricing diagnostic with tier effectiveness analysis, concentration risk assessment, optimization recommendations, and projected revenue impact.

This skill takes your actual pricing data — from a simple tier breakdown to a full billing platform export — and tells you which tiers are working, which are dead weight, and where you're leaving money on the table.

---

## Operating Principles

When analyzing pricing data, follow these principles:

- **Think in tiers, not averages.** A blended ARPU of $80 can mask a $29 tier with 60% of customers contributing 22% of revenue. Always decompose.
- **Revenue concentration is a risk metric.** If one tier or one customer segment accounts for >50% of revenue, flag it. Diversification matters.
- **Price gaps reveal strategy.** The gap between your cheapest and most expensive tier tells you more about your positioning than either price alone. Small gaps compress willingness-to-pay. Large gaps signal different buyer personas.
- **Benchmark against segment, not Silicon Valley.** A $35 ARPU is excellent for SMB self-serve. Don't compare it to enterprise ACV.
- **Show what the change would do.** Every pricing recommendation should include a projected revenue impact with stated assumptions. "Raise mid-tier by $10" means nothing without "adding ~$X/mo if retention holds."

---

## Phase 1: Classify and Route

Read the user's input and classify into one of two tiers:

### Tier 1 — Quick Pricing Check

**Trigger:** User provides fewer than 3 tiers with basic price/customer data, asks for a "quick look" / "pricing sanity check" / "how does my pricing look", or provides only top-line pricing without detail.

**Behavior:** Skip the interview. Produce a focused pricing diagnostic immediately. Output as Markdown in the chat.

### Tier 2 — Full Pricing Strategy Report

**Trigger:** User provides 3+ tiers with customer counts, mentions pricing restructure / board presentation / fundraising, asks for optimization recommendations or projected impact, provides billing period breakdowns (monthly vs annual), or asks for a "full analysis" / "pricing deep dive" / "pricing strategy report".

**Behavior:** Run a brief structured interview (Phase 2), then produce a comprehensive `.docx` report.

---

## Phase 2: Gather Context (Tier 2 Only)

Ask 3–5 targeted questions to fill gaps. Only ask what's missing — if the user already provided the data, skip that question. Frame it conversationally: *"A few quick questions so I can build a useful analysis — skip any you don't know."*

**Question categories** (ask only what's needed):

1. **Pricing structure** — How many pricing tiers do you have? What's the price and customer count for each? Are these monthly prices? Do you offer annual plans?
2. **Customer distribution** — How many total paying customers? How are they distributed across tiers? Has the distribution shifted in the last 6 months?
3. **Cost structure** — What are your fixed monthly costs (infrastructure, salaries)? What's your variable cost per customer? *(Mark `[NOT PROVIDED]` if the user doesn't know — don't block on this.)*
4. **Revenue dynamics** — Do you see expansion revenue (upgrades between tiers)? What's your monthly churn rate? Do you have annual vs. monthly billing data?
5. **Business context** — What stage are you? (pre-seed / seed / Series A / Series B+) What's your primary customer segment? (SMB / mid-market / enterprise) What's the analysis goal? (pricing restructure, fundraising prep, general health check)

If the user says "just draft it" or "I don't have that", proceed with what you have. Mark every gap with `[NOT PROVIDED — analysis would improve with this data]` rather than inventing numbers.

---

## Phase 3: Analyze and Produce Output

### Data Ingestion

Accept data in any of these formats:
- **CSV / spreadsheet upload** — Look for columns mapping to: tier/plan name, price, customer count, billing period (monthly/annual), MRR contribution. Parse and map automatically. Ask for clarification if column names are ambiguous.
- **Pasted table** — Markdown or tab-separated. Parse row by row.
- **Verbal description** — "We have 3 tiers: Starter at $29 with about 200 customers, Pro at $79 with 120, Enterprise at $249 with 30." Extract structured data from natural language.
- **Stripe/Chargebee/Paddle export** — Recognize common export formats from billing platforms. Map fields to internal schema.

### Computed Metrics

Calculate all of the following from the provided data. If a required input is missing, note what's needed rather than guessing.

| Metric | Formula | When to Calculate |
|--------|---------|-------------------|
| **Blended ARPU** | Sum of (tier price × tier customer share) | Always |
| **Effective ARPU** | Blended ARPU adjusted for annual discount adoption | When annual plan data exists |
| **Monthly Revenue (MRR)** | Sum of (tier price × tier customers) | Always |
| **Annual Revenue (ARR)** | MRR × 12 | Always |
| **Gross Margin %** | (MRR − fixed costs − variable costs) / MRR × 100 | When cost data is provided |
| **Break-even Customers** | Fixed costs / (ARPU − variable cost per customer) | When cost data is provided |
| **Revenue by Tier** | Tier price × tier customers for each tier | Always |
| **Revenue Concentration (%)** | Each tier's revenue as % of total | Always |
| **Tier Revenue Rank** | Tiers ranked by revenue contribution | Always |
| **Customer-Revenue Skew** | Compare each tier's customer % vs revenue % | Always |
| **Price Gap Ratios** | Price of tier N+1 / price of tier N | When 2+ tiers exist |
| **Estimated LTV** | Effective ARPU × 24 months (or ARPU / churn if churn provided) | Always (default 24mo) or when churn exists |
| **Annual Plan Revenue** | Annual customers × discounted annual price | When annual plan data exists |
| **Monthly Plan Revenue** | Monthly customers × monthly price | When annual plan data exists |
| **Expansion Revenue** | Revenue from upgrades between tiers per month | When upgrade data exists |
| **Contraction Revenue** | Revenue lost from downgrades between tiers per month | When downgrade data exists |
| **Net Tier Movement** | Expansion − Contraction | When both exist |

### Tier Effectiveness Analysis

For each pricing tier, produce a diagnostic:

| Dimension | What to Assess |
|-----------|---------------|
| **Revenue Pull** | What % of total revenue does this tier generate? Is it proportional to its customer share? |
| **Customer Gravity** | What % of customers are on this tier? Is it over- or under-concentrated? |
| **Price Positioning** | Where does this tier sit relative to the tiers above and below? Is the price gap appropriate for the value gap? |
| **Upgrade Friction** | If the gap to the next tier is >3× the current price, flag as potential upgrade barrier. |
| **Zombie Tier Detection** | If a tier has <5% of customers AND <5% of revenue, flag as a zombie tier — it's adding complexity without contributing. |
| **Anchor Tier** | Identify which tier serves as the pricing anchor (highest listed price that makes other tiers look reasonable). |

Rate each tier: **Driver** (high revenue pull), **Workhorse** (high customer count, moderate revenue), **Aspirational** (low adoption, high price — serves as anchor), or **Zombie** (low on both axes).

### Customer Concentration Risk

Calculate and assess:

- **Top-tier revenue dependency**: What % of revenue comes from the highest-priced tier? Flag if >50%.
- **Herfindahl-Hirschman Index (HHI) for revenue**: Sum of squared revenue shares across tiers. HHI > 0.5 = highly concentrated. 0.25–0.5 = moderately concentrated. <0.25 = diversified.
- **Single-tier failure scenario**: If you lost all customers on your highest-revenue tier, what would MRR drop to? How many months of growth (at current rate) to recover?
- **Customer count concentration**: Is one tier holding >60% of all customers? If so, that's where churn hits hardest.

### Pricing Optimization Opportunities

Identify and quantify specific opportunities:

1. **Price increase candidates** — Tiers where customer-revenue skew is negative (tier contributes more customers than revenue proportionally). Calculate: "Increasing [tier] by $X would add $Y/mo in MRR if [retention assumption]."

2. **Gap compression/expansion** — If adjacent tiers have a price ratio >4×, the jump may be too large for upgrades. If <1.5×, there's no meaningful differentiation. Recommend specific adjustments.

3. **Tier consolidation** — If two adjacent tiers have similar customer counts and <2× price difference, recommend merging with the higher price point and calculate the revenue impact.

4. **Missing tier detection** — If there's a gap in the price spectrum (e.g., $29 jumps to $199), recommend an intermediate tier and project adoption based on current customer distribution patterns.

5. **Annual plan optimization** — If annual adoption data exists, calculate: current effective discount, revenue impact of adjusting discount by +/− 5%, projected annual plan adoption at different discount levels using the 30–50% adoption benchmark.

6. **Expansion revenue capture** — If tier movement data exists, identify which upgrade paths generate the most revenue and recommend features or triggers to accelerate those paths.

For each opportunity, provide:
- What to change
- Projected monthly revenue impact (with stated assumptions)
- Confidence level: High (data-supported), Medium (pattern-supported), Low (hypothesis — needs testing)
- Suggested implementation approach (A/B test, grandfather existing, immediate change)

### Scenario Modeling

Project 12-month revenue under three pricing scenarios:

| Scenario | Description |
|----------|-------------|
| **Status Quo** | Current pricing, current customer distribution trends, current growth rate. |
| **Conservative Optimization** | Implement only high-confidence recommendations (price adjustments with <10% projected churn impact). |
| **Aggressive Restructure** | Implement all recommendations including tier consolidation and new tier introduction. Model a 5–15% short-term churn hit with recovery. |

For each scenario, project month-by-month:
- MRR by tier
- Total MRR
- Customer count by tier
- Blended ARPU trajectory
- Revenue delta vs. status quo (cumulative)

### Industry Benchmarks

Rate pricing health against stage-appropriate benchmarks:

**Early Stage (< $1M ARR)**
| Metric | 🟢 Strong | 🟡 Typical | 🔴 Concern |
|--------|-----------|-----------|------------|
| Blended ARPU (SMB) | > $50/mo | $25–50/mo | < $25/mo |
| Blended ARPU (Mid-market) | > $200/mo | $100–200/mo | < $100/mo |
| Gross Margin | > 75% | 65–75% | < 65% |
| Revenue Concentration (top tier) | < 35% | 35–50% | > 50% |
| Price tier count | 2–3 | 3–4 | 5+ |
| Annual plan adoption | > 40% | 25–40% | < 25% |

**Growth Stage ($1M–$10M ARR)**
| Metric | 🟢 Strong | 🟡 Typical | 🔴 Concern |
|--------|-----------|-----------|------------|
| Blended ARPU (SMB) | > $75/mo | $40–75/mo | < $40/mo |
| Blended ARPU (Mid-market) | > $300/mo | $150–300/mo | < $150/mo |
| Gross Margin | > 80% | 70–80% | < 70% |
| Revenue Concentration (top tier) | < 40% | 40–55% | > 55% |
| Net Revenue Retention | > 110% | 100–110% | < 100% |
| Expansion Revenue % of MRR | > 5% | 2–5% | < 2% |

**Scale Stage ($10M+ ARR)**
| Metric | 🟢 Strong | 🟡 Typical | 🔴 Concern |
|--------|-----------|-----------|------------|
| Blended ARPU | > $500/mo | $200–500/mo | < $200/mo |
| Gross Margin | > 82% | 75–82% | < 75% |
| Revenue Concentration (top tier) | < 45% | 45–60% | > 60% |
| Net Revenue Retention | > 120% | 110–120% | < 110% |
| Annual plan adoption | > 50% | 35–50% | < 35% |

---

## Output Format

### Tier 1 Output — Markdown (in chat)

```
## Pricing Diagnostic

### Current Pricing Structure
[Table: Tier | Price | Customers | MRR | % of Revenue | % of Customers]

### Key Metrics
[ARPU, MRR, ARR, Gross Margin, Break-even — each with stage benchmark rating 🟢/🟡/🔴]

### Tier Effectiveness
[Each tier rated as Driver / Workhorse / Aspirational / Zombie with one-line explanation]

### Concentration Risk
[HHI score, top-tier dependency %, one-line assessment]

### Top 3 Pricing Opportunities
[Numbered, specific, with projected revenue impact and assumptions]
```

### Tier 2 Output — `.docx` Report

Generate a formatted Word document using the docx skill. Include the following sections:

1. **Executive Summary** — 3 sentences: current pricing health, biggest risk, highest-impact opportunity. No fluff.

2. **Current Pricing Structure** — Full table of all tiers with price, customer count, MRR contribution, % of total revenue, % of total customers. Include blended ARPU, effective ARPU (if annual data), and gross margin.

3. **Tier Effectiveness Scorecard** — Each tier gets a classification (Driver / Workhorse / Aspirational / Zombie) and a one-paragraph explanation of what it's doing for the business. Include customer-revenue skew analysis (what % of customers vs what % of revenue).

4. **Revenue Composition Waterfall** — Break down total MRR by tier. If expansion/contraction data exists, show the waterfall: Starting MRR + New + Expansion − Contraction − Churn = Ending MRR, broken out by tier.

5. **Concentration Risk Assessment** — HHI score with interpretation. Top-tier dependency percentage. Single-tier failure scenario with recovery timeline. Overall risk rating: Low / Moderate / High.

6. **Price Gap Analysis** — Representation of the price spectrum. Gap ratios between adjacent tiers. Assessment of whether gaps align with value differentiation or create upgrade barriers.

7. **Pricing Optimization Opportunities** — 5–7 specific opportunities ranked by projected revenue impact. Each includes: what to change, why (which metric it addresses), projected monthly revenue impact (with assumptions), confidence level, and implementation approach.

8. **Scenario Projections** — 12-month tables for status quo / conservative / aggressive scenarios. Month-by-month MRR by tier, total MRR, customer count, blended ARPU. Cumulative revenue delta between scenarios. Key inflection points called out.

9. **Annual vs Monthly Analysis** — (if data available) Current split, effective discount analysis, projected impact of discount changes, adoption rate benchmarks.

10. **Benchmark Comparison** — Stage-matched benchmarks with specific gaps identified. Rank gaps by severity. For each concern-level metric, explain the business impact and what improving it would mean.

11. **Recommendations Summary** — Prioritized action list with timeline. Quick wins (implement this week), medium-term (this quarter), strategic (this half). Each tied to a specific revenue impact projection.

12. **Assumptions Log** — Every assumption made during the analysis, marked `[ASSUMED]`. What data point would refine each assumption. This section exists so the reader knows exactly where the analysis is soft.

---

## Phase 4: Review Loop

After delivering the output:

1. Ask: *"Does this capture your pricing situation accurately? Anything I'm missing or got wrong?"*
2. If the user provides corrections or additional data, re-run the affected calculations and update the document.
3. If a section is thin because data was missing, flag it: *"The concentration risk section is limited because I only have tier prices without customer counts. If you can share customer counts per tier, I'll add the full effectiveness analysis and optimization recommendations."*
4. If the user wants to test a specific pricing change: run a focused scenario showing the before/after impact on MRR, ARPU, and margin.

---

## Edge Cases

- **User provides only tier prices without customer counts**: Calculate price gap ratios and positioning analysis. Note that tier effectiveness, concentration risk, and revenue projections require customer counts. Produce a Tier 1 output focused on price structure assessment.
- **User provides a CSV or spreadsheet**: Parse it. Look for columns that map to plan name, price, customer count, billing period. Ask for clarification if column names are ambiguous. Handle common formats from Stripe (plan, amount, quantity), Chargebee (plan_id, plan_price, subscriptions), and generic exports.
- **User provides transaction-level data instead of tier summaries**: Aggregate by plan/price to construct the tier summary. Flag if the data suggests custom pricing (many unique price points), which indicates enterprise/negotiated deals that need separate treatment.
- **Fundraising context**: If the user mentions fundraising, emphasize metrics investors scrutinize: ARPU trajectory, net revenue retention, expansion revenue %, gross margin trend, pricing power indicators. Frame optimization recommendations in terms of ARR impact for valuation multiples.
- **Single-tier pricing**: Skip tier effectiveness and concentration analysis (meaningless with one tier). Focus on: is the price right for the segment, what would adding a second tier look like, and projected revenue impact of a price change at various elasticity assumptions.
- **Freemium model**: If a free tier exists, treat it separately. Calculate conversion rate to paid, revenue per free-to-paid conversion, and freemium pipeline value. Do not include free users in paying customer metrics.
- **Very early stage (< 50 customers)**: Customer distribution across tiers may not be statistically meaningful. Note this. Focus on price positioning, gap analysis, and unit economics rather than tier effectiveness percentages. Small sample caveat on all concentration metrics.
- **Usage-based or hybrid pricing**: If the user describes usage-based components, acknowledge that tier analysis is only one dimension. Note which metrics are affected and where usage data would improve the analysis.
