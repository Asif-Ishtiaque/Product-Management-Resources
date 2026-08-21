# VOLUME I — PRODUCT THINKING & THE ADVANCED MINDSET
### Parts II & III

> The gap between a mid-level PM and a senior PM is almost never knowledge. It is **what they do in the first ten minutes of an ambiguous problem.**

---

## 1. THE ROLE ARCHETYPES

The titles below are not seniority levels stacked on each other. They are **different jobs** that happen to share a name. Confusing them is the most common reason a strong PM interviews badly for a role they would be excellent at.

### 1.1 The differentiation matrix

| | **Feature PM** | **Product PM** | **Senior PM** | **Technical PM (TPM)** | **Platform PM** | **AI PM** | **Product Lead** | **Group PM** |
|---|---|---|---|---|---|---|---|---|
| **Unit of ownership** | A feature | A product surface | A problem space | A system / program | A capability used by others | A capability with non-deterministic behaviour | A team's outcomes | A portfolio of teams |
| **Primary question** | "Is it built right?" | "Are we building the right thing?" | "Is this the right problem to work on at all?" | "Will this hold under load, change, and failure?" | "Who else needs this, and what happens when they do?" | "Is the model good enough for the consequence of being wrong?" | "Is the team solving the right problems well?" | "Is the portfolio allocated correctly?" |
| **Primary artefact** | Stories, acceptance criteria | PRD, roadmap | Strategy doc, opportunity map | System design doc, dependency map, rollout plan | API contract, deprecation policy, DX docs | Eval suite, model spec, failure taxonomy | Team strategy, hiring plan | Portfolio strategy, resource allocation |
| **Primary stakeholder** | Engineering | Design + Engineering + Sales | Exec + cross-functional | Engineering leadership | Other product teams (internal customers) | Research/ML + Legal + Ops | Direct reports | Exec staff |
| **Definition of done** | Shipped and accepted | Adopted and retained | Outcome moved | Reliable at scale, migrations complete | Adopted by N teams without your help | Meets eval bar in production distribution | Team hits outcomes without you | Portfolio hits business outcomes |
| **Signature failure mode** | Ships things nobody asked for well | Ships the right thing too late | Overthinks; produces strategy nobody executes | Becomes the engineering manager's shadow | Builds a platform with zero adopters | Ships a demo that dies on real data | Manages activity instead of judgment | Becomes a status aggregator |
| **What gets you promoted out of it** | Owning the *why*, not the *what* | Choosing what NOT to do | Making others better at judgment | Making architecture a business argument | Getting adoption without mandate | Making eval a business metric | Multiplying through people | Reallocating capital, not just people |

### 1.2 The three titles you are actually targeting — precise distinctions

You listed TPM, Platform PM, and AI PM as targets. They are frequently confused, including by the companies hiring for them.

**Technical Product Manager vs Technical Program Manager.** These share the acronym and share almost nothing else. Note carefully, because you will apply to both:

| | Technical **Product** Manager | Technical **Program** Manager |
|---|---|---|
| Owns | A technical product's success | A cross-team program's delivery |
| Optimises | Right thing built | Thing delivered across dependencies |
| Metric | Adoption, retention, business outcome | Schedule, risk burn-down, dependency resolution |
| Says | "We should not build this" | "This will slip unless team B commits by the 14th" |
| Career adjacency | → Principal PM, Director of Product | → Senior TPM, Director of Engineering Programs |

Your background straddles both: PRD/backlog ownership is Product; multi-system integration and UAT programs across CRM/HRMS/tax is Program. **Decide which you want before your next application cycle, because the interview loops diverge hard.** Program loops test dependency mapping, risk, and escalation. Product loops test judgment, strategy, and metrics.

**Platform PM.** The distinguishing feature is *your customer is another engineering team.* This inverts almost every instinct: you cannot sell, you can only make adoption cheaper than the alternative. Your users can and will build their own version out of spite if your DX is bad. Volume VIII covers this in full.

**AI PM.** The distinguishing feature is *non-determinism.* Traditional PM assumes the same input yields the same output; the spec defines correctness. In AI, correctness is a **distribution**, and your central artefact is an evaluation suite, not a requirements doc. This is why your UAT-automation experience is more relevant than most people's — you already think in test corpora, expected-vs-actual, and acceptable failure classes.

---

## 2. THE OWNERSHIP LADDER

```
Feature Ownership
    → Product Ownership
        → Product Area Ownership
            → Business Outcome Ownership
                → Portfolio / Strategy Ownership
```

Each rung is a change in **what you are allowed to be wrong about.**

| Rung | You are trusted to decide | You are still told | The escape velocity move |
|---|---|---|---|
| **Feature** | How it works | What to build, why it matters | Start writing the "why" before someone hands it to you |
| **Product** | What to build | Which outcomes matter | Propose the outcome, not just the feature list |
| **Product Area** | Which problems to pursue | Which business results matter | Tie your area to a P&L line and defend it |
| **Business Outcome** | Which results to chase and the trade-offs | Where the company plays | Argue for and against your own area's funding honestly |
| **Portfolio** | Where to allocate capacity and capital | Nothing — you're setting it | — |

### 2.1 The diagnostic that tells you your real rung

Ignore your title. Answer this: **When you say "no" to a stakeholder, what happens?**

- They escalate and you get overruled → you are at Feature.
- They escalate, you're asked to justify, and your reasoning holds → Product.
- They come to you *before* asking, to check whether it fits → Product Area.
- They ask you what they should want → Business Outcome.
- You decide whose "no" gets funded next year → Portfolio.

**This is the honest test to run on yourself this week.** If you are a PM II whose "no" survives escalation on scope but not on strategy, you are between Feature and Product, and the next rung is bought with strategy artefacts — which is exactly why Volume III is your first priority.

### 2.2 The trap: title inflation without ownership expansion

Common in fast-growing SaaS companies, including in the Dhaka ecosystem and in US startups alike. You get "Senior PM" and still own a feature list. Two years later you interview at a company that measures the rung, not the title, and you are down-levelled.

**Countermeasure:** keep a running **Decision Log** (Volume X covers the mechanism). Every quarter, write down the five biggest decisions you personally owned, what you were wrong about, and what it cost. If the list is all "which of these three designs" and never "whether to do this at all," your rung is not moving regardless of your title.

---

## 3. THE EIGHT THINKING MODES

These are the actual cognitive skills. Each is taught to the full protocol.

---

### 3.1 FIRST-PRINCIPLES THINKING

**Plain.** Strip a problem down to things you know are true, then rebuild upward, instead of reasoning by analogy to what already exists.

**Deep.** Most product reasoning is analogical: *"Salesforce does it this way, so we should."* Analogy is fast and usually right, which is why it dominates — and why it fails catastrophically in exactly the situations that matter most, when the underlying constraints have changed. First-principles thinking is expensive; it is a tool for **high-consequence, irreversible decisions**, not for choosing a button label.

The mechanics:
1. List the constraints you believe are real.
2. For each, ask: *is this a law of physics, a law of economics, a regulation, a contract, or a habit?* Only the first four are real. Habits masquerade as constraints constantly.
3. Rebuild the solution using only real constraints.

**Real example (tax/compliance SaaS).** A team is asked to speed up a tax-return preparation workflow. The analogical answer: "add bulk actions and keyboard shortcuts, like every other productivity tool." The first-principles pass asks *what is actually irreducible here?*

- Irreducible: the statutory data a filing requires (regulation).
- Irreducible: the preparer's legal responsibility for accuracy (regulation).
- **Not** irreducible: that the preparer types the data. That's a habit inherited from paper forms.
- **Not** irreducible: that the workflow is linear form-by-form. That's a UI convention.

The rebuilt solution is not shortcuts — it is *ingest the source documents and have the preparer review exceptions.* Same goal, order-of-magnitude different product. That reframe is worth an entire roadmap, and analogical thinking would never have produced it.

**When to use.** Irreversible decisions. New market entry. When you're losing to a competitor on a dimension you assumed was fixed. When every option on the table feels like a 10% improvement.

**When NOT to use.** Under time pressure on reversible decisions — it burns days to re-derive what convention already got right. Also avoid it in **regulated correctness domains** where the convention encodes hard-won legal safety. Re-deriving how tax withholding should work from first principles is not insight; it's liability. First-principles thinking applies to *the workflow around the rule*, not to the rule.

**Alternatives.** Analogical reasoning (fast, safe, incremental); constraint relaxation (pick one assumed constraint and ask "what if this were free?" — 80% of the value at 20% of the cost); pre-mortems.

**Trade-off.** Time and social capital. First-principles conclusions sound arrogant to people who built the current system. You will need Volume X's influence mechanics to land them.

**Exercise.** Take the most annoying manual step in a product you own. Write the five constraints that make it exist. Label each: physics / economics / regulation / contract / habit. Kill one habit. Design what remains.

**Interview question.** *"Tell me about a time you challenged an assumption everyone else accepted. How did you know it was safe to challenge?"* — The panel is testing whether you can distinguish a real constraint from an inherited one, and whether you have the judgment to know when NOT to.

**Reference.** The canonical modern articulation is in Elon Musk interviews (E2) and in Rumelt's *Good Strategy/Bad Strategy* diagnosis chapter (E1, published book). Amazon's Leadership Principles include "Are Right, A Lot" and "Invent and Simplify," which encode a similar disposition — publicly documented on Amazon's jobs site (E1).

---

### 3.2 SYSTEMS THINKING

**Plain.** See the whole loop, not the single step. Understand that fixing one part usually moves the problem somewhere else.

**Deep.** Product systems have **stocks** (things that accumulate: users, tickets, technical debt, trust), **flows** (things that change stocks: signups, churn, commits), **feedback loops** (reinforcing or balancing), and **delays** (the reason most interventions look like failures before they look like successes).

The three things senior PMs see that mid-level PMs miss:

1. **Delays disguise causation.** You ship an onboarding change; retention doesn't move for 90 days because the cohort hasn't matured. Teams kill working changes at day 30 constantly.
2. **Balancing loops eat improvements.** You cut support ticket handling time by 30%; volume rises because agents now accept tickets they used to deflect. Net zero. This is why "efficiency" projects so often deliver nothing to the P&L.
3. **The bottleneck moves.** Optimising a non-bottleneck produces exactly zero throughput improvement (Goldratt's Theory of Constraints, E1 — *The Goal*). Most roadmaps are full of non-bottleneck optimisations because those are the ones that are easy to ship.

**Real example (workflow automation).** A team automates approval routing in an HRMS to cut approval time. Approval time drops from 3 days to 4 hours. Total request-to-completion time doesn't move — because the actual bottleneck was the *upstream* step where employees didn't know which form to submit, so 40% of requests bounced back. The automation optimised a non-bottleneck beautifully.

The systems-thinking version of this project starts by measuring **time-in-each-state across the whole workflow** before choosing where to intervene. That is a two-day analysis that would have redirected a two-quarter roadmap.

**When to use.** Any time a metric is not responding to changes you're confident should have moved it. Any time you're automating one step of a multi-step process. Platform work, always — platforms are pure systems problems.

**When NOT to use.** As an excuse for inaction. "It's a complex system" is the most sophisticated-sounding way to avoid shipping. If the intervention is cheap and reversible, ship it and observe; the system will tell you more than the model will.

**Alternatives.** Value stream mapping (concrete, faster, less general); Theory of Constraints (narrower, sharper); service blueprints (Volume II) for customer-facing systems.

**Trade-off.** Systems models are always wrong and sometimes useful. Over-modelling produces beautiful diagrams that no one uses.

**Exercise.** Map one workflow in your product as states with time-in-state. Find the state with the longest average dwell time *and* the highest variance. That is almost always the real bottleneck, and it is almost never the one people complain about.

**Interview question.** *"You shipped a feature that improved its target metric by 20%, but the business metric didn't move. Walk me through your diagnosis."*

**Reference.** Donella Meadows, *Thinking in Systems* (E1); Goldratt, *The Goal* (E1); Google's SRE book chapters on feedback and error budgets are a working example of a balancing loop designed on purpose (E1, published by Google).

---

### 3.3 STRATEGIC THINKING

**Plain.** Deciding what to do *by deciding what not to do*, based on a specific view of why you can win.

**Deep.** Covered fully in Volume III. The mindset component here is the discipline of **holding a position under social pressure.** Most strategy dies not from bad analysis but from a strategy that survives the doc and dies in the third stakeholder meeting because the PM couldn't defend a "no."

The tell of strategic thinking in conversation: the person can state **what they are deliberately giving up and why they're comfortable with it.** Someone who says "we'll do both" has no strategy; they have a wish list with a deadline.

**When NOT to use.** Genuinely: when you have no leverage and no information. A brand-new PM on a brand-new team should execute visibly for a quarter before proposing strategy. Strategy without credibility reads as arrogance and gets ignored, which burns the idea permanently.

**Interview question.** *"What's the most important thing your product team decided NOT to do last year, and what did that cost you?"* — If the candidate can't answer, they were not doing strategy.

---

### 3.4 CUSTOMER OBSESSION

**Plain.** Starting from the customer's reality rather than your product's.

**Deep.** The word is degraded by overuse, so define it operationally: **customer obsession is a mechanism, not a feeling.** Feelings don't survive quarterly pressure; mechanisms do.

Amazon publicly documents customer obsession as the first of its Leadership Principles, and publicly documents Working Backwards / PRFAQ as the mechanism that enforces it — you write the press release and FAQ *before* you build, from the customer's point of view (E1: Amazon jobs site for the Leadership Principles; E1/E2: *Working Backwards* by Colin Bryar and Bill Carr, both former Amazon executives, for the mechanism's details). The important lesson is not the artefact. It is that **they built a forcing function** so that customer-first thinking couldn't be skipped when the quarter got tight.

The B2B complication that generic PM books ignore: **in B2B, the customer is not one person.** You have at minimum:

| Role | Cares about | Can kill your deal | Will use the product |
|---|---|---|---|
| **Economic buyer** (CFO/owner) | Cost, risk, ROI | Yes | Rarely |
| **Champion** (dept head) | Their team's outcome, their own credibility | No, but drives it | Sometimes |
| **End user** (preparer, HR admin, sales rep) | Their daily friction | No | Yes, daily |
| **Technical gatekeeper** (IT/Security) | Integration, SSO, data residency, audit | **Yes, absolutely** | No |
| **Compliance/Legal** | Regulatory exposure | **Yes, absolutely** | No |

"Customer obsession" that only listens to end users produces a beloved product that doesn't sell. Obsession that only listens to buyers produces a product that gets bought and abandoned — which shows up as churn 14 months later when someone notices seat utilisation is 12%.

**Real example (tax/compliance).** End users want faster data entry. The economic buyer wants provable accuracy for audit defence. The compliance gatekeeper wants a full change-audit trail on every calculation. A "customer-obsessed" roadmap that ships only speed features loses the renewal to a slower competitor with better audit logging. In compliance software, **the buyer's job is avoiding catastrophe, not saving minutes.**

**When NOT to use.** When customers are asking for the thing that will destroy them. Customer obsession ≠ customer subservience. Enterprise customers routinely request configuration knobs that fragment your product into a thousand unmaintainable variants. The obsessive answer is understanding *why* they want the knob and solving that — which is often a permissions model or a template, not a knob. See Volume XI.

**Exercise.** For your product, write the five stakeholder roles above with the *actual named people* at your largest account. For each, write the one sentence they'd say to justify renewal. If you can't write one for the gatekeeper or compliance, you have a renewal risk you can't see.

**Interview question.** *"Tell me about a time you refused a customer request."* — Testing whether you distinguish need from request.

**Reference.** Amazon Leadership Principles, amazon.jobs (E1). Bryar & Carr, *Working Backwards*, 2021 (E2 — insider account, not official Amazon doctrine). Verify current wording; Amazon has amended the Leadership Principles set over time.

---

### 3.5 BUSINESS THINKING

**Plain.** Knowing how your product makes and loses money, precisely enough to argue about it with Finance.

**Deep.** Full treatment in Volume V. The mindset component: **every product decision is a capital allocation decision.** A quarter of engineering time is not "a quarter" — at a typical loaded cost it's a number with a currency sign, and it is being spent instead of something else.

The single highest-leverage habit here: **learn to state every proposal as a business case in one sentence with a number in it.** Not "this will improve the preparer experience," but "this removes ~6 minutes from a 40-minute workflow across ~1,200 preparers in peak season, which is X hours of billable capacity, against an estimated 8 engineer-weeks."

Even when the number is a rough estimate — say so, give the range, show the assumption. **A PM who shows a wrong-but-explicit model gets corrected and gains credibility. A PM who shows no model gets ignored.**

**When NOT to use.** Don't force revenue attribution onto everything. Some work is table-stakes reliability, regulatory obligation, or debt paydown; forcing a fake ROI number onto compliance work teaches your organisation that your numbers are decoration. Say plainly: "this is non-negotiable regulatory work, the question is only how cheaply we do it."

**Interview question.** *"How does your product make money, and what's the single biggest lever on gross margin?"* — A shocking number of PM candidates cannot answer this about their own product. Be able to.

---

### 3.6 TECHNICAL CURIOSITY

**Plain.** Understanding enough of how it works to know what's expensive, what's risky, and what's actually a lie.

**Deep.** Volume VIII goes deep. The mindset distinction:

**What a PM must know:** the shape of the system, where the coupling is, what the failure modes are, what makes a change 3 days vs 3 months, what the data model can and cannot express, what the integration contracts commit you to.

**What an engineer must know:** everything else.

The test isn't whether you can write the code. It's whether, when an engineer says *"that's a big change,"* you can ask the second question. Not "how long?" but *"is it big because of the data model, the coupling, the migration, or the testing surface?"* — because those four have completely different mitigations, and asking the right one is what earns technical credibility.

**When NOT to use.** When it becomes design-by-PM. Technical curiosity that ends in you specifying the implementation is not curiosity, it's territory. The line: **you own the constraints and the trade-off framing; engineering owns the design.**

**Exercise.** Draw your product's system diagram from memory. Show it to your tech lead. The gap between your drawing and reality is your technical debt as a PM. Redraw quarterly.

---

### 3.7 DECISION QUALITY

**Plain.** Judging decisions by the process and information at the time, not by how they turned out.

**Deep.** The core concept is **resulting** (Annie Duke's term, E1 — *Thinking in Bets*): evaluating a decision by its outcome. It is the single most corrosive habit in product organisations, because it punishes good bets that lost and rewards bad bets that won, and teams learn to optimise for defensibility rather than expected value.

A high-quality decision has:
1. A **clear frame** — what are we actually deciding, and what are we not?
2. **Real alternatives** — at least three, including "do nothing." One option is not a decision, it's a proposal.
3. **Relevant information** at proportionate cost — see the evidence-threshold table below.
4. **Clear values/trade-offs** — what we're optimising and what we'll sacrifice.
5. **Sound reasoning** — explicit, written, falsifiable.
6. **Commitment** — someone actually decides and the org moves.

**Evidence thresholds by reversibility** — this is the practical heart of decision quality:

| Decision type | Cost to reverse | Evidence bar | Who decides | Speed target |
|---|---|---|---|---|
| UI copy, config default | Hours | Judgment. Just ship. | PM alone | Same day |
| Feature within existing surface | Days–weeks | One evidence type (qual OR quant) | PM + tech lead | Same week |
| New product surface | 1–2 quarters | Two independent evidence types | PM + eng lead + design lead | Weeks |
| Data model / API contract change | Quarters–years | Triangulated evidence + migration plan | PM + architect + affected teams | Weeks, deliberately |
| Pricing/packaging change | Years (contracts, trust) | Quant + customer + finance modelling | Exec | Deliberately slow |
| Regulatory/compliance posture | Existential | Legal sign-off, no exceptions | Legal + exec | As slow as needed |

Amazon publicly documents this as **one-way vs two-way doors** — Jeff Bezos's 2015 shareholder letter describes Type 1 (irreversible, decide slowly and deliberately) and Type 2 (reversible, decide fast, push down) decisions (E1 — published shareholder letter). The dysfunction it names is real and universal: **organisations apply Type 1 process to Type 2 decisions as they grow, and become slow for no benefit.**

**Real example (your domain).** Adding a new field to a tax form view is a two-way door — ship it. Changing how the calculation engine versions its rules is a one-way door with a decade-long tail, because every historical return must remain reproducible for audit. **A PM who applies the same process to both is failing in one direction or the other.**

**When NOT to use.** Don't run full decision-quality process on two-way doors. The process itself has a cost, and a team that deliberates over reversible choices is a team that ships nothing.

**Exercise.** List your last ten decisions. Label each one-way or two-way. Then honestly mark which ones got more process than they deserved. Most PMs find they over-process reversible decisions and under-process data model changes.

**Interview question.** *"Describe a decision you made that turned out badly but that you'd make again with the same information."* — This is a direct test for resulting. A candidate who can't separate decision from outcome will not be trusted with ambiguity.

**Reference.** Bezos 2015 Letter to Shareholders (E1). Annie Duke, *Thinking in Bets* (E1). Note: Amazon's letters are archived on their IR site — verify current availability.

---

### 3.8 PRODUCT JUDGMENT

**Plain.** Consistently making good calls with incomplete information.

**Deep.** Judgment is the only PM skill that cannot be transferred by reading. It is **compressed, calibrated experience**, and it is built by a specific loop that most PMs never run:

```
PREDICT → COMMIT IN WRITING → SHIP → MEASURE → COMPARE → EXPLAIN THE GAP
```

The step everyone skips is **commit in writing, before the outcome.** Without it, hindsight rewrites your memory of what you expected, you never experience being wrong, and you accumulate years of experience without accumulating any calibration. This is why a 10-year PM can have 1 year of experience repeated 10 times.

**The mechanism: a prediction journal.** Before every meaningful launch, write:

```
FEATURE: Bulk client import for tax preparers
PREDICTION (written 2026-03-04, before launch):
  - 35% of firms with 50+ clients will use it within 30 days
  - Median import size: 80 clients
  - Support tickets will INCREASE by ~15 in month 1 (mapping errors)
  - Time-to-first-return for new firms drops from 6 days to under 2
CONFIDENCE: 60% on adoption, 80% on the ticket increase
WHAT WOULD MAKE ME WRONG: if firms don't have clean source data, adoption
  will be under 10% and the bottleneck is data quality, not import UX.
```

Thirty days later you compare. The value is almost entirely in the **explain-the-gap** step — that's where the model of your customers actually updates.

Six months of this produces more judgment than six years without it. It is also **the single best portfolio artefact you can build for a Senior PM interview**, because it is direct evidence of calibrated thinking, which is the thing they are actually screening for and almost no candidate can demonstrate.

**When NOT to use.** Don't predict trivia. Predict things where being wrong would change your strategy.

**Exercise.** Write predictions for your next three releases, right now, before you read further. Set a calendar reminder for 30 days after each.

**Interview question.** *"What's something you believed about your users a year ago that you now know is wrong? How did you find out?"* — This is the highest-signal PM question in existence. It tests calibration, humility, and whether the candidate actually looks at data.

---

## 4. HOW SENIOR PMs THINK DIFFERENTLY

The table most people want. Note that the left column is not *wrong* — it's **complete but narrow**. Seniority is scope of concern, plus willingness to hold uncertainty.

| Situation | Mid-level PM | Senior PM |
|---|---|---|
| Stakeholder requests a feature | Adds to backlog, prioritises it | Asks what changed to make this urgent now; finds the problem behind it |
| Given a goal | Plans how to hit it | Asks whether it's the right goal and what it trades against |
| Metric drops | Investigates the metric | Checks instrumentation first, then segments, then asks what *else* moved |
| Engineering says "6 months" | Negotiates scope | Asks what makes it 6 months; often finds a 3-week version of 80% of the value |
| Two customers want opposite things | Escalates for a decision | Determines which segment the strategy serves, decides, and documents why |
| Presenting to execs | Presents what was built | Presents the decision needed, with a recommendation |
| Roadmap challenged | Defends the roadmap | Shows the trade-off space; invites the exec to choose what to drop |
| A bet fails | Explains what went wrong | Explains what was learned and what it changes about the strategy |
| Doesn't know something | Hides it or guesses | Says "I don't know, here's how I'd find out, here's what I'd do meanwhile" |
| Ambiguous problem | Asks for clarity | Proposes a frame and asks for correction |

**That last row is the single most transferable behaviour in this book.** Junior PMs consume clarity. Senior PMs manufacture it. When handed a mess, the senior move is to write a one-page frame — *here's what I think we're deciding, here are the options, here's what I'd need to know* — and circulate it. It will be partly wrong. That's the point: **a wrong frame gets corrected in a day; a request for clarity gets ignored for a week.**

---

## 5. THE JUDGMENT CALIBRATION AUDIT (do this once)

A self-assessment that produces an actual development plan. Score yourself 1–5 on evidence, not aspiration.

| # | Statement | Evidence that you're a 4–5 |
|---|---|---|
| 1 | I can state my product's strategy in 3 sentences without notes | Colleagues state it the same way |
| 2 | I know what my product deliberately doesn't do, and why | You've declined a named deal/request on strategy grounds |
| 3 | I know my product's gross margin drivers | You've discussed them with Finance |
| 4 | I can draw the system architecture accurately | Your tech lead agrees with the drawing |
| 5 | I have written predictions I later checked | The journal exists |
| 6 | I have killed something I built | You can name it and the cost |
| 7 | I know which of my decisions were one-way doors | You treated them differently at the time |
| 8 | I've changed an exec's mind with evidence | You can name the meeting |
| 9 | My team makes good decisions when I'm away | Provable during leave |
| 10 | I can name my top 3 assumptions and how I'd test them | They're written down |

Scoring: **≤25** → you are operating at Feature/Product rung; focus Volumes II–III. **26–38** → Product/Area rung; focus Volumes V, VI, VIII. **≥39** → Business Outcome rung; focus Volume X and start the portfolio work in Volume XVI.

---

## 6. VOLUME I EXERCISES (portfolio-grade)

**Exercise 1.1 — The Constraint Audit.** Pick your most-complained-about workflow. List every constraint. Classify each: physics / economics / regulation / contract / habit. Produce a one-page memo proposing the removal of one habit-constraint. *Deliverable: 1-page memo. Interview use: "tell me about challenging an assumption."*

**Exercise 1.2 — The Rung Test.** Write your last 10 significant decisions. For each: what were you deciding, one-way or two-way, who could overrule you, were you overruled. *Deliverable: your honest current rung + the specific evidence you need to move up.*

**Exercise 1.3 — Start the Prediction Journal.** Three predictions, written before outcomes, with confidence levels and falsification conditions. *Deliverable: the journal itself — this becomes a genuine differentiator in senior interviews.*

**Exercise 1.4 — The B2B Stakeholder Map.** For your largest account, name the five roles from §3.4 and write each one's renewal justification in one sentence. *Deliverable: renewal risk you couldn't previously see.*

**Exercise 1.5 — The Architecture Redraw.** Draw your system from memory. Review with your tech lead. Note every gap. *Deliverable: your technical-credibility baseline. Repeat in 90 days.*

---

## 7. VOLUME I INTERVIEW BANK

1. What's the difference between a Product Manager and a Product Owner at your company — and is that difference correct?
2. Tell me about a decision you made that turned out badly but that you'd make again.
3. What does your product deliberately not do?
4. Tell me about a time you challenged a constraint everyone treated as fixed.
5. What did you believe about your users a year ago that's now wrong?
6. How does your product make money? What's the biggest lever on margin?
7. Describe a one-way door decision you made. How did your process differ?
8. An engineer says a change will take six months. What are your next three questions?
9. Your CEO wants a feature that contradicts your strategy. Walk me through the next two weeks.
10. What's the biggest thing you were wrong about last year, and what changed in how you work as a result?

---

*Volume I complete. Continue to `02-customer-problem-discovery.md`.*
