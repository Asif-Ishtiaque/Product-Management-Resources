# VOLUME III — PRODUCT STRATEGY, MARKET & ROADMAPS
### Parts VII, VIII & IX

> Strategy is not a plan for how to win. It is a **diagnosis of why you can win**, and a set of choices that follow from it. Everything else is a to-do list with ambition.

**This is your highest-priority volume.** Strategy fluency is the specific thing that separates a PM II from a Senior PM in hiring loops, and it is the thing tax/compliance PMs are most often assumed not to have.

---

# PART VII — PRODUCT STRATEGY

## 1. THE DEFINITIONAL LADDER

These five words are used interchangeably in most companies. That interchangeability is itself the primary cause of strategic drift, because a team that cannot distinguish a vision from a roadmap cannot tell when the roadmap has stopped serving the vision.

| Term | Answers | Time horizon | Changes | Failure mode when confused |
|---|---|---|---|---|
| **Mission** | Why we exist | Indefinite | Almost never | Becomes a poster; used to justify anything |
| **Vision** | What the world looks like if we succeed | 3–10 yrs | Rarely | Vague enough to be unfalsifiable |
| **Strategy** | How we will win, and what we give up | 1–3 yrs | On real change only | Confused with goals → becomes a number, not a choice |
| **Goals / OKRs** | What we'll achieve this period | Quarter–year | Every cycle | Confused with strategy → org chases metrics with no coherent theory |
| **Roadmap** | What we'll work on, in what order | 1–4 quarters | Continuously | Confused with commitment → becomes a contract you can't honour |

**The single most common organisational failure:** having goals and a roadmap but no strategy. It looks functional — there are numbers, there are dates, teams are busy — but there is no theory of why these actions produce a win, so every reprioritisation is a political argument rather than a strategic one. **If your team argues about priorities constantly, you don't have a prioritisation problem; you have a missing strategy.**

---

## 2. THE STRATEGY KERNEL

Richard Rumelt's *Good Strategy / Bad Strategy* (E1, published book) provides the most rigorous available definition. A strategy has exactly three parts:

1. **Diagnosis** — what is actually going on. The hard part. A good diagnosis simplifies an overwhelming reality into a *specific* named challenge.
2. **Guiding policy** — the overall approach chosen to deal with the diagnosis. It *rules things out*.
3. **Coherent actions** — a set of actions that reinforce each other and follow from the policy.

Rumelt's list of **bad strategy signatures** is the most useful diagnostic tool in this book:
- **Fluff** — abstraction masquerading as insight ("we will be a customer-centric, innovation-driven platform").
- **Failure to face the challenge** — no diagnosis at all.
- **Mistaking goals for strategy** — "grow ARR 40%" is a goal. It contains no theory.
- **Bad strategic objectives** — a long list of disconnected "priorities." (If there are seven priorities, there are none.)

### 2.1 Your requested structure, made rigorous

You asked for: **Context → Diagnosis → Choices → Bets → Trade-offs → Outcomes.** That is a superset of the kernel and it works well. Here is each field with the discipline that makes it real:

```
═══════════════════════════════════════════════════════
PRODUCT STRATEGY — [Product] — [Period] — [Owner]
═══════════════════════════════════════════════════════

1. CONTEXT  (facts only, no interpretation)
   Market:      size, growth, structural changes, regulatory shifts
   Customers:   segments, their trajectory, what's changing for them
   Us:          revenue mix, retention by segment, capability, capacity, constraints
   Competition: who's winning what, and where the money is moving
   ⚑ Discipline: anything here must be checkable by someone who disagrees with you.

2. DIAGNOSIS  (one paragraph, the hardest paragraph you will write)
   What is the central challenge? Not a list — the ONE thing that, if unaddressed,
   makes everything else irrelevant.
   ⚑ Test: could a competent competitor read this and disagree? If not, it's fluff.
   ⚑ Test: does it name something uncomfortable? Good diagnoses usually do.

3. CHOICES  (the guiding policy — what we will and will NOT do)
   We will:          [2–3 things]
   We will NOT:      [3–5 things, each one that someone credible currently wants]
   ⚑ Discipline: if the "will not" list contains nothing anyone wanted, you haven't
     made a choice, you've written a summary.

4. BETS  (each with a falsifiable hypothesis)
   Bet 1: We believe [X] because [evidence].
          If true, [outcome]. We'll know by [date] via [signal].
          If false, we will [specific action].
   ⚑ Discipline: a bet with no failure condition is a wish.

5. TRADE-OFFS  (what this costs us)
   By choosing this we accept:  [degraded thing 1], [delayed thing 2], [risk 3]
   Who will be unhappy:         [named function/segment], and our answer to them is:
   ⚑ Discipline: name the people, not the abstraction. "Sales will be unhappy about
     enterprise config requests" beats "there may be some GTM friction."

6. OUTCOMES  (how we'll know)
   Leading indicators (weeks):   
   Lagging indicators (quarters):
   Guardrails we won't breach:   
   Review cadence + who can change this strategy:
═══════════════════════════════════════════════════════
```

### 2.2 A worked example — regulated B2B SaaS

Written the way a Senior PM would actually write it. Fictional but structurally realistic for a mid-market tax & compliance platform.

> **CONTEXT.** 1,200 accounts, 78% mid-market firms (20–200 returns/season), 22% enterprise. NRR 104% overall but 91% in mid-market and 128% in enterprise. Two regulators in our primary market have published multi-year e-filing modernisation programmes, meaning our integration surface will change annually for at least three years. Two well-funded competitors have entered the mid-market with lower-price, narrower products. Our engineering capacity is ~40% consumed by annual regulation updates.
>
> **DIAGNOSIS.** *Our economics are inverted relative to our positioning.* We market and sell to mid-market, where we are being commoditised and where we lose money after support costs, while our enterprise segment quietly funds the company and receives the least product investment. Meanwhile 40% of capacity is a regulatory tax that grows every year and produces no differentiation. If we do nothing, mid-market margin compresses further, enterprise expansion stalls from neglect, and our capacity is fully consumed by compliance maintenance by year three.
>
> **CHOICES.** We will (a) make regulation-update work dramatically cheaper by moving rules out of code into a versioned rules platform; (b) invest the freed capacity into enterprise multi-entity, audit, and integration capabilities; (c) serve mid-market with a deliberately narrower, self-serve, low-touch product.
> We will **NOT**: build bespoke configuration for individual mid-market accounts; match competitor feature-for-feature in mid-market; take custom enterprise integration work that isn't reusable; add a fourth product line this year.
>
> **BETS.**
> Bet 1 — *Rules platform.* We believe ~60% of annual regulation work is mechanical rule change, not code change, based on an audit of last year's 340 change tickets. If true, we free ~25% of engineering capacity by Q3. Signal: cycle time per rule change, measured monthly. If we're not at a 40% reduction by end of Q2, the abstraction is wrong and we stop and reassess rather than push through.
> Bet 2 — *Enterprise depth drives NRR.* We believe multi-entity + audit-trail depth is the binding constraint on enterprise expansion, based on 11 of 14 expansion conversations stalling on those two capabilities. Signal: enterprise expansion pipeline, quarterly.
> Bet 3 — *Mid-market can be low-touch.* We believe a narrower self-serve product retains ≥85% of mid-market at a positive contribution margin. Signal: support cost per mid-market account. **This is our weakest bet** — if support cost doesn't fall by 50%, the segment is structurally unprofitable and we should partner or exit rather than continue.
>
> **TRADE-OFFS.** We accept: mid-market feature parity gaps and probable share loss in that segment; a visibly slower response to competitor launches; a rules-platform investment with no customer-visible output for two quarters. **Sales will be unhappy** — mid-market is where their volume is, and our answer is an explicit, published "we don't build this" list plus a reallocated quota mix toward enterprise. **Support will be unhappy** during the migration and needs headcount protection through Q3.
>
> **OUTCOMES.** Leading: rule-change cycle time; enterprise expansion pipeline; mid-market support cost/account. Lagging: enterprise NRR ≥135%; mid-market contribution margin ≥0; % capacity on regulatory maintenance ≤20%. Guardrail: **no reduction in filing accuracy or audit-trail completeness, ever** — a breach here stops the strategy, not just the project. Reviewed monthly; changeable only by the exec team with a written rationale.

**Study what makes this a strategy and not a plan:** the diagnosis names something uncomfortable and specific; the choices exclude things people actively want; every bet has a falsification condition and a pre-committed response; the trade-offs name which function will be angry and what the answer is; and there is a guardrail that can halt the whole strategy.

**Exercise 3.1 (the most valuable exercise in this book).** Write this document for your own product. One page. Show it to your engineering lead and your most senior sales counterpart separately and ask each: *"where is this wrong?"* Their disagreements are your real strategy work. *Deliverable: this is a portfolio artefact — bring it to interviews.*

---

## 3. COMPETITIVE ADVANTAGE & MOATS IN B2B SaaS

An advantage is only strategic if it **compounds** or is **costly to copy**. Most claimed advantages are neither.

| Moat | Mechanism | Strength in B2B SaaS | How you'd build it | How it dies |
|---|---|---|---|---|
| **Switching costs** | Migration is expensive/risky | **Very high** | Deep data history, embedded workflow, trained users, integrations | A competitor builds a great migration tool |
| **Workflow embeddedness** | You're where the work happens daily | **Very high** | Own the system of record for a critical process | Someone owns an adjacent, larger workflow and absorbs yours |
| **Regulatory/compliance trust** | Certifications, audit history, liability track record | **High, underrated** | SOC 2/ISO, published accuracy record, audit-defence tooling | One public failure |
| **Integration surface** | You connect to everything they use | **High** | Breadth of connectors + being the hub, not a spoke | Platform shift; a new hub emerges |
| **Data network effects** | More usage → better product for everyone | Medium (rare in B2B; data is siloed by contract) | Aggregate benchmarks, anonymised patterns, ML on pooled signal | Legal/contractual limits on data use |
| **Economies of scale** | Cost per customer falls | Medium | Multi-tenancy, shared infra | Cloud commoditises it |
| **Brand/trust** | Nobody gets fired for buying you | Medium–high in compliance | Time, references, category leadership | Slow erosion; hard to notice |
| **Proprietary tech** | You can do what they can't | **Usually low** | — | 18 months, usually less with AI |
| **Feature count** | Not a moat | **Zero** | — | Instantly |

**Two moats matter most in your domain and both are underused:**

**1. Compliance trust as a durable moat.** In tax and compliance, the buyer's job is avoiding catastrophe. A vendor with a published, verifiable accuracy and audit record has an advantage that a better-funded competitor cannot buy quickly — because **the moat is time, not money.** Very few compliance vendors deliberately productise this. Making your correctness *visible* (calculation traces, rule-version changelogs, an accuracy report, audit-defence exports) converts an invisible asset into a purchasable differentiator. This is a genuinely strong strategic idea available to you right now.

**2. Rule-versioning as a capability moat.** Every compliance vendor pays the annual regulation tax. The one who pays it at half the cost has a permanent structural margin advantage and can enter adjacent jurisdictions faster. This is invisible to customers and decisive to the P&L — which is exactly why it needs a PM to argue for it, since it will never appear on a customer request list.

**When NOT to chase a moat.** Early products should chase *any* traction. Moat-thinking applied prematurely produces elaborate architecture for a product with no users. Moats matter once you have something worth defending.

---

## 4. POSITIONING

Positioning is **context-setting**: telling the market what frame to judge you in. The strongest available practitioner treatment is April Dunford's *Obviously Awesome* (E1, published book), which structures it as:

```
1. Competitive alternatives   → What would they do if you didn't exist?
                                (Often: Excel + email. Not a vendor.)
2. Unique attributes          → What do you have that alternatives don't?
3. Value                      → What does that attribute enable, that they care about?
4. Who cares most             → Which segment cares disproportionately about that value?
5. Market category            → What context makes your value obvious?
6. (Optional) Trend           → What wave makes this urgent now?
```

**The step teams get wrong is #1.** They list vendors. In B2B the dominant alternative is almost always **the status quo**: a spreadsheet, a shared inbox, a junior employee doing it manually, or a decision to accept the pain. If you position against a vendor when you're actually competing against Excel, your entire message is aimed at the wrong contrast.

### 4.1 Competitor vs Alternative vs Substitute vs Status Quo

This distinction changes what you build, not just what you say.

| Type | Definition | Tax-prep example | What it means for product |
|---|---|---|---|
| **Direct competitor** | Same job, same approach, same segment | Another mid-market tax prep platform | Feature parity matters at the *decision-critical* level only |
| **Alternative** | Same job, different approach | Outsourcing prep to a BPO firm | You compete on total cost and control, not features |
| **Substitute** | Removes the job entirely | Regulator offers free direct-filing for simple returns | **Existential.** Segment can vanish. Watch regulators like competitors |
| **Status quo** | Doing it manually / not at all | Excel + email + a shared drive | Your enemy is inertia. Migration and anxiety-reduction beat features |

**Two strategic implications most PMs miss:**
- **In regulated markets, the regulator is a competitor.** When a tax authority ships a free filing portal, an entire segment's willingness to pay can collapse. Regulatory roadmaps belong in your competitive intelligence, tracked with the same rigour as competitor releases. This is a genuinely differentiated point of view you can bring to an interview.
- **Against status quo, your win rate is set by anxiety and habit** (Volume II, §2.4), not by feature comparison. Teams competing against Excel keep adding features and keep losing.

### 4.2 Positioning statement template

```
For [target segment]
who [situation / struggling moment],
[product] is a [market category]
that [key value delivered].
Unlike [the dominant alternative — often the status quo],
we [unique attribute that produces the value].
Proof: [evidence a sceptical buyer would accept]
```
**The "Proof" line is non-standard and you should always include it.** In B2B, especially compliance, claims without proof are noise. Proof is a reference customer, an audited number, a certification, or a public accuracy record.

---

# PART VIII — MARKET & COMPETITIVE STRATEGY

## 5. MARKET SIZING: TAM / SAM / SOM

| Term | Definition | Common lie |
|---|---|---|
| **TAM** | Total revenue if you had 100% of everyone who could conceivably buy | Inflated by including adjacent categories |
| **SAM** | The portion your product and go-to-market can actually serve today | Skipped entirely, which is where the honesty lives |
| **SOM** | What you can realistically capture in a defined period | Fantasised as a round percentage of TAM |

### 5.1 Two methods — always do both

**Top-down** (analyst report × filters): fast, defensible-sounding, usually wrong. Use for a sanity ceiling.

**Bottom-up** (count × price): slower, far more credible, and forces you to state assumptions.

```
BOTTOM-UP — Tax & compliance SaaS, mid-market segment, one country

# of accounting/tax firms in market                        ~14,000
× % with 20–200 returns/season (our SAM shape)                 38%   → 5,320
× % already using paid software (vs manual/Excel)              62%   → 3,298
× % on a platform we can realistically displace                45%   → 1,484
  (excludes those locked into an ecosystem or a captive vendor)
× average annual contract value                             $6,400
                                                      ─────────────
SAM (displaceable, annually)                                ~$9.5M

SOM (3 years): at a 12% win rate on the ~30% of that base that
evaluates alternatives in any given year:
  1,484 × 30% × 12% × 3 yrs × $6,400 ≈ $10.3M cumulative
  (≈ $3.4M ARR steady-state contribution from this segment)

ASSUMPTIONS TO CHALLENGE (ranked by impact on the answer):
  1. 45% displaceable — weakest number here; derived from 9 win/loss conversations
  2. 12% win rate — our current rate is 9%; assumes the strategy works
  3. $6,400 ACV — our realised (post-discount) figure, not list
  4. 30% evaluate annually — industry heuristic, unverified
```

**What makes this senior-grade:** the assumptions are ranked by how much they move the answer, the ACV is realised rather than list, and the weakest number is named. **A market size without a ranked assumption list is decoration.** In an interview, the sizing itself is worth little; naming which assumption the answer is most sensitive to is worth a lot.

**When NOT to size.** Don't size to justify a decision you've made. If the number comes out wrong and you adjust assumptions until it comes out right, you've built a rationalisation engine and everyone in the room can tell.

---

## 6. CLASSIC STRATEGY FRAMEWORKS — WITH HONEST LIMITATIONS

| Framework | Purpose | Genuine value | Real limitation | Use when |
|---|---|---|---|---|
| **Porter's Five Forces** | Industry structural attractiveness | Excellent for *why margins are what they are* | Static; built for 1980 manufacturing; weak on platforms, ecosystems, complements | Entering a new market or explaining margin structure |
| **SWOT** | Situation inventory | Fast, universally understood | Produces lists, not choices; no prioritisation; invites self-flattery | As a 30-minute input to a strategy doc, never as output |
| **PESTLE** | Macro-environment scan | **Genuinely high value in regulated markets** — the L and P are your product roadmap | Overkill for most feature work | Regulated domains, new geographies, annual planning |
| **Value chain** | Where value is created/captured | Shows where to integrate or divest | Hard to apply to software services | Make-vs-buy and platform decisions |
| **Ansoff Matrix** | Growth direction (existing/new × product/market) | Clarifies which *kind* of growth bet you're making | Says nothing about how | Portfolio and expansion planning |
| **Wardley Mapping** | Component evolution + strategic play | Best available tool for platform/build-vs-buy reasoning | Steep learning curve; small community | Platform strategy, Volume VIII |

**PESTLE deserves special attention in your domain.** For most SaaS PMs it's a box-ticking exercise. For a tax/compliance PM it is a **roadmap generator**: the Political and Legal dimensions produce mandatory work with hard dates, and a PM who tracks regulatory pipelines 18 months out can convert compliance obligation into first-mover advantage. Being the first vendor ready for a new e-filing mandate is worth more than any feature you could ship that quarter. **Make this an explicit quarterly practice and it becomes a visible strategic contribution — this is a promotion lever available to you specifically.**

---

## 7. COMPETITIVE INTELLIGENCE AS A PRACTICE

Not a document. A cadence.

| Cadence | Activity | Source |
|---|---|---|
| Continuous | Competitor changelog/release-notes monitoring | Their public docs, status pages, changelogs |
| Continuous | Win/loss reason capture at deal close | CRM field, enforced |
| Monthly | Pricing page diff | Their site |
| Monthly | Job posting analysis — **the highest-signal free source** | Their careers page |
| Quarterly | Win/loss interviews (neutral interviewer, not the AE) | 5–8 deals |
| Quarterly | Regulatory pipeline review | Regulator publications |
| Annually | Full competitive teardown | Trials, demos, references |

**Job postings are the most underused competitive signal available.** A competitor hiring three ML engineers and an "AI Product Manager" tells you their roadmap 9–12 months before it ships. A competitor hiring enterprise sales in a new geography tells you their expansion plan. It is public, free, and updated weekly. *(Note: I cannot verify current postings for you in this session — this is a practice to run yourself, continuously.)*

**Competitive intelligence anti-pattern:** letting it become a feature-matching machine. The purpose of CI is to understand *where the market is moving and where the money is*, not to generate parity backlog items. **If your CI process outputs a feature gap list, it has failed.** It should output a view on structural change.

---

# PART IX — PRODUCT VISION & ROADMAPS

## 8. ROADMAP ≠ FEATURE LIST

A roadmap communicates **intent under uncertainty**. A feature list communicates commitments. Confusing them is why roadmaps become political.

The core principle: **confidence decays with time horizon, and your roadmap format must express that decay.** A roadmap that presents Q4 with the same specificity as this sprint is lying, and everyone knows it, which is why nobody trusts roadmaps.

```
NOW              NEXT              LATER
(committed)      (probable)        (directional)
Specific         Problem-shaped    Theme-shaped
"Bulk client     "Reduce time      "Make deadline
 import v1"       lost to doc       risk visible
                  collection"       across a firm"
Confidence: 85%  Confidence: 60%   Confidence: 30%
Has a date       Has a quarter     Has no date
```

## 9. THE NINE ROADMAP TYPES

| Type | Organised by | Best audience | Use when | Fails when |
|---|---|---|---|---|
| **Outcome-based** | Business/customer outcomes | Exec, board | You have real outcome ownership | Team can't influence the outcome directly |
| **Theme-based** | Strategic themes | Exec, company-wide | Communicating direction without over-committing | Themes are so broad they're meaningless |
| **Now/Next/Later** | Confidence horizon | Internal team, most stakeholders | Default choice for agile B2B teams | Sales needs dates for contracts |
| **Opportunity** | Customer opportunities (from the OST) | Product + design + eng | Continuous discovery is running | Stakeholders want to see features |
| **Capability** | Product capabilities being built | Platform teams, architects | Building compound capability over time | Business can't see the value |
| **Platform** | Services + their consumers + migrations | Internal engineering customers | Platform PM work | Treated as a feature roadmap |
| **Technical** | Architecture evolution, debt, migration | Engineering leadership, CTO | Multi-quarter technical change | Used to hide feature work from the business |
| **Dependency-aware** | Sequenced by inter-team dependency | Program management, TPM work | Multi-team programs | Becomes a Gantt chart and calcifies |
| **Portfolio** | Products/areas + capital allocation | Exec, GPM/Director | Managing multiple products | Loses the customer thread entirely |

### 9.1 The B2B reality nobody's roadmap advice handles: sales wants dates

Standard advice — *"never put dates on roadmaps"* — is an **opinion**, and in enterprise B2B it is often wrong. Contracts, RFPs, implementation plans, and renewals sometimes genuinely require commitments.

The professional resolution is a **three-tier commitment model**, published explicitly:

| Tier | What it means | Who can promise it | Where it appears |
|---|---|---|---|
| **Committed** | Contractual. We will pay penalties / lose the deal if we miss | Product + Eng leadership sign-off, capacity reserved | Named quarter, in writing to customers |
| **Planned** | We intend to; capacity is allocated; not contractual | PM, with eng lead agreement | Quarter, marked "subject to change" |
| **Exploring** | We're investigating; may never happen | PM alone | No date. Ever. |

Then enforce one rule: **committed items consume a hard, capped percentage of capacity** (typically 20–30%). When Sales requests a new commitment, the question is not "can we?" but **"which existing commitment does this replace?"** That converts an emotional negotiation into an arithmetic one, which is the entire trick.

**This is one of the most immediately applicable things in this volume.** It removes the recurring roadmap fight without requiring you to win an argument about roadmap philosophy.

### 9.2 The strategic narrative

A roadmap without narrative is a list. The narrative is what makes an exec able to *repeat* your strategy in a meeting you're not in — which is the actual measure of whether alignment exists.

```
STRATEGIC NARRATIVE — one page, read aloud in under 3 minutes

1. WHERE WE ARE      Honest present state, including what isn't working
2. WHAT'S CHANGING   The external shift that makes now different
3. WHERE WE'RE GOING The destination, concretely enough to disagree with
4. HOW WE GET THERE  The 2–3 bets, in sequence, and why that sequence
5. WHAT WE'RE NOT DOING  The explicit exclusions
6. WHAT WE NEED      Decisions, capacity, or support you're asking for
```

**Point 6 is the one PMs omit and executives are waiting for.** Executives sit through many presentations that inform them. The one that asks for a specific decision is the one that gets remembered — and getting a decision made is the visible output of strategic influence.

### 9.3 Dependency-aware roadmapping (your TPM-adjacent skill)

For multi-team programs — which is most of your integration-heavy work — the roadmap must express dependency risk, not just sequence. Minimum viable structure:

| Item | Owner | Depends on | Dependency committed? | Slack | Risk if late |
|---|---|---|---|---|---|
| E-file submission v2 | Platform | Auth service scopes (Team B) | ⚠ Verbal only | 0 wks | Blocks the entire filing season release |
| Client portal upload | Web | Document service (Team C) | ✅ Written, Q2 | 3 wks | Degrades but doesn't block |

Three rules that prevent most program failures:
1. **A verbal dependency commitment is not a commitment.** Track the artefact (ticket, doc, signed-off scope), not the conversation.
2. **Zero-slack dependencies are the program's actual risk.** They deserve weekly attention; everything else deserves monthly.
3. **Publish the dependency map to the depended-upon teams.** Most missed dependencies are not refusals — they're teams that didn't know they were on your critical path.

That table, maintained honestly, is most of what a Senior TPM does and it is directly demonstrable in an interview.

---

## 10. VOLUME III EXERCISES

**Exercise 3.1 — Write the strategy.** (Restated because it matters most.) One page, using the §2.1 template, for your product. Get two hostile reviews. *Portfolio artefact.*

**Exercise 3.2 — The diagnosis test.** Write your product's diagnosis in one paragraph. Then delete every sentence a competitor would also write about themselves. If nothing remains, you had fluff. Rewrite.

**Exercise 3.3 — Alternatives audit.** List everything a customer could do instead of buying you, including doing nothing. Rank by how often you actually lose to each. *Most teams discover their #1 competitor isn't a company.*

**Exercise 3.4 — Bottom-up sizing.** Size one segment bottom-up. Rank assumptions by sensitivity. Identify the one you'd test first.

**Exercise 3.5 — Regulatory radar.** Build a PESTLE-driven 18-month regulatory pipeline for your primary market. Mark which items are mandatory, which are opportunities, and which could commoditise you. *This is the single most differentiated artefact a compliance PM can bring to an interview.*

**Exercise 3.6 — Commitment tiering.** Reclassify your current roadmap into Committed / Planned / Exploring. Calculate what % of capacity is committed. If it's over 40%, you have no strategy capacity, and that is the finding.

**Exercise 3.7 — The narrative.** Write the §9.2 narrative and deliver it verbally in 3 minutes to a peer. Ask them to repeat it back. The gap is your communication debt.

---

## 11. VOLUME III INTERVIEW BANK

1. What's your product's strategy? *(Then: what does it rule out?)*
2. What's the difference between a goal and a strategy?
3. How do you size a market for a product that doesn't exist yet?
4. Who is your biggest competitor? *(Strong answers often name the status quo.)*
5. Your CEO wants to enter a new segment. How do you evaluate it?
6. How do you handle a sales team that needs dates on a roadmap?
7. What's a moat you could build in your product? How long would it take a competitor to erase?
8. A competitor just launched your Q3 roadmap. What do you do Monday?
9. How do you decide what NOT to build?
10. Your strategy requires two quarters with no customer-visible output. How do you get that funded?
11. What external change in the next two years could make your product irrelevant?
12. Walk me through a strategy you wrote that turned out to be wrong. What was wrong in the diagnosis?

---

*Volume III complete. Continue to `04-industry-operating-models.md`.*
