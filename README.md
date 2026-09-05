# Loom: OASIS Human–AI Workflow and Experience Engineering

A human–AI workflow companion to the OASIS methodology that redesigns work around complementary human and machine strengths. It functions as an operating system for the handoff itself: authority, evidence, and fallback get decided at design time, not discovered during an incident.

```
TASK/DECISION → AI CONTRIBUTION → HUMAN CONTRIBUTION → AUTHORITY → EVIDENCE → FALLBACK → FEEDBACK → OUTCOME
```

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-yellow.svg)](LICENSE)
![Status](https://img.shields.io/badge/status-draft%20v1.0-orange)

**Companion repository:** [OASIS](https://github.com/knowledgetrailsai/OASIS) methodology — primarily [Chapter 16 — Human–AI Workflow and Experience Engineering](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-16-human-ai-workflow-and-experience-engineering.md), plus [Architecture Perspective 3: Process Architecture](https://github.com/knowledgetrailsai/OASIS/blob/main/architecture/perspective-03-process-architecture.md), Chapter 17, Chapter 18, and Chapter 24.

## What Loom Is For

Most AI programs succeed or fail on one thing, and it isn't model quality: whether the surrounding work was redesigned for a human and a machine to share it. A workflow that never says who has authority over a decision, or what a person sees before approving an AI-prepared action, is an **unfinished design** — not a training gap you can patch later.

```
Governing question: who is allowed to do what with the system,
and how do a human and a machine hand work back and forth?
```

Loom answers that with five pieces: a Workflow Blueprint that names authority, evidence, and fallback for every step; a six-mode autonomy ladder plus the evidence needed to move up or down it; trust calibration for *appropriate* reliance, not maximum reliance; a way to fit one hand-off inside a longer process a human still owns end to end; and the change-and-capability work that has to start at discovery, not at training.

## How to Use This Repository

Find the sentence below that matches what you're trying to do, and open the linked file. That's the fastest way in — read [00-navigation-and-methodology/how-to-use-this-repository.md](00-navigation-and-methodology/how-to-use-this-repository.md) next for the full role-and-task routing, or [00-navigation-and-methodology/knowledge-map.md](00-navigation-and-methodology/knowledge-map.md) for a worked example tracing one workflow through every section.

- **Designing a new human-AI workflow from scratch?** Start with [Blueprint Overview](02-workflow-blueprint/blueprint-overview.md), then fill in [the Template](02-workflow-blueprint/template.md).
- **Deciding whether to promote or demote an agent's autonomy?** Go straight to [Promotion and Demotion Criteria](03-progressive-autonomy/promotion-and-demotion-criteria.md); [Autonomy Ladder](03-progressive-autonomy/autonomy-ladder.md) explains the six modes it moves between.
- **Just need the escalation-trigger or workflow-blueprint template?** [templates/human-ai-workflow-blueprint.yaml](templates/human-ai-workflow-blueprint.yaml).
- **Deciding what evidence a human reviewer should see before approving an AI-prepared action?** [Authority and Evidence](02-workflow-blueprint/authority-and-evidence.md).
- **Worried people are over-trusting or under-trusting the system?** [Trust Calibration §04](04-trust-calibration/appropriate-reliance.md) — interface levers and the behavioral signals that tell you which way to correct.
- **Fitting one AI hand-off into a process a human still owns end to end?** [Process-to-Agent Participation Map](05-process-architecture-integration/process-to-agent-participation-map.md) and the [participation map template](templates/process-participation-map-template.md).
- **Planning the training and adoption work, not just the technical rollout?** [Change and Capability §06](06-change-and-capability/change-and-capability.md).
- **New to the repo and want the argument for why this is engineering, not a training problem?** [Why This Is Engineering](01-foundations/why-this-is-engineering.md).
- **Need a term defined?** [Glossary](glossary/terminology.md).

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

- **[OASIS](https://github.com/knowledgetrailsai/OASIS)** — the parent methodology. Loom implements its human–AI workflow chapter specifically, the way [Helm](https://github.com/knowledgetrailsai/HELM) implements deployment and operations, and [Forge](../Forge) implements data and knowledge engineering.
- **[Forge](../Forge)** — the data and knowledge companion (Chapter 15). The evidence a reviewer sees in a Loom workflow blueprint depends on Forge's grounding policy and readiness assessment.
- **[Helm](https://github.com/knowledgetrailsai/HELM)** — escalation triggers and override rates named in a Loom workflow blueprint feed Helm's incident-response and learning-loop instrumentation.
- **[Nexus](https://github.com/knowledgetrailsai/Nexus)** — the opportunity catalog. A use case's human-in-the-loop shape gets decided here (in Loom) once it reaches engineering.

## Status

Early scaffold: the structure is in place and first-pass content has been drafted section by section, working from the OASIS methodology and its architecture companions. Check each section to see what's drafted versus still a stub.

## License

Licensed under [CC BY-SA 4.0](https://github.com/knowledgetrailsai/OASIS/blob/main/LICENSE.md). Reuse and adaptation are welcome with credit to KnowledgeTrails-OASIS, a link to the license, an indication of changes, and release of adaptations under the same license.

## About Us

**Shripadraj Mujumdar** is an Agentic AI & Automation Strategist, Advisor, and Responsible AI Expert with 28+ years of experience in enterprise architecture and AI-driven transformation, including deep hands-on work in Agentic AI, Generative AI, and enterprise data and knowledge platforms. His practice spans designing multi-agent systems, knowledge-graph and RAG architectures, accelerated delivery capabilities, and Responsible AI governance frameworks aligned to global regulatory standards. This methodology ecosystem distills that practitioner experience — architecture, delivery, evaluation, governance, and economics — into a single, reusable body of work.

**Ankit Mirajkar** is a Data & AI Architect and technology consultant specializing in modern data platforms, enterprise data architecture, and Agentic AI. His expertise spans scalable data engineering, AI-ready data platforms, Generative AI, and cloud technologies, with a strong focus on turning complex data challenges into practical, production-ready solutions. He also works at the intersection of architecture, technology strategy, and innovation to help organizations build intelligent, scalable data ecosystems.
