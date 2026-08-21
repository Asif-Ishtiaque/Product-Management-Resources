# VOLUME II — CUSTOMER, PROBLEM & DISCOVERY
### Parts IV, V & VI

> A feature request is a customer's *solution* to a problem they haven't described. Your job is the archaeology.

---

# PART IV — CUSTOMER & USER UNDERSTANDING

## 1. THE B2B RESEARCH PROBLEM NOBODY WARNS YOU ABOUT

Every popular research method — JTBD, contextual inquiry, usability testing, the whole Continuous Discovery apparatus — was developed and popularised largely in consumer or SMB contexts where **you can talk to users freely and cheaply.**

In B2B, and especially in regulated B2B:

| Consumer assumption | B2B reality |
|---|---|
| You can recruit users easily | Access is gated by the account manager, who fears you'll annoy the customer |
| Users are the buyers | Buyer, champion, user, gatekeeper are four different people |
| You can observe usage | Their data is confidential; you may not be legally allowed to see their screen |
| Weekly interviews are feasible | A tax preparer in filing season will not give you 45 minutes in March |
| Behaviour is voluntary | Users are *required* to use your product; satisfaction and usage are decoupled |
| A/B testing is available | Changing a compliance workflow mid-cycle may be unacceptable or illegal |

**The last two are the ones that break naive frameworks.** In mandated software, high engagement can mean the product is *bad* — people spend longer because it's confusing. DAU is not a health metric when usage is compulsory.

**Your adapted research system for regulated B2B:**

| Constraint | Adaptation |
|---|---|
| Users are hard to reach | Mine the exhaust: support tickets, UAT failures, session recordings, in-app search queries, config changes. Cheaper and continuous. |
| Seasonality | Do generative research in the off-season. In peak season, only run in-context micro-research (2 questions, in-app) |
| Confidential data | Ask them to demo on their own screen with sanitized data; you watch, you don't record |
| Access gated by CS | Trade value for access: bring them findings, not just questions. Make research a customer benefit |
| Mandated usage | Measure *task completion time, error rate, rework, and support contact* — not engagement |

---

## 2. JOBS-TO-BE-DONE, DONE PROPERLY

### 2.1 The two JTBD schools (and why the confusion matters)

There are two distinct traditions using the same name. Mixing them produces mush.

| | **Jobs-as-Progress** (Christensen / Moesta) | **Jobs-as-Outcomes** (Ulwick / ODI) |
|---|---|---|
| Core unit | The struggling moment and the switch | The functional job step + desired outcome statements |
| Method | Switch interviews, timeline reconstruction | Outcome statements rated on importance × satisfaction |
| Output | A narrative of forces | A quantified opportunity score |
| Best for | Understanding *why* people change | Deciding *what* to improve, quantitatively |
| Weakness | Not quantifiable, small-n, story-seductive | Rigid; misses emotional/social jobs; survey-dependent |

**Use both, in sequence:** Progress-school interviews to discover the jobs → Outcome-school surveys to size and rank them. That sequence is the professional practice; picking one and evangelising it is the amateur move.

### 2.2 The job statement (and the four job types)

Format: **`When [situation], I want to [motivation], so I can [expected outcome].`**

Every job has four layers. Missing the last two is why "we built what they asked for and they still didn't switch."

| Layer | Question | Tax-prep example |
|---|---|---|
| **Functional** | What task? | File 400 client returns before the deadline |
| **Emotional** | What feeling sought/avoided? | Avoid the dread of a filing error surfacing 18 months later in an audit |
| **Social** | How do they want to be seen? | Be the firm that never misses a deadline; look competent to the client |
| **Financial** | What economic outcome? | Complete more returns per preparer-hour without adding headcount |

In compliance software, **the emotional job dominates purchase behaviour and nobody puts it in the PRD.** The buyer isn't buying speed. They're buying *the ability to sleep during filing season.* A feature that saves 4 minutes but increases uncertainty will lose to a slower feature that shows a green "validated against current rules" badge. That badge is not a feature; it's the emotional job made visible.

### 2.3 Job story vs user story — and when each belongs

Your house standard is Mike Cohn format + Gherkin acceptance criteria, which is correct for development-ready work. Job stories are a **discovery** artefact, not a replacement.

| | User story (Cohn) | Job story |
|---|---|---|
| Form | As a [role], I want [action] so that [outcome] | When [situation], I want to [motivation] so I can [outcome] |
| Anchors on | Persona | Situation/context |
| Best for | Building | Understanding |
| Failure mode | Persona becomes a fiction that justifies anything | Not implementable without translation |

**The pipeline:** job story (discovery) → problem statement (framing) → user story + Gherkin (execution). Skipping the middle step is how teams end up with well-formed stories for the wrong problem.

### 2.4 The Forces of Progress — the most useful diagnostic in B2B

Four forces determine whether a customer switches. **You must weaken the bottom two, not just strengthen the top two** — and almost every roadmap only works on the top two.

```
        PUSH of the situation          PULL of the new solution
        (what's broken today)          (what attracts them)
                    ↘                  ↙
                       [ SWITCH? ]
                    ↗                  ↖
        ANXIETY about the new     HABIT of the present
        (what could go wrong)     (inertia, sunk cost, comfort)
```

**Real example — why a superior tax product loses a deal:**
- Push: current tool is slow, error-prone. **Strong.**
- Pull: your product is faster with better validation. **Strong.**
- Anxiety: "If we migrate mid-year, what happens to our in-progress returns? Are prior-year filings still reproducible for an audit? What if your rule engine is wrong in a way we don't discover until the IRS calls?" **Overwhelming.**
- Habit: 30 preparers trained on the old UI; muscle memory in filing season. **Strong.**

Push+Pull lose to Anxiety+Habit constantly. The roadmap that wins this deal is not "more features." It is:
- **Anxiety reducers:** parallel-run mode (both systems, compare outputs), prior-year import with reconciliation report, published rule-version changelog, audit-trail export, sandbox with their real data.
- **Habit reducers:** import their templates, keyboard-parity mode, migrate mid-season with a per-client cutover rather than big-bang.

**This is the single highest-ROI reframe in B2B product management.** Anxiety-reduction features are systematically under-prioritised because they don't demo well and no customer requests them by name — customers express anxiety as *silence*, or as "we'll revisit next year."

### 2.5 Exercise & interview

**Exercise 2.1.** Interview three customers who *evaluated you and chose someone else* (or chose nothing). Map their four forces. Then look at your roadmap and count how many items reduce anxiety or habit. If the answer is zero, you have found your quarter.

**Interview question.** *"A customer says they love the product but didn't renew. How do you find out what actually happened?"* — Testing whether they know stated reasons ≠ real reasons, and whether they'd do a switch interview.

**Reference.** Christensen et al., *Competing Against Luck* (E1). Bob Moesta, *Demand-Side Sales* (E1). Ulwick, *Jobs to be Done: Theory to Practice* (E1). The forces diagram originates in the Re-Wired Group's switch interview work (E2).

---

## 3. RESEARCH METHODS: THE SELECTION TABLE

| Method | Answers | Sample | Cost | Use when | Do NOT use when |
|---|---|---|---|---|---|
| **Generative interview** | Why do they behave this way? | 5–8 per segment | Med | Problem space unclear | You need to predict behaviour at scale |
| **Switch interview** | What caused change? | 8–12 switchers | Med | Understanding churn/wins | No recent switchers exist |
| **Contextual inquiry** | What do they *actually* do? | 4–6 | High | Stated ≠ observed behaviour suspected | You can't legally observe |
| **Usability test** | Can they complete this? | 5 per iteration | Low | Validating a design | You need to know if they *want* it |
| **Diary study** | Behaviour over time | 8–15, 1–4 wks | High | Seasonal or episodic use | You need results this sprint |
| **Survey** | How many / how much? | 100s+ | Low | Sizing something you already understand | You don't know what to ask yet |
| **Behavioural analytics** | What happened? | All users | Low (if instrumented) | Quantifying known flows | Explaining *why* |
| **Session replay** | Where do they struggle? | 20–50 sessions | Low | Finding friction fast | Privacy/regulatory restrictions |
| **Support ticket mining** | What breaks? | All tickets | Very low | Continuous, always | You need unmet needs (tickets only show *present* product's failures) |
| **Win/loss analysis** | Why did we win/lose? | All deals | Med | Every quarter, B2B | Sales won't be honest — needs neutral interviewer |
| **Sales call listening** | What do buyers object to? | Ongoing | Very low | Always. Highest ROI/hour in B2B | You treat sales' interpretation as the finding |

**The B2B-specific top three by ROI:** support ticket mining, sales call listening, win/loss analysis. All three are nearly free, continuous, and systematically under-used because they're unglamorous. **Ticket mining alone will fill a quarter of your roadmap with things you can defend.**

**Critical limitation of ticket mining:** tickets only reveal problems with what exists. They will never tell you about the job you don't serve at all. That is what generative interviews are for. Teams that run on tickets alone build a locally-optimal product that slowly becomes irrelevant.

---

## 4. SEGMENTATION THAT ACTUALLY DRIVES DECISIONS

Four segmentation types, in ascending order of usefulness and cost:

| Type | Basis | Useful for | Failure mode |
|---|---|---|---|
| **Firmographic** | Size, industry, geo | Sales targeting, pricing tiers | Says nothing about product needs |
| **Behavioural** | What they do in-product | Lifecycle messaging, activation | Describes present users only; blind to non-users |
| **Needs-based** | What outcomes they want | Roadmap and packaging | Expensive to research; needs refresh |
| **Jobs-based** | What they're hiring you for | Strategy and positioning | Hardest; requires real interviews |

**The B2B trap:** segmenting by company size when the real variation is by **workflow complexity.** A 15-person tax firm handling complex multi-entity clients has more in common with a 200-person firm than with a 15-person firm doing simple individual returns. Segment by the job, then check whether it correlates with firmographics for sales purposes.

**Practical test for a good segment.** A segment is real if: (1) members behave measurably differently, (2) you would build differently for them, (3) you can identify which segment an account is in *without asking them.* Fail any of the three and you have a persona poster, not a segment.

### Personas: use with a specific warning

Personas fail when they become fiction ("Sarah, 34, likes yoga") that can justify any decision. A **useful** B2B persona contains only decision-relevant facts:

```
PREPARER — MID-COMPLEXITY FIRM
Volume: 200–500 returns/season, 60% recurring clients
Tools: your product + Excel + email + a scanner + the tax authority portal
Peak: 6 weeks, 55+ hrs/wk, 3 concurrent returns open at once
Success = returns completed per day with zero rejections
Fails when: source docs are incomplete; rules changed since last year
Won't tolerate: anything that adds a click during peak
Never sees: your billing, your admin panel, your reports
Decides nothing about purchase. Can kill adoption entirely by refusing to use it.
```

That last line is the one that matters and the one personas usually omit: **what power does this person have?**

---

## 5. JOURNEY MAP vs SERVICE BLUEPRINT vs WORKFLOW MAP

Frequently conflated; different tools.

| | Journey map | Service blueprint | Workflow/state map |
|---|---|---|---|
| Shows | Customer experience + emotion over time | Front-stage + backstage + support systems | States, transitions, dwell time |
| Best for | Finding emotional low points | Finding organisational causes of customer pain | Finding bottlenecks quantitatively |
| B2B fit | Good for buying journey | **Excellent** — B2B pain is usually backstage | **Excellent** for workflow products |
| Weakness | Often fictional if not research-based | Heavy to produce | Ignores emotion entirely |

**For workflow-automation products, the state map with dwell-time data is the highest-value artefact you can build**, and almost nobody builds it. It converts "users say it's slow" into "returns sit in *Awaiting Client Documents* for a median of 4.2 days with a p90 of 19 days" — which points at a completely different solution (client-side document upload with nagging) than the one people were asking for (faster form rendering).

---

## 6. WILLINGNESS TO PAY

| Method | How | B2B validity | Warning |
|---|---|---|---|
| **Van Westendorp** | 4 price-perception questions | Moderate | Measures perception, not behaviour. Anchoring-prone. |
| **Gabor-Granger** | "Would you buy at X?" descending | Moderate | Overstates; no budget reality |
| **MaxDiff / conjoint** | Trade-off choices across bundles | **Good** | Needs n≈150+; expensive |
| **Actual price testing** | Different prices to different cohorts | **Best** | Often infeasible/unfair in B2B contracts |
| **Win/loss price analysis** | Where deals died on price | **Best available in B2B** | Sales attributes everything to price; needs neutral probing |
| **Discount analysis** | What you actually close at | **Truth** | Your realised price is your real price |

**The B2B reality:** your discount table is your most honest WTP research and it already exists in your CRM. If your average discount is 22%, your list price is wrong by roughly 22% for that segment. Go look at it this week — it costs nothing and it is more reliable than any survey.

---

# PART V — PROBLEM FRAMING

## 7. PROBLEM ≠ SOLUTION

The most-repeated principle in product management, and the least practised, because **solutions are socially rewarded and problems are not.** Saying "we should build X" makes you look decisive. Saying "I don't think we understand the problem yet" makes you look slow. Seniority is partly the accumulated credibility to say the second thing.

### 7.1 The conversion ladder

Every feature request should be walked up this ladder before it enters a backlog:

```
FEATURE REQUEST   ("Add a bulk-edit button")
      ↓ ask: what are you trying to accomplish?
UNDERLYING PROBLEM ("Updating 200 clients' filing status takes 3 hours")
      ↓ ask: why does that matter to you?
CUSTOMER NEED     ("I must know which clients are at risk of missing the deadline, at any moment")
      ↓ ask: what does this cost the business?
BUSINESS OPPORTUNITY ("Deadline visibility is the #1 churn driver in firms >100 clients,
                       a segment that is 40% of ARR and 60% of expansion")
      ↓ ask: what else solves this?
SOLUTION SPACE    (bulk edit | a risk dashboard | automated status inference | proactive alerts)
```

Note what happened: the requested solution (bulk edit) is now **one of four candidates and probably not the best one.** A risk dashboard with automated status inference solves the need without the user doing 200 edits at all. **You cannot get there without walking the ladder.**

### 7.2 Worked conversions (do these until it's reflex)

**Case A — CRM.**
Request: "We need to export contacts to Excel." → Problem: "I build my weekly pipeline review deck manually, 90 minutes every Monday." → Need: "I need to present pipeline changes to my VP in a format they trust." → Opportunity: "Sales managers spend ~6 hrs/month on manual reporting; this is a top-3 complaint in QBRs and a differentiator for competitor Y." → Solution space: export | scheduled report | native pipeline-change view | Slack digest.
*The winning solution is probably the change-view, and it makes export irrelevant.*

**Case B — HRMS.**
Request: "Add a field for emergency contact secondary phone." → Problem: "We fail an audit checklist item." → Need: "Our HR records must satisfy a specific compliance schema." → Opportunity: "Every regulated customer has a slightly different mandatory-field schema; we're taking one-off field requests forever." → Solution space: this field | configurable custom fields | compliance-schema templates per jurisdiction.
*The request reveals a platform-shaped problem. Building the one field is the trap: you will build 200 of them.*

**Case C — Tax/compliance (the hard one).**
Request: "Let us override the calculated tax amount." → Problem: "Our engine's result disagrees with the client's expectation in edge cases." → Need: "I must be able to file a return I believe is correct, even when the software disagrees." → Opportunity: **This is not a feature question. It's a liability and trust question.** An unrestricted override destroys your correctness guarantee and your audit story; refusing it entirely blocks legitimate filings.
*Solution space: no override | override with mandatory documented reason + audit flag | "expert mode" gated by role with firm-level policy | fix the underlying edge cases and expose the calculation trace so preparers can verify rather than override.*
**The right answer is usually the last one** — the real need is *verifiability*, and override is the customer's proxy for it. Showing the calculation trace serves the need and strengthens rather than destroys the correctness guarantee.

That third case is the level of framing that gets you hired as a Senior PM. Notice it took no new technology — only refusing to treat the request as the problem.

### 7.3 The problem statement template

```
PROBLEM STATEMENT
Who:         [specific segment, not "users"]
Situation:   [when this occurs — trigger and context]
Struggle:    [what they're unable to do, in their words]
Current      [what they do today — the workaround IS the evidence]
workaround:
Cost:        [quantified: time, money, risk, error rate]
Frequency:   [how often, for how many]
Evidence:    [3 sources minimum, with type — qual/quant/behavioural]
Why now:     [what changed — this is the question most teams can't answer]
Not solving  [what happens if we do nothing — be honest, sometimes: nothing]
this means:
```

**"Why now" is the field that kills bad projects.** If nothing has changed — no new regulation, no competitor move, no customer growth, no cost shift — you are probably working on something that has been survivable for years and will remain so. That's not disqualifying, but it must be a conscious choice, not an accident.

**The workaround is your best evidence.** If customers have built an elaborate Excel workaround, the problem is real and valuable — they've already paid for it in labour. If there is no workaround, the problem may not be painful enough to pay for. *"Show me your spreadsheet"* is the single best question in B2B discovery.

### 7.4 Root cause: use 5 Whys carefully

5 Whys is a **heuristic**, not a method. Its documented weaknesses: it produces a single causal chain when reality has many, and the answer depends heavily on who's in the room.

Better for product work: **causal mapping** — write the symptom, then branch every plausible cause, then mark each as *evidenced / assumed / disproven.* You end with a map, not a line, and the assumed nodes become your research agenda.

Example — symptom: "trial-to-paid conversion dropped from 22% to 14%."
```
├── Fewer qualified trials       [check: source mix — EVIDENCED, paid social spend doubled]
├── Onboarding got worse         [check: activation rate by cohort — DISPROVEN, flat]
├── Competitor pricing changed   [check: win/loss notes — ASSUMED, needs 5 interviews]
├── Seasonality                  [check: same period last year — EVIDENCED, partial]
└── Instrumentation changed      [check: tracking deploy log — CHECK THIS FIRST, ALWAYS]
```
**Always check instrumentation first.** A meaningful share of "metric crashed" incidents are tracking bugs, and diagnosing a real cause for a fake drop wastes weeks.

---

## 8. OPPORTUNITY SIZING

Sizing is not forecasting. It is **deciding whether something is worth a conversation.** Aim for the right order of magnitude, show your assumptions, and refuse to add decimal places you haven't earned.

### The B2B sizing template

```
OPPORTUNITY: Automated document ingestion for tax prep

REACH
  Accounts affected:        340 of 1,200 (firms >100 returns/season)
  Users within:             ~4 preparers each = ~1,360 users
  Frequency:                ~250 returns/preparer/season

IMPACT PER EVENT
  Current:  ~12 min manual data entry per return
  Expected: ~3 min review of extracted data  (assumption: 85% extraction accuracy)
  Delta:    ~9 min/return

TOTAL
  1,360 × 250 × 9 min ≈ 51,000 hours/season saved across the customer base

VALUE CAPTURE  ← the step most PMs skip
  Customer value ≠ our revenue. How do we capture it?
    a) Retention:  addresses the #2 cited churn reason → est. 1.5pt churn reduction
    b) Expansion:  premium tier at +$X/seat → est. 25% attach in this segment
    c) Acquisition: removes the top objection in competitive deals
  Modelled: retention effect is most reliable; price it as a tier, not an add-on.

CONFIDENCE
  Reach:            HIGH (from account data)
  Time delta:       MEDIUM (from 6 timed observations — small n)
  85% accuracy:     LOW ← this is the assumption that decides the project
  Willingness to pay: LOW (untested)

ORDER OF MAGNITUDE: significant. WEAKEST LINK: extraction accuracy.
NEXT STEP: 2-week spike testing extraction on 200 real documents. Kill if <70%.
```

**The two disciplines that make this senior-grade:** (1) an explicit **value capture** section — customer value that you cannot capture is philanthropy; (2) naming the **weakest link** and making the next step a test of *that*, not a build.

---

## 9. ASSUMPTION MAPPING

Before committing, list assumptions and map them on **importance × evidence**.

```
              HIGH IMPORTANCE
                    │
   ⚠ TEST NOW       │   ✓ PROCEED
   (leap of faith)  │   (well-evidenced)
   ─────────────────┼─────────────────  → EVIDENCE
   ○ IGNORE         │   ○ DOCUMENT
   (low stakes)     │   (known, low stakes)
                    │
              LOW IMPORTANCE
```

**Six assumption categories** — the standard four plus two that regulated B2B requires:

| Category | Question | Tax/compliance example |
|---|---|---|
| **Desirability** | Do they want it? | Will preparers trust extracted data? |
| **Viability** | Does it work for the business? | Can we price it above the per-document OCR cost? |
| **Feasibility** | Can we build it? | Can extraction hit 85% on real, messy scans? |
| **Usability** | Can they use it? | Can they spot a wrong extraction faster than typing it? |
| **Compliance** ★ | Are we allowed? | Does processing client tax documents through a third-party OCR breach data residency or client-confidentiality obligations? |
| **Ethical/Consequence** ★ | What if we're wrong? | Who is liable when extraction silently produces a wrong figure on a filed return? |

**In regulated domains, the compliance assumption is usually the true leap of faith and it is usually discovered last, after the build.** Move it first. A two-hour conversation with legal at week zero routinely saves a quarter.

---

# PART VI — PRODUCT DISCOVERY

## 10. THE EVIDENCE HIERARCHY

Not all evidence is equal. Rank it, and state which kind you have.

| Rank | Type | Example | Strength | Weakness |
|---|---|---|---|---|
| 1 | **Behavioural, at scale, causal** | A/B test on real usage | Strongest | Expensive, slow, needs traffic |
| 2 | **Behavioural, at scale, observational** | Cohort analysis of existing users | Strong for what, weak for why | Confounded |
| 3 | **Behavioural, small n** | Prototype task completion | Real behaviour | Not generalisable |
| 4 | **Commercial** | Signed LOI, pre-payment, deal won/lost on it | **Very strong in B2B** | Slow; small n |
| 5 | **Stated preference, structured** | Conjoint, MaxDiff | Moderate | Hypothetical |
| 6 | **Stated preference, unstructured** | Interviews | Good for *why*, poor for *whether* | People misreport |
| 7 | **Analogical** | "Competitor X did it and grew" | Weak | Survivorship bias |
| 8 | **Authority** | "Our CEO thinks" / "Gartner says" | Weakest | Not evidence |

**The professional move: triangulate across types, not volume within one.** Twenty interviews are not stronger than five interviews plus one behavioural signal plus one commercial signal. Ten more interviews mostly buy you confidence, not accuracy.

**In B2B, rank 4 is your secret weapon.** A customer who will sign a contract amendment contingent on a feature has given you stronger evidence than any survey. *"Would you pay for this?"* is weak. *"Here's an addendum, will you sign it?"* is dispositive.

---

## 11. THE DISCOVERY METHOD LIBRARY

| Method | What it tests | Time | Cost | B2B/regulated fit | Do NOT use when |
|---|---|---|---|---|---|
| **Concierge** (you do it manually for real customers, openly) | Desirability + workflow reality | 2–6 wks | Low | **Excellent** | You can't legally handle their data |
| **Wizard of Oz** (looks automated, is manual, user unaware) | Desirability of the automated experience | 2–4 wks | Med | **Use with care** — see ethics below | Consequential/regulated outputs |
| **Fake door** (button for a nonexistent feature) | Interest | Days | V. low | **Often inappropriate** | Trust-critical products (see below) |
| **Landing page test** | Message-market fit | 1–2 wks | Low | Good for new segments | You need feature-level signal |
| **Prototype test** | Usability + comprehension | 1 wk | Low | Excellent | You need *whether they'd buy* |
| **Painted door with waitlist** | Interest, honestly | Days | Low | Good — the honest fake door | — |
| **Pilot / design partner** | Everything, in reality | 1–2 qtrs | High | **The B2B gold standard** | You need speed |
| **A/B test** | Causal effect | 2–8 wks | Med–high | Limited (see Vol VI) | Low traffic, or workflow-mandated products |
| **Spike / technical prototype** | Feasibility | 1–2 wks | Low | Essential for AI/extraction claims | The risk isn't technical |

### 11.1 The ethics gate — read before running fake doors or Wizard of Oz

These techniques are taught uncritically in most PM material. In regulated, high-consequence, or relationship-driven B2B they carry real risk:

- **Fake door in compliance software.** A tax preparer clicks "Auto-file with Tax Authority," gets "coming soon," and now wonders what else in your product is real. In a product whose entire value is trustworthiness, you have traded a small amount of demand data for a large amount of trust. **Use a clearly-labelled waitlist / "vote for this" instead** — you get most of the signal with none of the deception.
- **Wizard of Oz on consequential outputs.** If a human is silently producing outputs the user believes are system-generated, and those outputs feed a legal filing, you have a liability and disclosure problem, not a research technique.
- **Concierge is the ethical alternative to both** and is *better* in B2B anyway: you tell the customer you'll do it manually, they get real value immediately, and you learn the workflow in depth. It scales badly, which is exactly why it teaches you what to automate.

**Heuristic:** *if the customer would feel deceived on learning how the test worked, don't run it.* This costs you almost nothing in learning and protects the only asset a compliance product has.

### 11.2 Continuous discovery, adapted for seasonal B2B

The canonical practice (Teresa Torres, *Continuous Discovery Habits*, E1) is a weekly customer touchpoint by the trio of PM + designer + engineer, feeding an **Opportunity Solution Tree**:

```
                    DESIRED OUTCOME
              (reduce time-to-file by 30%)
                          │
        ┌─────────────────┼─────────────────┐
   OPPORTUNITY       OPPORTUNITY        OPPORTUNITY
   (data entry       (waiting on        (rework after
    is slow)          client docs)       validation errors)
        │                  │                  │
   ┌────┴────┐        ┌────┴────┐       ┌─────┴─────┐
  SOL   SOL          SOL      SOL      SOL        SOL
   │     │            │        │        │          │
 test  test         test     test     test       test
```

Two rules that make the tree useful rather than decorative:
1. **Opportunities are customer needs, never solutions.** "A bulk edit button" is not an opportunity. "Updating many clients at once is slow" is.
2. **You compare solutions within an opportunity, never across the whole tree.** Comparing "bulk edit" against "client document portal" is meaningless — they serve different opportunities. This single rule prevents most bad prioritisation.

**Seasonal adaptation for your context:** weekly interviews are impossible in filing season. Run a **two-mode year**: generative discovery (interviews, contextual inquiry, opportunity mapping) in the off-season; **in-context micro-research** during peak (one in-app question, session replay review, ticket triage participation, sitting in on support calls). Peak season is your richest observational period and your worst interview period — plan around that rather than fighting it.

### 11.3 The discovery decision gate

End every discovery cycle with an explicit, written verdict. Discovery without a decision gate becomes research theatre.

```
DISCOVERY VERDICT — [Opportunity name] — [date]
Opportunity:            [customer need]
Evidence gathered:      [type + rank from §10 for each source]
Strongest evidence for: 
Strongest evidence against: 
Leap-of-faith assumption remaining: 
Decision:  ☐ BUILD   ☐ TEST FURTHER   ☐ PARK (revisit when: ____)   ☐ KILL
Rationale (3 sentences):
If BUILD — what would make us stop:  [the kill criterion, defined NOW]
Decision owner:         Date:
```

**"What would make us stop" is the field that separates disciplined teams from feature factories.** Defining the kill criterion before you start is the only reliable defence against sunk-cost escalation, because after you start, nobody has the standing to propose killing it.

---

## 12. VOLUME II EXERCISES

**Exercise 2.2 — The Conversion Ladder Drill.** Take the ten most recent feature requests in your backlog. Walk every one up the ladder in §7.1. Count how many turn out to share an underlying problem. *In most B2B backlogs, 10 requests collapse into 3–4 problems. Those 3–4 are your actual roadmap.*

**Exercise 2.3 — Workaround Archaeology.** Ask five customers: "show me the spreadsheet you keep alongside our product." Screenshot each. The columns in those spreadsheets are your missing product. *Deliverable: annotated screenshots + the capability each implies.*

**Exercise 2.4 — Force Analysis on a Lost Deal.** Pick a deal you lost or a churned account. Interview someone involved. Map push/pull/anxiety/habit. *Deliverable: one-page force map + three anxiety-reduction candidates for the roadmap.*

**Exercise 2.5 — Sizing with Weakest Link.** Size your top opportunity using the §8 template. Identify the weakest-link assumption. Design the two-week test that resolves it. *Deliverable: opportunity brief with a kill criterion.*

**Exercise 2.6 — Opportunity Solution Tree.** Build one for your team's current quarterly outcome. Enforce the "opportunities are needs" rule strictly. *Deliverable: the tree + a note on which branch you have the least evidence for.*

---

## 13. VOLUME II INTERVIEW BANK

1. A customer asks for a specific feature. Walk me through the next 30 minutes of that conversation.
2. How do you do discovery when you can't easily talk to users?
3. What's the difference between a user need and a feature request? Give me an example from your product.
4. How would you size an opportunity when you have almost no data?
5. Your strongest evidence is 12 customer interviews. Your PM peer says that's not enough. Are they right?
6. How do you know when you've done enough discovery?
7. Describe a time discovery told you to kill something you personally wanted to build.
8. Would you run a fake-door test on a healthcare product? Why or why not?
9. Your win rate is fine but your renewal rate is dropping. Where do you look first?
10. How do you separate what a customer says from what they do?

---

*Volume II complete. Continue to `03-strategy-market-roadmaps.md`.*
