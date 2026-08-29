# Human–AI Workflow Blueprint: Overview

`Home › 02-workflow-blueprint › Overview`

Redesigning a workflow means fixing eight design decisions, per step, before any code or prompt gets written. Skipping one doesn't remove the decision — it just means the decision gets made implicitly, in production, usually by whichever engineer wrote the fallback path last.

| Element | Required design decision |
|---|---|
| Task and decision | What work is being changed and what outcome should improve? |
| AI contribution | Retrieve, classify, predict, generate, recommend, plan or execute? |
| Human contribution | Set intent, review evidence, approve, handle exception, empathize or accept accountability? |
| Authority | Who may decide or act for each case class and threshold? See the decision table in [authority-and-evidence.md](authority-and-evidence.md). |
| Evidence | What source, confidence and context must be visible? |
| Fallback | What happens when evidence, model, tool or downstream system fails? |
| Feedback | How are corrections captured, with what schema, and where do they land? |
| Outcome | What event, with what fields, marks this workflow as complete? |

## Where designs go wrong

The two most common defects: (1) "AI contribution" is described as a technology ("uses an LLM") instead of a cognitive function ("drafts a first-pass response"), which makes it impossible to derive what evidence a reviewer needs; (2) "authority" resolves to "the AI, usually" instead of a named role or a boolean expression over case attributes. See [authority-and-evidence.md](authority-and-evidence.md) for the fix to both.

## Worked example

[template.md](template.md) contains a fully filled-in blueprint for an expense-report anomaly-detection workflow — every field populated with concrete values, not placeholders. Use it as the reference shape when filling in a new one.

The fillable YAML schema is in [templates/human-ai-workflow-blueprint.yaml](../templates/human-ai-workflow-blueprint.yaml).
