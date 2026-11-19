# VOLUME XIII — FRAMEWORK LIBRARY & ANTI-PATTERNS
### Parts XXXV & XXXVI

> A framework is a structure for thinking. It produces a shape, never an answer. The senior skill is knowing which shape fits the problem — and when no shape does.

**How to use this volume.** The framework library is a lookup: when you're about to reach for something, check its "wrong use" row first. The anti-pattern library is a diagnostic: read the warning signs and check them against your own team honestly.

---

# PART XXXV — THE FRAMEWORK LIBRARY

## 1. DISCOVERY FRAMEWORKS

| Framework | Purpose | Inputs → Outputs | Best use | Wrong use & key limitation |
|---|---|---|---|---|
| **Design Thinking** | Human-centred problem solving | Empathy research → problem definition → ideas → prototype → test | Ill-defined human problems; getting non-designers to think about users | **Wrong use:** as a linear process with a deadline. **Limitation:** methodology, not strategy — says nothing about whether the problem is worth solving commercially |
| **Double Diamond** | Structuring divergence and convergence | A problem area → (diverge/converge) → defined problem → (diverge/converge) → solution | Explaining to stakeholders why you're not building yet | **Wrong use:** treating it as a project plan. **Limitation:** describes a shape, not a method |
| **Jobs-to-be-Done (Progress)** | Understanding why people switch | Switch interviews → forces of progress, job statements | Churn analysis, competitive losses, new market entry | **Wrong use:** as a quantitative sizing tool. **Limitation:** small-n, story-seductive; you'll believe a compelling narrative from 6 people |
| **JTBD (Outcome-Driven / ODI)** | Quantifying underserved needs | Outcome statements rated importance × satisfaction → opportunity scores | Ranking improvement areas with real survey capacity | **Wrong use:** with n<100 or badly written outcome statements. **Limitation:** misses emotional and social jobs entirely |
| **Continuous Discovery** | Sustaining customer contact | Weekly interviews + assumption tests → opportunity tree updates | Teams with regular customer access | **Wrong use:** in seasonal or access-gated B2B without adaptation. **Limitation:** assumes cheap, frequent access to users |
| **Opportunity Solution Tree** | Connecting outcomes to solutions | Desired outcome → opportunities → solutions → tests | Making prioritisation debates structured | **Wrong use:** putting solutions in opportunity nodes. **Limitation:** only as good as the outcome at the top |
| **Assumption Mapping** | Finding what could kill you | Assumptions → importance × evidence grid | Before committing to any significant build | **Wrong use:** listing only comfortable assumptions. **Limitation:** you can't map an assumption you can't see |

**The one worth internalising:** the Opportunity Solution Tree's rule that **you compare solutions only within an opportunity, never across the tree**. Comparing "bulk edit" to "client document portal" is meaningless — different opportunities. That single constraint prevents most bad prioritisation arguments.

---

## 2. STRATEGY FRAMEWORKS

| Framework | Purpose | Inputs → Outputs | Best use | Wrong use & key limitation |
|---|---|---|---|---|
| **Rumelt's Kernel** | Constructing an actual strategy | Situation → diagnosis, guiding policy, coherent actions | **The default. Use this one** | **Wrong use:** writing a diagnosis a competitor would also write. **Limitation:** demands honesty most orgs find uncomfortable |
| **SWOT** | Situation inventory | Internal/external scan → four lists | A 30-minute input to a strategy doc | **Wrong use:** as an output. **Limitation:** produces lists, not choices; invites self-flattery; no prioritisation |
| **PESTLE** | Macro-environment scan | Political/Economic/Social/Technological/Legal/Environmental scan → risk and opportunity list | **Regulated markets — the P and L are your roadmap** | **Wrong use:** on feature-level decisions. **Limitation:** breadth without depth |
| **Porter's Five Forces** | Industry structural attractiveness | Buyer/supplier power, entrants, substitutes, rivalry → margin explanation | Explaining why margins are what they are; new market entry | **Wrong use:** as a competitive-response tool. **Limitation:** static; built for 1980 manufacturing; weak on platforms and complements |
| **Value Chain** | Where value is created and captured | Activity decomposition → integration/divestment options | Make-vs-buy, platform boundaries | **Wrong use:** on pure software services. **Limitation:** designed for physical goods flows |
| **Ansoff Matrix** | Growth direction | Existing/new × product/market → four growth types | Naming which *kind* of bet you're making | **Wrong use:** as a plan. **Limitation:** says nothing about how, or whether you can |
| **Wardley Mapping** | Component evolution + strategic play | Value chain × evolution axis → map, then plays | Platform strategy, build-vs-buy at scale | **Wrong use:** without learning it properly. **Limitation:** steep curve, small practitioner community |
| **Positioning (Dunford)** | Setting the market context | Alternatives → attributes → value → segment → category | Before any messaging or GTM work | **Wrong use:** listing vendors as the alternative when the real one is Excel. **Limitation:** requires honesty about who you're actually for |

**Note on SWOT.** It survives because it's easy to run and everyone understands it. That's a real virtue for a 30-minute alignment exercise. It becomes harmful the moment it's presented *as* the strategy, because four lists with no forced choices let everyone read their preferred conclusion into the same document.

---

## 3. PRIORITIZATION FRAMEWORKS

Full treatment in Volume V. Reference form:

| Framework | Formula | Inputs → Outputs | Best use | Wrong use & key limitation |
|---|---|---|---|---|
| **RICE** | (Reach × Impact × Confidence) ÷ Effort | Usage data + estimates → ranked list | 15–40 comparable feature-level items on a mature product | **Wrong use:** on strategic bets or platform work. **Limitation:** effort denominator kills anything structural; ordinal impact used in multiplication |
| **ICE** | Impact × Confidence × Ease | Judgment → ranked list | Fast triage of growth experiments | **Wrong use:** for consequential decisions. **Limitation:** three guesses multiplied together |
| **WSJF** | Cost of Delay ÷ Job Size | CoD components + sizing → sequence | Genuine date-driven work — filing seasons, statutory deadlines | **Wrong use:** Job Size proxied by story points; uniform Time Criticality. **Limitation:** collapses to value/effort when CoD isn't differentiated |
| **Cost of Delay** | Value lost per unit time | Economic modelling → urgency, made explicit | Making deadline pressure arguable rather than emotional | **Wrong use:** where nobody can estimate the money. **Limitation:** the intangible profile makes debt look permanently deferrable |
| **MoSCoW** | Must/Should/Could/Won't | Stakeholder negotiation → scoped release | Fixed-date releases, RFPs, contracts | **Wrong use:** as a backlog method. **Limitation:** everything becomes "Must" without enforced quotas |
| **Opportunity Scoring** | Importance + max(Imp − Sat, 0) | Outcome survey → ranked underserved needs | ODI programmes with real survey capacity | **Wrong use:** small samples. **Limitation:** survey quality determines everything |
| **Kano** | Basic/Performance/Delight classification | Paired functional/dysfunctional questions → categories | Deciding **effort intensity** per feature | **Wrong use:** as a ranking. **Limitation:** categories decay — today's delighter is tomorrow's basic |
| **Impact/Effort 2×2** | Visual quadrants | Judgment → a shared picture | 20-minute workshop alignment | **Wrong use:** as a record of decisions. **Limitation:** everything drifts to the good quadrant |
| **Capacity allocation** | % per category | Strategy + honest accounting → buckets | **Portfolio level — the senior tool** | **Wrong use:** setting it once and never revisiting. **Limitation:** requires the authority to hold the line |

---

## 4. GROWTH FRAMEWORKS

| Framework | Purpose | Inputs → Outputs | Best use | Wrong use & key limitation |
|---|---|---|---|---|
| **AARRR** | Funnel diagnostic checklist | Instrumented funnel → stage-by-stage conversion | Finding which stage leaks | **Wrong use:** as a B2B growth model. **Limitation:** linear; assumes product-led acquisition and short cycles |
| **Growth loops** | Modelling compounding growth | Output → input mechanism → loop diagram | Designing durable growth rather than refilling a funnel | **Wrong use:** claiming a loop where there's only a funnel. **Limitation:** most B2B loops are slow and hard to instrument |
| **Funnel analysis** | Locating drop-off | Step conversion by segment → bottleneck | Any multi-step flow | **Wrong use:** aggregate only — mix shifts invert conclusions. **Limitation:** tells you where, never why |
| **Cohort analysis** | Measuring durability | Users grouped by start period → retention curves | Determining whether retention flattens | **Wrong use:** blending cohorts. **Limitation:** needs enough history; slow to read for annual contracts |
| **RFM** (recency/frequency/monetary) | Segmenting by behaviour | Transaction history → segments | Lifecycle targeting | **Wrong use:** in low-frequency B2B. **Limitation:** built for retail |

---

## 5. PRODUCT STRATEGY & GOAL FRAMEWORKS

| Framework | Purpose | Inputs → Outputs | Best use | Wrong use & key limitation |
|---|---|---|---|---|
| **North Star Metric** | Aligning an org on one value measure | Value hypothesis → single metric + input tree | Single-product companies with voluntary usage | **Wrong use:** mandated-use or seasonal products; multi-product portfolios. **Limitation:** any single metric is gameable |
| **OKRs** | Connecting outcomes to work | Objective + 3 measurable KRs → aligned goals | Teams that genuinely own outcomes | **Wrong use:** tied to compensation; written after the plan; on teams that can't influence the result. **Limitation:** becomes a reporting ritual within two cycles |
| **Metric tree** | Making causal assumptions explicit | Outcome → decomposition into controllable inputs | **Better default than a North Star for most B2B teams** | **Wrong use:** treating branches as facts. **Limitation:** every branch is a disputable claim (that's the point) |
| **Strategic bets** | Framing uncertainty honestly | Hypothesis + evidence + signal + falsification → funded bet | Multi-quarter uncertain investments | **Wrong use:** a bet with no failure condition. **Limitation:** requires an org that tolerates public wrongness |
| **Product Strategy Canvas** | One-page strategy summary | Context, diagnosis, choices, bets, trade-offs, outcomes | Communicating strategy upward and across | **Wrong use:** filling boxes without a real diagnosis. **Limitation:** a canvas can make fluff look structured |
| **Now / Next / Later** | Expressing confidence decay | Roadmap items → three horizons | Default roadmap format for agile B2B | **Wrong use:** when contracts genuinely require dates. **Limitation:** needs a commitment-tier overlay in enterprise |
| **Working Backwards / PRFAQ** | Forcing customer-first thinking | Press release + FAQ written before building → go/no-go | Big bets, new products | **Wrong use:** without a ruthless critique culture. **Limitation:** expensive; theatre at small scale |

---

## 6. THE FRAMEWORK SELECTION GUIDE

| Your situation | Reach for | Not |
|---|---|---|
| "We don't know what problem to solve" | Continuous discovery + OST | RICE |
| "We have 40 items and no order" | Capacity allocation, then RICE within buckets | One ranked list |
| "We don't know why customers leave" | Switch interviews + forces | NPS |
| "We can't agree what to build" | Rumelt kernel — you have a strategy problem | Another prioritisation framework |
| "A competitor launched something" | Positioning + Five Forces | Feature parity backlog |
| "Our metric moved and we don't know why" | Funnel + segment + cohort | A new dashboard |
| "We need to enter a new market" | PESTLE + bottom-up sizing + positioning | TAM from an analyst report |
| "Engineering wants a rewrite" | Cost of Delay + capacity allocation | RICE (it will lose) |
| "Should this be AI?" | The AI decision framework (Vol IX §10) | A capability demo |
| "Everything is urgent" | Strategy, then commitment tiers | Better estimation |

**The meta-rule:** *if a framework isn't changing what you'd decide, stop running it.* Framework output that confirms what everyone already thought is a ritual, and rituals consume the credibility you'll need for the decisions that matter.

---

# PART XXXVI — THE ANTI-PATTERN LIBRARY

Each entry: **Problem → Warning signs → Consequences → Better practice.**

---

### A1 — THE FEATURE FACTORY
**Problem.** The team measures output (features shipped) rather than outcomes, and nobody notices because the output is real and visible.
**Warning signs.** Roadmap is a list of features with dates. No one can name what a shipped feature changed. Nothing is ever removed. Success is "we delivered." Post-launch reviews don't exist. The word "outcome" appears only in slide titles.
**Consequences.** Product surface grows without value growing. Maintenance cost compounds. Users face increasing complexity. Team morale erodes because nobody can say whether their work mattered.
**Better practice.** Definition of done includes a 30-day adoption review (Vol XI §18). Every PRD names a metric and a target. A quarterly kill review. Capacity allocation with a health bucket.

---

### A2 — ROADMAP THEATER
**Problem.** The roadmap is a communication artefact designed to make stakeholders feel good, not a statement of intent.
**Warning signs.** Every quarter is equally full and equally specific. Nothing is ever removed, only pushed right. Different stakeholders have different versions. Items appear that no one on the team recognises.
**Consequences.** Nobody trusts the roadmap, so everyone negotiates outside it. Sales makes private promises. Planning becomes performance.
**Better practice.** Now/Next/Later with visible confidence decay. Three-tier commitment model (Vol III §9.1). One published version. When something is added, name what it displaced.

---

### A3 — VANITY METRICS
**Problem.** The team reports numbers that reliably go up and never inform a decision.
**Warning signs.** Cumulative totals. "Total registered users." Metrics with no denominator. No guardrails. Nobody can answer "what would we do differently if this doubled?"
**Consequences.** Real problems stay invisible. Leadership makes decisions on flattering data. When reality arrives it arrives all at once.
**Better practice.** The decision column (Vol XII §8, Exercise 12.3). Paired metrics. Delete anything that supports no decision.

---

### A4 — CARGO CULT AGILE
**Problem.** The ceremonies are performed; the principles they serve are absent.
**Warning signs.** Standups are status reports to the PM. Retros produce actions nobody does. Estimation is a negotiation. Sprint goals are lists of tickets. "That's not agile" used as an argument.
**Consequences.** Meeting overhead without adaptability. Cynicism. The process becomes the thing being protected.
**Better practice.** For each ceremony, name the decision it produces. Delete any that produce none. Volume IV's mechanism test applies: what fails, visibly, if it's skipped?

----

### A5 — SOLUTIONISM
**Problem.** Jumping to a solution before the problem is understood, because proposing solutions is socially rewarded and questioning problems isn't.
**Warning signs.** Requests enter the backlog as features. Discovery means "designing the thing we already decided." "Users asked for it" is a sufficient justification. The word "problem" doesn't appear in your PRDs.
**Consequences.** You build the customer's guess instead of solving their need. Requests multiply because each solution creates adjacent gaps.
**Better practice.** The conversion ladder on every request (Vol II §7.1). A problem statement section that can't be skipped.

----

### A6 — HiPPO DECISION MAKING
**Problem.** The Highest Paid Person's Opinion decides, and evidence is gathered afterward to support it.
**Warning signs.** Priorities change after every exec 1:1. Analysis is commissioned to justify decisions already made. People ask "what does [exec] think?" before "what do the customers do?"
**Consequences.** The organisation stops thinking. Evidence-gathering becomes theatre. Good people leave.
**Better practice.** Decision log with rationale and revisit triggers. Decision rights defined per decision type. Present options with trade-offs rather than a single proposal to approve. Note that a HiPPO decision is not automatically wrong — the anti-pattern is the *absence of a reasoning trail*, not the seniority of the decider.

---

### A7 — STAKEHOLDER-DRIVEN ROADMAP
**Problem.** The roadmap is the union of what each internal stakeholder wants, weighted by how loudly they ask.
**Warning signs.** Roadmap items map one-to-one onto internal departments. The loudest stakeholder gets the most. "Whose request is this?" is a meaningful question. No coherent theme.
**Consequences.** No strategy, only allocation. Nothing compounds. Every quarter starts from zero.
**Better practice.** Strategy with explicit exclusions. Capacity allocation. Every request walked up the conversion ladder. Publish the "we don't build this" list.

---

### A8 — CUSTOMER-REQUEST ROADMAP
**Problem.** Building what customers ask for, literally, in request order.
**Warning signs.** A feature-request voting board *is* the roadmap. Requests are counted rather than analysed. The biggest customers' requests always win.
**Consequences.** Local optimisation for existing customers; blindness to non-customers. Product fragments. You optimise for the market you have, never the one you want.
**Better practice.** Requests are evidence of problems, not instructions. Cluster into problems. Weight by strategy fit, not request count. **Talk to people who didn't buy.**

---

### A9 — METRIC GAMING
**Problem.** A metric became a target, so people optimise the number rather than the thing.
**Warning signs.** The metric improves while qualitative signal worsens. Definitions get quietly revised. Nobody can explain the improvement mechanically. Improvement coincides with a compensation cycle.
**Consequences.** You lose the ability to measure the thing you cared about, and you may not notice for a year.
**Better practice.** Paired metrics always (Vol XII §1.1). Keep metrics away from individual compensation. Ask "mechanically, what changed?" whenever a number improves.

---

### A10 — OVER-ENGINEERING
**Problem.** Building for scale, flexibility, or generality you don't have evidence you'll need.
**Warning signs.** Abstractions with one implementation. Configuration options nobody has requested. "We'll need this later." Architecture discussions longer than the feature would take to build.
**Consequences.** Slower delivery now; more code to maintain; the abstraction is usually wrong because it was designed against imagined requirements.
**Better practice.** Rule of three (Vol VIII §6). Build the specific thing; generalise on the third repetition. Note the counter-risk: **under-engineering the data model and permissions model is worse**, because those are one-way doors.

---

### A11 — AI FOR AI'S SAKE
**Problem.** Adding AI because it's expected, not because it's the right tool.
**Warning signs.** The feature is described by its technology rather than its outcome. No acceptable error rate defined. No eval set. The demo is impressive and the pilot metrics are absent. A deterministic rule would handle most of it.
**Consequences.** Cost with no value capture. Trust damage when it's wrong. Opportunity cost of a quarter.
**Better practice.** The AI decision framework (Vol IX §10), stopping at the first hard no. Benchmark against the deterministic baseline. Define the acceptable error rate from consequence class before building.

---

### A12 — PREMATURE SCALING
**Problem.** Building for a scale, segment, or geography you haven't validated.
**Warning signs.** Enterprise features before enterprise customers. Multi-currency before a second market. Hiring ahead of demand. "When we're big, we'll need…"
**Consequences.** Capital and time consumed on capability nobody uses; the actual bottleneck stays unaddressed.
**Better practice.** Validate the segment with a pilot before building for it. Ask "what breaks first at 3× and 10×?" — often it isn't what people assume.

---

### A13 — ANALYSIS PARALYSIS
**Problem.** Gathering more evidence instead of making a reversible decision.
**Warning signs.** Repeated requests for "one more cut of the data." Decisions pending for weeks with engineers blocked. Every new analysis produces a new objection.
**Consequences.** Decision latency measured in engineer-weeks. Competitors move. The team learns that raising an idea means a month of analysis.
**Better practice.** Classify the door first — two-way doors get shipped and observed. The 70% rule. Evidence thresholds by reversibility (Vol I §3.7). **If each new analysis produces a new objection, it isn't an evidence problem — it's a values or interest conflict (Vol X §8.1).**

---

### A14 — BUILDING WITHOUT DISCOVERY
**Problem.** Going from idea to build with no contact with a user.
**Warning signs.** "We know our users." Discovery means an internal workshop. Nobody on the team has spoken to a customer this quarter. Design starts from a solution brief.
**Consequences.** You build the team's mental model rather than the users' reality. The failure surfaces after launch, at maximum cost.
**Better practice.** A biweekly touchpoint at minimum. Exhaust mining (tickets, sales calls, session replay) when access is gated. Discovery verdict document with a written decision (Vol II §11.3).

---

### A15 — SHIPPING WITHOUT MEASUREMENT
**Problem.** Releasing with no instrumentation, no baseline, and no review date.
**Warning signs.** Analytics added after launch, if at all. No baseline recorded. Nobody knows the adoption rate of last quarter's features. "We'll look at it later."
**Consequences.** You can never learn. Every feature is a permanent maintenance obligation with unknown value. You cannot make a case for removal.
**Better practice.** Instrumentation is a PRD section with verification before GA (Vol VI §5). Prediction written before launch. Calendar entry at 30 days.

---

### A16 — CONFUSING ACTIVITY WITH OUTCOMES
**Problem.** Busyness is treated as progress.
**Warning signs.** Status updates list activities, not results. Velocity is the headline. "We're heads-down." Success measured by whether the plan was executed rather than whether it worked.
**Consequences.** A team can execute perfectly against a wrong plan for a year, and everyone involved will have positive performance reviews.
**Better practice.** Every plan states the outcome and the leading indicator. Monthly outcome review distinct from delivery review. The prediction review (Vol X §3).

---

### A17 — CONFUSING CONSENSUS WITH ALIGNMENT
**Problem.** Everyone stopped arguing, which is mistaken for agreement.
**Warning signs.** Decisions that "everyone agreed to" get quietly relitigated. Silence in meetings read as assent. Work progresses slowly for reasons nobody names. People raise objections privately afterwards.
**Consequences.** Passive resistance, which costs far more than an explicit disagreement. Decisions have to be made repeatedly.
**Better practice.** Ask directly: *"Who disagrees, and what would change your mind?"* Establish disagree-and-commit explicitly. Write down what was decided and who committed. **Treat silence as unknown, never as yes.**

---

### A18 — THE PERPETUAL PILOT
**Problem.** A pilot that never concludes, because concluding would require a decision.
**Warning signs.** The pilot has been "wrapping up" for two quarters. No success criteria were defined at the start. Scope grows to accommodate the next objection.
**Consequences.** Resources consumed indefinitely; the option value of deciding is never realised.
**Better practice.** Every pilot has a written end date, success criteria, and a pre-committed decision rule — including what "no" looks like.

---

### A19 — THE INVISIBLE PLATFORM TEAM
**Problem.** Platform work succeeds, becomes invisible, and gets defunded.
**Warning signs.** "What does that team actually do?" Platform roadmap has no business narrative. Leverage isn't measured. Consuming teams take the platform for granted.
**Consequences.** Investment stops, debt accumulates, and the cost reappears eighteen months later distributed across every team.
**Better practice.** Publish the counterfactual quarterly in engineer-weeks avoided (Vol VIII §10). Name the consuming teams as customers with satisfaction measured.

---

### A20 — HERO CULTURE
**Problem.** Outcomes depend on specific individuals working heroically.
**Warning signs.** One engineer understands the calculation engine. Launches require someone's weekend. The team celebrates rescues rather than the absence of crises. Nobody takes uninterrupted leave.
**Consequences.** Key-person risk. Burnout. Systemic problems stay hidden because heroics keep absorbing them.
**Better practice.** Treat every heroic rescue as an incident with a root cause. Rotate ownership deliberately. **The Level 10 test: what happens when you're away for three weeks?**

---

## 7. VOLUME XIII EXERCISES

**Exercise 13.1 — Framework inventory.** List every framework your team uses. For each, write the decision it changed most recently. Delete any that haven't changed one in six months.

**Exercise 13.2 — Anti-pattern self-audit.** Score your team 0–3 on each of A1–A20 (0 = absent, 3 = severe). Be honest — the value is entirely in the honesty. *Deliverable: your top three, with one countermeasure each. Most teams have three or four at a 2+.*

**Exercise 13.3 — The silence test.** In your next decision meeting, ask explicitly: "Who disagrees, and what would change your mind?" *Deliverable: an honest read on whether you have alignment or just consensus.*

**Exercise 13.4 — Kill review.** Identify three features with low adoption. For each: keep, improve, or remove — with a written rationale. *Deliverable: possibly your first deliberate removal, which is the hardest and most valuable habit to start.*

---

## 8. VOLUME XIII INTERVIEW BANK

1. What's your favourite prioritization framework, and when does it fail?
2. What's the difference between a framework and a methodology?
3. How would you tell whether a team is a feature factory?
4. Your team has consensus on a decision. How do you know it's real alignment?
5. When would you *not* use OKRs?
6. Describe a time you used a framework and it gave you the wrong answer.
7. What's the most common anti-pattern you've seen, and how did you address it?
8. A stakeholder says "the framework says we should do X." How do you respond?

---

*Volume XIII complete. Continue to `14-case-studies.md`.*
