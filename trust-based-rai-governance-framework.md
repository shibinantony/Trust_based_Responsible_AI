# Trust-Based Responsible AI & Governance — Reference Framework for Regulated Banking

> A vendor-neutral, reusable reference model for governing AI across the **build** and **run**
> phases of a regulated financial-services platform. It is designed to be adopted as-is,
> forked, or embedded into a wider solution architecture.
>
> **Scope:** frameworks, operating models, control mappings and patterns only.
> No client, partner, product, pricing or deal-specific content.

---

## 0. How to read this framework

This is a **reference model**, not a product. It expresses one idea:

> Responsible AI & Governance is the **trust fabric** of an AI-assisted, AI-enabled platform —
> the thing that makes the platform explainable, controllable, resilient and evidence-ready
> for its board, its customers and its supervisors.

The framework is organised as:

1. Governing principle (trust) → 2. Phased posture (build the framework → operationalise it)
→ 3. Operating model & RACI → 4. Reference architecture (four-layer control plane)
→ 5. Regulatory mapping → 6. Roadmap pattern → 7. Tooling posture → 8. Resourcing & intake model.

Everything is **proportionate and reuse-first**: start light, reuse existing SDLC / ITSM / IAM /
logging / evidence stores, and expand the governance footprint only as AI adoption, autonomy and
risk increase.

---

## 1. Governing principle — trust as the design goal

AI use cases are organised around **demonstrable trust**, answered with four questions for every
use case:

- **Who benefits?**
- **Who remains accountable?**
- **What evidence proves acceptable behaviour?**
- **How do people intervene or recover?**

A common set of **Responsible AI tenets** applies consistently, and the *depth* of assurance rises
with the AI's intended purpose, decision influence and autonomy:

| Tenet | Governing question |
|---|---|
| **Accountability** | Is there a named human owner for this AI's behaviour and outcomes? |
| **Fairness** | Is the outcome equitable across affected populations, and is that tested? |
| **Security** | Is the AI, its data and its tooling protected against misuse and attack? |
| **Privacy** | Is personal data minimised, secured, transparent and lawful across the lifecycle? |
| **Transparency** | Can we explain what the AI does, why, and disclose when a human is interacting with it? |

> Generative AI is treated as primary; **agentic AI is introduced selectively and semi-autonomously
> under human approval**, with autonomy earned progressively under governance.

---

## 2. Phased governance posture — build the framework, then operationalise it

Governance is defined **from the build phase**, not as an afterthought, with a deliberately light
initial footprint that grows as AI adoption scales — tracked by a continuous **regulatory watch**.

| Phase | Governance activity | Nature of work |
|---|---|---|
| **Build** | Create the framework: policy, classification method, controls, reference architecture, evidence model — embedded into the solution design. | *Framework-building* |
| **Run** | Operationalise the framework: continuous monitoring, evidence generation, incident & change governance, supervisory reporting. | *Operationalising* |

### 2.1 AI in the build phase — AI-assisted delivery
AI accelerates the engineering work *around* the regulated core (which typically does not permit
in-product AI automation) and feeds validated inputs into it.

| Use case | What the AI does | Autonomy & trust controls |
|---|---|---|
| Requirements generation | Generates/structures requirements for customisation and integration | Generative; human review & sign-off; grounding & provenance |
| Architecture & design | Produces design artefacts and diagrams from requirements | Generative / light agentic; human approval; traceable rationale |
| Test case & script generation | Creates functional and integration tests | Light agentic; human oversight; coverage evidence |
| Infrastructure-as-Code / CI-CD | Generates pipeline, container and deployment artefacts | Agentic with human approval gates; secure-pipeline controls |

### 2.2 AI in the run phase — AI-enabled IT operations
In run, AI supports **IT operations** rather than core business operations. The framework built
earlier is now operationalised — controls run continuously, generate evidence and feed reporting.

| Use case | What the AI does | Autonomy & trust controls |
|---|---|---|
| Incident / problem / change | Assists triage, root-cause and change management via ITSM | Agentic, semi-autonomous; human approval; segregation of duties |
| Operational fixes & integration | Generates code fixes, adapters/connectors, queries | Bounded permissions; approval gates; kill/rollback; immutable logs |
| Observability | Monitors platform and pipeline health, surfaces anomalies | On-the-loop human oversight; audit trail |

> **Autonomy curve:** progresses under governance from a majority-human balance in early build
> toward a higher agentic share over time; the governance footprint scales *in step*.

---

## 3. Operating model — one path, one point, one chain

Three principles keep governance embedded rather than bolted-on as a separate approval gate:

- **One accountable decision path** — the regulated entity retains accountability for trust outcomes.
- **One coordination point** — a single AI Governance function for intake, forum, evidence status and escalations.
- **One versioned evidence chain** — a single, stable, auditable record per use case.

### 3.1 Generic roles & accountabilities

| Role (generic) | Accountability |
|---|---|
| **Regulated entity — governance & risk owners** | Accountable for trust outcomes, policy direction, use-case acceptance, board/supervisory linkage; validate classification; approve production activation. |
| **Account & programme leadership** | Owns proposal integration, commercial commitments, customer interface, delivery prioritisation; confirms included tools and use cases. |
| **AI Governance practice** | Single coordination point; provides use-case assessment, control mapping, classification method and assurance design. |
| **Regulatory & assurance advisor** | Regulatory advisory, audit-readiness, explainable-AI assurance for supervisory engagement. |
| **Delivery, platform & cloud teams** | Provide feature/config facts; implement controls in architecture, SDLC and run; generate test, release, log, change and incident evidence. |

### 3.2 RACI template for key governance activities
`A = Accountable · R = Responsible · C = Consulted · I = Informed`
*(Accountability retained by the regulated entity; delivery partners responsible for building and operating controls.)*

| Governance activity | Regulated entity | Account | AI Gov | Assurance advisor | Delivery | Platform vendor |
|---|:--:|:--:|:--:|:--:|:--:|:--:|
| AI policy & risk appetite | A | C | R | C | I | I |
| AI use-case inventory & classification | A | I | R | C | C | C |
| Classification memo approval | A | I | R | C | I | I |
| Control implementation (SDLC / Run) | I | A | C | I | R | C |
| Supplier assurance (vendor AI / partners) | A | C | R | C | C | R |
| Monitoring, evidence & audit (Run) | A | I | R | C | R | I |
| Supervisory / Board reporting | A | C | R | R | I | I |

### 3.3 Cadence & the single evidence chain
- **Change-triggered intake** — any new use case, model, tool or autonomy change updates inventory, classification and controls *before* go-live.
- **Joint governance forum** — feeds the existing programme steering rather than adding a separate structure.
- **Lifecycle assurance gates** — `design → pre-test → pre-release → material change → retirement`, embedded in the delivery pipeline.
- **One evidence chain**, linked by a stable use-case identifier and stored in an immutable (WORM) repository:

```
trust card → classification → control plan → build/release evidence
           → run/incident evidence → consolidated board / resilience / supervisory reporting
```

---

## 4. Reference architecture — a four-layer control plane

The Responsible AI & Governance control plane is **embedded** into the technical architecture,
governing AI across four layers. The AI execution surface doubles as the base governance
instrument, so control, traceability and evidence are **native to where AI runs** rather than
bolted on through separate tooling (which reduces vendor lock-in).

> **Segmentation pattern (optional, common in regulated banking):** a *gateway / neutral zone*
> that ring-fences the institution and admits only validated, regulator-ready transactions into a
> *core / main zone* for execution, ledger posting and enterprise data ownership. Data lineage,
> PII and residency are governed *across* both zones.

| Layer | What it governs |
|---|---|
| **Strategic** | Use-case governance, AI risk appetite, risk-tiering at intake, third-party/vendor governance, cost-to-value. |
| **Functional** | Agents, orchestration & knowledge: agent identity and scope, model & prompt governance, RAG source control, decision thresholds. |
| **Technical** | Data, tools, platform & security: data lineage / PII / residency, tool permissions & sandboxing, IAM / least-privilege, prompt-injection controls, safety filters. |
| **Operational** | Observability & assurance: logs & traces, KPIs, audit & incident governance, human-oversight approvals, change-impact & rollback. |

**Cross-cutting control plane over all four layers:**
- The RAI tenets — *Accountability · Fairness · Security · Privacy · Transparency*
- Regulatory compliance — *EU AI Act, GDPR, NIST AI RMF, ISO/IEC 27001 / 42001 / 23894, DORA, NIS2, national supervisory expectations*
- A **human-control spectrum** — `Human-in-Command → in-the-Loop → on-the-Loop → out-of-the-Loop`
- Agents governed as **digital workers** (identity, scope, permissions, audit).

### 4.1 The governance control instrument (capability, not a product)
A governance & compliance capability should embed governance **where AI executes**: trace every
prompt, agent and action (which agent, who enabled it, full audit trail), apply role-based access
control, and land evidence natively in an immutable (WORM) store — while remaining framework-aligned
(ISO/IEC 42001, EU AI Act, FINOS). This avoids a separate governance-tool footprint and its
associated lock-in.

---

## 5. Regulatory & standards mapping

Regulatory obligations are implemented as **evidence views over one control system** (governed by
ISO/IEC 42001) — not as separate parallel programmes. Legal interpretation and classification remain
with the regulated entity's Legal & Compliance (supported by an assurance advisor); the AI Governance
function defines the method, evidence model and control mapping.

| Framework | What it requires for AI | Primary evidence |
|---|---|---|
| **ISO/IEC 42001 (AIMS)** | The AI Management System spine — policy, roles, impact assessment, controls, audit, continual improvement. | AIMS documentation; control catalogue; audit records |
| **EU AI Act** | Know the AI in use, its purpose and accountable owner; classify by risk; apply proportionate controls; transparency & AI literacy. | AI inventory; classification memo; model/system cards; oversight & test evidence |
| **DORA (incl. Art. 30(3))** | ICT resilience, incident reporting, third-party oversight, uninterrupted supervisory/audit access — AI must not weaken any of it. | Third-party register; resilience tests; incident chronology; audit-access evidence |
| **GDPR & national DP** | Personal data in prompts, models, test data and operations stays limited, secure, transparent, accountable; EU residency by design. | Data lineage; DPIA; access & minimisation; rights handling |
| **NIS2** | Cyber hygiene, least-privilege, vulnerability control, incident accountability across AI tooling. | Identity & access matrix; security tests; vulnerability evidence |
| **National supervisor / ECB-SSM** | Entity retains supervisory accountability; supports inspection and prudential reporting (e.g. COREP/FINREP). | Approved classification; bilingual evidence index; supervisory pack |
| **NIST AI RMF** | Common operating language — *Govern / Map / Measure / Manage* — aligned to ISO/IEC 42001. | Risk register; control-test cadence |
| **FINOS (open framework)** | Open financial-services AI governance framework; align and embed as a control reference. | Mapped control catalogue; governance-as-code checks |

> **Design intent:** governance is proportionate and cost-aware. Reuse existing SDLC, ITSM, IAM,
> WORM evidence and centralised logging; embed controls into the delivery pipeline; keep a light
> footprint in early build that expands with adoption.

---

## 6. Roadmap pattern — framework → operationalise

A generic, phase-aligned roadmap mapped to a `30 / 60 / 90 / 120`-day operational cadence with a
defined outcome at each stage.

| Horizon | Phase focus | Key governance actions | Outcome |
|---|---|---|---|
| **Phase 1** | Build – Identify | AI use-case inventory across build, run and vendor AI offerings; risk-tiering; embed the RAI framework into the architecture. | Framework baseline & risk view |
| **Phase 2** | Build – Framework setup | AI policy, roles & RACI; approval gates; configure governance-studio controls; align to compliance-by-design & DORA. | Framework built; light-touch controls |
| **Phase 3** | Build – Embed controls | Embed controls in SDLC/CI-CD; model/system cards; logging; human oversight; secure gates; XAI evidence design where selected. | Governed build; evidence capture begins |
| **Phase 4** | Run – Operationalise | Operationalise monitoring; incident/change linkage via ITSM; resilience/supervisory-ready reporting from the WORM chain. | Governed run; audit-ready reporting |
| **Beyond** | Run – Scale & improve | Expand agentic & vendor AI adoption under governance; periodic audits, re-classification, policy updates. | Scaled, continuously assured AI |

The governance footprint tracks the **AI adoption curve** — light in build, deepening in run.

---

## 7. Tooling posture — reuse-first, capability-led

Governance is operationalised through **tooling rather than manual effort**, but tooling is
capability-led and reuse-first. Lead with certified native capability; treat any third-party
governance product as an *option layered only where it demonstrably extends the native controls*,
never as a default. This avoids vendor lock-in and keeps total cost of ownership honest.

### 7.1 Native capability (primary)
| Capability | Role in governance |
|---|---|
| Governance & Compliance control instrument | Base control — prompt/agent/action tracing, RBAC, policy enforcement, audit evidence, native to where AI executes. |
| ISO/IEC 42001 AI Management System | Certified management-system spine — policy packs, classification method, control catalogue, audit evidence. |
| Red-teaming & AI assurance | Adversarial & robustness testing across GenAI and agentic use cases, feeding the release gate and monitoring. |
| Solution-native controls | Reuse existing ITSM/GRC, IAM, SIEM/SOAR, centralised logging and WORM evidence store rather than duplicating tooling. |

### 7.2 Third-party landscape — evaluate by *category*, not by name
When a genuine gap exists, evaluate the market by **capability category** and confirm pricing via a
vendor RFI. Weigh EU data-residency, integration with the existing architecture, and total cost of
ownership.

| Capability category | Typical coverage | Selection notes |
|---|---|---|
| Design-time governance & policy packs | Build-phase policy, model factsheets, classification templates | Prefer EU-native templates where residency matters |
| Continuous monitoring & GRC | Drift / bias / quality monitoring, evidence reuse, GRC workflows (Run) | Must integrate with existing logging & evidence chain |
| LLM & agentic red-teaming | Pre-release validators, jailbreak tests, run-time policy enforcement | Layer only where native red-teaming has a proven gap |

> Any third-party tool is added **only** where it demonstrably extends the native controls.

---

## 8. Resourcing & intake model

### 8.1 Resource-sizing principles (no figures — principle-only)
Detailed FTE loading and commercials are always confirmed after use-case scope; this framework
carries **principles**, not numbers:

- **RAI lead / architect** drives framework build, control mapping, classification method, supplier assurance design — heaviest in build.
- **Governance analyst(s)** scale with use-case count and risk tier (inventory, classification, evidence, memos).
- **Governance operations (Run)** are steady-state: monitoring, re-classification, audits, reporting, forum facilitation.
- **Red-teaming & assurance** are per-release and periodic in run.
- **Platform licence & implementation** only if a third-party tool is selected; otherwise native.
- **Training & enablement** covers AI literacy (EU AI Act Art. 4), role-based RAI training, supplier awareness.

> **Reuse-first principle:** reuse existing SDLC / ITSM / IAM / logging; add specialist effort or
> tooling only for a proven gap. Loading is light in build, increases into run as adoption scales.

### 8.2 Governance intake model — the operational front door
A single, lightweight intake path ensures every new or changed AI capability is governed before
it goes live, without becoming a bottleneck.

| Step | Trigger | Action & output |
|---|---|---|
| **1. Register** | New/changed use case, model, tool or autonomy level | Log in AI inventory with owner, purpose and data; assign a stable use-case ID |
| **2. Classify** | Registration complete | Risk-tiering; draft classification memo; determine control depth |
| **3. Plan controls** | Classification agreed | Map controls to ISO 42001 / DORA / GDPR / NIS2; identify reuse vs new effort |
| **4. Assure** | Before release | Evidence review; red-teaming where warranted; human-oversight sign-off at the gate |
| **5. Operate & review** | Live in run | Continuous monitoring; periodic re-classification; feedback into policy & roadmap |

The intake path is the operational front-door to the evidence chain (§3.3) and scales with the AI
adoption curve — light and fast in build, deepening into continuous assurance in run.

---

## 9. Reuse checklist

- [ ] Adopt the RAI tenets (§1) as your baseline principles.
- [ ] Split governance into **build (framework) vs run (operationalise)** (§2).
- [ ] Stand up **one decision path, one coordination point, one evidence chain** (§3).
- [ ] Deploy the **four-layer control plane** with the human-control spectrum (§4).
- [ ] Map obligations as **evidence views over one control system** (§5).
- [ ] Sequence delivery with the **framework → operationalise roadmap** (§6).
- [ ] Lead with **native capability**, evaluate third-party tools by category (§7).
- [ ] Run every change through the **5-step intake model** (§8.2).

---

*Reference framework · vendor-neutral · regulator-aligned. Provided as reusable material.
See `LICENSE` for terms. Contributions welcome via pull request.*
