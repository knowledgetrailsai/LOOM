# Human–AI Workflow Blueprint: Overview

`Home › 02-workflow-blueprint › Overview`

Redesigning a workflow starts by naming what is changing and why, for every meaningful step. The table below is the minimum set of design decisions a workflow needs before it is safe to build. Skipping any one tends to surface later as an incident or an unexplained override.

| Element | Required design decision |
|---|---|
| Task and decision | What work is being changed and what outcome should improve? |
| AI contribution | Retrieve, classify, predict, generate, recommend, plan or execute? |
| Human contribution | Set intent, review evidence, approve, handle exception, empathize or accept accountability? |
| Authority | Who may decide or act for each case class and threshold? |
| Evidence | What source, confidence and context must be visible? |
| Fallback | What happens when evidence, model, tool or downstream system fails? |
| Feedback | How are corrections captured without creating surveillance or incentive problems? |
| Outcome | How is successful completion linked to the original business measure? |

## Where designs go wrong

The first two rows — task/decision and AI contribution — are where most designs go wrong. See [authority-and-evidence.md](authority-and-evidence.md) for why the AI-contribution framing and the authority field deserve the most design discipline.

The blueprint expresses every row above as a step-by-step specification: AI role, human role, authority, evidence shown, interface, approval requirement, override mechanism, fallback, escalation trigger and target, and a feedback loop into the [Chapter 18 evaluation dataset](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-18-evaluation-and-reliability-engineering.md). Filling it out per step turns "a human reviews the output" into something a team can build and rely on.

The fillable YAML schema is in [templates/human-ai-workflow-blueprint.yaml](../templates/human-ai-workflow-blueprint.yaml).
