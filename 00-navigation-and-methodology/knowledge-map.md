# Knowledge Map

`Home › 00-navigation-and-methodology › Knowledge Map`

Loom implements one OASIS methodology chapter — [Chapter 16: Human–AI Workflow and Experience Engineering](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-16-human-ai-workflow-and-experience-engineering.md) — but Chapter 16 sits at a hinge point in OASIS: everything before it builds capability, everything after it assumes authority and evidence are already decided.

```
Ch.14 (Intelligence & Agent Engineering) — what the system CAN do
        ↓
Ch.15 (Data & Knowledge Engineering) — governed, sufficient evidence it can draw on
        ↓
Ch.16 (Human–AI Workflow & Experience Engineering) ── THIS REPOSITORY
   — who is allowed to do what, how human and machine hand work back and forth
        ↓
Ch.17 (Enterprise Integration & Tool Engineering) — tool contracts assume the
   authority model decided here already exists
        ↓
Ch.18 (Evaluation & Reliability Engineering) — escalation-correctness evaluation
   assumes the escalation triggers named here already exist
```

Most AI programs succeed or fail here — not on model quality, but on whether the surrounding work was redesigned for the new division of labor. This is engineering, not change management bolted on afterward: a workflow that never specifies who has authority over a decision is an unfinished design, not a training gap.

## Worked example: one workflow, traced end to end

A claims-intake-and-triage workflow moves through every layer this repository covers:

1. **Blueprint** ([02-workflow-blueprint](../02-workflow-blueprint/blueprint-overview.md)): for each step — intake, classification, routing, exception handling — name the AI contribution, the human contribution, authority, evidence shown, fallback, feedback, and outcome.
2. **Process placement** ([05-process-architecture-integration](../05-process-architecture-integration/process-to-agent-participation-map.md)): claims intake is one step inside a longer settlement process a human process owner still owns end to end.
3. **Autonomy** ([03-progressive-autonomy](../03-progressive-autonomy/autonomy-ladder.md)): the classification step starts in shadow mode, graduates to assist, and — once override rates and evaluation results support it — to approve-to-act.
4. **Trust calibration** ([04-trust-calibration](../04-trust-calibration/appropriate-reliance.md)): the interface shows confidence and source evidence so a reviewer doesn't rubber-stamp routing decisions.
5. **Change and capability** ([06-change-and-capability](../06-change-and-capability/adoption-and-training.md)): claims handlers are engaged during discovery, not first told about the change in a training session.
6. **Feedback into evaluation** (Chapter 18, outside this repo): every human correction of a triage decision becomes a new evaluation case.

## Related OASIS chapters and documents

| Reference | What it contributes |
|---|---|
| [Chapter 14 — Intelligence and Agent Engineering](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-14-intelligence-and-agent-engineering.md) | Establishes system capability that Chapter 16 assumes is already built |
| [Chapter 15 — Data and Knowledge Engineering](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-15-data-and-knowledge-engineering.md) | The evidence a workflow blueprint's "evidence shown to human" field depends on — see [Forge](../../Forge) |
| [Chapter 16 — Human–AI Workflow and Experience Engineering](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-16-human-ai-workflow-and-experience-engineering.md) | The primary source for this entire repository |
| [Architecture Perspective 3: Process Architecture](https://github.com/knowledgetrailsai/OASIS/blob/main/architecture/perspective-03-process-architecture.md) | The enterprise-wide view of where a single hand-off sits inside a longer business process |
| [Chapter 17 — Enterprise Integration and Tool Engineering](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-17-enterprise-integration-and-tool-engineering.md) | Tool contracts that assume this repository's authority model is already decided |
| [Chapter 18 — Evaluation and Reliability Engineering](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-18-evaluation-and-reliability-engineering.md) | Escalation-correctness evaluation and the feedback loop this repo's blueprint feeds |
| [Chapter 24 — Roles, Teams and Governance Forums](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-24-roles-teams-and-governance-forums.md) | The Business Outcome Owner role and "process owner is never the agent" principle |
| [Chapter 32 §7 — Human–AI Workflow Blueprint](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-32-templates-checklists-and-tools.md#7-human-ai-workflow-blueprint) | The fillable template this repo's `templates/` directory reproduces |
| [Tools: Workflow and Intelligence Templates §7](https://github.com/knowledgetrailsai/OASIS/blob/main/tools/02-workflow-and-intelligence-templates.md#7-human-ai-workflow-blueprint) | The YAML schema for the blueprint |

## Companion repositories

- **[Forge](../../Forge)** — Chapter 15 (Data and Knowledge Engineering); the evidence a Loom workflow shows a human reviewer is only as trustworthy as Forge's grounding policy and readiness assessment.
- **[Helm](https://github.com/knowledgetrailsai/HELM)** — Chapter 17/18/19/21 (AgentOps); escalation triggers and override rates named in a Loom workflow blueprint feed Helm's incident-response and learning-loop instrumentation.
- **[Nexus](https://github.com/knowledgetrailsai/Nexus)** — the opportunity catalog; a use case's human-in-the-loop shape is decided here once it reaches engineering.
