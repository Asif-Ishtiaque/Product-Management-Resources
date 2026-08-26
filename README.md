# THE ADVANCED PRODUCT MANAGEMENT STUDY MATERIALS
### A practitioner-grade curriculum for PM → Senior PM → Technical PM → Platform PM → AI PM → Product Lead → GPM

**Version:** 1.0 (Volume I released)
**Audience:** Practicing Product/Project Managers in B2B SaaS with 2+ years shipping real software
**Assumed baseline:** PRDs, BRDs, user stories, backlog, roadmaps, Agile/Scrum, sprint planning, QA/UAT, Jira, Confluence, stakeholder management
**What this book does NOT do:** re-teach any of the above

---

## 0.1 — READ THIS FIRST: RESEARCH & EVIDENCE DISCLOSURE


What this means in practice:

| | Status |
|---|---|
| Live web search | **Not available in this session** |
| Underlying knowledge currency | Reliable through **~May 2026** |
| Company practice claims | Drawn from publicly published primary sources I can identify by name — labelled with evidence strength |
| Verification burden | **On you.** Every company claim in this book carries a pointer to the primary source so you can check freshness yourself |

I also cannot guarantee that any specific book, paper, blog post, or job description I name still exists at the URL or in the form I describe. **Treat every citation as a lead to verify, not a fact to quote.** Career pages, engineering blogs, and AI-company role definitions in particular change fast — the AI PM sections (Parts XIX–XX) have the shortest shelf life in the entire book.

### The Evidence Ladder (used on every company claim in this book)

| Label | Meaning | Example of what qualifies |
|---|---|---|
| **E1 — Documented** | The company itself published it, in a durable, named artefact | Amazon's Leadership Principles page; Netflix Culture memo; Google's re:Work OKR guide; the Google SRE book |
| **E2 — Attributed** | A named, identifiable insider stated it publicly on the record | A founder/exec interview, a conference talk, a signed engineering-blog post, a book by a former exec |
| **E3 — Reported / patterned** | Consistently described across multiple credible secondhand sources, or visible across many public job descriptions, but not company-confirmed | "Recurring language across current public PM postings at X" |
| **E4 — Insufficient** | I cannot support the claim. **The book says so explicitly.** | Most of Apple's internal product process |

**Rule enforced throughout:** never "FAANG companies do X." Only "Amazon publicly documents X (E1)," "Reed Hastings publicly stated Y (E2)," or "Public evidence insufficient (E4)."

### The three questions to ask before importing any company's practice

1. **What constraint was it built for?** Amazon's six-pager exists because Amazon runs enormous cross-org meetings where reading speed beats presenting charisma. If your meeting is five people, the six-pager is cosplay.
2. **What does it cost to run?** Most elite mechanisms are expensive. Working Backwards costs weeks. Netflix-style autonomy costs a very high talent-density bar you probably cannot hire for.
3. **What breaks if you adopt it partially?** Some practices are load-bearing systems, not techniques. The most instructive failure in the industry is the "Spotify model" (see Volume IV) — copied worldwide from two 2012 papers that described an *aspiration*, by people who skipped the culture the structure depended on.

---

## 0.2 — VOCABULARY DISCIPLINE

Most PM writing is sloppy about what kind of thing it is describing. This book is not. Every named concept in this book carries one of these tags.

| Type | Definition | Test | Example |
|---|---|---|---|
| **Principle** | A belief about what is true, independent of method | Can be violated but not "not applicable" | "Problem ≠ solution" |
| **Framework** | A structure for organising thinking; produces a shape, not an answer | Has named components you fill in | RICE, Porter's Five Forces, Opportunity Solution Tree |
| **Methodology** | A prescribed sequence of activities with roles and artefacts | Has steps and a defined order | Scrum, Design Thinking, Double Diamond |
| **Practice** | A repeatable behaviour a team does | Has a cadence | Weekly customer interview, weekly business review |
| **Mechanism** | A practice with a forcing function that makes it self-sustaining | Fails loudly if skipped | PRFAQ gate before funding; error budget freeze |
| **Standard** | A rule with an authority behind it | Non-compliance has consequences | WCAG 2.2 AA, SOC 2, GDPR, ISO 27001 |
| **Heuristic** | A rule of thumb that is usually right and cheap to apply | Has known failure cases | "If two teams need it, it's a platform" |
| **Opinion** | A defensible view held by a credible person | Other credible people disagree | "Roadmaps should never have dates" |

**Why this matters for your promotion:** Senior PMs are trusted because they say *"this is a heuristic, and here's where it breaks"* instead of *"the framework says."* Mislabelling an opinion as a standard is the single fastest way to lose an engineering lead's confidence.

---

## 0.3 — THE TEACHING PROTOCOL

Every major concept in this book is taught in this order. If a section skips a step, the step was genuinely not applicable — not forgotten.

1. **Plain** — one paragraph, no jargon
2. **Deep** — the mechanics, the maths, the second-order effects
3. **Real example** — drawn from B2B SaaS, and wherever possible from tax/compliance, CRM, HRMS, workflow automation, or API/platform contexts
4. **When to use**
5. **When NOT to use** ← the section most books omit and the one that separates senior from mid
6. **Alternatives** — what else solves this
7. **Trade-offs** — what you give up
8. **Exercise** — do it on your own product
9. **Interview question** — what a hiring panel asks about it
10. **Reference** — the primary source, with evidence label

---

## 0.4 — THE MASTERY MODEL

The book is built on this progression. Read it as a **loop with a widening radius**, not a ladder. A Director still does product thinking; they just do it across a portfolio instead of a feature.

```
PRODUCT THINKING
  └→ CUSTOMER UNDERSTANDING
      └→ PROBLEM FRAMING
          └→ PRODUCT STRATEGY
              └→ DISCOVERY
                  └→ PRIORITIZATION
                      └→ PRODUCT DESIGN
                          └→ EXECUTION
                              └→ ANALYTICS
                                  └→ GO-TO-MARKET
                                      └→ ADOPTION & GROWTH
                                          └→ PLATFORM / ECOSYSTEM
                                              └→ TECHNICAL PM
                                                  └→ AI PM
                                                      └→ LEADERSHIP
                                                          └→ ORG INFLUENCE
                                                              └→ PORTFOLIO STRATEGY
```

**The load-bearing insight:** every arrow is a *translation loss point*. Strategy that survives to execution is rare not because any single step is hard, but because meaning leaks at each handoff. The senior PM's real job is reducing leakage across the whole chain — which is why "PM manages clarity, not engineers" (Part XVI) is the thesis of the execution volume.

---

## 0.5 — FULL ARCHITECTURE: 49 PARTS → 18 VOLUMES

| Vol | File | Parts | Contents | Status |
|---|---|---|---|---|
| **0** | `README.md` | I | Evidence standard, vocabulary, teaching protocol, architecture | ✅ **Built** |
| **I** | `01-product-thinking-and-mindset.md` | II, III | Mastery model, role archetypes, ownership ladder, 8 thinking modes, product judgment | ✅ **Built** |
| **II** | `02-customer-problem-discovery.md` | IV, V, VI | Customer understanding, JTBD, problem framing, discovery system, evidence hierarchy | ✅ **Built** |
| **III** | `03-strategy-market-roadmaps.md` | VII, VIII, IX | Strategy kernel, moats, positioning, TAM/SAM/SOM, competitive analysis, 9 roadmap types | ✅ **Built** |
| **IV** | `04-industry-operating-models.md` | XXXIII, XXXIV | Company-by-company evidence audit + the comparison matrix with E4 cells marked | ✅ **Built** |
| **V** | `05-prioritization-and-economics.md` | X, XI | Prioritization mastery, when NOT to score, capacity allocation, SaaS unit economics, AI margin structure | ✅ **Built** |
| **VI** | `06-analytics-and-experimentation.md` | XII, XIII | Metric trees, B2B analytics constraints, causal inference without experiments, Simpson's paradox | ✅ **Built** |
| **VII** | `07-design-requirements-execution.md` | XIV, XV, XVI | IA, state machines, unhappy-path budget, advanced PRD, edge-case taxonomy, execution health | ✅ **Built** |
| **VIII** | `08-technical-and-platform-pm.md` | XVII, XVIII | API contracts, temporal/bitemporal data, distributed systems, Feature→Capability→Platform, DX, deprecation | ✅ **Built** |
| **IX** | `09-ai-product-management.md` | XIX, XX | Consequence classes, eval design, failure taxonomy, AI UX, agent autonomy ladder, AI decision framework | ✅ **Built** |
| **X** | `10-ops-stakeholders-leadership.md` | XXI–XXV | Mechanisms vs habits, the product operating system, influence, coaching, decision framework, risk triggers | ✅ **Built** |
| **XVIII** | `99-master-map-and-closing.md` | XLIX + final | 10-level master map, 25 highest-leverage skills, the closing thesis | ✅ **Built** |
| XI | `11-gtm-launch-growth-b2b.md` | XXVI–XXXI | GTM, launch readiness, growth, B2B/enterprise, SaaS strategy, quality | ⬜ Queued |
| XII | `12-metrics-masterclass.md` | XXXII | Full metric library: definition → formula → interpretation → limitation → decision | ⬜ Queued |
| XIII | `13-framework-library-and-antipatterns.md` | XXXV, XXXVI | Framework reference + anti-pattern library | ⬜ Queued |
| XIV | `14-case-studies.md` | XXXVII | 20+ deep cases across SaaS, marketplace, platform, AI, CRM, HRMS, fintech | ⬜ Queued |
| XV | `15-case-interviews.md` | XXXVIII | 205 cases: product sense, strategy, analytics, prioritization, execution, technical, AI, leadership | ⬜ Queued |
| XVI | `16-projects-and-simulations.md` | XXXIX, XL | 5 portfolio projects + 10 leader simulations | ⬜ Queued |
| XVII | `17-toolkit-os-and-senior-skills.md` | XLII, XLIII, XLIV | Tooling, the PM operating system, Senior→Principal skill deltas | ⬜ Queued |
| XVIII+ | `18-capstone-plan-matrix-library.md` | XLI, XLV–XLVIII | Glossary, capstone, 180-day plan, skill matrix, reference library | ⬜ Queued |

**Volumes 0–X plus the closing synthesis are built — all ten levels of the Master Map are now covered end to end.** What remains is reference and practice material: metrics library, framework/anti-pattern reference, case studies, the 205-case interview bank, portfolio projects, the toolkit, the capstone and the 180-day plan. Say `build vol 12` (or any volume number) to continue. Volumes are independent — build in whatever order serves your next interview or next quarter.

---

## 0.6 — HOW TO USE THIS BOOK (given your situation)

You are a PM II in B2B tax/compliance SaaS targeting Senior PM / TPM / Platform PM / AI PM roles, with international positioning as the goal. That specific position changes the reading order.

**Your actual bottleneck is not knowledge. It is evidence.** You can already describe WSJF. What a hiring panel at a US/EU company wants is proof you have exercised judgment under ambiguity with a business outcome attached. Every volume therefore ends with an **artefact** you can put in a portfolio or reference in an interview.

### Recommended order for your goals

| Priority | Volume | Why for you specifically |
|---|---|---|
| 1 | **III** (Strategy) ✅ | Highest-frequency Senior PM interview failure mode. Tax/compliance PMs get typed as "requirements people" — strategy fluency is how you break the type. |
| 2 | **VIII** (Technical/Platform) ✅ | Directly serves the TPM and Platform PM targets. Your API-integration and workflow-engine work is already platform work; you need the vocabulary to *name* it as such. |
| 3 | **VI** (Analytics/Experimentation) ✅ | Your known portfolio gap. Compliance products rarely A/B test — Part XIII teaches causal inference *without* experiments, which is the rarer skill. |
| 4 | **IX** (AI PM) ✅ | Fastest-moving market demand, shortest shelf life — do it close to when you'll use it. |
| 5 | **XV** (Case interviews) ← do last | Do last. Practising cases before the underlying models are solid trains you to produce fluent nonsense. |

### Reframing your domain (use this language, it is accurate)

Tax and compliance software is not a niche you need to escape. It is a **high-consequence, deterministic-calculation, regulation-versioned, deadline-cyclical workflow platform.** Say that instead of "tax software."

| What you actually have | What it maps to in a general PM market |
|---|---|
| Tax logic engines with versioned rules | **Deterministic calculation engines** with correctness guarantees and rule versioning — same class of problem as pricing engines, billing, payroll, risk scoring |
| Filing deadlines and seasonal peaks | **Non-negotiable external deadlines + extreme load seasonality** — a capacity and reliability planning problem |
| Regulation changes each year | **Compliance-versioned product surface** — one of the hardest forms of technical-debt and migration management |
| CRM + HRMS + workflow + reporting | **Multi-product portfolio with shared platform services** — auth, notifications, workflow, reporting are platform capabilities |
| QA/UAT automation | **Correctness as a product feature**, not a QA activity — the closest analogue to AI evaluation in traditional software |

That last row is the sharpest one you own. **A PM who has run 200+ UAT cases against a calculation engine already understands evaluation harnesses, regression suites, and correctness thresholds — which is exactly the skill AI PM roles are desperate for.** Volume IX makes that bridge explicit.

---

## 0.7 — WHAT "ADVANCED" MEANS HERE

Three tests. If a section fails all three, it does not belong in this book.

1. **Does it change a decision?** Not "is it true" — does knowing it make you choose differently under pressure?
2. **Does it survive contact with a hostile stakeholder?** If a VP Sales can dismantle it in one sentence, it wasn't advanced.
3. **Does it scale past you?** Advanced practice produces systems that keep working when you're on leave. See Part XLIX, competency #10.

---

*Volume 0 complete. Continue to `01-product-thinking-and-mindset.md`.*
