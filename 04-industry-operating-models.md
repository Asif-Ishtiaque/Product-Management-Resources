# VOLUME IV — INDUSTRY OPERATING MODELS
### Parts XXXIII & XXXIV

> The purpose of this volume is not to help you copy anyone. It is to make you **immune to cargo cult**, which is the most expensive disease in product management.

---

## 0. READ THIS BEFORE ANY OTHER PAGE IN THIS VOLUME

**I have no live web access in this session.** Every claim below is drawn from publicly published material I can name, current to roughly **May 2026**. I have labelled each claim with the evidence ladder from the README:

- **E1 — Documented:** the company published it in a durable, named artefact
- **E2 — Attributed:** a named insider stated it publicly on the record
- **E3 — Reported / patterned:** consistently described secondhand, or visible across public job descriptions; not company-confirmed
- **E4 — Insufficient:** I cannot support the claim, and I say so

**Three warnings you should take seriously:**

1. **Companies change.** Reorgs, leadership changes, and layoffs reshape operating models fast. A practice documented in 2021 may be dead. **Verify before citing anything here in an interview.**
2. **A published artefact is not proof of universal internal practice.** Amazon publishes its Leadership Principles; that does not mean every Amazon team lives them equally. Netflix publishes a culture memo; that is an aspiration statement authored by leadership. Treat all of it as *what the company says about itself*, which is genuinely informative — and different from what it does.
3. **Insider books are E2, not E1.** *Working Backwards* and *No Rules Rules* are excellent and were written by people who were there. They are still individual accounts, sometimes retrospective and sometimes flattering.

**Where I don't know, this volume says "Public evidence insufficient." That appears many times below and it is the most honest thing in the document.**

---

## 1. AMAZON

**Evidence quality overall: STRONG.** Amazon is the most publicly documented product operating model in existence, partly self-published and partly through insider books.

| Practice | What it is | Evidence |
|---|---|---|
| **Leadership Principles** | A published set of principles (Customer Obsession, Ownership, Invent and Simplify, Are Right A Lot, Dive Deep, Have Backbone; Disagree and Commit, Bias for Action, and others) used explicitly in hiring and performance | **E1** — published on amazon.jobs. *Amazon has amended the set over time; check current wording.* |
| **Working Backwards / PRFAQ** | Before building, write the press release and FAQ as if the product had launched, from the customer's perspective. The document is critiqued and iterated; many ideas die here | **E1/E2** — Amazon has publicly referenced Working Backwards; the operational detail comes from Bryar & Carr, *Working Backwards* (2021), both former Amazon executives |
| **Six-page narrative memos, no PowerPoint** | Meetings begin with ~20–30 minutes of silent reading of a densely written narrative, then discussion | **E1/E2** — Bezos publicly discussed narratives and the PowerPoint ban; the 2017 shareholder letter discusses six-page memos and high standards |
| **One-way vs two-way doors** | Irreversible decisions get deliberate process; reversible ones are pushed down and decided fast | **E1** — 2015 Letter to Shareholders |
| **Two-pizza teams** | Small autonomous teams owning a service end to end | **E2/E3** — widely reported and described in insider accounts; the concept has publicly evolved toward "single-threaded ownership" |
| **Single-threaded leadership** | One leader whose *only* job is that initiative | **E2** — *Working Backwards* |
| **Bar Raiser** | A trained interviewer outside the hiring team with veto power | **E1/E2** — Amazon has published about Bar Raiser on its own channels |
| **Input vs output metrics (WBR)** | Weekly business reviews focused on controllable input metrics rather than lagging outputs | **E2** — *Working Backwards* describes this in detail |

**The transferable core.** Amazon's mechanisms all share one design property: **they make the desired behaviour unskippable.** You cannot get funding without a PRFAQ. You cannot skip reading because the room reads together. You cannot let a hiring manager lower the bar because the Bar Raiser has a veto. This is the real lesson — *not the six-page format.* Ask of any practice you admire: **what is the forcing function?** If there isn't one, it's a suggestion, and suggestions die under quarterly pressure.

**When to adopt.** Large orgs, cross-functional decisions with many stakeholders, high-consequence irreversible bets, distributed teams where writing beats meetings.

**When NOT to adopt.** Small teams with high context — a five-person team writing six-pagers is performing rigour, not producing it. Fast-moving exploratory work where the cost of the document exceeds the cost of just trying it. **And critically: don't adopt the artefact without the critique culture.** A PRFAQ nobody is allowed to shred is a marketing document. The value is in the ruthless review, which requires psychological safety and senior time. Most adoptions copy the template and skip both.

**The cheap version that actually works for a team your size:** a one-page "customer letter" before any project over two weeks — who is the customer, what changes for them, what they'd say, what they'd object to. 90% of the value, 10% of the cost.

---

## 2. GOOGLE

**Evidence quality overall: STRONG for engineering and measurement practices; MODERATE for product management specifically.**

| Practice | What it is | Evidence |
|---|---|---|
| **OKRs** | Objectives with measurable Key Results, set at multiple levels, publicly visible | **E1** — Google published an OKR guide via re:Work; also John Doerr, *Measure What Matters* (E1 book, E2 for the Google specifics) |
| **SRE model, error budgets, SLOs** | Reliability as a product feature with an explicit budget; exceeding the error budget halts feature work | **E1** — the Google SRE book, published by Google and freely available |
| **HEART framework** | UX metrics: Happiness, Engagement, Adoption, Retention, Task success — mapped through Goals-Signals-Metrics | **E1** — Rodden, Hutchinson & Fu, published Google research paper (2010) |
| **Design Sprint** | 5-day structured problem-solving sprint | **E1** — developed at Google Ventures; Knapp et al., *Sprint* |
| **APM programme** | Associate Product Manager rotational programme | **E1** — publicly documented on Google careers |
| **Launch reviews / readiness** | Structured pre-launch review across privacy, legal, reliability | **E1/E3** — the SRE book documents production readiness reviews; the broader launch process is E3 |
| **20% time** | Engineers spending part of their time on self-directed work | **E1 historically** (2004 IPO founders' letter); **E3/E4 currently** — widely reported to have diminished; I cannot verify its present status |

**The transferable core: error budgets.** This is arguably the single most exportable mechanism in this entire volume and almost nobody outside infrastructure uses it. The idea: agree an explicit reliability target (say 99.9%), which defines an allowable failure budget. Spend it on shipping speed. **Exceed it, and feature work stops until reliability is restored.** It converts the eternal "quality vs speed" argument into an arithmetic rule agreed in advance by both sides.

**Direct application to your domain:** in tax/compliance, define a **correctness budget** rather than an uptime budget — e.g. calculation-defect escape rate, or count of filings requiring amendment due to product error. Breach it and feature work stops. This turns quality from a virtue nobody can prioritise into a constraint everybody must respect, and it is the kind of mechanism that gets a PM noticed.

**When to adopt OKRs.** When you have genuine outcome ownership and the ability to influence the results.

**When NOT to adopt OKRs.** Three cases, all common: (1) when teams don't control the outcome — you get sandbagging or despair; (2) when they're used for performance review — Doerr and most practitioners explicitly warn against this, because it converts OKRs into commitments and kills ambition; (3) when the real planning happens elsewhere and OKRs are written afterward to describe it, which is the most common failure and is pure overhead.

---

## 3. META

**Evidence quality overall: MODERATE.** Strong on engineering and experimentation infrastructure, weaker on current product management process.

| Practice | Evidence |
|---|---|
| **"Move fast and break things" → "Move fast with stable infrastructure"** — an explicit, publicly announced change of the engineering motto | **E2** — Zuckerberg stated the change publicly at F8 (2014) |
| **Engineering bootcamp** — new engineers spend weeks exploring codebases and teams before choosing placement | **E1/E2** — described in Meta's own engineering/careers material |
| **Large-scale experimentation infrastructure** — company culture of testing nearly everything | **E1** — Meta researchers published on their experimentation platform; PlanOut was open-sourced with an accompanying paper (Bakshy, Eckles, Bernstein, 2014) |
| **Data-driven product culture; analytics fluency expected of PMs** | **E3** — consistently reported and reflected in public role descriptions |
| **Current internal product review cadence and decision rights** | **E4 — Public evidence insufficient.** I will not describe Meta's internal product review process. |

**The transferable core: experimentation as infrastructure, not as a project.** The strategic lesson is that Meta invested in *making experiments cheap*, and the consequence was a culture that could afford to be uncertain. Teams that run experiments as one-off projects run few experiments and learn slowly.

**When NOT to adopt.** Low-traffic B2B products, where you will never reach statistical power on most surfaces (Volume VI covers what to do instead). Also: mandated-use workflow products, where the engagement metrics that experimentation optimises are not measures of value. **Copying an experimentation culture into a product with 1,200 accounts produces theatre and false confidence.**

---

## 4. NETFLIX

**Evidence quality overall: STRONG for culture (self-published); MODERATE for product process.**

| Practice | Evidence |
|---|---|
| **Culture memo — "Freedom & Responsibility," context not control, high talent density, "keeper test," candid feedback** | **E1** — Netflix publishes its culture document publicly |
| **Elaboration by leadership** | **E2** — Hastings & Meyer, *No Rules Rules* (2020) |
| **Extensive A/B testing of product and artwork, published methodology** | **E1** — Netflix Tech Blog has published a multi-part experimentation series |
| **DHM heuristic (Delight customers, in Hard-to-copy, Margin-enhancing ways)** | **E2** — publicly taught by Gibson Biddle, former VP Product at Netflix; his framing, not an official Netflix doctrine |
| **Current internal roadmap and prioritisation process** | **E4 — Public evidence insufficient.** |

**The transferable core: "context, not control."** The mechanism is that leaders are obliged to supply enough context — strategy, economics, constraints, and the reasoning behind them — that individuals can make good decisions without approval. Note the direction: **this makes leadership *more* work, not less.** It is not "leave people alone." Most organisations that claim to copy Netflix autonomy have simply removed the control and never supplied the context, producing chaos and then blaming autonomy.

**The precondition nobody copies: talent density.** Netflix pairs autonomy with an explicitly stated policy of only keeping people they'd fight to retain, plus high compensation. **The autonomy is downstream of the density.** Adopting the autonomy without the density — which most companies cannot afford or won't do — is the single most predictable failed transplant in this volume.

**When to adopt.** Senior, expensive teams where the cost of slow decisions exceeds the cost of some wrong ones.

**When NOT to adopt.** Junior teams; high-consequence regulated environments where an individual's wrong call creates legal exposure. **This is directly relevant to you:** in tax and compliance, "context not control" applies to *product decisions* but emphatically not to *correctness decisions*. Calculation logic, rule versioning, and filing behaviour need control, review gates, and sign-off. Knowing where to draw that line is a mature judgment and a good interview answer.

---

## 5. APPLE

**Evidence quality overall: WEAK. This is the honest section.**

| Claim | Evidence |
|---|---|
| **Functional organisation rather than business-unit structure; experts leading experts; leaders with deep domain expertise** | **E2** — "How Apple Is Organized for Innovation," *HBR* (2020), co-authored by Joel Podolny, then Dean of Apple University, and Morten Hansen. This is the strongest public source on Apple's structure. |
| **DRI (Directly Responsible Individual)** — one named person accountable for each item | **E3** — widely reported, including in Lashinsky's *Inside Apple* (2012); journalist account, not company-confirmed |
| **Deep secrecy; need-to-know compartmentalisation** | **E3** — consistently reported |
| **Apple's product management process, discovery methods, prioritisation, metrics practice** | **E4 — Public evidence insufficient.** Anyone who tells you "how Apple does product management" is almost certainly extrapolating from product outcomes. |

**What is genuinely transferable is the functional-organisation argument**, because it is published and reasoned: in a functional org, the people who decide are the people with the deepest expertise in the thing being decided, rather than general managers optimising a business unit's P&L. The published trade-off is that this requires leaders with real domain depth and it scales poorly across unrelated businesses.

**The DRI concept is worth stealing regardless of its provenance**, because it solves a real and universal problem: diffuse accountability. One name per decision, written down. That costs nothing.

**Do not tell an interviewer "Apple does X" unless X is in the HBR piece.** It is a common way to lose credibility with a panel that knows the literature.

---

## 6. MICROSOFT

**Evidence quality overall: MODERATE-TO-STRONG**, particularly for engineering practices and role definitions.

| Practice | Evidence |
|---|---|
| **PM role defined as understanding customer needs and translating them into prioritised requirements, working with engineering and design** | **E1** — Microsoft's public careers material describes the Product Manager role in these terms |
| **Historical "Program Manager" tradition; consolidation of PM/PgM titles** | **E1 historically; E3** for the specifics and timing of the consolidation |
| **Public agile transformation of the Azure DevOps team** — moving to short cycles, feature teams, continuous delivery | **E1/E2** — documented in a public blog series by Aaron Bjork and colleagues; unusually detailed and worth reading |
| **Cultural shift to "growth mindset," customer obsession, "learn-it-all not know-it-all"** | **E1/E2** — publicly stated by Satya Nadella; *Hit Refresh* (2017) |
| **Engineering system consolidation ("One Engineering System")** | **E2/E3** — publicly discussed by Microsoft engineering leaders |

**The transferable core for you specifically.** Microsoft's public Azure DevOps transformation writing is the **single most useful published account of a large enterprise team changing how it works** — feature teams, three-week sprints, a specific planning cadence, and honest description of what broke. Unlike most of the material in this volume, it is at a scale and in a context (enterprise software, long-lived product, real customers with contracts) that resembles yours. **If you read one thing from this volume, read that series.**

Microsoft is also the most useful company for you to study on the **Program Manager** tradition, given your TPM target. The Microsoft PM lineage was historically closer to "own the definition and coordinate the delivery" than to the Silicon Valley "mini-CEO" framing, and understanding that lineage will help you read job descriptions accurately.

---

## 7. OpenAI & ANTHROPIC (and AI labs generally)

**Evidence quality: MODERATE for published safety/technical artefacts; WEAK for internal product process. Highest volatility in this entire volume.**

**Disclosure:** I am a model made by Anthropic. I do not have privileged information about Anthropic's internal product practices, and I am not going to speculate about them. Everything below is what is publicly published.

| Practice / artefact | Evidence |
|---|---|
| **Public model documentation** — model cards, system cards, usage policies | **E1** — both labs publish these |
| **OpenAI: publishes a model spec describing intended model behaviour; publishes a preparedness/risk framework** | **E1** |
| **Anthropic: publishes a Responsible Scaling Policy, model cards, and safety research including Constitutional AI** | **E1** |
| **Evaluation-centric development** — capability and safety evals as the central artefact of model releases | **E1** — evident in both labs' published release documentation |
| **AI PM role scope: agents, developer platform/API, evals, safety and safeguards, model behaviour, enterprise deployment** | **E3** — a recurring pattern across public AI-lab job descriptions. Verify current postings yourself; these change monthly |
| **Internal prioritisation, roadmapping, and product review processes at either lab** | **E4 — Public evidence insufficient.** |

**The transferable core, and it's a big one: evals are the product spec.** In AI products, the artefact that defines "correct" is not a requirements document — it is an **evaluation suite**: a corpus of inputs, expected behaviours, and thresholds. Public model documentation from both labs is essentially an eval report. This is the mental model shift that defines AI PM, and Volume IX builds it out.

**Why this matters for your positioning.** You have built a 211-case UAT suite against a commission engine and found a real defect through it. That is structurally the same skill: define the behaviour space, build a test corpus, set a threshold, measure, and treat regression as a release blocker. **When you interview for AI PM roles, this is the story — not "I've used ChatGPT."** Almost every candidate has prompt experience; very few have built an evaluation harness for a system where being wrong has legal consequences.

**When NOT to copy AI-lab practices.** Their release cadence, tolerance for capability uncertainty, and research-driven roadmapping assume a research organisation with frontier models. If you are building an AI *feature* on someone else's model, your constraints are the opposite: you don't control the model, you control the evaluation, the fallback, and the workflow around it.

---

## 8. SPOTIFY — THE MOST IMPORTANT CASE IN THIS VOLUME

**Evidence quality: STRONG, including strong evidence that the famous version was never fully real.**

| Fact | Evidence |
|---|---|
| **The "Spotify model" — squads, tribes, chapters, guilds — was described in a 2012 whitepaper and video by Henrik Kniberg and Anders Ivarsson** | **E1** — published by the authors, who were working with Spotify |
| **The model was an aspirational snapshot, not a finished system, and Spotify itself moved on** | **E2** — publicly stated by people involved, including Kniberg cautioning against copying it and Joakim Sundén (a Spotify agile coach at the time) writing publicly that it was never fully implemented and that copying it was a mistake |
| **Spotify's current operating model** | **E4 — Public evidence insufficient.** |

**Why this is the most important case here.** The Spotify model became, for roughly a decade, the most copied organisational design in software — adopted by banks, telcos, and enterprises worldwide, complete with the vocabulary. It was copied from a **two-document description of an aspiration at one company at one moment**, by organisations that took the org chart and skipped the culture, autonomy, and trust the structure depended on. The people who wrote it publicly told everyone to stop.

**The four questions this teaches — apply them to everything else in this volume:**

1. **Is this a description of what they do, or what they aspire to?**
2. **Is it current?** Organisational models decay in 2–3 years.
3. **Am I copying the structure or the mechanism?** Structure without mechanism is theatre.
4. **What precondition does it depend on that I don't have?** (Netflix: talent density. Amazon: writing culture and senior review time. Spotify: trust and autonomy. Apple: deep-expert leaders.)

**The general law: practices are downstream of constraints.** Amazon writes because it is enormous and distributed. Netflix decentralises because it hires expensively. Apple centralises around function because it makes deeply integrated hardware. **Copy the constraint-analysis, not the artefact.**

---

## 9. STRIPE, UBER, AIRBNB

| Company | Publicly evidenced | Evidence | Insufficient |
|---|---|---|---|
| **Stripe** | API design as a first-class product: explicit versioning, backwards-compatibility discipline, documentation treated as a product surface. Publishes *Increment* magazine and Stripe Press | **E1** — visible in and stated by their public API documentation and versioning policy; **E3** for the internal culture that produces it | Internal PM process: **E4** |
| **Uber** | Extensive public engineering blog: ML platform (Michelangelo), data platform, mobile architecture | **E1** — company engineering blog | Product management process: **E4 — Public evidence insufficient** |
| **Airbnb** | Publicly eliminated the standalone traditional PM role, merging product management and product marketing into a single function, with founder-led design review and a functional org | **E2** — stated repeatedly and publicly by Brian Chesky in interviews and talks (2022–2023) | Current details and durability of the change: **E3/E4** |

**Stripe is the most directly relevant of the three to you**, because your work is API- and integration-heavy and your platform ambitions are real. Their public API versioning and backwards-compatibility policy is a **case study in treating a contract as a product**: you can read the actual artefact rather than a description of it. Volume VIII builds on this.

**Airbnb is the most interesting counterexample in this volume.** A well-known company publicly concluded that the standard PM role was wrong *for them*, and said so on the record. Whatever you think of the decision, it is a useful antidote to the assumption that the Silicon Valley PM model is a law of nature. **Good interview material:** being able to discuss it thoughtfully signals that you think about operating models rather than just following one.

---

## 10. THE COMPARISON MATRIX (Part XXXIV)

Cells are labelled with evidence strength. **"Insufficient" is used liberally and honestly.** Read the cells as *what the company has publicly said or published about itself*, not as verified internal reality.

| Practice area | Amazon | Google | Meta | Netflix | Apple | Microsoft | OpenAI | Anthropic | When useful to you |
|---|---|---|---|---|---|---|---|---|---|
| **Customer obsession** | LP #1, enforced via PRFAQ mechanism (E1/E2) | Stated; "focus on the user" (E1, founders' letter) | Insufficient | Stated in culture doc (E1) | Implied by functional model (E2) | Publicly stated cultural pillar (E1/E2) | Insufficient | Insufficient | Always — but only if you attach a forcing function |
| **Product discovery method** | Working Backwards / PRFAQ (E1/E2) | Design Sprint (E1, from GV) | Insufficient | Insufficient | Insufficient | Insufficient | Insufficient | Insufficient | PRFAQ for big bets; Design Sprint for bounded problems |
| **Strategy artefact** | Narrative memo (E1/E2) | OKRs (E1) | Insufficient | "Context not control" briefing (E1, principle only) | Insufficient | Insufficient | Insufficient | Insufficient | Write a narrative; use OKRs only for measurement |
| **Roadmap practice** | Insufficient | Insufficient | Insufficient | Insufficient | Insufficient | Insufficient | Insufficient | Insufficient | **Nobody's roadmap process is well documented. Ignore anyone who claims otherwise.** |
| **Decision making** | One-way/two-way doors; Disagree and Commit (E1) | Insufficient (OKR-adjacent) | Insufficient | Highly decentralised, "informed captain" (E1/E2) | DRI (E3) | Insufficient | Insufficient | Insufficient | Adopt door-classification and named-DRI immediately; both are free |
| **Product review** | Narrative-read meetings; WBR on input metrics (E2) | Insufficient | Insufficient | Insufficient | Insufficient | Insufficient | Insufficient | Insufficient | Silent-read reviews work at any size ≥8 people |
| **Experimentation** | Insufficient (public detail thin) | SRE/measurement culture (E1); HEART (E1) | Published experimentation platform + papers (E1) | Published experimentation series (E1) | Insufficient | Insufficient | Eval-driven releases (E1) | Eval-driven releases (E1) | Only where you have power to detect an effect |
| **Metrics philosophy** | Controllable **input** metrics over outputs (E2) | OKRs + HEART + SLOs (E1) | Insufficient | Insufficient | Insufficient | Insufficient | Eval benchmarks (E1) | Eval benchmarks + RSP thresholds (E1) | **Input-metric focus is the most portable idea here** |
| **Eng collaboration** | Two-pizza / single-threaded ownership (E2) | SRE + error budgets (E1) | Bootcamp; eng-led culture (E1/E2) | Insufficient | Functional, expert-led (E2) | Feature teams, published transformation (E1/E2) | Insufficient | Insufficient | Error budgets; feature teams |
| **Technical depth expected of PM** | Insufficient (varies by org) | Insufficient (varies) | E3 — analytics/technical fluency reflected in public postings | Insufficient | E2 — expert leadership implies depth | E1 — role descriptions emphasise translating needs to specs with eng | E3 — AI/technical depth in public postings | E3 — same | Depth is role-specific, not company-specific. **Read the actual JD.** |
| **Product ownership model** | End-to-end team ownership (E2) | Insufficient | Insufficient | Insufficient | Functional, not GM (E2) | Insufficient | Insufficient | Insufficient | End-to-end ownership is near-universally good |
| **Launch process** | Insufficient | Production readiness reviews (E1, SRE book) | Insufficient | Insufficient | Insufficient | Insufficient | System cards / staged release (E1) | Model cards / staged release, RSP (E1) | Adopt a readiness checklist regardless (Volume XI) |
| **Autonomy** | High within teams, mechanism-constrained (E2) | Insufficient | Insufficient | Very high, explicitly (E1) | Lower; functional coordination (E2) | Insufficient | Insufficient | Insufficient | Autonomy scales with talent density and consequence-of-error |
| **Documentation culture** | Very high, narratives (E1/E2) | High (design docs, SRE book) (E1) | Insufficient | Memo culture (E1/E2) | Low/secretive (E3) | Insufficient | High for model docs (E1) | High for model/safety docs (E1) | **Writing is the cheapest scaling mechanism that exists** |
| **AI product practice** | Insufficient | Insufficient (research publications ≠ product process) | Insufficient | Insufficient | Insufficient | Insufficient | Model spec + preparedness framework (E1) | RSP + model cards + Constitutional AI research (E1) | Study the published artefacts, not the imagined process |
| **Platform thinking** | AWS as an internal-platform-turned-product (E2/E3) | Insufficient for PM process | Insufficient | Insufficient | Insufficient | Insufficient | API platform (E1, the product itself) | API platform (E1, the product itself) | Stripe's public API policy is the better study |

### 10.1 What the matrix actually tells you

Look at the **Roadmap practice** row: every cell is "Insufficient."

That is the most important finding in this volume. **The practice PMs argue about most is the one with essentially zero credible public evidence from elite companies.** Every confident claim you've read about "how FAANG does roadmaps" is extrapolation, consultancy marketing, or one person's experience on one team generalised into a law.

Contrast with the rows that are well-evidenced: decision classification, error budgets, input metrics, written narratives, published evaluation artefacts. **Those are the practices worth importing, because they are documented, mechanism-based, and portable.**

---

## 11. PRACTICE → CONTEXT → ADOPT / DON'T ADOPT

The decision table. Use this instead of the matrix when you're actually choosing something to try.

| Practice | Origin | Constraint it was built for | Adopt when | Do NOT adopt when | Cheap version for a mid-size team |
|---|---|---|---|---|---|
| **PRFAQ / Working Backwards** | Amazon (E1/E2) | Huge org, many stakeholders, expensive mistakes | Big bets, new products, cross-org initiatives | Small teams; exploratory work; no critique culture | One-page customer letter before any 2+ week project |
| **Six-page narrative + silent read** | Amazon (E1/E2) | Meetings where presentation skill was beating substance | Meetings ≥8 people; complex decisions | Standups; small high-context teams | 2-page memo, 10-min silent read |
| **One-way / two-way doors** | Amazon (E1) | Growing org applying heavy process to everything | **Always. Free. Adopt today** | Never a reason not to | Tag every decision in your log |
| **Error budgets / SLOs** | Google (E1) | Endless reliability-vs-features conflict | You have a recurring quality-vs-speed fight | No reliable measurement of the quality dimension | A **correctness budget** for compliance defects |
| **OKRs** | Intel→Google (E1) | Aligning many teams on measurable outcomes | Teams genuinely own outcomes | Tied to compensation; teams lack control; plans written after the fact | 1 objective, 3 KRs, per team, per quarter. Nothing more |
| **HEART metrics** | Google (E1) | UX quality being unmeasurable | Defining metrics for a UX-heavy surface | Mandated-use products (engagement misleads) | Goals-Signals-Metrics on one workflow |
| **Design Sprint** | GV (E1) | Slow, consensus-bound decision cycles | A bounded problem and 5 clear days | Ongoing discovery; ill-defined problem space | 2-day version; skip the full prototype |
| **Continuous discovery / OST** | Torres (E1, practitioner) | Teams building without customer contact | You can reach customers weekly | Seasonal access constraints (adapt per Vol II §11.2) | Biweekly, off-season-weighted |
| **Context not control** | Netflix (E1) | Slow decisions from senior, expensive people | High talent density; reversible decisions | Junior teams; regulated correctness decisions | Publish the strategy + the constraints, monthly |
| **DRI** | Apple (E3) | Diffuse accountability | Always. Free | Never | One name in every doc header |
| **Bar Raiser** | Amazon (E1/E2) | Hiring bar eroding under growth pressure | You're scaling hiring fast | Tiny teams; no trained interviewers | One neutral interviewer with a real veto |
| **Squads/tribes/chapters** | Spotify 2012 (E1, aspirational) | A specific company at a specific moment | **Rarely. See §8** | You're copying the org chart, which is the usual case | Skip. Solve the actual coordination problem instead |
| **Eval-driven release gates** | AI labs (E1) | Non-deterministic systems | **Any AI feature. Also any calculation engine** | Purely deterministic UI work | A regression corpus + a threshold + a blocker rule |
| **API versioning + backwards-compat policy** | Stripe (E1) | Thousands of integrators who cannot be broken | Any external API | Purely internal, single-consumer APIs | A written deprecation policy, published |

---

## 12. HOW TO USE COMPANY PRACTICES IN AN INTERVIEW (without sounding like a cargo cultist)

This matters practically for your job search, so it's worth being explicit.

**Weak answer:** *"I'd use the Amazon Working Backwards approach because it's a best practice at FAANG."*
Signals: you copy, you don't reason, and you use "FAANG" as an authority.

**Strong answer:** *"I'd write something like a PRFAQ, but I'd be honest that the reason Amazon's version works is the review culture around it, not the format. On a team of eight I'd do a one-page customer letter instead — the forcing function I actually want is that we can't fund the work until someone has written what changes for the customer. The six-page version would be rigour theatre at our size."*
Signals: you know the source, you know the mechanism, you know the precondition, and you've adapted for constraints. **That is what a Senior PM sounds like.**

The general shape: **name the source → name the mechanism → name the precondition → adapt to your constraint → say what you'd measure to know it's working.**

---

## 13. VOLUME IV EXERCISES

**Exercise 4.1 — Mechanism extraction.** Pick three practices you admire. For each write: what behaviour does it force, what happens if you skip it, what precondition does it need. Then mark which preconditions you have.

**Exercise 4.2 — The correctness budget.** Design a Google-style error budget for your compliance product, but on correctness rather than uptime. Define: the metric, the threshold, the measurement method, and what stops when it's breached. *Deliverable: a one-page proposal. This is genuinely novel in most compliance orgs and is exactly the kind of mechanism a Senior PM is expected to invent.*

**Exercise 4.3 — Cargo cult audit.** List every process your team runs. For each: where did it come from, what problem does it solve, what would break if you stopped. *Most teams find 2–3 rituals that would cost nothing to delete.*

**Exercise 4.4 — Evidence discipline drill.** Take three claims you've read about how a famous company works. Try to find the primary source. Note how many you can't. *This habit will save you in interviews.*

---

## 14. VOLUME IV INTERVIEW BANK

1. What's a practice from another company you'd bring to us — and what would you *not* bring?
2. Why do you think the Spotify model failed to transfer?
3. How would you introduce a new process to a sceptical team?
4. What's the difference between a process and a mechanism?
5. When should a team NOT use OKRs?
6. Amazon uses six-page narratives. Would you? Defend either answer.
7. How would you decide whether to adopt a practice you read about?
8. Netflix emphasises autonomy. Where would autonomy be dangerous in our product?

---

*Volume IV complete. Continue to `99-master-map-and-closing.md`, or say `build vol 5` to continue the curriculum in sequence.*
