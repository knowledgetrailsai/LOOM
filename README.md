# Loom: OASIS Human–AI Workflow and Experience Engineering

A human–AI workflow companion to the OASIS methodology — redesigning work around complementary human and machine strengths, organized as a **control plane**: authority, evidence and fallback decided at design time, not discovered during an incident.

```
TASK/DECISION → AI CONTRIBUTION → HUMAN CONTRIBUTION → AUTHORITY → EVIDENCE → FALLBACK → FEEDBACK → OUTCOME
```

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-yellow.svg)](LICENSE)
![Status](https://img.shields.io/badge/status-draft%20v1.0-orange)

**Companion repository:** [OASIS](https://github.com/knowledgetrailsai/OASIS) methodology — primarily [Chapter 16 — Human–AI Workflow and Experience Engineering](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-16-human-ai-workflow-and-experience-engineering.md), plus [Architecture Perspective 3: Process Architecture](https://github.com/knowledgetrailsai/OASIS/blob/main/architecture/perspective-03-process-architecture.md), Chapter 17, Chapter 18, and Chapter 24.

## Why This Exists

Most AI programs succeed or fail here — not on model quality, but on whether the surrounding work was redesigned for the new division of labor. A workflow that never specifies who has authority over a decision, or what a person sees before approving an AI-prepared action, is an **unfinished design**, not a training gap.

```
Governing question: who is allowed to do what with the system,
and how do a human and a machine hand work back and forth?
```

Loom gives this full operational treatment: the Human–AI Workflow Blueprint that names authority, evidence and fallback per step; the six-mode progressive autonomy ladder and the evidence that justifies moving up or down it; trust calibration for appropriate (not maximum) reliance; how a single hand-off sits inside a longer process a human still owns end to end; and the change-and-capability work that has to start at discovery, not at training.

## Start Here

New to this repository? Read [00-navigation-and-methodology/how-to-use-this-repository.md](00-navigation-and-methodology/how-to-use-this-repository.md) — it routes you by role and task. See [00-navigation-and-methodology/knowledge-map.md](00-navigation-and-methodology/knowledge-map.md) for the full model, including a worked example tracing one workflow end to end through every section below.

## Repository Structure

### 00 · Navigation and Methodology
- [Knowledge Map](00-navigation-and-methodology/knowledge-map.md)
- [How to Use This Repository](00-navigation-and-methodology/how-to-use-this-repository.md)

### 01 · Foundations
- [Why This Is Engineering](01-foundations/why-this-is-engineering.md)
- [Principles](01-foundations/principles.md)
- [Roles and Ownership](01-foundations/roles-and-ownership.md)

### 02 · Workflow Blueprint
- [Overview](02-workflow-blueprint/blueprint-overview.md)
- [Authority and Evidence](02-workflow-blueprint/authority-and-evidence.md)
- [Template](02-workflow-blueprint/template.md)

### 03 · Progressive Autonomy
- [Autonomy Ladder](03-progressive-autonomy/autonomy-ladder.md)
- [Promotion and Demotion Criteria](03-progressive-autonomy/promotion-and-demotion-criteria.md)

### 04 · Trust Calibration
- [Appropriate Reliance](04-trust-calibration/appropriate-reliance.md)
- [Interface Design Levers](04-trust-calibration/interface-design-levers.md)
- [Behavioral Signals](04-trust-calibration/behavioral-signals.md)

### 05 · Process Architecture Integration
- [Process-to-Agent Participation Map](05-process-architecture-integration/process-to-agent-participation-map.md)
- [Process Ownership Model](05-process-architecture-integration/process-ownership-model.md)
- [Process Risk Classification](05-process-architecture-integration/process-risk-classification.md)

### 06 · Change and Capability
- [Change and Capability](06-change-and-capability/change-and-capability.md)
- [Adoption and Training](06-change-and-capability/adoption-and-training.md)
- [Transition Metrics](06-change-and-capability/transition-metrics.md)

### Reference
- [Glossary](glossary/terminology.md)
- [Templates](templates/human-ai-workflow-blueprint.yaml)
- [Full Index](INDEX.md)

## Relationship to Companion Repositories

- **[OASIS](https://github.com/knowledgetrailsai/OASIS)** — the parent methodology; Loom implements its human–AI workflow chapter specifically, the way [Helm](https://github.com/knowledgetrailsai/HELM) implements deployment/operations and [Forge](../Forge) implements data and knowledge engineering.
- **[Forge](../Forge)** — the data and knowledge companion (Chapter 15); the evidence shown to a reviewer in Loom's workflow blueprint depends on Forge's grounding policy and readiness assessment.
- **[Helm](https://github.com/knowledgetrailsai/HELM)** — escalation triggers and override rates named in a Loom workflow blueprint feed Helm's incident-response and learning-loop instrumentation.
- **[Nexus](https://github.com/knowledgetrailsai/Nexus)** — the opportunity catalog; a use case's human-in-the-loop shape is decided here once it reaches engineering.

## Status

Scaffold stage — structure and first-pass content drafted section by section from the OASIS methodology and its architecture companions. See each section for what's drafted versus still a stub.

## License

Content licensed under [CC BY-SA 4.0](LICENSE), matching the parent OASIS methodology. Credit Shripadraj Mujumdar, KnowledgeTrails, and Loom; indicate changes and release adaptations under the same license.

## About Us

**Shripadraj Mujumdar** is an Agentic AI & Automation Strategist, Advisor, and Responsible AI Expert with 28+ years of experience in enterprise architecture and AI-driven transformation, including deep hands-on work in Agentic AI, Generative AI, and enterprise data and knowledge platforms. His practice spans designing multi-agent systems, knowledge-graph and RAG architectures, accelerated delivery capabilities, and Responsible AI governance frameworks aligned to global regulatory standards. This methodology ecosystem distills that practitioner experience — architecture, delivery, evaluation, governance, and economics — into a single, reusable body of work.
