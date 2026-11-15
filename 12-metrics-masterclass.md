# VOLUME XII — THE METRICS MASTERCLASS
### Part XXXII

> A metric is a compression of reality. Every compression discards something. The discipline is knowing what yours discarded.

**How to use this volume.** It's a reference library, not a reading. Each metric carries: definition, formula, interpretation, limitation, related metrics, and — the field that matters most — **the decision it actually supports.** A metric that supports no decision is instrumentation debt.

---

## 1. THREE LAWS BEFORE THE LIBRARY

### 1.1 Goodhart's Law
> **When a measure becomes a target, it ceases to be a good measure.**

Any metric tied to compensation, promotion, or resource allocation will be optimised — including in ways that destroy the thing it was measuring. Support teams measured on ticket closure close tickets. Teams measured on velocity inflate points.

**The countermeasure is paired metrics.** Never a speed metric without a quality guardrail; never a volume metric without a value guardrail.

| Primary | Mandatory pair |
|---|---|
| Ticket closure rate | Reopen rate, CSAT |
| Deploy frequency | Change failure rate |
| Feature adoption | Task success rate |
| Returns filed per preparer | Amendment rate |
| Time-to-file | Calculation defect rate |
| AI automation rate | Human intervention rate on audited samples |

### 1.2 The definition law
> **A metric without a written, versioned definition is three metrics.**

"Active user" means five different things to five teams, and every cross-functional metric argument you've ever sat through was actually a definition argument. Maintain a metric dictionary: name, precise definition, SQL or query source, owner, last changed, and *why* it's defined that way. **When a definition changes, the historical series breaks — annotate the chart.**

### 1.3 The variance law
> **A number without its normal range is not information.**

Covered in Volume VI §5. Repeated here because it's the most common failure in metric reporting: you cannot interpret 24% without knowing the metric normally sits between 22% and 31%.

---

## 2. PRODUCT METRICS

| Metric | Formula | Interpretation | Key limitation | Decision it supports |
|---|---|---|---|---|
| **Activation rate** | Accounts reaching the value moment within N days ÷ new accounts | Whether new customers reach value | The "value moment" must be empirically derived, not chosen | Whether to invest in onboarding vs acquisition |
| **Time to value (TTV)** | Median days from signup to first value moment | Onboarding friction | Median hides a bimodal distribution — check p75 | Where to cut steps in setup |
| **Feature adoption** | Users using feature ≥1× ÷ **eligible** users | Whether a build was worth it | Denominator must be eligible, not all users. First-use ≠ habitual use | Iterate, promote, or remove |
| **Feature retention** | Adopters still using it in month 2/3 | Whether adoption stuck | Small n on new features | Whether the feature solved a real job |
| **Breadth** | Distinct core capabilities used per account per month | Product entrenchment | Counting capabilities nobody needs inflates it | Expansion and cross-sell targeting |
| **Depth** | Actions per active user per period | Intensity of use | Higher isn't better in efficiency tools | Whether the workflow is being fully used |
| **Task success rate** | Completed tasks ÷ attempted | **The best single quality measure for workflow tools** | Requires defining task start/end precisely | UX investment priorities |
| **Rework rate** | Tasks requiring redo ÷ completed | Hidden cost of poor quality | Hard to instrument; needs explicit state modelling | Where friction actually is |
| **Seat utilisation** | Active seats ÷ licensed seats | **The best leading indicator of contraction** | "Active" definition is load-bearing | Renewal risk 6–12 months out |
| **DAU/WAU/MAU** | Unique actives per period | Engagement | **Near-meaningless for seasonal or mandated-use B2B** | Consumer products; rarely useful here |
| **Stickiness (DAU/MAU)** | DAU ÷ MAU | How habitual usage is | Same seasonal problem | Consumer; skip in your context |
| **Cohort retention** | % of a cohort active in month N | Whether value is durable | Must be cohorted, never blended | Whether you have PMF in a segment |
| **Conversion rate** | Progressed ÷ entered, per funnel step | Where you lose people | Aggregate rates hide mix shifts (Simpson's) | Which step to fix |
| **NPS** | %Promoters − %Detractors | Directional sentiment | Severe response bias; not predictive of B2B renewal on its own | Trend watching only. Never a target |
| **CSAT** | % satisfied on a specific interaction | Interaction quality | Measures the interaction, not the product | Support quality |
| **Support contact rate** | Tickets ÷ active accounts ÷ month | Product friction expressed as cost | Deflection to docs looks like improvement | Where usability debt is, in money |

### 2.1 The three worth knowing deeply

**Activation.** Everything downstream depends on it, and it's the cheapest place to move retention. **The value moment must be derived, not chosen:** compare retained and churned cohorts on early actions, find the action with the largest separation, then test whether it's a *lever* or a *marker* (Volume VI §8.3). Most teams pick a value moment by intuition and optimise a marker for a year.

**Seat utilisation.** The single most valuable B2B leading indicator, and it's product-owned. A 40-seat account with 12 active users has already decided its renewal size; you just haven't been told. It gives you 6–12 months of warning at zero analytical cost.

**Task success rate.** For mandated-use workflow software, this replaces engagement entirely. Preparers aren't choosing to spend time in your product; they're trying to finish work. The right question is not "how engaged are they" but "how often does the work complete, correctly, first time."

---

## 3. BUSINESS & SaaS METRICS

| Metric | Formula | Interpretation | Key limitation | Decision it supports |
|---|---|---|---|---|
| **MRR / ARR** | Σ normalised recurring revenue | Scale of the recurring business | Excludes services; one-offs must not be included | Planning, valuation |
| **New / Expansion / Contraction / Churned MRR** | The four movement components | *Where* growth comes from | Requires clean movement accounting | Which product problem to solve |
| **ARPA** | ARR ÷ accounts | Average account value | Meaningless across a bimodal base — segment it | Packaging and tiering |
| **GRR** | (Start − churn − contraction) ÷ Start | Retention with no upsell credit; caps at 100% | Doesn't reflect expansion potential | Whether the product holds |
| **NRR** | (Start − churn − contraction + expansion) ÷ Start | **The headline B2B health metric** | Can mask a bleeding base (read with GRR) | Growth model viability |
| **Logo churn** | Accounts lost ÷ accounts at start | Customer count attrition | Ignores revenue weight — losing 10 small ≠ losing 1 large | Segment health |
| **CAC** | Fully loaded S&M spend ÷ new customers | Cost to acquire | Must include salaries; attribution across long cycles is imperfect | Channel and motion efficiency |
| **CAC payback** | CAC ÷ (ARPA × gross margin %) | Months to recover acquisition cost | Sensitive to the margin figure used | **The number cash-constrained boards watch** |
| **LTV** | (ARPA × GM%) ÷ churn rate | Lifetime value | Assumes constant churn forever, undiscounted. Cap the horizon | Rough channel economics only |
| **LTV:CAC** | LTV ÷ CAC | Unit economics health | Easily inflated by optimistic churn or revenue-not-margin | Sanity check, not a target |
| **Gross margin** | (Revenue − COGS) ÷ Revenue | Scalability of the model | COGS must include support, infra, third-party, AI inference | Pricing, architecture, support investment |
| **Contribution margin by segment** | GM minus segment-specific variable cost | **Which segments actually make money** | Requires honest cost allocation | Segment strategy — see Volume III |
| **Rule of 40** | Growth % + profit margin % | Blunt balance check | Ignores quality of growth | Board-level positioning |
| **Magic number** | Net new ARR ÷ prior-period S&M spend | Sales efficiency | Lags; noisy quarter to quarter | Whether to add sales capacity |
| **Expansion rate** | Expansion MRR ÷ starting MRR | Growth from existing base | Doesn't distinguish price increases from real expansion | Packaging effectiveness |
| **Discount rate** | (List − realised) ÷ list | **Your actual pricing error** | Sits in CRM, rarely analysed | Repricing decisions |

### 3.1 NRR decomposed — the PM's version

```
NRR = 1 − churn − contraction + expansion

  churn        → the product failed, or the need changed  → retention/onboarding
  contraction  → seats bought, not used                   → activation/adoption
  expansion    → more seats, usage, or tier               → packaging/value metric
```

**Read GRR and NRR together, always.** NRR 118% with GRR 84% means a few accounts are expanding hard while the base bleeds — concentration risk that looks like health on one number.

**Contraction is the component PMs own most directly and watch least.** It's downstream of user activation and seat utilisation, both product metrics, both visible a year in advance.

---

## 4. ENGINEERING METRICS

### 4.1 DORA — the four keys

Published research on software delivery performance (E1 — the DORA / *Accelerate* research programme; the four metrics are widely published and the annual State of DevOps reports are public).

| Metric | Definition | What good looks like (directional) | What it tells a PM |
|---|---|---|---|
| **Deployment frequency** | How often code reaches production | Daily or better for high performers | Batch size and release friction |
| **Lead time for changes** | Commit → running in production | Under a day for high performers | How fast you can respond to anything |
| **Change failure rate** | % of deployments causing degradation | Low single digits to ~15% | Quality of the delivery process |
| **Time to restore (MTTR)** | Incident → resolved | Under an hour for high performers | Blast radius of being wrong |

**Why a PM should care:** these four together describe **how expensive it is to be wrong**, which determines how much discovery rigour you need. A team that deploys daily with a 5% failure rate and restores in 20 minutes can afford to try things. A team that releases monthly with a 30% failure rate must be right up front — which means more upfront validation, and that's a product process decision.

**The critical pairing:** deployment frequency and lead time are speed; change failure rate and MTTR are stability. **Optimising the first pair alone produces a team that ships breakage quickly.** DORA's central finding is that high performers achieve both, which contradicts the assumed trade-off.

**Do not use DORA to compare teams or as an individual target.** Goodhart applies with force.

### 4.2 Reliability and performance

| Metric | Definition | Limitation | Decision supported |
|---|---|---|---|
| **SLO attainment** | % of time an SLI met its target | Only as good as the SLI chosen | Whether to spend the error budget on features |
| **Error budget remaining** | Allowed failure minus consumed | Requires an agreed SLO | Feature work vs reliability work — automatically |
| **p50 / p95 / p99 latency** | Percentile response times | **Averages actively mislead** | Where to optimise; who's suffering |
| **Error rate** | Failed requests ÷ total | Must be segmented by endpoint and customer | Where reliability work goes |
| **Incident count / duration** | Frequency and length | Severity classification is subjective | Systemic vs one-off problems |
| **Cycle time** | Work started → delivered | Excludes queue time before start | Where the delivery bottleneck is |
| **Escaped defect rate** | Defects found in production ÷ total | Depends on detection quality | Whether testing investment is working |
| **Interrupt ratio** | Unplanned ÷ total work | Requires disciplined tagging | Whether you have a health problem masquerading as a process problem |

**The p99 point deserves repeating because it's a genuine B2B insight:** your p99 experience usually belongs to your largest customer, because their data volume produces the tail. An average of 800ms with a p99 of 14 seconds means your most valuable account is having a bad time invisibly.

---

## 5. AI PRODUCT METRICS

Cross-reference Volume IX §4.2. **The whole category is measured against a distribution, not a specification** — every number here needs its eval set named alongside it.

| Metric | Formula / method | Interpretation | Key limitation | Decision it supports |
|---|---|---|---|---|
| **Task success rate** | Successful outputs ÷ attempts, on a defined eval set | The headline quality number | Entirely dependent on how "success" is defined and on set composition | Ship / don't ship |
| **Field-level accuracy** | Correct fields ÷ total fields | Extraction quality | Averages across fields of wildly different importance — weight them | Which fields need human review |
| **Groundedness** | Claims supported by retrieved sources ÷ total claims | RAG faithfulness | Requires a judge (human or model), with its own error rate | Whether to tighten retrieval or generation |
| **Citation accuracy** | Citations that actually support the claim ÷ citations | Trustworthiness of references | Expensive to label | Whether to expose citations at all |
| **Hallucination/fabrication rate** | Unsupported confident assertions ÷ outputs | Risk exposure | Definition varies widely — write yours down | Consequence class assignment |
| **Refusal rate** | Declined requests ÷ requests, on a benign set | **Over-refusal is a product failure too** | Needs a curated benign set | Prompt/policy tuning |
| **Format validity** | Schema-conformant outputs ÷ outputs | Downstream integration safety | Doesn't measure content correctness | Whether constrained decoding is needed |
| **Human intervention rate** | Outputs requiring correction ÷ outputs | **The business metric — maps directly to labour saved** | Users may accept wrong output (see complacency) | ROI and pricing |
| **Edit distance** | How much the user changed the output before using it | Passive usefulness signal | Noisy per-instance; useful in aggregate | Which output types are actually good |
| **Cost per task** | (Input + output tokens × price) × (1 + retry rate) + overhead | Unit economics | Must be computed at p95 volume, not average | Pricing, model routing |
| **Latency p50/p95** | Time to usable output | UX viability | Streaming changes perceived latency | Whether the interaction pattern works |
| **Eval regression delta** | Score change vs current production | Whether a change is safe | Requires a stable held-out set | **The release gate** |
| **Drift indicator** | Scheduled eval score over time | Whether the vendor's model changed under you | Needs a fixed set and a regular cadence | When to re-tune or pin a version |
| **Escalation rate** | Tasks handed to a human ÷ total | Autonomy achieved in practice | Can be gamed by over-escalating | Whether the autonomy rung is right |

**The two to lead with, depending on audience:**
- **To engineering and in release gates:** eval regression delta against protected cases.
- **To executives and finance:** human intervention rate. It converts model quality into hours and money — "correction required on 18% of fields, down from 31%" is a sentence a CFO can act on, and "94% accuracy" is not.

---

## 6. CHOOSING METRICS: THE SELECTION PROCESS

```
1. NAME THE DECISION      What choice will this number change?
                          No decision → don't instrument it
2. FIND THE OUTCOME       What business/customer result matters?
3. BUILD THE TREE         Decompose into inputs the team controls (Vol VI §2.1)
4. PICK THE PAIR          Primary + guardrail. Never one alone
5. DEFINE PRECISELY       Write it down. Version it. Name an owner
6. ESTABLISH BASELINE     Current value AND normal variance
7. SET THE REVIEW         Who looks, how often, and what triggers action
```

### 6.1 The metric review cadence

| Altitude | Metrics | Cadence | Question |
|---|---|---|---|
| Team | 2–3 inputs + guardrails | Weekly | Did anything move beyond variance? |
| Product | Outcome + funnel + quality | Monthly | Are we moving the outcome? |
| Business | NRR/GRR, margin, CAC payback, segment contribution | Quarterly | Is the model working? |
| Strategy | Bet-specific leading indicators | Monthly + quarterly | Is a bet failing? |

**The rule that makes reviews useful: every metric in a review has a named owner who is expected to explain it.** A dashboard nobody owns is decoration, and a review where the answer to "why did that move?" is silence is a status meeting.

---

## 7. THE VANITY METRIC LIBRARY

Not useless — **useless as targets.** Each is fine as context and corrosive as a goal.

| Vanity metric | Why it misleads | Use instead |
|---|---|---|
| Total registered users | Never decreases; includes the dead | Active accounts; seat utilisation |
| Page views / sessions | More can mean confusion | Task success; time-to-complete |
| Total features shipped | Activity, not outcome | Adoption of what shipped |
| Velocity / story points | Team-relative, gameable, not comparable | Cycle time; outcomes moved |
| Cumulative downloads/signups | Cumulative anything hides the trend | Cohort retention |
| Time in app | In efficiency tools, **lower is better** | Task completion rate |
| NPS as a target | Response bias; weak B2B renewal correlation | GRR; support contact rate |
| Number of integrations built | Built ≠ used | Integrations with active usage |
| AI "accuracy" with no eval set named | Unfalsifiable | Task success on a named, versioned set |
| Model benchmark scores | Not your distribution | Your eval suite on your data |

**The tell for a vanity metric: ask "if this number doubled, what would we do differently?"** If the answer is "celebrate," it's vanity.

---

## 8. VOLUME XII EXERCISES

**Exercise 12.1 — Metric dictionary.** Write precise, versioned definitions for your ten most-used metrics, with query source and owner. Circulate. *Deliverable: the end of definitional arguments, permanently.*

**Exercise 12.2 — Pair every metric.** For each metric your team reports, name the guardrail that prevents gaming it. Any metric with no pair is a Goodhart risk. *Deliverable: a paired dashboard.*

**Exercise 12.3 — The decision column.** Take your current dashboard and, for each metric, write the decision it supports. Delete anything where you can't. *Most dashboards shrink by half, and become useful.*

**Exercise 12.4 — Segment contribution margin.** Compute contribution margin for your two largest segments, including support and implementation cost. *Deliverable: possibly the most consequential number in your company that nobody has calculated.*

**Exercise 12.5 — DORA baseline.** With your tech lead, measure the four keys for one month. *Deliverable: an evidence-based view of how expensive it is for your team to be wrong — which tells you how much upfront rigour your process needs.*

**Exercise 12.6 — Vanity audit.** Find every metric in a recurring report or QBR deck. Apply the "if it doubled" test. *Deliverable: a shorter, more honest report.*

---

## 9. VOLUME XII INTERVIEW BANK

1. What's your product's North Star, and what does it fail to capture?
2. What's the difference between GRR and NRR? When would you care more about GRR?
3. How would you measure the success of a feature in a product people must use?
4. What guardrail would you pair with "deployment frequency"?
5. Explain CAC payback and why a board might prefer it to LTV:CAC.
6. What's wrong with reporting average latency?
7. How do you know a metric movement is real?
8. Give me a vanity metric from your current product and what you'd replace it with.
9. What would you measure to predict revenue contraction two quarters out?
10. How would you measure an AI feature's quality to a CFO rather than to an engineer?
11. Your team's velocity doubled. What do you check before celebrating?
12. Design a metric tree for [their product].

---

*Volume XII complete. Remaining: Volumes XIII–XVII (frameworks & anti-patterns, case studies, the 205-case interview bank, projects & simulations, toolkit, capstone & 180-day plan).*
