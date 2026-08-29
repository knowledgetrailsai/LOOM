# Process-to-Agent Participation Map

`Home › 05-process-architecture-integration › Process-to-Agent Participation Map`

Adapted from [Architecture Perspective 3: Process Architecture §1](https://github.com/knowledgetrailsai/OASIS/blob/main/architecture/perspective-03-process-architecture.md#1-process-to-agent-participation-map).

Chapter 16 (this repository) addresses human–AI workflow design at the level of a single interaction: how a human and an agent hand off a task to each other, when to interrupt for approval, how to design for override. Process Architecture takes the wider view a process owner needs: a business process (claims intake through settlement; a hire from requisition through onboarding) is usually longer, more branched, and touches more systems than any single agent's scope — an agent typically owns one or a few steps within a process it does not own end-to-end.

One row per process step, for each business process that includes agentic participation:

| Process | Step | Executed by (human / task agent / specialist agent) | Decision authority at this step | Handback trigger | Process owner |
|---|---|---|---|---|---|
| | | | | | |

Without this map, it becomes unclear where an agent's authority starts and stops relative to the surrounding human-owned process, and process owners lose visibility into how much of "their" process now runs through agentic components they did not design.

The fillable version is in [templates/](../templates/).
