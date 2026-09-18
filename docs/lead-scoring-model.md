# Lead Scoring Model — AI Lead Nurturing Platform

## Two Scoring Dimensions

Lead scoring is split into two dimensions that are tracked separately, 
not combined into a single number:

- **Fit Score** — how well this lead matches our Ideal Customer Profile 
  (ICP). Based on firmographic data that changes slowly or not at all 
  (company size, industry, job title).
- **Engagement Score** — how active and sales-ready this lead is right 
  now. Based on behavioral data that changes quickly (page visits, email 
  interactions, content downloads).

**Why keep them separate:** A high-Fit / low-Engagement lead ("perfect 
customer, not ready yet") and a low-Fit / high-Engagement lead ("very 
active, but doesn't match our ICP — possibly a student or competitor") 
require completely different actions. Merging them into one score would 
destroy this distinction and lead to mis-routed leads.

---

## MVP: Rule-Based Scoring

Explainable, fast to ship, and easy to debug — no ML dependency for 
launch.

| Signal | Type | Points |
|---|---|---|
| Company size matches ICP (e.g. 50–500 employees) | Fit | +15 |
| Job title matches buyer persona (e.g. VP/Director+) | Fit | +15 |
| Industry matches target verticals | Fit | +10 |
| Pricing page visit | Engagement | +10 |
| Demo request | Engagement | +25 |
| Case study / whitepaper download | Engagement | +5 |
| Email open | Engagement | +2 |
| Email click | Engagement | +5 |
| 14 days of inactivity | Engagement | −10 |
| 30 days of inactivity | Engagement | −20 |

**Segment thresholds:**
- 0–30 → **Cold** (long-term nurture, low-touch content)
- 31–60 → **Warm** (active nurture sequence, engagement-building content)
- 61+ → **Hot** (routed to sales)

These weights are PM/growth-team assumptions at launch — they are not 
derived from data yet. That's precisely why V2 exists.

---

## V2: Predictive Model

Once enough closed-won / closed-lost data accumulates from the MVP and 
V1 phases, scoring shifts from static assumptions to a model trained on 
actual outcomes.

**Input features:**
- Firmographic: company size, industry, job title
- Behavioral: page visits, content engagement, email interaction, 
  time-to-first-response
- Source channel: organic, paid, referral

**Output:** a conversion probability (0–100%), internally.

**Why the output is still shown as Cold/Warm/Hot:** Even though the 
model produces a probability, it's translated back into the familiar 
three-tier label for the sales team's dashboard. This preserves a 
consistent mental model and avoids requiring sales reps to learn to 
interpret a new metric — the model gets smarter under the hood, but the 
interface sales sees doesn't change. Consistency of interface reduces 
adoption friction, even as the underlying intelligence improves.

**What V2 is expected to surface that MVP can't:** the model may 
discover that certain signals (e.g. case study downloads) predict 
conversion far more strongly than the MVP's assumed weights, or that 
job title matters less than company size for this specific business. 
This is the core value of moving from rules to a learned model — it 
corrects assumptions the MVP had no way of testing.