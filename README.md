# Trust-Based Responsible AI & Governance — Reference Framework for Regulated Banking

A vendor-neutral, **reusable** reference model for governing AI across the *build* and *run* phases
of a regulated financial-services platform. It captures the **framework layer only** — operating
model, control plane, regulatory mapping, roadmap and intake patterns — with no client, partner,
product, pricing or deal-specific content.

Part of the **AI Governance-as-Code** body of work: governance expressed as portable, versionable,
auditable artefacts rather than static documents.

## What's in here

| File | Purpose |
|---|---|
| [`trust-based-rai-governance-framework.md`](trust-based-rai-governance-framework.md) | The full reference framework (principles → operating model → architecture → regulatory mapping → ro[...] 
| [`examples/use-case-classification.yaml`](examples/use-case-classification.yaml) | Governance-as-code example: a machine-readable AI use-case record + classification. |
| [`examples/control-mapping.yaml`](examples/control-mapping.yaml) | Governance-as-code example: mapping a control to public frameworks with evidence. |

## The core idea

> Responsible AI & Governance is the **trust fabric** of an AI-assisted, AI-enabled platform — what
> makes it explainable, controllable, resilient and evidence-ready for its board, its customers and
> its supervisors.

Trust is the governance objective, not a replacement for risk management. Regulations and standards
such as the EU AI Act and NIST AI RMF use risk assessment and proportionate controls to help establish
trustworthy AI. This framework makes that relationship explicit: risk is managed; trust is evidenced.

Built on three design commitments:

1. **Build the framework, then operationalise it** — governance defined from day one, light in build, deepening in run.
2. **One decision path · one coordination point · one evidence chain** — embedded, not bolted-on.
3. **Reuse-first, proportionate, vendor-neutral** — reuse existing SDLC/ITSM/IAM/logging; native-capability-led; controls scale with the AI adoption curve.

## Standards referenced (all public)

ISO/IEC 42001 · ISO/IEC 23894 · ISO/IEC 27001 · EU AI Act · DORA · GDPR · NIS2 · NIST AI RMF · OECD AI Principles · FINOS AI Governance Framework. See the [research basis](trust-based-rai-governance-framework.md#10-research-basis) for primary-source links.

## Who it's for

Solution architects, AI governance leads, risk & compliance teams, and delivery partners building or
running AI on regulated banking platforms — as a starting scaffold to fork and adapt.

## Status & contributions

Reference material, provided as-is. Issues and pull requests welcome. The project is licensed under the MIT License — see [LICENSE](LICENSE).

---

> This is a generalised reference model. It contains no confidential, client-specific or
> organisation-specific information and is intended for open reuse.
