# VOLUME VIII — TECHNICAL & PLATFORM PRODUCT MANAGEMENT
### Parts XVII & XVIII

> You are not being asked to write the code. You are being asked to know what makes a change expensive, what makes a system fragile, and what a contract commits you to for the next five years.

**This volume serves your TPM and Platform PM targets directly.** Much of your existing work — API integrations, workflow engines, shared services across CRM/HRMS/tax, rule versioning — is already platform work. What's usually missing isn't the experience; it's the vocabulary to name it as such and the frameworks to reason about it in interviews.

---

# PART XVII — TECHNICAL PRODUCT MANAGEMENT

## 1. THE LINE: WHAT A PM MUST KNOW vs WHAT AN ENGINEER MUST KNOW

| Topic | PM must know | Engineer must know |
|---|---|---|
| **APIs** | What the contract promises, who depends on it, what breaks consumers, versioning cost | Implementation, framework, performance tuning |
| **Data model** | What entities exist, their relationships, what the model *cannot* express | Schema design, indexing strategy, query plans |
| **Migrations** | That they're expensive and risky, why they can't be rushed, what the rollback story is | How to execute them safely |
| **Caching** | That stale data is a product decision with user consequences | Invalidation strategy, cache topology |
| **Queues / async** | That "it happened" and "the user sees it" are different moments | Broker choice, delivery guarantees, DLQ handling |
| **Microservices** | The coordination cost and the failure-mode change | Service boundaries, mesh, deployment |
| **Security** | The authorization model, tenancy isolation, what data classification applies | Implementation, crypto, hardening |
| **Observability** | What questions you'll need to answer in production, and whether you can | Instrumentation, tooling, alerting |
| **Scalability** | Where the cliff is, what the peak looks like, what degrades first | How to move the cliff |
| **AI/ML** | Capability boundaries, evaluation, cost per call, failure behaviour | Model architecture, training, serving |

**The test isn't recall. It's whether you can ask the second question.**

> Engineer: *"That's a big change."*
> Weak PM: *"How long?"*
> Strong PM: *"Is it big because of the data model, the coupling, the migration, or the test surface?"*

Those four have completely different mitigations:

| Reason it's expensive | What it means | Your move |
|---|---|---|
| **Data model** | The schema can't express the concept | Can we model it alongside and migrate later? Is a narrower version expressible today? |
| **Coupling** | Many things depend on this code path | Can we add rather than change? Feature-flag the new path? |
| **Migration** | Existing data must be transformed | Can we run both models concurrently? Migrate lazily on access? |
| **Test surface** | It touches many behaviours that must stay correct | Can we narrow the blast radius? Is shadow mode viable? |

**Learn those four sentences.** Asking that question once in an interview does more for your technical credibility than reciting a systems-design glossary.

---

## 2. APIS AND CONTRACTS

### 2.1 The mental model

**An API is a promise you cannot easily withdraw.** Once a customer integrates, that contract is part of your product surface, and breaking it breaks their business — which is why API design is a product decision, not an implementation detail.

| Style | Shape | Good for | Cost |
|---|---|---|---|
| **REST** | Resources + HTTP verbs | Broad compatibility, caching, simplicity | Over/under-fetching; many round trips |
| **GraphQL** | Client specifies the shape | Complex nested reads, varied clients | Server complexity; caching is harder; easy to write expensive queries |
| **Webhooks** | You push events to them | Real-time notification without polling | Delivery guarantees, retries, security, consumer downtime |
| **gRPC** | Binary RPC | Internal service-to-service, high throughput | Poor browser story, less accessible to partners |
| **Bulk/batch** | File or job-based | Large volume, periodic sync | Latency; error handling on partial failure |

**In your domain, bulk and webhooks matter disproportionately.** Tax and payroll integrations are volume-and-deadline shaped, not chatty-request shaped. A partner importing 8,000 client records wants a batch job with a status endpoint and a partial-failure report — not 8,000 POSTs.

### 2.2 The things PMs must specify (and usually don't)

| Concern | Why it's yours | The question |
|---|---|---|
| **Idempotency** | Retries are inevitable; double-filing a return is catastrophic | Can a client safely retry? Is there an idempotency key? |
| **Pagination** | Determines whether large accounts work at all | Cursor or offset? What's the max page size? Is the ordering stable? |
| **Rate limits** | A product decision about fairness and cost | What are the limits, per what, and what does a client see when throttled? |
| **Error semantics** | Determines whether integrators can build reliably | Are errors machine-readable, with codes and remediation? Is it retryable? |
| **Versioning** | Determines your future cost forever | How do consumers opt into changes? |
| **Deprecation** | Trust event | What notice, what migration support, what's the policy? |
| **Partial failure** | Batch operations always partially fail | Does the whole batch fail, or does it report per-item results? |
| **Auth model** | Determines who can integrate and how safely | API keys, OAuth 2.0 client credentials, or per-user delegated access? |

**Idempotency is the one to internalise for compliance systems.** If a client's network times out after your server processed a filing submission, and they retry, the correct behaviour is to return the original result — not to file twice. An idempotency key on every mutating endpoint is the standard mechanism, and it is a *product requirement* because the consequence is legal, not technical.

### 2.3 Versioning and deprecation

**Stripe's public API versioning approach** (E1 — visible in their published API documentation and versioning policy) is the most instructive publicly readable example: dated versions, accounts pinned to the version they integrated against, backwards-compatible changes shipped without a version bump, and a defined set of what counts as breaking. You can read the actual artefact rather than a description of it.

**What counts as breaking (a useful default list to publish):**
- Removing or renaming a field, endpoint, or enum value
- Changing a field's type or making an optional field required
- Adding a new *required* request parameter
- Changing error codes or HTTP status semantics
- Tightening validation on previously-accepted input

**What is safe:** adding optional request fields, adding new response fields (if consumers are told to ignore unknown fields), adding new endpoints, adding new enum values *if* you documented that consumers must tolerate them.

**A deprecation policy is a product artefact, and publishing one is a genuine platform-maturity signal:**

```
DEPRECATION POLICY
  Notice period:      12 months for breaking changes (24 for enterprise contracts)
  Notification:       email to technical contacts + dashboard banner +
                      deprecation headers on responses + changelog
  Usage visibility:   we tell you which of your integrations use the deprecated path
  Migration support:  guide, side-by-side period, engineering office hours
  Sunset:             hard date, published at announcement, not moved
```

**Exercise 8.1.** Write this policy for your product's most-integrated API, including the breaking-change definition. *Deliverable: a publishable artefact and a strong platform-PM interview exhibit.*

---

## 3. DATA — THE PART THAT MATTERS MOST IN YOUR DOMAIN

### 3.1 Fundamentals a PM should hold

| Concept | Plain meaning | Product consequence |
|---|---|---|
| **Normalisation** | Store each fact once | Fewer inconsistencies; more joins; slower reads |
| **Denormalisation** | Duplicate for read speed | Faster reads; risk of divergence |
| **Index** | A lookup structure | Fast reads on indexed fields, slower writes; "add a filter" is not free |
| **Transaction / ACID** | A set of changes succeeds or fails together | Whether a partial state can be observed by a user |
| **Foreign key / cascade** | Relationship enforcement | Whether deleting a client deletes their returns |
| **Soft delete** | Mark deleted, don't remove | Recoverability vs. right-to-erasure tension |
| **Audit log** | Append-only record of who did what | **In compliance, this is a product feature and a legal requirement** |
| **Migration** | Structural change to existing data | Downtime risk, rollback difficulty, the reason "small" changes take months |

### 3.2 Temporal data — the concept that defines compliance software

Most systems answer *"what is true now?"* Compliance systems must answer **"what was true then, and what did we believe then?"** Those are different questions and they need different data models.

| Model | Answers | Needed for |
|---|---|---|
| **Current-state only** | What is true now | Most CRUD apps |
| **Valid-time (effective dating)** | What was true *in the real world* on date D | Tax rules effective from a statutory date; salary effective dates in HRMS |
| **Transaction-time** | What did *our system* record, and when | Audit: "what did you know on the day you filed?" |
| **Bitemporal** | Both, independently | Regulated finance, tax, insurance, payroll |

**Why this is the single highest-value technical concept for you:** a tax return filed on 15 March under rule version 2026.1 must remain reproducible three years later, even after the rules have changed twice and a correction was applied retroactively to the rule itself. Answering "recalculate this return exactly as it was calculated then" requires that rule versions be first-class, versioned, effective-dated entities — not code deployed and overwritten.

**And this is precisely the "rules platform" bet in the Volume III worked strategy.** Moving rules from code into a versioned, effective-dated rules store does three things at once: it makes annual regulation updates dramatically cheaper, it makes historical reproducibility a property of the system rather than an archaeology exercise, and it makes jurisdictional expansion a configuration problem rather than a fork. **That is a platform argument, an economics argument, and a compliance argument in one — which is exactly the kind of multi-dimensional case a Senior/Principal PM is expected to construct.**

### 3.3 SQL for PMs — what to actually learn

You do not need to optimise queries. You need to answer your own questions without waiting three days for an analyst. The realistic 90% list:

```sql
SELECT ... FROM ... WHERE                    -- filtering
JOIN (inner vs left — know the difference)   -- combining
GROUP BY + COUNT / SUM / AVG                 -- aggregation
HAVING                                       -- filtering aggregates
ORDER BY, LIMIT                              -- ranking
CASE WHEN                                    -- bucketing
DATE_TRUNC / date arithmetic                 -- cohorts and time series
CTEs (WITH ...)                              -- readable multi-step queries
Window functions (ROW_NUMBER, LAG)           -- first-action, sequences, retention
```

**The one to actually master is `LEFT JOIN` plus `WHERE ... IS NULL`** — "accounts that have *not* done X." Almost every interesting product question is a negative: which accounts never activated, which users never used the feature, which firms have licensed seats with no logins. Analysts get asked this constantly and PMs almost never write it themselves.

---

## 4. DISTRIBUTED SYSTEMS — THE PRODUCT-RELEVANT PARTS

### 4.1 Async and queues

When work is queued rather than done immediately, **"the user pressed the button" and "the thing happened" become separate events**, and every gap between them is a product design problem:

- What does the user see between the two? (Volume VII §6, "loading" and "partial" states)
- How do they know it succeeded?
- What happens if it fails 40 minutes later — email? in-app? silence?
- Can they retry safely? (idempotency again)
- What's in the dead-letter queue, and who looks at it? **A DLQ nobody monitors is a silent data-loss mechanism.**

**"Exactly-once delivery" is essentially a myth in distributed systems.** The practical guarantee is at-least-once delivery plus idempotent consumers. The product consequence: design for duplicates. In a filing system, that's the difference between a robust integration and a double-submission incident.

### 4.2 Consistency

**Eventual consistency** means different parts of the system may briefly disagree. This is usually fine and occasionally catastrophic.

The product question is always: **who observes the inconsistency, and what do they do with it?**

> A preparer updates a client's address, immediately opens the return, and sees the old address. They "fix" it again. Now you have two edits, possible conflict, and a user who no longer trusts the system.

**Where you can accept eventual consistency:** dashboards, analytics, search indexes, notification delivery, aggregate counts.
**Where you should not:** anything a user immediately reads back after writing, anything feeding a legal filing, permission and access checks, financial balances.

### 4.3 Microservices vs monolith — the honest version

The trade-off is almost never technical. It's organisational.

| | Monolith | Microservices |
|---|---|---|
| Deployment | One unit — simple, coupled | Independent — flexible, coordination-heavy |
| Team scaling | Contention over one codebase | Teams ship independently |
| Debugging | Stack trace | Distributed tracing required |
| Failure mode | Everything fails together | **Partial failure — the harder product problem** |
| Data | Transactions are easy | Cross-service transactions are painful |
| Right when | Small team, one domain, evolving boundaries | Many teams, stable boundaries, independent scaling needs |

**The PM-relevant insight:** microservices convert a *code* problem into a *coordination and product* problem. Partial failure becomes user-visible, and someone has to decide what the product does when the notification service is down but filing works. That someone is you. Distributed architecture doesn't remove complexity; it relocates it into your requirements.

### 4.4 Performance vocabulary

- **Latency** = how long one operation takes. **Throughput** = how many per unit time. Optimising one can hurt the other.
- **Use percentiles, never averages.** An average page load of 800ms with a p99 of 14 seconds means your largest, most valuable accounts are having a terrible time and the average is hiding it. **In B2B, the p99 experience often belongs to your biggest customer** — their data volume is what produces the tail.
- **Back-of-envelope estimation** is a real PM skill: 3,000 preparers × 250 returns × 8 documents = 6M documents/season; concentrated in 6 weeks ≈ 1M/week ≈ ~2.4/second average, with peaks perhaps 10× that. Now you can have a meaningful conversation about capacity, cost, and whether the vendor's rate limit works.

### 4.5 Observability

Three signals: **logs** (what happened), **metrics** (how much/how often), **traces** (the path of one request through many services).

**The PM question is not "do we have monitoring." It's: when a customer calls and says "my filing failed at 4pm yesterday," can we reconstruct exactly what happened for that specific account, within minutes?** If the answer is no, that's a requirement, and it's yours to write.

**SLI / SLO / SLA:**
- **SLI** — the measurement (e.g. % of filing submissions succeeding within 30s)
- **SLO** — your internal target (99.9%)
- **SLA** — the contractual promise with penalties (99.5% — always set below your SLO)

Google's SRE book (E1, published by Google) is the authoritative public treatment, including the error-budget mechanism covered in Volume IV.

---

## 5. SECURITY & TENANCY

| Concept | Meaning | Product decision it drives |
|---|---|---|
| **Authentication** | Who are you? | SSO/SAML/OIDC support — a **hard enterprise requirement**, not a feature |
| **Authorization** | What may you do? | The permissions model — the highest-consequence product decision in multi-user B2B |
| **RBAC** | Permissions via roles | Simple, familiar; gets awkward when firms want exceptions |
| **ABAC** | Permissions via attributes (client, office, engagement) | Flexible; harder to explain and administer |
| **Tenant isolation** | One customer cannot reach another's data | Existential. A single breach ends a compliance vendor |
| **Encryption at rest / in transit** | Storage and network protection | Table stakes; will appear in every security questionnaire |
| **Data residency** | Where data physically lives | Determines which markets you can enter at all |
| **Least privilege** | Minimum access necessary | Should shape defaults, not just capability |
| **Audit trail** | Immutable record of access and change | Product feature *and* legal obligation in your domain |

**The permissions model deserves specific attention because it's the most under-designed surface in B2B SaaS.** Firms need: partners who see everything, preparers who see assigned clients, reviewers who see a queue, admins who manage users but shouldn't read client tax data, and external clients who see only their own return. Retrofitting that onto a model built for "admin and user" is a multi-quarter migration. **Design the permissions model before the second customer, not after the fiftieth.**

---

# PART XVIII — PLATFORM PRODUCT MANAGEMENT

## 6. FEATURE → CAPABILITY → PLATFORM

```
FEATURE            Solves one problem for one user group in one product
   ↓  (generalise when a second consumer needs the same thing)
CAPABILITY         A reusable service with a defined interface, used by 2+ surfaces
   ↓  (invest when the consumer set is open-ended and self-service matters)
PLATFORM           A set of capabilities others build on without your involvement
```

**The promotion tests — do not skip a level:**

| Step | Test | If it fails |
|---|---|---|
| Feature → Capability | Do **two or more** real consumers need this, with genuinely similar requirements? | Keep it a feature. Two similar-looking needs often diverge on inspection |
| Capability → Platform | Can a new consumer adopt it **without talking to your team**? | You have a shared service, not a platform. That's fine — just don't claim otherwise |

**The rule of three.** Don't abstract on the first repetition. On the second, note the pattern. On the third, you have enough information to abstract correctly. **Abstracting at N=1 produces an abstraction shaped like one use case with a generic name** — the most common and most expensive platform mistake, because the wrong abstraction is harder to remove than the duplication it replaced.

---

## 7. WHAT INVERTS WHEN YOUR CUSTOMER IS ANOTHER TEAM

| | Product PM | Platform PM |
|---|---|---|
| Customer | End users | **Other engineering teams** |
| They can | Complain | **Build their own instead, and will** |
| Adoption via | Marketing, sales, UX | **Making it cheaper than the alternative** |
| Success | Usage, retention, revenue | **Adoption without your involvement** |
| Failure | Nobody uses it | Everyone forks it, or a mandate forces adoption and everyone resents you |
| Your leverage | Product quality | Documentation, defaults, migration cost, and trust |
| Breaking changes | Annoying | **Betrayal — you broke their production** |

**The defining constraint: your users are the only user group in software who can trivially replace you.** A tax preparer cannot build their own tax platform. An engineering team absolutely can and will build their own notification wrapper if yours is confusing, slow to adopt, or unreliable — and they'll be right to.

**Consequence: mandates don't work.** You can force teams to *use* a platform. You cannot force them to *rely* on it. Mandated platforms accumulate defensive workarounds, shadow implementations, and quiet resentment, and the platform team ends up with all the responsibility and none of the trust. **Adoption must be earned by being genuinely cheaper than the alternative**, and "cheaper" includes the cost of understanding it.

---

## 8. DEVELOPER EXPERIENCE AS THE PRODUCT

DX is not documentation. It's the total cost of getting a working integration.

**The metric that matters most: time-to-first-successful-call.** From "I have a reason to use this" to "I got a 200 with real data." Measure it by watching a new engineer do it, unassisted, with a stopwatch. Target under 30 minutes for an internal capability. If it's four hours, adoption will be low regardless of how good the service is.

**The DX checklist:**

| Element | Bar |
|---|---|
| **Quickstart** | Working example in under 10 minutes, copy-pasteable |
| **Reference docs** | Every field, every error code, every limit |
| **Errors** | Machine-readable code + human message + what to do next + a link |
| **Sandbox** | Realistic test environment with seeded data, no production risk |
| **Client libraries** | For the languages your consumers actually use |
| **Changelog** | Every change, dated, with breaking clearly marked |
| **Support path** | A channel with a real response-time expectation |
| **Observability for consumers** | They can see their own usage, errors, and rate-limit status |

**Error messages are the highest-ROI DX investment and the most neglected.** A developer spends the majority of integration time in failure states. `400 Bad Request` costs an hour. `400 — invalid_tax_year: 'tax_year' must be between 2019 and 2026; received 2018. See /docs/errors#invalid_tax_year` costs thirty seconds. Same engineering effort to produce, two orders of magnitude difference in adoption friction.

---

## 9. PLATFORM METRICS

Product metrics don't transfer. Use these:

| Metric | Definition | Tells you |
|---|---|---|
| **Adoption breadth** | # of consuming teams/services | Is it a platform or a shared library? |
| **Adoption depth** | % of eligible use cases going through it | Are there shadow implementations? |
| **Time-to-first-call** | Onboarding friction | Whether DX is real |
| **Self-service rate** | % of integrations completed with zero platform-team involvement | **The single best platform health metric** |
| **Support burden** | Tickets per consuming team per month | Whether the abstraction is right |
| **Breaking-change frequency** | Per year | Your trust balance |
| **Migration completion time** | Announcement → last consumer migrated | Whether you can ever evolve |
| **Reliability by consumer** | SLO attainment per consuming team | Whether you're a dependency they can trust |
| **Cost per unit** | Infra cost per call/event | Whether the platform scales economically |

**Self-service rate is the one to lead with.** If every integration requires a meeting with your team, you have a consulting practice wearing a platform's name — and it will not scale past a handful of consumers.

---

## 10. THE PLATFORM TRAPS

| Trap | Looks like | Reality | Prevention |
|---|---|---|---|
| **Premature abstraction** | Building the platform first | You built for imagined consumers with imagined needs | Rule of three |
| **The ivory tower** | Elegant design, zero adopters | Built without a first real consumer | Always have a committed launch customer |
| **The mandate** | Leadership forces adoption | Compliance without reliance; workarounds proliferate | Earn it; measure self-service rate |
| **The god service** | One service does everything | Nobody can change it; it's a monolith with network calls | Clear boundaries; one responsibility |
| **The leaky abstraction** | Consumers must understand your internals | You didn't abstract, you relocated | If docs must explain your architecture, the interface is wrong |
| **Version sprawl** | Six live versions | You can never deprecate | Deprecation policy from day one |
| **Invisible value** | "What does the platform team even do?" | Real leverage, no narrative | Publish leverage metrics: engineer-weeks saved, incidents avoided |

**The last one is the career risk in platform PM.** Platform work is invisible when it works. If a rules platform makes regulation updates take three days instead of three weeks, nobody notices — they just stop complaining. **Publish the counterfactual quarterly:** "18 rule changes this quarter at an average of 2.1 days each; on the previous approach this would have been ~14 days each — approximately 43 engineer-weeks avoided." That paragraph is what gets a platform team funded next year, and writing it is your job.

---

## 11. SHARED CAPABILITIES IN YOUR ENVIRONMENT

You already run a multi-product portfolio (tax, CRM, HRMS, workflow, reporting) — which means shared capabilities either exist deliberately or exist accidentally in triplicate.

| Capability | Platform question | Signal it should be shared |
|---|---|---|
| **Identity & access** | One user, one login, across all products? | Customers ask why they have three logins |
| **Permissions/roles** | One model or three divergent ones? | Same firm structure re-modelled per product |
| **Notifications** | One service for email/in-app/SMS with preferences and audit? | Each product built its own email sender |
| **Workflow engine** | One state machine engine, or hard-coded flows per product? | Approval logic reimplemented per product |
| **Reporting** | Shared query/report layer or per-product exports? | Every product has its own CSV export |
| **Document service** | Storage, versioning, retention, virus scanning, OCR | Multiple upload implementations |
| **Rules engine** | Versioned, effective-dated rule evaluation | Business logic embedded in code across products |
| **Audit log** | One immutable trail across products | Compliance asks for a cross-product audit and you can't produce it |

**The two highest-leverage for you specifically are the rules engine and the audit log**, because both are simultaneously platform investments, compliance requirements, and cost reducers — which means they can be funded from three different budgets and defended to three different audiences. That triple-justification property is exactly what makes a platform bet winnable, and identifying it is a senior move.

---

## 12. BUILD vs BUY vs PARTNER

| | Build | Buy | Partner/Integrate |
|---|---|---|---|
| Choose when | It's differentiating; you need deep control | Commodity; someone does it better | The capability belongs to someone else's domain |
| True cost | Build + maintain forever + opportunity cost | Licence + integration + lock-in + their roadmap | Integration + relationship + their reliability |
| Risk | Underestimating maintenance (usually 3–5× build) | Vendor dependency, price changes, acquisition | Their outage becomes your outage |

**The decision rule:** build what differentiates you; buy what doesn't. The honest test — *if we do this 20% better than the market, does a single customer choose us for it?* If no, buy.

**Applied to your domain:** the tax calculation engine and rule versioning are core — build. Document OCR, email delivery, e-signature, and virus scanning are not — buy, and design the interface so you can swap vendors. **The build-vs-buy decision should always come with an exit plan**, because vendor pricing changes and acquisitions happen; if swapping the OCR vendor requires touching forty files, you didn't buy a capability, you married one.

---

## 13. DEPRECATION WITHOUT BREAKING TRUST

The hardest platform skill, and the one that determines whether you can evolve at all.

```
1. ANNOUNCE     Date, reason, migration path, sunset date. Never move the sunset date
                once announced — moving it teaches consumers deadlines aren't real
2. INSTRUMENT   Know exactly who is using it and how much. Tell them; they often don't know
3. ASSIST       Migration guide, side-by-side operation, office hours, and — for the
                largest consumers — do part of the migration yourself
4. WARN         Deprecation headers on responses, dashboard notices, escalating cadence
5. DEGRADE      Optional: brownouts (brief planned outages) before sunset so consumers
                discover dependencies while it's still safe
6. SUNSET       On the announced date, for everyone. Exceptions destroy every future deadline
```

**The counter-intuitive rule:** the friendliest thing you can do is hold the date. A platform team that always extends teaches every consumer to ignore deprecation notices, which means the *next* deprecation costs ten times more and the team can never modernise anything.

---

## 14. VOLUME VIII EXERCISES

**Exercise 8.2 — The architecture redraw, formalised.** Draw your product's services, data stores, external integrations, and the direction of each dependency. Review with your tech lead. Mark every place where two products duplicate a capability. *Deliverable: a platform opportunity map.*

**Exercise 8.3 — The temporal data audit.** For your compliance product, answer in writing: can we reproduce a filing exactly as calculated on its filing date, including the rule version applied? If not, what's missing? *Deliverable: a gap analysis that doubles as a compliance risk register entry and a platform business case.*

**Exercise 8.4 — API contract review.** Take your most-used external API and check it against §2.2: idempotency, pagination, rate limits, error semantics, versioning, partial failure. *Deliverable: a prioritised contract-debt list.*

**Exercise 8.5 — Time-to-first-call.** Watch an engineer who has never used your API integrate against it. Time it. Don't help. *Deliverable: the most honest DX assessment you will ever get.*

**Exercise 8.6 — The "why is this expensive" log.** For one month, every time engineering says something is big, record which of the four reasons (§1) it was. *Deliverable: a pattern. If it's "migration" every time, you have a data model problem, not an estimation problem.*

**Exercise 8.7 — The platform counterfactual.** Write the quarterly leverage paragraph from §10 for a shared capability your org already has. *Deliverable: the paragraph that funds the team.*

---

## 15. VOLUME VIII INTERVIEW BANK

**Technical PM**
1. What's the difference between something a PM must know and something an engineer must know?
2. An engineer says a change is expensive. What do you ask?
3. How would you decide between REST and webhooks for a partner integration?
4. What's idempotency and why would a PM care?
5. Your product must reproduce a calculation from three years ago exactly. What does that require?
6. When is eventual consistency acceptable and when is it not?
7. Explain SLI, SLO, and SLA, and why the SLA should be lower than the SLO.
8. How do you decide what to log?
9. Your p50 is fine and your p99 is terrible. What's likely happening and who's affected?
10. How would you approach a data model change that affects existing customer data?

**Platform PM**
11. When does a feature become a platform capability?
12. How do you drive adoption of an internal platform without a mandate?
13. How do you know your platform is succeeding?
14. Walk me through deprecating an API that 40 customers depend on.
15. How do you decide build vs buy?
16. What's the most common platform mistake and how do you avoid it?
17. Two teams need similar capabilities with slightly different requirements. What do you do?
18. How do you justify platform investment against customer-facing features?
19. Your platform has high adoption but high support burden. What does that tell you?
20. What would you do in your first 90 days as a platform PM on an existing platform?

---

*Volume VIII complete. Continue to `09-ai-product-management.md`.*
