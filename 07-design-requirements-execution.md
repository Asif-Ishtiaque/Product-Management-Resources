# VOLUME VII — DESIGN, REQUIREMENTS & EXECUTION
### Parts XIV, XV & XVI

> A shipped feature is not a finished product, and a written requirement is not a shared understanding. This volume is about closing both gaps.

---

# PART XIV — PRODUCT DESIGN

## 1. WHAT A PM ACTUALLY OWNS IN DESIGN

The failure modes sit at both extremes. PMs who treat design as a service function hand over a spec and receive pixels. PMs who over-reach draw the screens themselves and destroy the relationship.

The correct division:

| PM owns | Designer owns | Jointly owned |
|---|---|---|
| The problem and who has it | The interaction model | Information architecture |
| Constraints (technical, regulatory, commercial) | Visual and interaction craft | The user flow |
| Success criteria | Design system fidelity | Edge and error states |
| Trade-off framing and the decision | Usability of the chosen direction | Scope of the first release |
| Which segment wins when they conflict | Accessibility implementation | Accessibility requirements |

**The sentence that defines the boundary:** *"I own what problem we're solving and what constraints are real. You own how it works. When those collide, we decide together and I make the final call on scope."*

**The most common PM design mistake is not drawing screens — it's specifying a solution while calling it a requirement.** "The user needs a dropdown to select filing status" is a design decision disguised as a requirement. "The preparer must be able to determine filing status for a client in under 15 seconds, including the ~12% of cases with mid-year changes" is a requirement. The second gives the designer room and gives you a testable outcome.

---

## 2. INFORMATION ARCHITECTURE — THE HIGHEST-LEVERAGE DESIGN DECISION

IA is how the product's concepts are named, grouped, and related. It is the part of design PMs influence most and think about least.

**Why it matters more than screens:** IA encodes the mental model users are forced to adopt. Screens can be redesigned in a sprint. **A wrong IA becomes a data model, then an API, then a permissions model, then a customer's trained habit — and after that it's a multi-quarter migration.** IA is a one-way door wearing a two-way door's clothes.

### The B2B IA questions that matter

1. **What is the primary object?** In a tax platform: is the central object the *client*, the *return*, or the *engagement*? This choice propagates into navigation, permissions, billing, reporting, and search — and firms with multi-entity clients will experience an object choice that doesn't match their reality as constant friction.
2. **What's the hierarchy?** Firm → office → team → preparer → client → engagement → return → form → field. Every level you expose is a level of configuration, permissions, and reporting you must support forever.
3. **Does your vocabulary match theirs?** If preparers say "engagement" and your product says "project," every conversation with your product costs a translation. Language mismatches are invisible in usability tests with your own team and glaring with real users.
4. **What's a container vs. an attribute?** Is "tax year" a container that holds returns, or an attribute on a return? Both are defensible; they produce entirely different products.

**Exercise 7.1.** Write your product's object model as a list of nouns and their relationships. Show it to three customers and ask them to describe their work using your nouns. Every place they stumble or substitute their own word is an IA defect. *Deliverable: an annotated object model — this is also the input for the data model conversation in Volume VIII.*

---

## 3. FLOWS, TASKS AND STATES

Three different artefacts, routinely conflated.

| Artefact | Shows | Best for |
|---|---|---|
| **User flow** | The path a person takes through screens | Onboarding, purchase, linear tasks |
| **Task flow** | The steps to complete a job, independent of UI | Understanding the job before designing |
| **State machine** | The states an object can be in and legal transitions | **Workflow products — this is the design** |

**For workflow and compliance software, the state machine is the product design.** A return is in Draft → Data Collection → Preparation → Internal Review → Client Review → Signed → Filed → Accepted/Rejected → Amended. Everything else — screens, notifications, permissions, reporting, SLAs — is downstream of that model.

Three rules for state design that prevent most workflow product defects:

1. **Every state must have an owner.** If a return is in "Client Review," who is accountable for moving it? A state with no owner is where work goes to die, and it will show up as p90 dwell time in your workflow analytics (Volume II §5).
2. **Every transition needs a trigger and a permission.** Who can move it, under what conditions, and is it reversible? "Can you un-file a return?" is a product question with legal consequences.
3. **Model the backward transitions explicitly.** Teams design the happy forward path and then discover that returns bounce backward constantly. Rework paths are not edge cases in professional workflows; they're 20–40% of transitions.

---

## 4. HEURISTICS, TESTING, AND WHAT THEY'RE WORTH

**Nielsen's 10 usability heuristics** (E1 — published by Nielsen Norman Group) remain the standard evaluation checklist: visibility of system status, match with the real world, user control and freedom, consistency, error prevention, recognition over recall, flexibility, minimalist design, help users recover from errors, documentation.

Label them correctly: these are **heuristics**, not standards. They're a cheap first-pass filter that catches obvious problems without recruiting users. They do not tell you whether you solved the right problem.

**The "5 users finds 85% of problems" claim** (Nielsen, E1) is widely misquoted. It holds for *one* homogeneous user group testing *one* interface for *usability* defects. It does not hold when: you have distinct segments (test 5 *per segment*), you're testing desirability rather than usability, or the problems are infrequent-but-severe. In B2B with novice, intermediate, and power users on the same screen, five users tests one third of your population.

**Prototype fidelity — match it to the question:**

| Fidelity | Answers | Cost | Risk |
|---|---|---|---|
| Sketch / whiteboard | Is the concept right? | Minutes | Users can't imagine it |
| Wireframe | Is the structure right? | Hours | Debates about visual design derail it |
| Interactive mockup | Can they complete the task? | Days | Looks finished; invites polish feedback |
| Coded prototype | Does it feel right at real speed with real data? | Weeks | Gets shipped by accident |

**The B2B-specific rule: test with the customer's own data.** A tax preparer looking at a screen of realistic-but-fake clients will nod along. The same preparer looking at a screen with their *actual* 400 clients will immediately tell you the sort order is wrong, the density is unusable, and the filter you're proud of doesn't include the one they need. Density and scale problems only surface at real volume.

---

## 5. ACCESSIBILITY — A STANDARD, NOT A PREFERENCE

Distinguish clearly: **WCAG 2.2 (W3C) is a standard.** It has levels (A, AA, AAA), and AA is the common procurement and legal threshold. It is referenced by regulation in multiple jurisdictions and by procurement policy in most public-sector and large-enterprise buying.

**Why this belongs in a product management book rather than a design one:** in B2B, accessibility is a **deal qualifier**. Enterprise and public-sector procurement frequently requires an accessibility conformance report. A product that can't produce one gets filtered out before anyone sees a demo — which appears in your data as deals that never existed rather than deals you lost.

**The PM-owned decisions:**
- Conformance target (AA is the practical default) and when it applies — new work only, or remediation of existing surfaces too?
- Whether accessibility is in the definition of done or a separate backlog (if it's a separate backlog, it will never be done)
- Budget for an audit and a published conformance report
- Whether keyboard-only operation is fully supported — which in dense professional tools also serves your power users, who are your most valuable and most vocal segment

**The strategic reframe:** keyboard-first, screen-reader-compatible design and high-throughput professional workflows want the same things — no mouse dependency, clear focus, predictable structure, meaningful labels. Accessibility work in a professional tool is usually power-user work with a compliance certificate attached. That is how you fund it.

---

## 6. THE UNHAPPY PATH BUDGET

Most PRDs spend 90% of their words on the happy path and one line on errors. Users spend a disproportionate share of their emotional experience on the other paths — and in compliance software, the unhappy path is where liability lives.

**Required states for every meaningful surface:**

| State | The question | Common failure |
|---|---|---|
| **Empty** | First-time and zero-data — what do they do next? | Blank screen; the highest-leverage onboarding surface, wasted |
| **Loading** | What's happening and how long? | Spinner with no context on a 40-second operation |
| **Partial** | Some data loaded, some failed | Silently showing incomplete data — dangerous in reporting |
| **Error — user recoverable** | What went wrong and what do I do? | "An error occurred" |
| **Error — not recoverable** | Who do I contact, with what reference? | No support code, no context preserved |
| **Permission denied** | Can't or shouldn't see this? | Revealing the existence of records they can't access |
| **Stale** | The data is old — do they know? | Silently serving cached compliance data |
| **Concurrent edit** | Someone else changed this | Last-write-wins, silently destroying work |
| **Degraded** | A dependency is down; what still works? | The whole product fails because notifications are down |

**The compliance-specific one is "stale."** If a rule changed and a return was calculated under the previous version, the user must know. Silent staleness in a calculation engine is not a UX defect; it's an audit finding.

**Exercise 7.2.** Take your most-used screen. Write all nine states. Count how many are actually implemented. *In most B2B products the answer is three or four, and the gaps map exactly to your top support ticket categories.*

---

## 7. PM + DESIGNER COLLABORATION

**The anti-pattern: the relay race.** PM writes a PRD → hands to design → design produces mockups → hands to engineering. Every handoff loses context, and the designer is reduced to rendering decisions someone else made without the design knowledge that would have improved them.

**The working model — the trio.** PM, designer, and a senior engineer engage the problem *together*, from discovery. Teresa Torres's continuous-discovery work (E1, practitioner) formalises this as the "product trio." The point isn't the ceremony; it's that the person who knows what's technically cheap is present when the design is chosen, and the person who knows how people behave is present when the problem is framed.

**What good looks like in practice:**
- The designer attends customer interviews, not a summary of them
- The engineer sees the flow before it's finalised and says "that version is three weeks, this version is three days" — while it can still change
- The PM brings constraints early, not as late-stage rejections
- Disagreements are resolved by evidence or by an explicit, documented decision — never by seniority alone

**The single question that fixes most PM–designer friction:** instead of "can you make this screen," ask **"here's the problem, here's who has it, here are the three constraints I know are real — what are our options?"**

---

# PART XV — PRODUCT REQUIREMENTS

## 8. THE REQUIREMENTS TAXONOMY

Most PRDs cover two of these nine categories and get blindsided by the other seven.

| Category | Answers | Who's the source | Commonly missed |
|---|---|---|---|
| **Business** | Why does the company want this? | PM, exec, finance | The success definition |
| **Functional** | What must the system do? | PM, users | — (this is the part everyone writes) |
| **Non-functional** | How well must it do it? | PM + engineering | **Almost always missing or untestable** |
| **Technical** | What architectural constraints apply? | Engineering | Treated as engineering's private business |
| **Data** | What data, from where, retained how long? | PM + eng + legal | Retention, residency, lineage |
| **Analytics** | What must we be able to measure? | PM | Instrumentation as an afterthought |
| **Security** | Who can do what, and how is it protected? | Security + PM | Authorization model, tenancy isolation |
| **Compliance** | What are we legally obliged to do? | Legal + PM | Audit trail, reproducibility, disclosure |
| **Rollout** | How does this reach users safely? | PM | Migration of existing data and users |

### 8.1 Non-functional requirements, made testable

An NFR that can't be verified is a wish. Convert every one into a number with a measurement method.

| Category | Bad (untestable) | Good (testable) |
|---|---|---|
| Performance | "Fast" | p95 page render < 1.5s at 500 clients per firm; p95 calculation < 800ms |
| Scale | "Handles many users" | 3,000 concurrent preparers; 50,000 returns/day at seasonal peak |
| Availability | "Reliable" | 99.9% monthly, excluding announced maintenance; **99.99% during the 6-week filing window** |
| Durability | "Don't lose data" | RPO 5 minutes, RTO 1 hour; verified by quarterly restore test |
| Correctness | "Accurate" | Zero calculation defects escaping to production; measured by shadow-mode divergence rate |
| Security | "Secure" | Tenant isolation verified by automated test; encryption at rest and in transit; annual pen test |
| Compliance | "Auditable" | Every calculation reproducible with the rule version applied, retained 7 years |
| Accessibility | "Accessible" | WCAG 2.2 AA on all new surfaces; keyboard-complete |
| Compatibility | "Works everywhere" | Last 2 versions of Chrome/Edge/Safari/Firefox; named minimum screen width |

**The seasonal availability row is the kind of detail that marks a PM who understands their domain.** A uniform 99.9% target is wrong for a business with a filing deadline: an hour of downtime in July is an inconvenience, and an hour on deadline day is an existential event. Requirements should reflect that asymmetry explicitly.

---

## 9. THE ADVANCED PRD FRAMEWORK

```
═══════════════════════════════════════════════════════════════
PRD — [Name]        Owner: [name]   Status: Draft/Review/Approved
Decision needed by: [date]          Last updated: [date]
═══════════════════════════════════════════════════════════════

1. PROBLEM
   Who has it, in what situation, what does it cost them, how often.
   Evidence (3 sources, each labelled qual/quant/behavioural/commercial).
   ⚑ If this section could describe a competitor's product too, it's too vague.

2. CONTEXT
   Why now. What changed. How this fits the strategy.
   What we already tried and what happened.

3. USERS
   Primary user, secondary users, and the people affected who never log in
   (approver, auditor, client, regulator).
   Explicitly: who is NOT a user of this.

4. GOALS
   Outcome we're trying to move + current baseline + target + how measured.
   Max 3. If there are five goals there is no goal.

5. NON-GOALS
   What this deliberately does not address, and why.
   ⚑ The most useful section in the document. It's what prevents scope drift
     and it's what you point at when someone asks "why doesn't it also…"

6. REQUIREMENTS
   6.1 Functional          — numbered, each with a priority (Must/Should/Could)
   6.2 Non-functional      — with numbers and measurement methods (§8.1)
   6.3 Data                — sources, model changes, retention, residency, lineage
   6.4 Security & permissions — who can do what; tenancy isolation
   6.5 Compliance          — obligations, audit trail, reproducibility, disclosure
   6.6 Analytics           — events, baseline, guardrails (Volume VI §5)

7. EDGE CASES
   Enumerated using the taxonomy in §10. Each with expected behaviour.
   ⚑ "TBD" here is a decision deferred to an engineer at 4pm on a Friday.

8. METRICS
   Primary success metric + baseline + target + window.
   Guardrails that must not degrade.
   How we'll know if we were wrong.

9. RISKS
   Risk → probability → impact → mitigation → trigger → owner.

10. DEPENDENCIES
    Team, what's needed, committed or not, artefact reference, slack, risk if late.

11. ROLLOUT
    Flag strategy, cohorts, migration of existing data/users, comms,
    enablement, support readiness, rollback plan and its trigger.

12. EVALUATION
    How we verify it works before GA and how we monitor after.
    For deterministic logic: test cases and shadow-mode divergence threshold.
    For AI/ML: eval set, metrics, acceptance thresholds, failure taxonomy.
    ⚑ This section is what makes a PRD AI-ready. See Volume IX.

13. OPEN QUESTIONS
    Question → owner → needed by.
═══════════════════════════════════════════════════════════════
```

**Two sections deserve emphasis because they're what elevate this above a standard PRD:**

**Non-goals (5).** This is the requirements-level version of the strategy "we will not" list. It converts a hundred future "why doesn't it also…" conversations into one pointer.

**Evaluation (12).** Most PRDs stop at requirements and assume "QA will test it." Naming, up front, *what evidence will convince us this works* changes what gets built. For your domain it's shadow-mode divergence thresholds; for AI features it's an eval set with acceptance bars. Same structural idea, and it's the bridge between your UAT background and AI product work.

---

## 10. EDGE CASE TAXONOMY

Stop discovering edge cases in UAT. Generate them systematically — run every requirement through these eight lenses.

| Lens | Ask | Tax/CRM/HRMS example |
|---|---|---|
| **Boundary** | Zero, one, maximum, one-over, negative, empty string, null | A firm with 1 client; a firm with 12,000; a return with zero income |
| **State** | What if the object is in an unexpected state? | Editing a return that was filed 30 seconds ago |
| **Concurrency** | Two actors at once | Preparer and reviewer editing the same return; two admins changing the same permission |
| **Permission** | What if the actor lacks rights mid-operation? | User's role is revoked while their bulk operation is running |
| **Data quality** | Malformed, missing, duplicated, wrong-encoding input | Scanned document with a smudged figure; duplicate client records |
| **Temporal** | Time zones, DST, year boundaries, retroactive changes, leap years | A rule change effective mid-year applied to a return started before it; a filing at 23:59 in a different time zone |
| **Scale** | 100× the expected volume | Bulk import of 5,000 clients; a report over 10 years of data |
| **Failure** | A dependency is unavailable or slow | The tax authority's filing endpoint is down at deadline; the document service times out mid-upload |

**The temporal lens is the one that breaks compliance products**, and it deserves a standing question in every PRD you write: *what happens to work in progress when the rules change underneath it?* The answer is never "nothing." It is either "we recalculate and notify," "we pin the version and disclose," or "we block and require review" — and choosing between those is a product decision with legal weight, not a technical detail.

---

## 11. ACCEPTANCE CRITERIA — GHERKIN, USED WELL

Your house standard is Mike Cohn story format with Gherkin acceptance criteria. That's a sound choice. Three refinements that separate good Gherkin from ritual Gherkin:

**1. Write at the behaviour level, not the UI level.**
```
✗  Given I click the "Filing Status" dropdown
   When I select "Married Filing Jointly"
   Then the page reloads

✓  Given a client whose marital status changed during the tax year
   When the preparer sets filing status to "Married Filing Jointly"
   Then the system applies the joint-filing rule set for that tax year
   And flags the return for review with reason "mid-year status change"
```
The first breaks when the dropdown becomes a radio group. The second describes what must remain true regardless of implementation, which is the entire point of an acceptance criterion.

**2. One behaviour per scenario, and use Scenario Outline for data variation.** A scenario with five `And`s in the `When` is testing an entire workflow and will fail ambiguously.

**3. Know when Gherkin is the wrong tool.** It is excellent for discrete, rule-driven behaviour — which is most of your domain. It is poor for: non-functional requirements (write those as numbers), exploratory or visual quality, complex calculation matrices (use a decision table instead, it's far more readable at 40 rows), and AI behaviour where correctness is a distribution rather than an assertion.

**For calculation-heavy requirements, a decision table beats Gherkin outright:**

| Entity type | Residency | Income band | Rule set | Review required |
|---|---|---|---|---|
| Individual | Resident | < threshold A | R-101 | No |
| Individual | Resident | ≥ threshold A | R-102 | No |
| Individual | Non-resident | any | R-140 | Yes |
| Partnership | Resident | any | R-210 | Yes |

Forty rows of this is readable and reviewable by a domain expert. Forty Gherkin scenarios are not, and the domain expert is the person whose review actually catches errors.

---

# PART XVI — EXECUTION EXCELLENCE

## 12. THE THESIS

> **A PM does not manage engineers. A PM manages clarity, alignment, decisions, and outcomes.**

Unpacked into what you're actually accountable for:

| You manage | Meaning | Failure looks like |
|---|---|---|
| **Clarity** | Everyone knows what we're building and why | Engineers making product decisions at 4pm because the spec was silent |
| **Alignment** | Everyone agrees it's worth building | Passive resistance; work that quietly doesn't progress |
| **Decisions** | Open questions get resolved fast, by the right person | A blocked ticket for six days waiting on an answer nobody owned |
| **Outcomes** | The thing that ships moves the metric | Shipped on time, adopted by nobody |

**The corollary that matters for your seniority:** when a sprint fails, the useful question is not "did people work hard enough" — it's *which of those four did I fail to provide?* Almost always it's clarity or decisions, and both are yours.

---

## 13. BACKLOG STRATEGY

Hygiene is keeping the backlog tidy. **Strategy is deciding what the backlog is for.**

**The default failure: the backlog as a landfill.** Every request is added so no one feels dismissed. Within eighteen months it contains 800 items, nobody reads past the top 40, and its only real function is making the team feel guilty. A backlog you can't read isn't a plan; it's an archive.

**A healthy structure:**

| Layer | Horizon | Detail | Size |
|---|---|---|---|
| **Ready** | Next 1–2 sprints | Fully specified, estimated, dependencies cleared | ~2 sprints of capacity |
| **Refined** | This quarter | Problem clear, approach sketched, sized roughly | ~1 quarter |
| **Candidate** | Next quarter | A problem statement, no solution | 20–40 items |
| **Icebox** | Not now | Recorded so it can be found, not maintained | Unbounded, unread, that's fine |

**The discipline is the rule that items expire.** Anything in Candidate for more than two quarters moves to Icebox automatically. If it matters, it'll come back — customers are relentless about the things that genuinely hurt. This one rule keeps the backlog readable, and readable backlogs get used.

**Story mapping** is the tool for structuring work around a user journey rather than a flat list: the backbone is the sequence of activities, and slices beneath it are releasable increments. It's most valuable for a new product or a major workflow change, and largely unnecessary for steady-state feature work on a mature surface.

---

## 14. ESTIMATION — WHAT IT'S ACTUALLY FOR

Estimates are wrong. That's not a defect; it's the nature of estimating novel work. The mistake is expecting them to be right rather than using them for what they're good at.

**Three legitimate uses:**
1. **Relative sequencing** — is this bigger than that?
2. **Capacity sanity check** — can 12 things plausibly fit in a sprint?
3. **Risk detection** ← the most valuable and least used

**Estimation as a risk detector:** when three engineers independently estimate 2, 5, and 13, the useful output is not the average. **It's the disagreement**, which means they're imagining different problems. Ten minutes spent on "what are you seeing that I'm not?" surfaces a hidden dependency or an unstated assumption more reliably than any planning ritual. Wide spread is a signal to talk, not to average.

**What estimates are not for:** performance measurement, commitments to customers, or comparing teams. Any of those turns estimates into negotiations, and estimates that are negotiated stop carrying information.

**On #NoEstimates:** the position that teams should slice work small and count throughput instead of estimating is a legitimate **opinion** with real supporting practice — not a standard, and not universally applicable. It works well for steady-state teams with consistent work types. It works poorly when you owe an external party a date, which in enterprise B2B is often.

**The forecasting alternative worth knowing:** for a team with history, throughput-based forecasting (how many items did we complete in the last ten sprints, what's the distribution) predicts delivery dates better than summed estimates, because it incorporates the interrupts and rework that estimates systematically exclude. If you have six months of consistent data, use it.

---

## 15. TECHNICAL DEBT — HOW TO FUND IT

The standard taxonomy is Martin Fowler's quadrant (E1, published):

| | **Reckless** | **Prudent** |
|---|---|---|
| **Deliberate** | "We don't have time for design" | "We ship now and deal with consequences" ← legitimate |
| **Inadvertent** | "What's layering?" | "Now we know how we should have done it" ← unavoidable |

**Why this matters practically:** only the reckless quadrants indicate a process problem. Prudent-deliberate debt is a *decision*, and decisions can be tracked, priced, and repaid on purpose. Prudent-inadvertent debt is what learning looks like and shouldn't be treated as failure.

**Getting debt funded — three approaches, in order of effectiveness:**

1. **Allocation, not justification** (best). Health work gets 15–25% of capacity as a standing agreement (Volume V §4). No per-item ROI argument required, because per-item ROI arguments for debt always lose.
2. **Attach it to adjacent feature work.** "This feature is 3 weeks on the current structure or 5 weeks including the refactor, and every subsequent feature in this area is 40% faster." This is honest and it works, but it only pays down debt where features happen to land.
3. **Cost of Delay in business terms** (for large items). "This migration is 8 engineer-weeks. Without it, each regulation update costs 3 extra weeks, four times a year." That's a payback calculation an exec can act on.

**What doesn't work:** describing debt in engineering vocabulary to a business audience. "We need to refactor the persistence layer" gets deferred forever. "Every rule change currently costs us three weeks and it should cost three days" gets funded — and it's the same project.

**The register.** Maintain a technical debt register with: what it is, business consequence, cost to fix, cost of not fixing per quarter, and trigger (the event that makes it urgent). Reviewed quarterly with your tech lead. This is a genuinely senior artefact and few PMs maintain one.

---

## 16. QA AND UAT AS DECISION PROCESSES

This is your existing strength. Here's how to frame it at a senior level.

**The reframe: testing is not a phase that confirms correctness. It is an evidence-generating process that supports a release decision.** The question is never "did we test it" but **"do we have enough evidence to accept the risk of releasing?"**

| Level | Question answered | Owner | PM's role |
|---|---|---|---|
| Unit | Does this function behave? | Engineering | None |
| Integration | Do components work together? | Engineering | Flag cross-system risk |
| End-to-end | Does the workflow complete? | Eng + QA | Define the critical journeys |
| **UAT** | **Does it solve the user's problem in their reality?** | **PM + real users** | **Own it** |
| Regression | Did we break something existing? | Automation | Own the priority of what's covered |
| Shadow / parallel run | Does new logic match expected outputs at population scale? | Eng + PM | Own the divergence threshold |
| Performance | Does it hold at peak? | Eng | Own the peak definition |

**Three things that make UAT a decision process rather than theatre:**

1. **Acceptance criteria defined before the build**, not negotiated during UAT. UAT that discovers requirements is a requirements failure surfacing late and expensively.
2. **Real users with real data and real tasks.** UAT run by the internal team who built it validates that it works as they imagined it.
3. **A written exit decision.** "Accepted with 3 known issues, tracked as X/Y/Z, deferred because [reason], owned by [name], due [date]." Not a thumbs-up in a meeting.

**Your commission-engine UAT work — 211 cases, a Python validator, a real defect found — is a strong senior artefact, and the way to tell it is as a decision process, not a test count.** The number of cases is the least interesting fact. The interesting facts are: how you chose the coverage, what risk model drove it, what threshold would have blocked the release, and what the defect would have cost undetected. That framing converts "detail-oriented" into "owns release risk," and it's the same structure as an AI evaluation harness (Volume IX).

---

## 17. RELEASE, CHANGE, AND INTERRUPTS

### 17.1 Change management is a product responsibility

Shipping a change to enterprise users without preparation generates support load, erodes trust, and can breach contracts that specify notice periods for material changes.

Minimum standard for any user-visible change in B2B:

| Change type | Notice | Required |
|---|---|---|
| Bug fix, no behaviour change | None | Release note |
| New optional feature | Release note | Enablement material |
| Changed existing workflow | 2–4 weeks | Comms, updated docs, CS briefing, opt-in period if possible |
| Removed feature | 1–2 quarters | Direct outreach to users of it, migration path, exec sign-off |
| Pricing/packaging | Per contract | Legal review, account-by-account plan |
| **Anything during filing season** | **Don't** | If unavoidable: exec sign-off and hypercare staffing |

**That last row is a real policy, not a joke.** A change freeze during your customers' peak is one of the highest-trust, lowest-cost commitments a compliance vendor can make, and it's the kind of operating decision a Senior PM proposes.

### 17.2 Interrupt management

Unplanned work is the largest silent destroyer of roadmaps, and most teams don't measure it.

**Measure it first:** for one month, tag every item as planned or unplanned. Compute the percentage. Teams routinely discover 30–50% and are genuinely surprised, because unplanned work is invisible in the sprint plan by definition.

**Then manage it structurally:**
- **Reserve capacity** for interrupts rather than pretending they won't happen — a plan at 100% of capacity is a plan that fails at the first escalation.
- **Rotate a designated responder** so interrupts hit one person instead of fragmenting the whole team. Focused work is destroyed by context switching far more than by hours lost.
- **Categorise the source.** If 60% of interrupts trace to one subsystem, you've found a health problem masquerading as a process problem — and now you have the data to fund fixing it.

---

## 18. EXECUTION HEALTH DIAGNOSTICS

| Symptom | Usually means | Not usually |
|---|---|---|
| Stories bounce back from QA repeatedly | Acceptance criteria are ambiguous | Engineers are careless |
| Sprints consistently overcommit | Interrupts aren't reserved for | Team is slow |
| Engineers ask many questions late | The PRD deferred decisions | Engineers won't read |
| Scope grows mid-sprint | Non-goals weren't written | Stakeholders are unreasonable |
| Estimates vary wildly | People are imagining different problems | Estimation skill |
| Shipped features aren't adopted | Discovery gap | Marketing gap |
| Everything is urgent | No strategy to arbitrate with | Poor prioritisation technique |
| Dependencies always slip | Verbal commitments, not tracked artefacts | Other teams are unreliable |

**The pattern across the whole table: most execution problems are upstream problems presenting downstream.** That's the diagnostic instinct to build — when execution hurts, look at clarity and decisions first, process second.

---

## 19. VOLUME VII EXERCISES & INTERVIEW BANK

**Exercise 7.3 — The state machine.** Model your core workflow object's states, transitions, owners, permissions, and backward paths. Overlay dwell-time data. *Deliverable: the design artefact and bottleneck evidence in one page.*

**Exercise 7.4 — Rewrite a PRD.** Take a PRD you wrote and restructure it into the §9 framework. The Non-goals and Evaluation sections will be the hardest and most valuable. *Portfolio artefact.*

**Exercise 7.5 — Edge case sweep.** Run one requirement through all eight lenses in §10. Count new cases found. *Most people find 8–15 they'd have discovered in UAT.*

**Exercise 7.6 — NFR conversion.** Take five untestable NFRs from your current docs and convert them to numbers with measurement methods.

**Exercise 7.7 — Debt register.** Build the §15 register with your tech lead: consequence, cost to fix, cost of not fixing per quarter, trigger. *Deliverable: a fundable proposal instead of a complaint.*

**Exercise 7.8 — Interrupt audit.** Tag one month of work as planned/unplanned and categorise the sources.

**Interview questions**
1. How do you work with designers? Where does your responsibility end?
2. What's in your PRD that most PRDs don't have?
3. How do you find edge cases before QA does?
4. Engineering says six months. What are your next three questions?
5. How do you get technical debt prioritized?
6. What's a non-functional requirement you've owned, and how was it verified?
7. A sprint failed. How do you diagnose it?
8. How do you decide a feature is ready to release?
9. What do you do when acceptance criteria are disputed during UAT?
10. How do you roll out a workflow change to enterprise customers?

---

*Volume VII complete. Continue to `08-technical-and-platform-pm.md`.*
