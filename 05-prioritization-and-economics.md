# VOLUME V — PRIORITIZATION & PRODUCT ECONOMICS
### Parts X & XI

> A prioritization framework never told anyone what to build. It tells you whether your reasoning is consistent. Those are very different services, and confusing them is why teams "do RICE" and still ship the wrong things.

---

# PART X — PRIORITIZATION MASTERY

## 1. THE CORE MISUNDERSTANDING

Scoring frameworks are **consistency and communication instruments**. They force you to state your assumptions in comparable units so that two people arguing about two features are arguing about the same dimensions. That is genuinely valuable.

What they are not: a source of priorities. **Priorities come from strategy.** If you don't have a diagnosis and a set of choices (Volume III), a scoring model will faithfully rank a list of things that shouldn't be on the list at all — with a decimal point, which makes it worse, because now the wrong answer looks rigorous.

The diagnostic: **if your framework's output ever surprises you and you accept it without argument, you're using it as an oracle and you've outsourced judgment to arithmetic.** A healthy relationship with a scoring model is: it produces a ranking, the ranking looks wrong somewhere, and investigating *why* it looks wrong teaches you something — either your inputs were sloppy or your intuition was.

---

## 2. THE FRAMEWORK LIBRARY

### 2.1 Comparison table

| Framework | Formula / mechanism | Inputs needed | Good at | Breaks when | Best fit |
|---|---|---|---|---|---|
| **RICE** | (Reach × Impact × Confidence) ÷ Effort | Usage data, effort estimates | Comparing many similar-sized features | Items differ wildly in size or type; strategic bets | Mature product, data available, feature-level work |
| **ICE** | Impact × Confidence × Ease | Judgment only | Fast triage of a long list | Used for anything consequential — it's three guesses multiplied | Growth experiment backlogs |
| **WSJF** | Cost of Delay ÷ Job Size | CoD components, sizing | Sequencing when delay has real cost | Job Size is proxied by story points; CoD is guessed uniformly | SAFe environments; date-sensitive portfolios |
| **Cost of Delay** | Value lost per unit time of delay | Economic modelling | Making urgency explicit and arguable | No one can estimate the money | Deadline-driven and regulated work |
| **MoSCoW** | Must / Should / Could / Won't | Stakeholder negotiation | Scope negotiation inside a fixed release | Everything becomes "Must" | Fixed-date releases, contracts, RFPs |
| **Opportunity Scoring** | Importance + max(Importance − Satisfaction, 0) | Survey of outcome statements | Finding underserved needs quantitatively | Survey quality is poor; n too small | ODI/JTBD work with real survey capacity |
| **Kano** | Basic / Performance / Delight classification | Paired survey questions | Deciding where to invest *effort intensity* | Treated as a prioritization ranking (it isn't) | Feature-set design, packaging |
| **Impact/Effort 2×2** | Visual quadrants | Judgment | Fast alignment in a room | Everything drifts to "high impact, low effort" | Workshops, quick triage |
| **Weighted scoring** | Σ(criterion × weight) | Agreed criteria + weights | Multi-stakeholder decisions with real trade-offs | Weights are set after seeing the scores | Vendor selection, platform bets |
| **Capacity allocation** | % of capacity per category | Strategy + honest accounting | **Everything at portfolio level** | Treated as fixed rather than a quarterly choice | Any team with mixed obligations |

### 2.2 RICE — with the critique you need before using it

```
RICE = (Reach × Impact × Confidence) / Effort

Reach:      # of users/accounts affected per time period (real number)
Impact:     3 = massive, 2 = high, 1 = medium, 0.5 = low, 0.25 = minimal
Confidence: 100% / 80% / 50%
Effort:     person-months
```

**Three problems that senior PMs handle explicitly:**

1. **Confidence is applied to the wrong thing.** It multiplies the whole numerator, implying uniform uncertainty. In reality you're often highly confident about reach (you have the data) and wildly uncertain about impact (you're guessing). Fix: **apply confidence per-factor, or better, run the score twice — optimistic and pessimistic — and look at the range.** Items whose rank is stable across the range are safe bets; items that swing ten places are actually research tasks, not build tasks.

2. **Impact is an ordinal scale being used in multiplication.** "3 = massive" and "1 = medium" implies massive is exactly three times medium. It isn't; nobody knows what it is. This is fine for rough sorting and dishonest for precise ranking. **Never present RICE scores to two decimal places.** Round to bands: High / Medium / Low. The false precision is what gets you caught out by a sceptical exec.

3. **Effort denominators reward small things forever.** RICE systematically favours quick wins, which is why RICE-driven roadmaps quietly become incrementalism. Nothing structural ever wins on RICE because its effort is large and its reach is initially zero. **Any capability, platform, or architecture investment will lose every RICE contest it enters.** This is the single most important limitation, and the fix is not a better score — it's capacity allocation (§4).

**When to use RICE:** comparing 15–40 broadly comparable feature-level items on a mature product with usage data.
**When NOT to use RICE:** strategic bets, platform work, compliance mandates, anything where reach starts at zero, or a list with fewer than about eight items (just argue it out — the model costs more than it saves).

### 2.3 WSJF — you already use this, so here's where it goes wrong

```
WSJF = Cost of Delay / Job Size

Cost of Delay = User-Business Value + Time Criticality + Risk Reduction/Opportunity Enablement
```

**The two failure modes I see most often:**

**Failure 1 — Job Size proxied by story points.** Story points measure complexity as perceived by the team, not duration or cost. Using them as the denominator means a well-understood but genuinely long piece of work scores as "small." Fix: use **calendar duration to value delivery**, including dependency wait time. A 5-point story that waits three weeks on another team is not small.

**Failure 2 — Time Criticality assigned uniformly.** Most teams give nearly everything a 5 because everything feels urgent. This collapses WSJF into "value divided by size," which is just Impact/Effort with extra steps. Fix: force a distribution and require a **reason** in the Time Criticality field — a date, a contract, a season, a competitor move. If you can't name what changes on a specific date, Time Criticality is not high.

**Where WSJF genuinely shines in your world:** filing seasons and regulatory effective dates give you *real* time criticality, not invented urgency. A rule change with a statutory effective date has an actual cliff — value is high before the date and near zero after, because customers will have found another way to comply. That is textbook Cost of Delay and it is one of the few places the framework earns its complexity.

### 2.4 Cost of Delay — the four profiles

The most under-taught idea in prioritization. Value does not decay uniformly with delay; it has a *shape*, and the shape determines sequencing.

```
STANDARD              FIXED DATE            EXPEDITE            INTANGIBLE
value                 value                 value               value
 │‾‾‾╲                 │‾‾‾‾‾‾│              │╲                  │      ╱‾‾‾
 │    ╲                │      │              │ ╲                 │    ╱
 │     ╲___            │      └────          │  ╲___             │___╱
 └────────── time      └────────── time      └────────── time    └────────── time

Gradual decay.        Cliff at a date.      Very high now,      Nothing happens
Most features.        Regulatory work,      decays fast.        for a long time,
                      filing seasons.       Incidents, deals    then it matters
                                            with a close date.  a lot. Tech debt,
                                                                platform work.
```

**The intangible profile is why technical debt never gets prioritized.** Its cost curve is flat for a long time and then steepens sharply, and every scoring framework evaluated at a point in time reads that flat section as "low urgency." By the time the curve bends, you're in the expensive part.

This is a genuinely useful thing to say out loud in a roadmap meeting: *"Debt has an intangible cost-of-delay profile — it looks cheap to defer right up until it isn't, so we handle it with allocation, not scoring."*

### 2.5 Kano — commonly misused

Kano classifies features by how satisfaction responds to execution quality:

| Category | Behaviour | Implication |
|---|---|---|
| **Basic (must-be)** | Absence causes anger; presence causes nothing | Meet the bar, don't over-invest |
| **Performance** | Satisfaction scales linearly with quality | Invest proportionally to competitive pressure |
| **Delight (attractive)** | Absence is fine; presence delights | Small investments, high differentiation |
| **Indifferent** | Nobody cares | Stop |
| **Reverse** | Some users actively dislike it | Segment or make optional |

**The misuse:** treating Kano as a ranking. It isn't — it tells you **how much effort a feature deserves**, not what order to build in. A Basic feature can be top priority (if you don't have it) and simultaneously deserve minimal polish.

**Kano decays.** Today's delighter is tomorrow's basic. SSO was a differentiator in enterprise SaaS; now its absence disqualifies you. Re-classify annually or you'll keep investing in things that have become table stakes.

---

## 3. WHEN NOT TO USE A SCORING FRAMEWORK AT ALL

This section matters more than the frameworks.

| Situation | Why scoring fails | Do this instead |
|---|---|---|
| **Strategic bets** | The whole point is that the evidence doesn't exist yet; confidence scores will bury it | Write the bet with a falsifiable hypothesis (Vol III §2.1) and fund it from a reserved allocation |
| **Regulatory / compliance mandates** | Not optional; scoring implies it could lose | Bucket it as mandatory, then optimise *cost*, not priority |
| **Keeping the lights on** | Reliability work has no "reach" | Allocation + an error/correctness budget (Vol IV §2) |
| **One-way doors** | Score hides the asymmetry between being right and being wrong | Decision doc with options, evidence, and reversibility analysis |
| **Fewer than ~8 items** | The model costs more than the argument | Just argue. Write down the reasoning |
| **The decision is already made** | Scoring becomes laundering | Say the decision and its reason. Fake analysis destroys trust permanently |
| **Items are not comparable** | You cannot rank a migration against a button | Bucket first, then rank within buckets |
| **The score determines funding** | Goodhart's law: everyone inflates their inputs | Have someone other than the requester estimate reach and effort |

**On that last row.** Any number that decides who gets resources will be gamed — not maliciously, but through motivated estimation. The countermeasure is **separating the estimator from the beneficiary**: engineering sizes effort, analytics supplies reach, and the PM owns impact with a written rationale. When one person supplies all three inputs for their own proposal, the output is advocacy with a formula on top.

---

## 4. CAPACITY ALLOCATION — THE SENIOR TOOL

The single most useful shift from mid-level to senior prioritization: **stop maintaining one ranked list. Allocate capacity across categories first, then rank within each.**

One list forces incomparable things to compete, and the outcome is always the same — the legible, near-term, customer-visible thing wins, and platform, debt, and reliability starve until they cause an incident.

### The four-bucket model for regulated B2B

| Bucket | What's in it | Typical allocation | Ranked by |
|---|---|---|---|
| **Mandatory** | Regulatory changes, security obligations, contractual commitments | 20–35% (spikes seasonally) | Deadline, then cost to comply |
| **Strategic bets** | The 2–3 things the strategy says will make you win | 25–35% | Not ranked — funded or not |
| **Customer-driven** | Requests, friction, adoption blockers, competitive gaps | 20–30% | RICE / opportunity scoring |
| **Platform & health** | Debt, reliability, developer productivity, migrations | 15–25% | Risk exposure × leverage |

**Four things this unlocks immediately:**

1. **The mandatory number becomes visible.** If regulatory work is consuming 40% of capacity, that's not a prioritization problem, it's a *strategy* problem — and it's exactly the diagnosis in the Volume III worked example. You can't see it while everything is in one list.
2. **Strategic bets stop losing to quick wins**, because they never enter the same contest.
3. **The negotiation changes shape.** When Sales wants something added, the question is "which customer-driven item does it replace?" — not "is this important?" Nobody argues about importance; everyone can do arithmetic.
4. **You can defend platform work without an ROI fiction.** You don't need to prove a migration beats a feature on RICE. You need agreement that health gets 20%.

**Reset the allocation quarterly, deliberately.** It's a strategic choice, not a constant. Filing season may require 50% mandatory; the off-season is when you buy down debt and build platform.

**Exercise 5.1.** Categorise your last two completed quarters of work into the four buckets and compute the actual percentages. Compare to what you'd have said they were. *Almost every team discovers mandatory + unplanned interrupt work is far higher than they believed, which is itself the most valuable finding available to you this month.*

---

## 5. PRIORITIZATION vs SEQUENCING

Two different questions, routinely merged.

- **Prioritization** = what deserves capacity. Answered by value and strategy.
- **Sequencing** = what order, given dependencies, risk, and learning. Answered by architecture and uncertainty.

The highest-value item is frequently not the first item, for three legitimate reasons:

1. **Dependency.** It needs a capability that doesn't exist. Building the enabler first is not a detour.
2. **Risk retirement.** Do the thing that could kill the project *first*, cheaply, even if it isn't the most valuable — this is the whole logic behind the "weakest link" test in Volume II §8. A team that builds the easy 80% first and discovers in month four that extraction accuracy is 60% has sequenced badly, not prioritized badly.
3. **Learning order.** Some builds teach you what the next one should be. Sequence for information gain when uncertainty is high.

**Heuristic:** *prioritize by value, sequence by uncertainty.* Do the most uncertain consequential thing early and the most certain valuable thing next.

---

## 6. PART X EXERCISES & INTERVIEW BANK

**Exercise 5.2 — Range-based RICE.** Score your top 12 backlog items with optimistic and pessimistic inputs. Flag any item whose rank moves more than five places. Those aren't build items; they're research items. *Deliverable: a re-sorted backlog plus a short research list.*

**Exercise 5.3 — Cost of Delay profiles.** Assign one of the four CoD shapes to every item in your current quarter. Count how many are "intangible." *That count is your future incident rate.*

**Exercise 5.4 — The allocation conversation.** Propose a four-bucket allocation for next quarter to your manager, with the current-state percentages from Exercise 5.1 as evidence. *Deliverable: a one-page proposal. This is a visibly senior move and costs you nothing to make.*

**Interview questions**
1. Walk me through how you prioritize. *(Then: when does that method fail?)*
2. When would you not use a scoring framework?
3. How do you get platform or technical work prioritized against features?
4. Sales brings a €200k deal contingent on a feature that isn't on the roadmap. What do you do?
5. Your top-scored item and your intuition disagree. Which wins?
6. How do you prevent stakeholders from gaming your prioritization inputs?
7. What's the difference between prioritization and sequencing?

---

# PART XI — PRODUCT ECONOMICS

## 7. WHY THIS IS THE FASTEST CREDIBILITY GAIN AVAILABLE TO YOU

Most PMs speak in user outcomes and let someone else translate to money. That translation is where influence lives, and giving it away is why product loses arguments to sales and finance.

You do not need to be an accountant. You need to be able to hold a fifteen-minute conversation with your CFO without flinching, and to state any proposal as a business case with a range and a named assumption.

---

## 8. THE METRICS, PROPERLY DEFINED

### 8.1 Revenue

| Metric | Definition | Formula | The trap |
|---|---|---|---|
| **MRR / ARR** | Recurring revenue, normalised monthly/annually | Σ recurring subscription value | One-off implementation and services fees are **not** ARR. Including them inflates valuation and misleads planning |
| **Bookings** | Total contract value signed | Σ TCV | Signed ≠ earned ≠ collected. A 3-year deal books once and earns over 36 months |
| **Recognised revenue** | Revenue earned in a period | Per accounting policy | Diverges from cash and from ARR; know which one your exec means |
| **ACV** | Annual contract value per customer | ARR ÷ customers | An average across a bimodal base is meaningless — segment it |
| **ARPU / ARPA** | Revenue per user / per account | ARR ÷ users or accounts | In B2B, per-**account** is the useful one; per-seat masks utilisation problems |

### 8.2 Retention — where B2B SaaS actually lives

| Metric | Formula | What it tells you |
|---|---|---|
| **Logo churn** | Accounts lost ÷ accounts at start | How many customers left |
| **Gross Revenue Retention (GRR)** | (Start ARR − churn − contraction) ÷ Start ARR | Retention with **no credit for upsell**. Caps at 100%. The honest measure of whether the product holds |
| **Net Revenue Retention (NRR)** | (Start ARR − churn − contraction + expansion) ÷ Start ARR | The single most important number in B2B SaaS. >100% means you grow without new customers |

**Why NRR dominates:** at NRR of 120%, an existing cohort grows a fifth every year with no sales cost. At 90%, you must acquire aggressively just to stand still — you're filling a leaking bucket, and every efficiency gain in marketing is consumed by the leak.

**Always read GRR and NRR together.** NRR of 115% with GRR of 85% means a handful of accounts are expanding hard while the base is bleeding — a concentration risk that looks like health on one number. This exact pattern shows up in the Volume III worked example, where NRR is 104% overall but 91% in mid-market.

**The PM-relevant decomposition** — NRR is four separate product problems wearing one number:

```
NRR = 1 − (churn) − (contraction) + (expansion)

churn       → the product failed, or the buyer's need changed  → retention/onboarding work
contraction → seats bought but not used                        → activation and adoption work
expansion   → more seats, more usage, higher tier              → packaging and value-metric work
```

Contraction is the one PMs miss. **Seat utilisation is a leading indicator of contraction 6–12 months out**, and it is entirely a product metric. If a 40-seat account has 12 active users, that renewal is already smaller; you just haven't been told yet.

### 8.3 Acquisition economics

| Metric | Formula | Healthy range (mid-market B2B, directional) | Note |
|---|---|---|---|
| **CAC** | Total S&M spend ÷ new customers | — | Must include salaries, not just ad spend |
| **CAC Payback** | CAC ÷ (ARPA × gross margin %) | Under ~18 months | **The number cash-constrained boards actually watch** |
| **LTV** | (ARPA × gross margin %) ÷ churn rate | — | See the warning below |
| **LTV:CAC** | LTV ÷ CAC | 3:1 or better | Easy to fake |
| **Rule of 40** | Growth % + profit margin % ≥ 40 | — | A blunt but widely used health check |

**The LTV warning.** LTV computed as `ARPA ÷ churn` assumes churn stays constant forever and discounts nothing. With a 2% monthly churn assumption you get a 50-month lifetime, which is a made-up number extrapolated from a few months of data. Two corrections that make it honest:

1. Use **gross margin**, not revenue. Revenue you spend serving the customer isn't lifetime value.
2. Cap the horizon at 3–5 years, or discount future cash flows. An unbounded LTV is a marketing artefact.

**When a founder shows you LTV:CAC of 8:1, the first question is which churn number and which margin they used.** Asking it politely is a senior move.

---

## 9. GROSS MARGIN — THE PART PMs IGNORE AND SHOULDN'T

```
Gross Margin % = (Revenue − COGS) / Revenue
```

**COGS in SaaS** is not zero. It includes:

| Component | Typical driver | PM's lever |
|---|---|---|
| Hosting / infrastructure | Compute, storage, egress | Architecture, data retention policy, query efficiency |
| Third-party APIs | Per-call vendor fees (e-filing, KYC, document, payment) | Caching, batching, tier negotiation, deciding what's included vs metered |
| **AI inference** | Tokens/calls per task | Model selection, prompt size, caching, routing, when *not* to use a model |
| Customer support | Ticket volume × handling cost | **This is a product metric.** Every confusing screen is a recurring COGS line |
| Implementation / onboarding | Human hours per new account | Self-serve setup, migration tooling, templates |
| Data / content licensing | Per-account or per-use fees | Packaging decisions |

**The reframe that changes how you're seen:** support cost and onboarding cost are *product outputs*, not operational overhead. A product that generates 3 tickets per account per month at $18 fully-loaded handling cost is spending $648/account/year — which against a $6,400 ACV is ten points of gross margin, sitting in someone else's budget line where product never looks at it.

**Contribution margin** goes one level further: gross margin minus the variable cost of serving *that segment*, including its disproportionate support and success load. This is how you discover that a segment with healthy revenue is losing money — the finding that drives the Volume III strategy example.

### 9.1 AI features change margin structure — read this before your next AI proposal

Traditional software has near-zero marginal cost per use. **AI features do not.** Every invocation costs money, and the cost scales with usage rather than with accounts. This inverts a core SaaS assumption and most product plans still ignore it.

```
WORKED EXAMPLE — AI document extraction on a tax platform

Assumptions (illustrative; use your own vendor pricing):
  Documents per return                    8
  Returns per account per season        250
  Documents per account per season    2,000
  Cost per document (model + retries)  $0.02
  ────────────────────────────────────────
  AI COGS per account per season        $40

  Plus: re-runs from failed extractions (~15%)      +$6
  Plus: human review tooling / QA sampling           +$4
  ────────────────────────────────────────
  Realistic AI COGS per account                     ~$50

Against an ACV of $6,400 that is ~0.8 points of gross margin — acceptable.

NOW CHANGE ONE ASSUMPTION:
  A power-user segment processes 1,500 returns → 12,000 documents → ~$300/account.
  On a flat-price plan, your heaviest, most valuable-looking accounts are your
  worst-margin accounts. On a seat-based price, cost scales with usage while
  revenue scales with seats — and those two diverge without limit.
```

**The three product decisions this forces, all of which are yours to make:**

1. **Value metric alignment.** If cost scales with documents, price should relate to documents — a usage component, a fair-use cap, or a tier boundary. Selling unlimited AI on a flat seat price is a margin time bomb.
2. **Model routing.** Not every call needs the most capable model. Cheap model first, escalate on low confidence. This is a product decision with a direct margin line, and it is one of the clearest ways a PM demonstrably improves the P&L.
3. **When not to use AI at all.** If a deterministic rule handles 70% of documents at zero marginal cost, routing those to the rule and only the remainder to a model can cut inference cost by two-thirds with no quality loss. Volume IX develops this.

**This is the highest-signal thing you can bring to an AI product interview.** Most candidates discuss capability. Very few discuss unit economics, and the ones who do are immediately read as senior.

---

## 10. PRICING & PACKAGING — THE PM'S LARGEST LEVER

Pricing changes flow almost entirely to the bottom line, which makes it the highest-leverage variable in the business and the one PMs most often avoid because it "belongs to" finance or sales.

### 10.1 Model comparison

| Model | Aligns with | Pros | Cons | Fits when |
|---|---|---|---|---|
| **Per seat** | Team size | Predictable, easy to sell and forecast | Punishes broad adoption; breaks if cost scales with usage; drives seat-sharing | Value scales with people (CRM, HRMS) |
| **Usage-based** | Consumption | Margin-safe; low entry barrier; expands automatically | Unpredictable for the buyer — a real objection in budgeted enterprises | Value and cost both scale with volume (API, AI, filings) |
| **Tiered / packaged** | Segment needs | Simple; supports land-and-expand | Tier design is hard; wrong boundaries leave money everywhere | Distinct segments with distinct needs |
| **Hybrid (platform + usage)** | Both | Predictable floor plus upside | More complex to explain and to bill | Most mature B2B SaaS ends up here |
| **Per outcome** | Delivered result | Strongest value alignment | Attribution disputes; hard to measure | Rare; needs an unambiguous outcome |

### 10.2 Choosing the value metric

The value metric is *what you charge for*. Getting it right matters more than getting the price right, because the wrong metric misaligns you from the customer permanently.

**Three tests:**
1. **Does it scale with the value the customer receives?** (Returns filed scales with value. Logins does not.)
2. **Does it scale with your cost to serve?** (If not, you have the AI margin problem above.)
3. **Can the customer predict it?** (If they can't forecast their bill, enterprise procurement will resist regardless of the total.)

For a tax platform: *returns filed* passes all three; *seats* passes 1 and 3 but fails 2 once AI is in the product; *documents processed* passes 2 but fails 3.

**The hybrid resolution:** a seat- or tier-based platform fee that customers can budget, plus a usage component with an included allowance sized so most accounts never exceed it. Predictable for them, margin-safe for you.

### 10.3 Packaging: the good/better/best discipline

- **Tier boundaries should be drawn on segment need, not on feature count.** The question is "which capabilities does this segment genuinely require," not "how do we split 40 features into three piles."
- **Never put reliability, security, or audit integrity behind a tier in a compliance product.** It reads as "we sell you the safe version," and it will be quoted back to you in a procurement review.
- **Move things up-tier only with warning.** Removing a feature from a tier a customer already has is a trust event, and in B2B it surfaces at renewal with interest.

---

## 11. THE PM'S ECONOMIC LEVER MAP

Print this. It's the translation layer between what you do and what finance sees.

| You improve | Directly moves | Second-order effect |
|---|---|---|
| Activation / time-to-first-value | CAC payback, early churn | Expansion earlier in the lifecycle |
| Onboarding self-service | Implementation COGS, gross margin | Faster payback, better sales efficiency |
| Feature adoption depth | Contraction, NRR | Higher renewal ACV |
| Seat utilisation | Contraction (leading indicator) | Renewal size 6–12 months out |
| Error/rework rate | Support COGS, churn | Trust, referenceability, win rate |
| Self-serve config | Professional services cost | Scalability of the segment |
| AI model routing | Gross margin | Ability to include AI in lower tiers |
| Migration tooling | Win rate vs status quo | Reduces the anxiety force (Vol II §2.4) |
| Packaging/tier redesign | ARPA, expansion | Segment profitability |
| Deprecating a feature | Maintenance cost, focus | Sometimes churn — model it first |

---

## 12. PART XI EXERCISES & INTERVIEW BANK

**Exercise 5.5 — Build your product's unit economics.** One page: ACV, gross margin (with COGS components), CAC payback, GRR, NRR by segment. Where you don't know a number, write "unknown" rather than guessing, then go and find three of them. *Deliverable: the page, plus a list of what you couldn't find — which is itself a finding.*

**Exercise 5.6 — Support cost as product debt.** Take your top 10 support ticket categories by volume. Multiply by handling cost. Express as points of gross margin. *This converts "usability improvement" into a finance conversation, which is the entire point.*

**Exercise 5.7 — The AI margin model.** For any AI feature you're considering, build the §9.1 model with your real vendor pricing, then stress it at the 95th-percentile account. *Deliverable: a cost-per-account curve and a pricing recommendation.*

**Exercise 5.8 — Discount archaeology.** Pull realised price vs list price by segment from your CRM. *Your average discount is your pricing error, and it's sitting in a system you already have access to.*

**Interview questions**
1. How does your product make money? What's the biggest lever on gross margin?
2. What's the difference between GRR and NRR, and when would you care more about one?
3. Your NRR is 118% and your GRR is 84%. What's happening and what do you do?
4. How would you price an AI feature?
5. A feature would delight customers and reduce margin by four points. How do you decide?
6. What's wrong with an LTV:CAC ratio of 9:1?
7. How do you decide between seat-based and usage-based pricing?
8. Which product metric would you watch to predict revenue contraction two quarters early?

---

*Volume V complete. Continue to `06-analytics-and-experimentation.md`.*
