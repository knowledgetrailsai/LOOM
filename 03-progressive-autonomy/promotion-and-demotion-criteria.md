# Promotion and Demotion Criteria

`Home › 03-progressive-autonomy › Promotion and Demotion Criteria`

## Moving up a rung is evidence-based, not calendar-based

A workflow graduates from assist to approve-to-act because [evaluation results](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-18-evaluation-and-reliability-engineering.md) and override rates support it, not because it has been live for a quarter. Calendar-based promotion optimizes for the appearance of progress rather than actual reliability, and it tends to surface as a production incident precisely when a rare case the system was never actually tested against finally occurs.

## Moving down a rung is equally normal

It is equally normal to move down a rung — after a policy or model change, or a sustained rise in override rate — until confidence is re-established. Treating demotion as a failure discourages teams from doing it when they should, which is itself a trust-calibration risk (see [04-trust-calibration](../04-trust-calibration/appropriate-reliance.md)).

## Signals that justify a promotion or demotion decision

| Signal | Direction it supports |
|---|---|
| Evaluation results (Chapter 18) consistently at or above threshold across representative cases | Promotion |
| Override rate low and stable across a representative period | Promotion |
| Override rate rising, especially concentrated in a specific case type | Demotion |
| A policy or model change with unverified downstream effect on this workflow | Demotion (until re-verified) |
| Rubber-stamping detected in trust-calibration monitoring (fast, uniform approval times) | Investigate before further promotion — the human layer may not actually be exercising oversight |

## Recording the decision

Every promotion or demotion should be recorded against the workflow's [Human–AI Workflow Blueprint](../02-workflow-blueprint/template.md) — the authority field for the affected step changes, and that change is itself a release, following the same discipline [Helm](https://github.com/knowledgetrailsai/HELM)'s release-management practice applies to any production system-behavior change.
