# VOLUME VI — PRODUCT ANALYTICS & CAUSAL THINKING
### Parts XII & XIII

> Most PMs report metrics. Few interpret them. Almost none know their product's normal variance — which means almost none can tell you whether a number that moved actually moved.

**This is your identified portfolio gap.** Compliance and workflow products rarely A/B test, so if you don't build causal reasoning deliberately, the market will read your background as "requirements and delivery." Part XIII exists specifically to make you fluent in causal inference *without* experimentation, which is a rarer and more valuable skill than running A/B tests.

---

# PART XII — PRODUCT ANALYTICS

## 1. THE CHAIN

```
METRIC → INSIGHT → HYPOTHESIS → DECISION → EXPERIMENT → back to METRIC
```

Each arrow is a place teams stall:

| Arrow | The stall | What it looks like |
|---|---|---|
| Metric → Insight | Reporting without interpreting | A dashboard nobody acts on; a weekly deck of numbers with no verbs |
| Insight → Hypothesis | Observation mistaken for explanation | "Activation is low in enterprise" — that's a fact, not a hypothesis |
| Hypothesis → Decision | Analysis paralysis | Six more cuts of the data, no decision |
| Decision → Experiment | Shipping without measurement | Feature launches with no success criterion defined beforehand |
| Experiment → Metric | No feedback loop | Nobody checks 30 days later |

**A hypothesis has a specific grammar** and most don't meet it:

> *We believe **[specific change]** for **[specific segment]** will cause **[specific metric]** to move by **[magnitude]** because **[mechanism]**. We'll know within **[time]**. If it doesn't, we were wrong about **[the mechanism]**.*

The "because" clause is what makes it falsifiable and what makes a failure informative. Without a stated mechanism, a failed test teaches you nothing except that one variant lost.

---

## 2. METRIC TYPES — GET THIS RIGHT FIRST

| Type | Definition | Example (tax platform) | Controllable? | Lag |
|---|---|---|---|---|
| **Input** | Things the team directly acts on | # of returns with auto-imported documents | Yes | Immediate |
| **Output** | Direct result of inputs | Median time-to-file per return | Mostly | Days–weeks |
| **Outcome** | Business/customer result | Returns per preparer per season; NRR | Influenced, not controlled | Months |
| **Guardrail** | Must not degrade | Calculation defect rate; p95 page load | Yes | Immediate |
| **Vanity** | Looks good, drives nothing | Total registered users; page views | — | — |

**Amazon publicly emphasises focusing teams on controllable *input* metrics rather than lagging outputs** (E2 — described in detail in *Working Backwards*; the underlying logic appears in shareholder letters, E1). The reasoning is sound and portable: a team cannot act on "increase NRR." It can act on "increase the share of returns using auto-import," and if the causal chain is right, NRR follows.

**Your practical rule:** every team should have **one outcome it's accountable for** and **two or three inputs it actually manages**. Reporting on outcomes weekly produces anxiety and no action, because outcomes don't move weekly.

### 2.1 The metric tree — the artefact to build

More useful than any single North Star, and it makes causal assumptions explicit and arguable.

```
OUTCOME:  Returns completed per preparer per season
   │
   ├── Returns started per preparer
   │      ├── # of clients onboarded          [input: client import success rate]
   │      └── % of clients with complete docs [input: doc portal adoption]
   │
   ├── Time per return  ────────────────────────────────────── (the biggest lever)
   │      ├── Data entry time      [input: auto-extraction coverage %]
   │      ├── Waiting time         [input: median dwell in "awaiting docs"]
   │      ├── Validation rework    [input: validation errors per return]
   │      └── Review time          [input: % returns needing manual trace review]
   │
   └── Rejection / amendment rate
          ├── Calculation defects  [GUARDRAIL: defect escape rate]
          └── Submission errors    [input: pre-submission validation pass rate]
```

**Every branch is a claim about causality that someone can dispute.** That's the value — the tree turns "we should improve the product" into ten specific, testable assertions, and it shows instantly which team owns which branch.

**Exercise 6.1.** Build this for your product. Take it to your engineering lead and your data analyst separately and ask which branch they think is wrong. *Deliverable: the tree plus the disputed branches, which become your analytics roadmap.*

### 2.2 North Star metrics — use with care

A North Star is a single metric capturing the core value delivered. Done well it aligns an organisation. Done badly it becomes the thing everyone games.

**Selection criteria:** it must (1) reflect customer value, not company value, (2) be influenceable by product work, (3) lead revenue rather than lag it, (4) be hard to game without actually delivering value.

**Where it fails, and these matter for you:**
- **Mandated-use products.** Engagement-flavoured North Stars are actively misleading when usage is compulsory. More time in your product may mean it's harder to use.
- **Seasonal products.** A metric that swings 5× between March and August tells you nothing week to week. Use season-over-season or same-period-last-year comparisons, and say so explicitly on every chart.
- **Multi-product portfolios.** One North Star across CRM, HRMS, and tax is so abstract it stops meaning anything. Use per-product North Stars with a shared outcome layer above.

**Better default for B2B workflow software:** a **task-success composite** — completed units of work per active user per period, with a quality guardrail attached. For your domain: *returns filed per preparer per week, with amendment rate as guardrail.* It resists gaming because you can't inflate it without doing real work correctly.

---

## 3. THE B2B ANALYTICS PROBLEM

Every consumer-derived analytics playbook assumes large N, voluntary usage, and short feedback loops. You have none of these. Adaptations:

| Problem | Why it breaks the playbook | Adaptation |
|---|---|---|
| **Small N** | 1,200 accounts can't reach significance on most tests | Account-level analysis, longer windows, qual triangulation; treat quantitative signal as *directional* and say so |
| **Account vs user** | 40 users in one account aren't 40 independent observations | Cluster at the account level. Treating users as independent inflates significance dramatically — a common and serious error |
| **Mandated usage** | Engagement ≠ value | Measure task completion, error rate, rework, support contact |
| **Seasonality** | Every metric swings enormously | Always compare same-period-prior-year; never month-over-month in a seasonal business |
| **Long feedback loops** | Renewal signal arrives 12 months late | Build leading indicators: seat utilisation, feature breadth, support trend, admin logins |
| **Buyer ≠ user** | Product metrics don't predict renewal on their own | Combine product signal with commercial signal in account health |
| **Concentration** | 20 accounts may be 60% of revenue | Weight analysis by revenue, not by account count. An "average account" may not exist |

### 3.1 Account health — the B2B replacement for engagement

```
ACCOUNT HEALTH (weighted; tune weights against actual churn history)

  Utilisation      seats active ÷ seats licensed        (30%)  ← best contraction predictor
  Breadth          # of core capabilities used ≥1×/mo   (20%)  ← stickiness
  Task success     completion rate, error/rework rate   (20%)  ← is it working for them
  Support signal   ticket rate, sentiment, escalations  (15%)  ← friction
  Admin engagement admin logins, config changes         (10%)  ← is anyone stewarding it
  Commercial       payment history, exec turnover        (5%)  ← context

  RED = any single component in bottom decile, regardless of composite.
```

**That last rule matters.** A composite can look fine while one component collapses. Utilisation at 15% is a renewal problem even if everything else is green, and averaging hides it.

**Validate the weights against history, don't invent them.** Take last year's churned accounts, score them at T-6 months, and check whether your model would have flagged them. If it wouldn't have, the weights are decoration.

---

## 4. CORE MEASURES, PRECISELY

| Measure | Formula | The definitional trap |
|---|---|---|
| **Activation** | % of new accounts reaching a defined value moment within N days | The value moment must be *empirically* linked to retention, not chosen by vibes. Find it by comparing retained vs churned cohorts |
| **Adoption (feature)** | Users/accounts using feature ≥1× ÷ eligible | Denominator must be *eligible* users, not all users. Reporting adoption against an ineligible base is the most common analytics lie |
| **Depth** | Actions per user per period | Higher isn't automatically better in workflow tools |
| **Breadth** | # of distinct capabilities used | The strongest simple retention correlate in most B2B SaaS |
| **Stickiness** | DAU/MAU | **Near-useless for seasonal B2B.** A preparer using it daily for six weeks and never in July is healthy |
| **Retention (cohort)** | % of a cohort still active in month N | Define "active" as a meaningful action, not a login |
| **Time to value** | Signup → first value moment | The metric most correlated with CAC payback |

### 4.1 Reading a retention curve

```
%active
100│╲
   │ ╲
   │  ╲___________  ← FLATTENS: a durable segment exists. This is what PMF looks like
   │
   │╲
   │ ╲
   │  ╲___
   │      ╲___
   │          ╲___  ← NEVER FLATTENS: no durable value. More acquisition won't save it
   └──────────────── months
```

**The flattening is the whole signal.** The absolute retention level matters less than whether the curve reaches an asymptote. A curve that flattens at 35% means you have a real product for 35% of who you're acquiring — the problem is targeting, not the product. A curve that never flattens means you're leaking regardless of how many you pour in, and every marketing pound is wasted.

**Always plot cohorts separately, never blended.** Blended retention mixes cohorts of different ages and different acquisition sources and can trend upward while every individual cohort worsens — a straightforward instance of the mix problem in §8.5.

---

## 5. INSTRUMENTATION IS A PRODUCT REQUIREMENT

If it isn't in the PRD, it doesn't exist. Add this section to every PRD you write:

```
ANALYTICS REQUIREMENTS
  Decision this data will support:      [if you can't name one, don't instrument it]
  Events:            name, trigger, properties, PII classification
  Identity:          user_id, account_id, session — how are they joined?
  Success metric:    definition + measurement window + expected direction
  Guardrails:        what must not degrade, and the threshold
  Segment cuts:      which dimensions must be sliceable from day one
  Baseline:          current value + normal variance  ← almost always missing
  Verification:      who confirms events fire correctly, before GA
  Retention/privacy: how long stored, jurisdiction, deletion path
```

**The baseline-and-variance line is the one that separates competent from senior.** If you don't know that weekly activation normally ranges 22–31%, you cannot tell whether 24% is a problem. Teams without baselines spend enormous effort investigating noise and then congratulate themselves when it reverts.

---

## 6. THE DIAGNOSTIC PLAYBOOK: "THE METRIC MOVED"

Run this in order. Skipping steps is how weeks get lost.

**1. Is it real? (Check instrumentation FIRST — always.)**
Recent deploys, SDK changes, tracking plan edits, bot filtering, a renamed event, a new consent banner suppressing collection. A meaningful share of "our metric crashed" incidents are measurement bugs, and diagnosing a real cause for a fake drop is pure waste.

**2. Is it outside normal variance?**
Compare against the trailing distribution, not last week. If the metric normally swings ±20% week to week, a 15% drop is noise. **Say so out loud** — talking a team out of reacting to noise is a genuine senior contribution and almost nobody does it.

**3. Is it composition or behaviour?**
Did the *mix* of users change, or did the *same* users change? Hold the mix constant and re-check. This single step resolves a large share of confusing movements (see Simpson's paradox, §8.5).

**4. Where in the funnel?**
Decompose into the metric tree. Find the specific branch. "Conversion dropped" is not actionable; "document-upload step completion dropped from 71% to 44%" is.

**5. Which segment?**
Cut by plan, size, geography, acquisition source, tenure, platform, browser, app version. A metric that moved uniformly across all segments is usually external or instrumentation; a metric that moved in one segment is usually a specific cause.

**6. What else changed?**
Your releases, someone else's releases, pricing, marketing spend and channel mix, a competitor launch, a regulatory deadline, a holiday, an outage, a support policy change.

**7. Ask a human.**
Five support tickets or two customer calls will often resolve in an hour what a week of slicing won't. Quantitative tells you *what*; only people tell you *why*.

**Exercise 6.2.** Write this playbook as a one-page runbook for your team, with your product's actual dashboards and event names filled in. *Deliverable: a runbook. This is a visible ops contribution and takes an afternoon.*

---

# PART XIII — EXPERIMENTATION & CAUSAL THINKING

## 7. EXPERIMENT DESIGN

### 7.1 The design document

```
EXPERIMENT: [name]
Hypothesis:        We believe [change] for [segment] will cause [metric] to move
                   [direction] by [magnitude] because [mechanism].
Primary metric:    ONE. Decided before launch. Non-negotiable.
Secondary:         2–4, exploratory only — cannot be used to declare a win
Guardrails:        must not degrade beyond [threshold] — e.g. error rate, latency,
                   support contacts, and in your domain: calculation defect rate
Unit of assignment: user | account | session   ← in B2B this is almost always ACCOUNT
MDE:               smallest effect worth detecting, chosen for BUSINESS relevance
Sample size:       computed from baseline, MDE, power (0.8), alpha (0.05)
Duration:          ≥ 1 full business cycle; ≥ 2 weeks; never stop at significance
Stopping rule:     defined in advance
Decision rule:     if primary +X% and no guardrail breach → ship.
                   Ambiguous → [pre-committed action]
Who decides:       [name]
```

**Two lines carry most of the value:**

**The MDE must be a business decision, not a statistical one.** Ask: how small an improvement would still be worth the maintenance cost of this feature forever? If a 0.5% lift isn't worth keeping the code, don't design a test to detect it — because detecting small effects requires enormous samples and long durations you probably don't have.

**Unit of assignment in B2B is the account.** Users within an account talk to each other, share workflows, and are trained together. Randomising by user creates contamination and, worse, treats 40 correlated users as 40 independent samples, which inflates your apparent significance badly. Randomise by account and analyse by account.

### 7.2 Why sample size is brutal, in one line

The sample needed scales roughly with **1/MDE²**. Halving the effect you want to detect quadruples the sample. Detecting a 1% relative lift instead of a 5% one needs roughly 25× the traffic.

**What this means for a 1,200-account product:** you can reliably detect large effects and nothing else. That is not a failure — it's a design constraint. It means your experimentation strategy should be *few, large, bold changes*, not continuous micro-optimisation. Teams with small N who copy a high-volume experimentation culture run underpowered tests, get noisy results, and make confident decisions on nothing. That is worse than not testing.

### 7.3 The four ways experiments lie

| Problem | Mechanism | Prevention |
|---|---|---|
| **Peeking** | Checking daily and stopping when significant. With repeated looks, false-positive rate rises far above 5% | Fix duration in advance, or use sequential-testing methods designed for it |
| **Multiple comparisons** | 20 secondary metrics at α=0.05 → ~1 false positive by chance | Declare one primary metric before launch. Secondaries generate hypotheses, never conclusions |
| **Novelty / primacy** | Users react to *change*, not the change's merit. Effects decay (novelty) or reverse (primacy, from disrupted habits) | Run ≥2 weeks; check whether the effect holds in week 2+; segment new vs existing users |
| **Survivorship in the sample** | Only users who reached the surface are measured; those who bounced earlier are invisible | Define the population at the point of *eligibility*, not exposure |

### 7.4 Significance vs meaning

- **p < 0.05** means: if there were no true effect, data this extreme would occur under 5% of the time. It does **not** mean 95% probability the effect is real, and it says nothing about size.
- **Statistically significant** and **practically significant** are independent. With enough traffic, a 0.05% lift is significant and worthless.
- **Prefer confidence intervals.** "+3.2% (95% CI: +0.4% to +6.0%)" tells you the effect is probably positive but might be small. "p = 0.03" tells you almost nothing you can act on. Reporting intervals also stops the binary win/lose framing that pushes teams to ship marginal changes.

---

## 8. CAUSAL THINKING WITHOUT EXPERIMENTS

This is the section that matters most for your career, because **your domain often can't A/B test** — and a PM who reasons causally without experiments is more valuable than one who can only read a test dashboard.

### 8.1 When experiments are inappropriate

| Situation | Why | Do instead |
|---|---|---|
| **Low traffic** | Underpowered; noise reads as signal | Staged rollout with matched comparison; qual + pre/post |
| **Contractual/enterprise** | You can't give customers different products with different terms | Beta cohorts with consent; opt-in pilots |
| **Compliance-critical paths** | Deliberately serving a possibly-worse filing experience may be unacceptable or illegal | Shadow mode: run the new logic, log the outcome, don't act on it |
| **One-way doors** | Pricing, data model, brand — you can't unship the learning | Decision doc + qualitative + modelling |
| **Network / cross-account effects** | Treatment leaks between groups, breaking independence | Switchback or geo/segment-level assignment |
| **Long feedback loops** | Renewal signal is 12 months out | Test against a validated leading indicator instead |
| **Ethical constraints** | Withholding a safety improvement is not a test | Ship it; measure pre/post |
| **Seasonal cliffs** | The test window changes the world mid-experiment | Run in a stable window or use same-period-prior-year |

### 8.2 The alternatives toolkit

| Method | How | Strength | Weakness |
|---|---|---|---|
| **Staged rollout with holdout** | Ship to 80%, hold 20% back for a defined period | Nearly as good as an A/B test; operationally easy | Requires flagging; holdout groups get "forgotten" |
| **Pre/post with a control group** | Compare changed cohort to an unchanged similar cohort | Simple; works with small N | Groups must be genuinely comparable |
| **Difference-in-differences** | Compare *change* in treated vs *change* in control | Removes shared time trends — good for seasonal products | Assumes parallel trends absent treatment; test that assumption first |
| **Shadow mode** | Run new logic silently, log what it *would* have done | **Ideal for calculation engines and AI** — zero user risk | Doesn't measure behaviour, only correctness |
| **Regression discontinuity** | Compare just-above vs just-below a threshold (plan limits, account size) | Strong causal claim near the cutoff | Only valid near the threshold |
| **Switchback** | Alternate treatment over time within the same population | Handles network effects | Needs many switch periods |
| **Instrumented qual** | 8 structured sessions with the same task and measurement | Fast, explains mechanism | Small n; not generalisable |
| **Synthetic control** | Construct a weighted comparison from untreated units | Works with one treated unit | Requires history and care |

**Shadow mode deserves emphasis for you.** For a calculation engine, rules platform, or extraction model, you can run the new version against real production inputs, log the divergences, and analyse them — with zero risk to a single filing. It gives you a full-population correctness comparison rather than a sampled behavioural one, and it's often *better* evidence than an A/B test would have been. **This is a strong, specific thing to describe in a TPM or AI PM interview.**

### 8.3 Confounders and selection bias

**Confounder** — a third variable causing both the observed cause and effect.

> *Observed:* accounts using the API integration retain 22 points better.
> *Naive conclusion:* push API adoption to improve retention.
> *Likely reality:* accounts that integrate are larger, better resourced, and more committed — the same traits that cause retention. Integration is a **marker**, not a lever.
> *Test:* find similar-sized, similar-tenure accounts that did and didn't integrate. If the gap shrinks toward zero, it was confounded. If it holds, you may have a real lever.

This pattern — "users who do X retain better, so make everyone do X" — is the most common analytical error in product management, and it produces roadmaps full of forced adoption of things that were never causal.

**Selection bias** — your sample isn't representative of the population you're concluding about.

> Surveying in-app produces responses only from people still using the product. The people whose opinion would change your roadmap left months ago. **Churned-customer research is the highest-value and least-conducted research in B2B SaaS.**

### 8.4 Regression to the mean

Extreme measurements tend to be followed by less extreme ones, for purely statistical reasons.

> *Setup:* you target the 50 worst-performing accounts by usage with a CS intervention. Next quarter their usage improves 30%. Success declared.
> *Problem:* some fraction of those accounts were at a temporary low. They'd have improved without you. Selecting on an extreme guarantees apparent improvement.
> *Fix:* select 100 low-usage accounts, intervene on a random 50, compare. Without a control group you cannot separate the intervention from the arithmetic.

**This is the single most common false success story in customer success and growth programmes**, and being the person in the room who names it is high-value.

### 8.5 Simpson's paradox — worked example

A trend present in every subgroup reverses when the groups are combined.

> **Setup.** You ship a new self-serve onboarding flow. Trial-to-paid conversion:
>
> | | Before | | After | |
> |---|---|---|---|---|
> | Segment | Trials | Conv. | Trials | Conv. |
> | SMB | 400 | 24% (96) | 700 | 22% (154) |
> | Enterprise | 600 | 9% (54) | 300 | 8% (24) |
> | **Total** | **1,000** | **15.0%** | **1,000** | **17.8%** |
>
> **Overall conversion rose from 15.0% to 17.8%. Conversion fell in both segments.**
>
> **Mechanism.** SMB converts far better than Enterprise. Marketing changed channel mix at the same time, shifting SMB from 40% to 70% of trials. The mix improvement swamped the within-segment decline.
>
> **Consequence if undetected:** you declare the onboarding flow a success, roll it out fully, and it is actively hurting conversion in both segments while the mix effect masks it.
>
> **Prevention:** *always segment before concluding, and always check whether the mix changed.* Step 3 of the §6 playbook exists for exactly this.

**Why this hits B2B especially hard:** your segments have wildly different conversion, retention, and revenue characteristics, and mix shifts constantly with sales focus and marketing spend. Aggregate metrics in a mixed B2B base are misleading by default, not occasionally.

### 8.6 The reviewer's checklist

Apply to any analysis, including your own:

1. What's the denominator, and is it the *eligible* population?
2. What's the unit of analysis, and are those units independent?
3. Did the mix change over the comparison period?
4. What else changed at the same time?
5. Was the metric definition stable across the whole window?
6. Was the population selected on an extreme value?
7. Who's missing from this sample?
8. Is this within normal variance?
9. Was the primary metric chosen before or after seeing the data?
10. If this is right, what else should be true — and is it?

**Question 10 is the strongest one.** If auto-import genuinely cut data entry time, then time-in-"data entry" state should have dropped, support tickets about entry should have fallen, and returns-per-preparer should have risen. If only the headline metric moved and none of its consequences did, the headline metric probably moved for another reason.

---

## 9. VOLUME VI EXERCISES

**Exercise 6.3 — Find your true activation moment.** Compare retained vs churned cohorts on actions taken in the first 14 days. Identify the action with the largest separation. Then check for confounding: is it a lever or a marker? *Deliverable: a defensible activation definition — most teams have one chosen by intuition.*

**Exercise 6.4 — Baseline and variance sheet.** For your ten most-reported metrics, record the mean and the range over the last 12 comparable periods. *Deliverable: a one-page reference that ends arguments about whether something "dropped."*

**Exercise 6.5 — Design an experiment you can't run.** Take a decision your product genuinely can't A/B test. Design the best available causal alternative from §8.2, with its assumption stated and how you'd check it. *Deliverable: a portfolio artefact that directly addresses your experimentation gap — arguably stronger than an A/B test writeup, because it demonstrates judgment rather than tool use.*

**Exercise 6.6 — Confounder hunt.** Find one "users who do X retain better" claim in your organisation. Test it against a matched comparison. *Deliverable: either a validated lever or a corrected belief. Both are wins.*

**Exercise 6.7 — Shadow-mode plan.** Design a shadow-mode evaluation for a change to your calculation or rules engine: what you log, how you classify divergences, what threshold gates the release. *This is the bridge artefact to Volume IX.*

---

## 10. VOLUME VI INTERVIEW BANK

1. Your key metric drops 20% overnight. Walk me through your first hour.
2. How do you pick a North Star metric? When is one a bad idea?
3. You have 900 accounts. How do you run a valid experiment?
4. When should you *not* A/B test?
5. Explain a confounder using an example from a product you've worked on.
6. Conversion is up overall but down in every segment. What happened?
7. What's the difference between statistical and practical significance?
8. Accounts that use Feature X retain 20 points better. What do you do with that?
9. Your CS team intervened on the 50 worst accounts and they improved 30%. Did the intervention work?
10. How do you measure success for a feature in a product people are required to use?
11. What would you instrument before shipping, and how do you decide?
12. How do you know when a metric movement is noise?

---

*Volume VI complete. Continue to `07-design-requirements-execution.md`, or say `build vol 8` to jump to Technical & Platform PM.*
