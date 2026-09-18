# Customer Journey — AI Lead Nurturing Platform

This document breaks down the full lead lifecycle for a sales-led B2B SaaS 
company, from anonymous visitor to closed customer. Each stage defines what 
the user does, what the system does, and why the stage matters for the 
overall product.

---

## 1. Awareness
The user discovers the company through content (SEO, blog, paid ads, 
LinkedIn) or referral. No system action yet — this is pre-lead, but it 
matters because acquisition channel later becomes a scoring input (some 
channels historically convert better than others).

## 2. Visit
The user lands on the website — pricing page, case studies, blog posts, 
product pages. Behavioral tracking begins here: pages visited, time on 
page, repeat visits. This is the first data source available for scoring, 
even before the visitor identifies themselves.

## 3. Lead Capture
The user fills a form — demo request, gated content download (whitepaper, 
e-book), or newsletter signup. This is the moment an anonymous visitor 
becomes an identified lead in the CRM. Different capture actions signal 
different intent: a demo request signals far higher intent than a 
whitepaper download, and this distinction feeds directly into the 
Engagement Score.

## 4. Qualification (AI Lead Scoring)
The system combines firmographic data (company size, industry, job title) 
with behavioral data (pages visited, content engaged with, email 
interactions) to calculate a lead score and assign a segment: Cold, Warm, 
or Hot. This is the core AI decision point in the journey — everything 
downstream depends on this classification. See `lead-scoring-model.md` 
for the full scoring logic.

## 5. Nurturing
If the lead isn't sales-ready yet (Cold/Warm), it enters an automated but 
personalized email sequence. Content and cadence are tailored to the 
lead's segment and demonstrated interest — e.g., a lead who engaged with 
pricing-related content receives ROI-focused follow-up content next. The 
lead's score is continuously recalculated as they engage further, which 
means a lead can move segments (Cold → Warm → Hot) or regress (due to 
inactivity) at any point in this stage.

## 6. Sales Handoff
Once a lead crosses the Hot threshold, it's automatically routed to a 
sales rep with full context: score, behavioral history, and an 
AI-suggested next action (e.g., "This lead viewed pricing 3x this week — 
recommend offering a demo now"). This removes manual triage from the 
sales team and ensures no hot lead sits in a queue.

## 7. Conversion
The sales rep conducts a demo/sales call informed by the lead's full 
journey data, leading (ideally) to a closed deal. Post-conversion, the 
lead transitions into onboarding — outside this project's scope, but the 
closed-won/closed-lost outcome feeds back into the scoring model as a 
labeled training example (see the feedback loop in the automation 
workflow).

---

## Why this journey structure matters

The journey is intentionally built around a single question at each 
stage: **"What does the system need to decide here, and what does it need 
to know to decide well?"** This keeps the AI's role scoped to specific 
decision points (Qualification, Nurturing content, Handoff recommendation) 
rather than being a vague, everywhere-at-once layer — which is a 
deliberate product choice, not a technical limitation.