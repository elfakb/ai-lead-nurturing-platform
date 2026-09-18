# A/B Test Design — AI-Generated vs. Template Emails

## Hypothesis

AI-generated personalized emails will achieve a higher click-through 
rate (CTR) than generic template emails, because content relevance to 
the lead's demonstrated interest increases engagement.

Framing the hypothesis with the *why* (relevance drives engagement) 
rather than just the *what* (AI is better) makes the result easier to 
interpret — if the test fails, it tells us something specific: either 
personalization isn't landing, or relevance isn't actually the 
engagement driver we assumed.

## Test Design

- **Control group:** Leads receive the existing generic template email 
  for their current nurture stage.
- **Variant group:** Leads receive the AI-generated personalized email 
  (human-approved in MVP/V1) for the same nurture stage.
- **Randomization:** Leads are randomly assigned to control/variant at 
  the moment they enter the nurture sequence — not by segment. 
  Randomizing by segment would confound results: if Hot leads 
  disproportionately ended up in the variant group, any lift would be 
  attributable to segment quality, not email type.
- **Primary metric:** Click-through rate (CTR)
- **Secondary metrics:** 
  - Open rate — does personalization improve the subject line's pull
  - Unsubscribe rate — does personalization feel intrusive rather than 
    helpful
  - Downstream: nurture-to-Hot conversion rate

## Sample Size & Duration

Minimum sample size is calculated using a standard significance 
calculator, targeting 95% confidence and 80% statistical power, based 
on the current baseline CTR and the minimum detectable effect that 
matters to the business (e.g. a 15% relative lift — smaller lifts may 
not be worth the added complexity of AI-generated content).

The test runs for a minimum of **2 full nurture cycles** to account for 
weekday/weekend variation in email engagement, and is not stopped early 
based on interim results — early stopping on promising-looking interim 
data ("peeking") inflates false positive rates and would undermine the 
test's validity.

## Guardrail Metric

Unsubscribe rate is tracked as a guardrail, not just a secondary metric. 
Even if the variant wins on CTR, a statistically significant increase in 
unsubscribe rate is treated as a disqualifying signal. Personalization 
that drives short-term clicks at the cost of long-term list health isn't 
a win — this guardrail keeps the test honest about what "success" 
actually means for the business.

## Reading the Result

- **Variant wins on CTR, guardrail holds:** proceed to wider rollout, 
  feed result into the approval-rate gating logic for V2 automation.
- **Variant wins on CTR, guardrail fails:** investigate — likely a 
  tone/frequency issue rather than a content-relevance issue; iterate 
  before re-testing.
- **No significant difference:** re-examine the personalization inputs 
  (Step 5) — the issue may be that current signals aren't granular 
  enough to produce meaningfully different content from the templates.