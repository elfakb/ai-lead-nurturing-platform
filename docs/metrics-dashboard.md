# Metrics & Dashboards — AI Lead Nurturing Platform

Different stakeholders need different views into the same system. 
Rather than one dashboard for everyone, metrics are split by audience 
and by what decision each metric is meant to inform.

---

## 1. Business / North Star Metrics
**Audience: PM & Leadership**

| Metric | Why it matters |
|---|---|
| Lead-to-Customer Conversion Rate | The north star — every other metric ultimately should move this |
| Sales Cycle Length | Tests the hypothesis that reaching the right lead at the right time shortens time-to-close |
| Cost per Acquisition (CAC) | Indirect signal of how much manual sales effort the automation is offsetting |

## 2. Engagement Metrics
**Audience: Marketing**

| Metric | Why it matters |
|---|---|
| Open / Click-through rate (by segment) | Operational health of nurture content; expected to differ meaningfully between Hot and Cold segments |
| Unsubscribe rate | Early warning if personalization feels excessive or misdirected |
| Nurture-to-Hot conversion rate | How effectively nurturing is moving leads toward sales-readiness, and how long that takes |

## 3. AI Performance Metrics
**Audience: Product / AI team**

| Metric | Why it matters |
|---|---|
| Scoring precision & recall | Precision: of leads marked Hot, how many actually convert. Recall: of leads that actually convert, how many were caught as Hot. Optimizing for precision alone causes the model to under-flag leads and miss opportunities — both must be tracked together |
| Email approval rate | % of AI-drafted emails approved without edits by marketing. This is both a quality signal and an operational gate (see below) |
| Personalization lift | CTR/conversion difference between AI-generated and template emails, measured via the A/B test in `ab-test-design.md` |

---

## Why Email Approval Rate Is More Than a Quality Metric

The approval rate directly determines when a lead segment is allowed to 
move from human-reviewed to auto-sent emails in V2. A segment only makes 
that transition once its approval-without-edits rate stays above a 
defined threshold (e.g. 90%) over a sustained window — not on a fixed 
timeline. This makes the expansion of AI autonomy a data-driven decision 
rather than a calendar-driven one, and it's the same principle applied 
throughout this project: **trust is earned incrementally, and the 
metrics are what earn it.**