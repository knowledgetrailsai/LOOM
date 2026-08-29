# Loom

**Companion repository:** [OASIS](https://github.com/knowledgetrailsai/OASIS) methodology — [Chapter 16 — Human–AI Workflow and Experience Engineering](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-16-human-ai-workflow-and-experience-engineering.md)

## What this repository is

**Loom** is the human–AI workflow companion to the OASIS methodology — the practical discipline of redesigning work around complementary human and machine strengths: explicit authority, usable oversight, trust calibration, progressive autonomy, and accessible experiences. The name reflects what the repo actually governs — weaving human judgment and AI capability into one workflow, thread by thread, rather than bolting AI onto an unchanged process.

**In plain terms:** OASIS's methodology chapter tells you *what* a redesigned workflow must decide and *why*. Loom gives you *how* — the actual workflow blueprint template, the autonomy-ladder criteria for moving a rung up or down, and the trust-calibration signals to instrument before launch.

## How this repository is organized

- **[00-foundations](00-foundations/)** — why this is engineering, not change management bolted on afterward
- **[01-workflow-blueprint](01-workflow-blueprint/)** — the required design decisions per step: task, AI contribution, human contribution, authority, evidence, fallback, feedback, outcome
- **[02-progressive-autonomy](02-progressive-autonomy/)** — the six-mode autonomy ladder (shadow → recommend → assist → approve-to-act → exception-based → bounded autonomy) and evidence-based promotion/demotion
- **[03-trust-calibration](03-trust-calibration/)** — appropriate reliance, interface design levers, and behavioral signals (over-reliance, rubber-stamping, automation bias)
- **[04-change-and-capability](04-change-and-capability/)** — adoption, role redesign, training, accessibility, and transition metrics
- **[glossary](glossary/)** — shared terminology
- **[templates](templates/)** — copyable starting points (Human–AI Workflow Blueprint)

## Chapters Implemented So Far

| OASIS chapter | Implemented in |
|---|---|
| [Ch. 16 — Human–AI Workflow and Experience Engineering](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-16-human-ai-workflow-and-experience-engineering.md) | All sections above |

## Relationship to companion repositories

- **[OASIS](https://github.com/knowledgetrailsai/OASIS)** — the parent methodology; Loom implements its human–AI workflow chapter specifically, the way [Helm](https://github.com/knowledgetrailsai/HELM) implements deployment/operations and [Codex](../Codex) implements data and knowledge engineering.
- **[Codex](../Codex)** — the data and knowledge companion (Chapter 15); the evidence shown to a reviewer in Loom's workflow blueprint depends on Codex's grounding policy and readiness assessment.
- **[Helm](https://github.com/knowledgetrailsai/HELM)** — escalation triggers and override rates named in a Loom workflow blueprint feed Helm's incident-response and learning-loop instrumentation.
- **[Nexus](https://github.com/knowledgetrailsai/Nexus)** — the opportunity catalog; a use case's human-in-the-loop shape is decided here once it reaches engineering.

## Status

Scaffold stage — structure in place, content being drafted section by section. See each folder for what's drafted versus still a stub.

---

**Next:** [00-foundations/why-this-is-engineering.md](00-foundations/why-this-is-engineering.md)
