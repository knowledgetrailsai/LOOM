# Loom: OASIS Human–AI Workflow and Experience Engineering

A human–AI workflow companion to the OASIS methodology that redesigns work around complementary human and machine strengths. It functions as an operating system for the handoff itself: authority, evidence, and fallback get decided at design time, not discovered during an incident.

```
TASK/DECISION → AI CONTRIBUTION → HUMAN CONTRIBUTION → AUTHORITY → EVIDENCE → FALLBACK → FEEDBACK → OUTCOME
```

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-yellow.svg)](LICENSE)
![Status](https://img.shields.io/badge/status-draft%20v1.0-orange)

**Companion repository:** [OASIS](https://github.com/knowledgetrailsai/OASIS) methodology — primarily [Chapter 16 — Human–AI Workflow and Experience Engineering](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-16-human-ai-workflow-and-experience-engineering.md), plus [Architecture Perspective 3: Process Architecture](https://github.com/knowledgetrailsai/OASIS/blob/main/architecture/perspective-03-process-architecture.md), Chapter 17, Chapter 18, and Chapter 24.

## Why This Exists

Most AI programs succeed or fail on one thing, and it isn't model quality: whether the surrounding work was redesigned for a human and a machine to share it. [Chapter 14](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-14-intelligence-and-agent-engineering.md) establishes what an intelligence system can do; [Chapter 15](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-15-data-and-knowledge-engineering.md) (see [Forge](../Forge)) makes sure it has governed, sufficient evidence. Neither answers who is allowed to do what with the system, or how a human and a machine hand work back and forth — that gap is what this repository closes.

A workflow that never says who has authority over a decision, or what a person sees before approving an AI-prepared action, is an **unfinished design**, not a training gap you can patch later. This repository's templates decide authority, evidence, and fallback at design time, alongside the model and the data pipeline, and treats adoption as workflow engineering rather than communication that happens after the system is already built.

## What Loom Is For

```
Governing question: who is allowed to do what with the system,
and how do a human and a machine hand work back and forth?
```

Loom answers that with five pieces, each building on the one before: a Workflow Blueprint that names authority, evidence, and fallback for every step; a six-mode autonomy ladder plus the evidence needed to move up or down it; trust calibration for *appropriate* reliance, not maximum reliance; a way to fit one hand-off inside a longer process a human still owns end to end; and the change-and-capability work that has to start at discovery, not at training.

## The Workflow Blueprint

Redesigning a workflow means fixing eight design decisions, per step, before any code or prompt gets written: the task and decision being changed, the AI contribution, the human contribution, authority, evidence, fallback, feedback, and outcome. Skipping one doesn't remove the decision — it just means the decision gets made implicitly, in production, usually by whichever engineer wrote the fallback path last. Two defects show up most often: "AI contribution" described as a technology ("uses an LLM") instead of a cognitive function ("drafts a first-pass response for human review"), which hides what evidence a reviewer actually needs; and "authority" resolving to "the AI, usually" instead of a named role or a boolean expression over case attributes, which is exactly what makes accountability evaporate the first time something goes wrong. See [02-workflow-blueprint/blueprint-overview.md](02-workflow-blueprint/blueprint-overview.md) for the full eight-decision table and [authority-and-evidence.md](02-workflow-blueprint/authority-and-evidence.md) for the fix to both defects, or go straight to the fully filled-in worked example in [template.md](02-workflow-blueprint/template.md).

## Progressive Autonomy

Autonomy is not a single on/off decision made at launch; it's a ladder a workflow climbs one rung at a time, from shadow mode (the system observes and produces non-operational output while a human does the normal work) through recommend, assist, and approve-to-act, to exception-based operation and finally bounded autonomy. Shadow mode is the cheapest place to find a blind spot — it answers cheaply and safely whether the system's judgment agrees with an experienced human's across a representative range of cases, and skipping it is usually a false economy. Most enterprise workflows never need to go past exception-based operation, where routine cases run within clear rules and a human reviews exceptions and a sample of the rest; that's a durable end state, not a waypoint. Promotion between rungs is evidence-based, not calendar-based: a workflow is promoted only when a large enough sample (n ≥ 500 AI-assisted decisions) shows the statistical upper bound on the override/error rate, not just the point estimate, below the rung's target threshold — a 2% point estimate on 30 decisions carries far more uncertainty than 2% on 5,000, and promoting on the point estimate alone is exactly what produces incidents on rare cases the sample never covered. See [03-progressive-autonomy/autonomy-ladder.md](03-progressive-autonomy/autonomy-ladder.md) and [promotion-and-demotion-criteria.md](03-progressive-autonomy/promotion-and-demotion-criteria.md).

## Trust Calibration

The objective is appropriate reliance, not maximum trust. A user who defers to every AI recommendation looks efficient until the recommendation is wrong; a user who quietly re-does the AI's work looks diligent until you realize the redesign delivered no benefit — and both failure modes look identical on a naive throughput metric, which is exactly why trust calibration needs its own deliberate measurement rather than being inferred from output volume. Interfaces are the primary lever: they should surface source quality, uncertainty, limitations, the scope of the proposed action, and the consequence of approving it, visible where a reviewer will actually see it rather than buried in a tooltip. Correction and escalation also have to be genuinely easy to use, not just present on paper — a friction-heavy override mechanism produces the appearance of a well-governed workflow while quietly failing its actual purpose, since an override path that exists but isn't used when it matters governs nothing. See [04-trust-calibration/appropriate-reliance.md](04-trust-calibration/appropriate-reliance.md), [interface-design-levers.md](04-trust-calibration/interface-design-levers.md), and [behavioral-signals.md](04-trust-calibration/behavioral-signals.md) for the signals that tell you which way to correct.

## Fitting Into the Wider Process

A single hand-off is not the same scope as the business process it sits inside. A business process, claims intake through settlement, a hire from requisition through onboarding, is usually longer, more branched, and touches more systems than any single agent's scope; an agent typically owns one or a few steps within a process it does not own end-to-end. This repository models that wider process as a directed graph of steps and transitions, and holds three principles about it: the process owner is never the agent (a named human or function owns the end-to-end outcome regardless of how many steps are agent-executed); an agent's autonomy is scoped to the step level and never inherited automatically across the whole process; and handback points — the conditions under which control returns to a human — are designed in advance, not incidental. Every process step is also scored for risk on three inputs (value, reversibility, and regulatory sensitivity), since a step that's irreversible or regulated needs a different authority model than one that's cheap to undo. See [05-process-architecture-integration/process-to-agent-participation-map.md](05-process-architecture-integration/process-to-agent-participation-map.md), [process-ownership-model.md](05-process-architecture-integration/process-ownership-model.md), and [process-risk-classification.md](05-process-architecture-integration/process-risk-classification.md).

## Change and Capability

Adoption work has to start earlier than most programs schedule it. Engaging users during discovery and evaluation surfaces objections and edge cases while they're still cheap to address; if training is people's first contact with the change, it's too late, because the roles and incentives around their job have already been decided without them. Roles, capacity, incentives, quality checks, and performance measures need to be redesigned alongside the workflow, not as an afterthought — a workflow can be technically correct and still fail if people are measured and resourced as though the old process were still running. Training itself has to cover the purpose and limits of the system, how to interpret the evidence shown, what an approval actually commits the approver to, and data-handling responsibilities, not just interface mechanics, with accessibility, language, channel, and digital-literacy needs designed in from the start rather than retrofitted later. See [06-change-and-capability/change-and-capability.md](06-change-and-capability/change-and-capability.md), [adoption-and-training.md](06-change-and-capability/adoption-and-training.md), and [transition-metrics.md](06-change-and-capability/transition-metrics.md).

## Roles and Ownership

[Chapter 24 — Roles, Teams and Governance Forums](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-24-roles-teams-and-governance-forums.md) names the enterprise role this repository's authority-and-evidence decisions ultimately answer to: the **Business Outcome Owner**, accountable for outcome baseline, target, process authority, and value realization. That role is why "the process owner is never the agent" is a principle rather than a preference — accountability always sits with a named human, regardless of how many steps in a process are agent-executed. A Product/Service Owner, a Data/Knowledge Owner (the counterpart on [Forge](../Forge)'s side), and a Model/AI Steward round out the roles a Loom workflow blueprint's fields depend on or feed. See [01-foundations/roles-and-ownership.md](01-foundations/roles-and-ownership.md) for the full mapping.

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
