# VOLUME XI — GTM, LAUNCH, GROWTH, B2B & QUALITY
### Parts XXVI, XXVII, XXVIII, XXIX, XXX & XXXI

> Shipping is the midpoint of the work, not the end of it. This volume covers everything between "the code is merged" and "the business is better."

---

# PART XXVI — GO-TO-MARKET

## 1. WHAT THE PM OWNS

In companies with a Product Marketing function, GTM is a partnership. In companies without one — which includes most mid-market B2B SaaS, likely including yours — **the PM owns it by default**, and the most common failure is not owning it badly but not realising you own it at all.

| Area | PM owns | PMM owns (or PM absorbs) |
|---|---|---|
| Target segment definition | ✅ | Refines with market data |
| Value proposition | ✅ (the substance) | The articulation |
| Positioning | Jointly | Jointly |
| Pricing & packaging | ✅ (the model) | Price points, competitive check |
| Messaging & naming | Input | ✅ |
| Sales enablement content | Input on substance | ✅ |
| Launch plan | ✅ | Campaign execution |
| Competitive intelligence | Structural view | Battlecards |
| Analyst/press | — | ✅ |
| Post-launch adoption | ✅ | Demand generation |

**The line that matters:** the PM owns *what is true* about the product and who it's for. Marketing owns *how it's said*. When a PM lets marketing invent the "who," you get campaigns aimed at a segment the product doesn't serve, and the resulting churn looks like a product failure.

---

## 2. ICP — AND WHY IT'S NOT A PERSONA

Three distinct concepts, routinely conflated:

| Concept | Unit | Answers | Used by |
|---|---|---|---|
| **Segment** | A group of accounts | How the market divides | Strategy |
| **ICP (Ideal Customer Profile)** | An *account* | Which accounts should we pursue? | Sales, marketing |
| **Persona** | A *person* | Who inside the account do we design and sell for? | Product, design, messaging |

**A useful ICP is a filter, not a description.** It must be applicable to a list of companies without asking them anything:

```
ICP — mid-market tax & compliance
  Firm size:            20–200 returns per preparer per season, 5–40 preparers
  Complexity:           handles multi-entity or cross-jurisdiction clients
  Current state:        using a paid competitor or an Excel-heavy manual process
  Tech posture:         has someone responsible for IT; will accept cloud
  Trigger events:       partner change, new jurisdiction, audit event, a bad season
  Disqualifiers:        single-jurisdiction simple returns only (we're overkill;
                        they'll churn on price); firms requiring on-prem deployment
```

**The disqualifiers line is what makes it useful and it's the line everyone omits.** An ICP with no exclusions doesn't help sales qualify out, which means your team spends its expensive time on deals that would churn anyway. **Bad-fit customers cost more than no customers**: they consume support, demand roadmap concessions, churn at renewal, and give bad references.

**Validate the ICP against your own data, don't invent it.** Take your best cohort — highest NRR, lowest support cost, best references — and describe what they have in common. Then take your worst churn cohort and do the same. The delta is your real ICP and your real disqualifier list. Almost nobody does this exercise, and it takes a day.

---

## 3. GTM MOTIONS AND WHEN EACH FITS

| Motion | ACV range (directional) | Requires | Product implication |
|---|---|---|---|
| **Self-serve / PLG** | < ~$5k | Instant value, no implementation, transparent pricing | Onboarding *is* the sales team; free tier or trial design is product work |
| **Inside sales** | ~$5k–50k | Demo, short trial, light implementation | Trial environments, sandbox data, admin setup that a rep can do live |
| **Field / enterprise sales** | > ~$50k | Pilots, security review, procurement, implementation | Configuration, SSO, audit, migration tooling, contractual SLAs |
| **Partner / channel** | Varies | Partner economics, certification, co-selling | Multi-tenant partner administration; white-label considerations |

**The mismatch failure is the common one:** a $9k ACV product sold with a field-sales motion loses money on every deal because CAC exceeds what the account can ever return. **A GTM motion is a product decision** — if the strategy says a segment must be low-touch, the product must be self-serve, and that determines a year of roadmap.

**This is the Volume III worked strategy in operational form.** "Serve mid-market with a deliberately narrower, self-serve, low-touch product" is a GTM motion choice that implies specific product work: self-service onboarding, in-product configuration, migration tooling, and deflection of support into documentation.

---

## 4. SALES ENABLEMENT — WHAT SALES ACTUALLY NEEDS

PMs habitually give sales a feature list. Sales needs five things, and none of them is a feature list:

1. **Who to sell it to** — the ICP filter and, critically, the disqualifiers
2. **The problem language** — the words the buyer uses, not your internal terminology
3. **The three objections and the honest answers**, including "we don't do that, here's what we do instead"
4. **A demo path** — the specific 8-minute sequence that lands, with a prepared dataset
5. **Proof** — a reference customer, a number, a certification

**The most underrated of these is #3.** Sales reps encounter the same objections repeatedly and improvise answers when unequipped — which is how a rep ends up promising a feature that doesn't exist. **Giving them an honest "no, and here's why that's the right trade-off" prevents more roadmap damage than any prioritisation framework.**

**The feedback loop is the other half.** Sales sits on the highest-volume market signal in the company and it evaporates unless captured structurally: a required loss-reason field with a controlled vocabulary, ten minutes in the sales weekly for you to ask "what did you hear," and quarterly win/loss interviews run by someone who isn't the account owner.

---

# PART XXVII — PRODUCT LAUNCH & RELEASE

## 5. RELEASE ≠ LAUNCH

The single most useful decoupling in modern product delivery.

- **Release** — the code is in production. A technical event.
- **Launch** — the market is told. A commercial event.

Separating them lets you deploy continuously, turn features on for cohorts, validate with real users, and announce only when you're confident. Coupling them means every announcement is also your first production test, which is how launch-day incidents happen.

**The mechanism is feature flags**, and the associated product decisions are yours:

| Rollout technique | What it is | Use for |
|---|---|---|
| **Dark launch** | Deployed, off for everyone | De-risking the deploy itself |
| **Internal / dogfood** | On for employees | Catching the obvious |
| **Canary** | On for a small % of traffic | Detecting errors and performance regressions |
| **Ring deployment** | Concentric cohorts: internal → friendlies → early → general | **The default for B2B** |
| **Cohort targeting** | On for specific accounts | Design partners, pilots, contractual sequencing |
| **Percentage rollout with holdout** | X% get it; a holdout doesn't, for measurement | Causal measurement without a formal A/B test (Volume VI §8.2) |

**Flag hygiene is a real cost.** Flags left in the codebase indefinitely become permanent conditional complexity and a source of "it works for that customer but not this one" bugs. Every flag needs an owner and a removal date at creation. This belongs in your rollout requirements section.

---

## 6. LAUNCH TIERS

Not everything deserves a launch. Tiering prevents both over-announcing minor changes and under-preparing major ones.

| Tier | What it is | Required |
|---|---|---|
| **T3 — Ship** | Bug fixes, minor improvements | Release note. Nothing else |
| **T2 — Announce** | New capability within an existing surface | Release note, in-app notice, docs, CS briefing, enablement one-pager |
| **T1 — Launch** | New product, major capability, pricing change | Everything in T2 plus: readiness review, phased rollout, sales enablement session, migration plan, hypercare, exec sign-off, post-launch review |

**Decide the tier at PRD time, not two weeks before shipping.** Tier determines lead time: a T1 launch needs 6–8 weeks of parallel non-engineering work, and discovering that late is how launches slip for reasons that have nothing to do with the code.

---

## 7. THE LAUNCH READINESS FRAMEWORK

```
═══════════════════════════════════════════════════════════════
LAUNCH READINESS — [Feature]   Tier: T1/T2/T3   Target: [date]
Decision: GO / GO WITH CONDITIONS / NO-GO        Owner: [name]
═══════════════════════════════════════════════════════════════

PRODUCT
  ☐ Acceptance criteria met; UAT accepted with known issues documented
  ☐ Edge cases from the taxonomy addressed or consciously deferred
  ☐ Empty / error / permission / degraded states implemented (Vol VII §6)
  ☐ Accessibility conformance for new surfaces
  ☐ Feature flag exists, tested off and on, with a named owner

ENGINEERING
  ☐ Performance verified at projected peak (not average)
  ☐ Monitoring and alerting in place for the new paths
  ☐ Error budget / correctness budget headroom available
  ☐ Rollback tested — not just "possible," actually exercised
  ☐ Load and dependency risks assessed (including third parties)

DATA & ANALYTICS
  ☐ Events instrumented AND verified firing correctly in staging
  ☐ Baseline recorded, with normal variance (Vol VI §5)
  ☐ Success metric, target, and review date agreed
  ☐ Guardrail metrics defined with alert thresholds

SUPPORT & SUCCESS
  ☐ Support team trained; internal FAQ published
  ☐ Known issues documented with workarounds
  ☐ Escalation path defined for launch-related issues
  ☐ Capacity assessed for expected ticket volume

SALES & MARKETING
  ☐ Positioning and messaging agreed
  ☐ Enablement delivered (session, not just a document)
  ☐ Objection handling including honest "we don't do X"
  ☐ Demo environment and script ready

LEGAL / COMPLIANCE / SECURITY
  ☐ Data handling reviewed; DPA/sub-processor updates if needed
  ☐ Terms or disclosures updated if behaviour changes
  ☐ Regulatory implications assessed and signed off
  ☐ Security review complete for new external surfaces

CUSTOMER READINESS  (B2B-specific, frequently skipped)
  ☐ Migration plan for existing data and users
  ☐ Notice period honoured for workflow changes
  ☐ Named-account outreach for anyone materially affected
  ☐ Documentation and in-product guidance updated
  ☐ Not launching during customers' peak season

DECISION
  Go / no-go criteria stated in advance
  Rollback triggers: [specific, observable — not "if it goes badly"]
  Hypercare: [who, hours, duration]
  Post-launch review: [date, already in calendars]
═══════════════════════════════════════════════════════════════
```

**Two lines carry disproportionate weight.** *"Rollback tested, actually exercised"* — an untested rollback is a hope, and you discover it doesn't work at the worst possible moment. *"Rollback triggers, specific and observable"* — decided calmly in advance, because in the middle of an incident nobody is capable of deciding whether things are bad enough.

## 8. HYPERCARE AND THE POST-LAUNCH REVIEW

**Hypercare** is a defined period of elevated attention: named people, defined hours, a dedicated channel, and a daily check on the guardrail metrics. Typically 1–2 weeks for T1. **It needs an explicit end date** or it decays into ordinary support and nobody notices when it ended.

**The post-launch review is the step almost universally skipped**, and skipping it is why organisations don't learn.

```
POST-LAUNCH REVIEW — 30 days after launch
  1. What we predicted (pull the written prediction — Vol I §3.8)
  2. What happened (the actual numbers)
  3. Where we were wrong, and what we now believe instead
  4. What surprised us
  5. What we'd do differently in the process
  6. Decision: double down / adjust / stop
```

**Item 6 is the one with teeth.** Most features are shipped and then simply exist forever, consuming maintenance regardless of whether anyone uses them. A launch that missed its target by an order of magnitude should trigger a real conversation about removal — and having that conversation once makes it possible to have it again.

---

# PART XXVIII — GROWTH PRODUCT MANAGEMENT

## 9. AARRR AND ITS LIMITS

The pirate metrics framework — Acquisition, Activation, Retention, Referral, Revenue — is a **useful diagnostic checklist** and a poor model of how B2B actually grows.

**Where it breaks in B2B:**
- Acquisition is largely sales-driven, not product-driven
- Activation happens at *two* levels — the account (implemented, configured, rolled out) and the user (personally productive) — and they can diverge completely
- Referral works through professional networks and references, not in-product sharing
- Revenue is decoupled from usage by annual contracts, so the funnel's final step lags everything by up to a year

**The B2B reframe:** growth is **retention plus expansion**, with acquisition as a support function. At 120% NRR you grow 20% annually with zero new customers. At 90% you must acquire aggressively to stand still. **Which means the highest-leverage "growth" work in B2B is usually activation, adoption depth, and seat utilisation — all of which look like core product work rather than growth work.**

## 10. LOOPS BEAT FUNNELS

A funnel is linear and needs constant refilling. A loop compounds: an output becomes an input.

**Loops that genuinely work in B2B:**

| Loop | Mechanism | Product work required |
|---|---|---|
| **Land-and-expand** | One team succeeds → adjacent teams adopt → account grows | Easy in-account expansion; per-team onboarding; visible cross-team value |
| **Integration loop** | Customer integrates you → switching cost rises → your data becomes their system of record → more integrations | API quality, connector breadth, being the hub |
| **Multi-sided / client-facing** | Your customer's clients touch your product → they experience it → some become customers | Client portal quality; tasteful branding |
| **Content/SEO from product data** | Aggregate anonymised insight → published benchmarks → inbound | Data pipeline, legal clearance for aggregate use |
| **Professional network referral** | Preparer moves firms → advocates for your product | Individual attachment, not just account attachment |
| **Marketplace/ecosystem** | Third parties build on you → more reasons to stay | Platform work (Volume VIII) |

**The professional-network loop is under-exploited in vertical B2B.** In accounting, tax, and HR, practitioners move between firms and carry tool preferences with them. Designing for *individual* attachment — personal settings that follow the user, a free personal tier, community, certification — turns staff turnover from a churn risk into a distribution channel.

## 11. ACTIVATION — THE HIGHEST-LEVERAGE GROWTH SURFACE

**Two-level activation in B2B, and both must be designed:**

| Level | Definition | Fails when |
|---|---|---|
| **Account activation** | Configured, data migrated, users provisioned, first real work completed | Implementation drags; the champion leaves mid-rollout |
| **User activation** | This individual completed a real task and got value | Rolled out to 40 seats, 12 people ever log in |

**Account activation without user activation is the single most common cause of B2B contraction** — it's the pattern behind low seat utilisation (Volume VI §3.1), and it surfaces as a smaller renewal 12 months later.

**Design principles that hold:**
- **Time-to-first-value is the metric.** Every step between signup and first real outcome is a place to lose them
- **Reduce setup, don't explain it.** Import their data, provide templates, infer configuration from what you can see. A tour is a workaround for a setup problem
- **Make the first success real.** A demo dataset teaches the UI; their own data teaches the value
- **Design for the rollout, not just the first user.** The champion must be able to onboard their team without you — which means invitation flows, role templates, and shareable setup

---

# PART XXIX — B2B PRODUCT MANAGEMENT

## 12. THE BUYING COMMITTEE

Already introduced in Volume I §3.4. The operational consequences:

| Role | Kills the deal by | Product implication |
|---|---|---|
| Economic buyer | Not funding it | ROI evidence, TCO clarity |
| Champion | Losing internal credibility | Give them a win they can show, early |
| End user | Refusing to adopt | Usability, migration, keyboard parity |
| IT / security | Failing the review | SSO, audit logs, certifications, data residency |
| Legal / procurement | Contract terms | DPA, SLA, liability, data portability |
| Finance | Payment terms, budget cycle | Billing flexibility, annual invoicing |

**The champion's problem is the one PMs most consistently ignore.** Your champion has staked internal credibility on you. If your rollout is messy, *they* look bad. Designing for the champion's success — a fast visible win, materials they can present internally, a dashboard showing adoption progress — is a product decision that materially affects renewal, and it appears nowhere in most PRDs.

## 13. PROCUREMENT & SECURITY REVIEW — PRODUCT REQUIREMENTS IN DISGUISE

For enterprise deals, this is where product gaps become lost revenue. **The security questionnaire is a requirements document that your prospects wrote for you**, and you should treat it that way: collect every questionnaire you've received, tabulate the questions you answered badly, and prioritise the recurring ones.

Common blockers, all of which are product work:

| Blocker | What it means |
|---|---|
| SSO / SAML / SCIM | Table stakes above a certain size. Not optional |
| SOC 2 Type II / ISO 27001 | A certification with a real audit cost and a 6–12 month lead time |
| Penetration test report | Annual, third-party |
| Data residency | Where data is stored and processed. Can gate entire markets |
| DPA and sub-processor list | Every vendor in your stack, disclosed |
| Audit logs, exportable | Who did what, retrievable by the customer |
| Data portability / exit | What they get when they leave. Increasingly contractual |
| RBAC granularity | Their org structure must be expressible |
| Uptime SLA with credits | A contractual commitment tied to your SLO |
| Business continuity / DR | RPO and RTO, documented and tested |

**Plan the certification lead time.** SOC 2 Type II requires an observation period — typically 3–12 months. A PM who realises in Q3 that a Q4 enterprise push requires a certification that takes nine months has lost a year. **Put certifications on the roadmap as capability items with dates.**

## 14. CONFIGURATION vs CUSTOMISATION — THE MOST IMPORTANT B2B PRODUCT LINE

| | Configuration | Customisation |
|---|---|---|
| What | Customer changes settings within designed bounds | Code or behaviour built for one customer |
| Cost | Built once, used by all | Maintained forever, tested forever, blocks upgrades |
| Scales | Yes | No |
| Sales pressure | Moderate | **Intense, especially from large deals** |

**The rule: say yes to configuration, almost always no to customisation.** Each customisation is a permanent tax — it must be regressed on every release, it constrains refactoring, and it creates a customer who cannot be upgraded.

**The professional response to a customisation request:** *"What outcome do you need? Let me see whether we can express that as configuration that other customers would also use."* Roughly 70% of customisation requests are configuration requests in disguise, and the remaining 30% split into things that should be on the roadmap for everyone and things that should be a firm no.

**When customisation is genuinely justified:** a deal large enough that the lifetime maintenance cost is clearly worth it, *modelled explicitly and signed off by someone who owns the P&L*, with a defined sunset plan for folding it into the core product. Write the maintenance cost down. It's usually 3–5× the build.

## 15. THE ONE-BIG-CUSTOMER PROBLEM

When one account is a large share of revenue, their roadmap becomes your roadmap by gravity, not by decision. Symptoms: quarterly plans reshaped by one QBR; a growing "special handling" list; engineers who know which customer each conditional branch is for.

**Countermeasures:** track the percentage of capacity consumed by your top account and report it; require that anything built for them is expressed as general capability; and be explicit at the exec level that concentration is a strategic risk, not just a commercial one. **Naming it is the PM's job** — nobody else in the company has both the visibility and the incentive to say it.

---

# PART XXX — PRODUCT STRATEGY FOR SaaS

## 16. LAND AND EXPAND

```
LAND                   EXPAND                       DEEPEN
Small, fast, low-risk   More seats, teams, products   More critical workflows
entry point             within the account            = harder to remove

Product requirements at each stage:
LAND     Fast time-to-value; minimal implementation; low commitment
EXPAND   Easy in-account addition; visible value to adjacent teams;
         admin tooling that scales; per-team onboarding
DEEPEN   Integration depth; system-of-record status; historical data accumulation
```

**The expansion motion must be designed into the product, not bolted onto sales.** If adding a second team requires a services engagement, expansion is throttled by capacity. If it requires an admin to click "invite team" and select a role template, expansion is throttled by nothing.

## 17. THE PACKAGING DECISIONS THAT MATTER

Building on Volume V §10:

| Decision | The question | Common error |
|---|---|---|
| **Value metric** | What do we charge for? | Choosing a metric that scales with value but not with cost (fatal once AI is in the product) |
| **Tier boundaries** | What separates good/better/best? | Splitting by feature count instead of segment need |
| **What's always included** | What never sits behind a tier? | Putting security, audit, or reliability up-tier in a compliance product — a procurement disaster |
| **Expansion mechanic** | How does revenue grow with usage? | No mechanic at all — flat price regardless of value delivered |
| **Migration path** | How do existing customers move? | Grandfathering forever, creating unmaintainable legacy plans |

**The single most consequential packaging error in vertical B2B is a value metric that doesn't scale with cost to serve.** You discover it when your largest, happiest, most reference-able customers turn out to be your least profitable.

---

# PART XXXI — PRODUCT QUALITY

## 18. "SHIPPED ≠ DONE"

A feature is done when it is **adopted, reliable, supported, and delivering the outcome.** Shipping is roughly the halfway point, and treating it as the finish line is the mechanical cause of the feature factory.

**Redefine done in your team's working agreement:**

```
DEFINITION OF DONE
  ☐ Acceptance criteria met
  ☐ Edge and error states handled
  ☐ Instrumented and events verified
  ☐ Documented (user-facing and internal)
  ☐ Support briefed
  ☐ Rolled out to the target cohort
  ☐ Adoption reviewed at 30 days against the prediction
  ☐ Flag removed or a removal date set
```

The last two are what change behaviour. **A team that must review adoption at 30 days starts caring about adoption at design time.**

## 19. THE QUALITY DIMENSIONS

| Dimension | Measured by | Who notices when it's bad |
|---|---|---|
| **Functional correctness** | Defect escape rate; in your domain, calculation defects | Everyone, eventually and expensively |
| **UX quality** | Task success, time-on-task, error rate, support contacts | Users daily; buyers at renewal |
| **Technical quality** | Change failure rate, cycle time, incident rate | Engineering, then everyone |
| **Reliability** | SLO attainment, incident frequency and duration | Customers immediately |
| **Performance** | p95/p99 latency at real data volumes | **Your largest customers first** |
| **Security** | Vulnerabilities, time-to-patch, audit findings | Once. Catastrophically |
| **Accessibility** | WCAG conformance | Procurement, before you meet them |
| **Data quality** | Completeness, accuracy, timeliness, consistency, lineage | Anyone who reports on it |

### 19.1 Data quality deserves its own treatment

Under-covered in general PM material, and central to reporting, compliance, and AI products.

| Dimension | Question | Failure in your domain |
|---|---|---|
| **Completeness** | Are required values present? | A report silently excludes records with a null field |
| **Accuracy** | Do values match reality? | An imported client record with a transposed identifier |
| **Consistency** | Do systems agree? | CRM and tax product disagree on the client's entity type |
| **Timeliness** | Is it current enough for the decision? | A dashboard showing data as of last night, presented as live |
| **Uniqueness** | Any duplicates? | The same client entered twice; both get filings |
| **Lineage** | Where did this come from and what transformed it? | A figure in an audit that nobody can trace to a source |
| **Validity** | Does it conform to the rules? | A date outside the permitted tax year |

**The most damaging data quality failure is silent partial data.** A report that shows 847 of 900 records with no indication that 53 were dropped is worse than one that fails, because someone will make a decision on it. **Any aggregate view should state its denominator and flag exclusions** — that is a product requirement, and it belongs in your PRD template.

## 20. QUALITY AS A BUDGET, NOT A VIRTUE

Quality loses every argument framed as "quality vs speed," because speed has a date attached and quality doesn't. Reframe it as a **budget agreed in advance** — the mechanism from Volume IV §2:

```
CORRECTNESS BUDGET  (adapted from Google's error budget model, E1)
  Metric:      calculation defects escaping to production per quarter
  Budget:      [N] — agreed by product and engineering
  Measurement: shadow-mode divergence + customer-reported + internal detection
  Consequence: budget exhausted → feature work pauses; the next sprint is
               correctness work until the budget is restored
  Review:      monthly; the budget itself is reset quarterly as a deliberate choice
```

**Why it works:** it converts an unwinnable values argument into an arithmetic rule that both sides agreed to when nobody was under pressure. Everything else about quality follows from having that agreement.

---

## 21. VOLUME XI EXERCISES

**Exercise 11.1 — ICP from your own data.** Describe your best cohort (highest NRR, lowest support cost) and your worst churn cohort. Write the ICP and, more importantly, the disqualifier list. *Deliverable: a filter sales can apply to a list of companies.*

**Exercise 11.2 — Security questionnaire audit.** Collect the last ten questionnaires you've received. Tabulate every question you answered badly or with a workaround. *Deliverable: an enterprise-readiness roadmap written by your prospects.*

**Exercise 11.3 — Launch readiness dry run.** Take your last significant launch and score it retrospectively against §7. *Deliverable: the specific gaps that caused your last messy launch.*

**Exercise 11.4 — Two-level activation.** Measure account activation and user activation separately. Find accounts that activated at the account level and failed at the user level. *Deliverable: your contraction pipeline, visible 12 months early.*

**Exercise 11.5 — Customisation inventory.** List every customer-specific behaviour in your product. Estimate the per-release testing cost. *Deliverable: a number that will change how the next customisation request is answered.*

**Exercise 11.6 — Correctness budget proposal.** One page, using §20. *Deliverable: a mechanism that ends the quality argument permanently.*

**Exercise 11.7 — Post-launch review.** Run one, properly, on something that shipped 30+ days ago, including the "double down / adjust / stop" decision. *Deliverable: possibly your first deliberate feature removal.*

---

## 22. VOLUME XI INTERVIEW BANK

1. Who is your ICP, and who do you deliberately disqualify?
2. How do you decide whether a feature needs a launch?
3. Walk me through your launch readiness process.
4. What are your rollback criteria, and who decides?
5. How would you grow a B2B product that isn't acquisition-constrained?
6. What's the difference between account activation and user activation?
7. A $500k customer demands a customisation. Walk me through the conversation.
8. How do you handle enterprise security review requirements on a roadmap?
9. What does "done" mean on your team?
10. How do you get quality prioritized when there's a hard deadline?
11. Your biggest customer's requests are consuming 40% of capacity. What do you do?
12. How would you measure the quality of a reporting product?

---

*Volume XI complete. Continue to `12-metrics-masterclass.md`.*
