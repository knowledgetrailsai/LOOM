# Human–AI Workflow Blueprint Template

`Home › 02-workflow-blueprint › Template`

Reproduced from [Tools: Workflow and Intelligence Templates §7](https://github.com/knowledgetrailsai/OASIS/blob/main/tools/02-workflow-and-intelligence-templates.md#7-human-ai-workflow-blueprint).

```yaml
human_ai_workflow_blueprint:
  workflow_name: ""
  step_sequence:
    - step: ""
      ai_role: ""                  # what the system does at this step
      human_role: ""                # what the human does at this step
      authority: "AI acts | AI recommends, human decides | human acts, AI assists"
      evidence_shown_to_human: ""
      interface: ""                 # where/how the human interacts (dashboard, chat, embedded in existing tool)
      approval_required: true|false
      override_mechanism: ""
      fallback_if_ai_unavailable: ""
      escalation_trigger: ""
      escalation_target: ""
  feedback_loop:
    how_human_corrections_are_captured: ""
    how_corrections_feed_back_to_evaluation: ""     # link to Chapter 18 Evaluation Strategy and Dataset
  outcome_event: ""                 # what marks this workflow as complete / successful
```

A copy of this schema, ready to fill in, is in [templates/human-ai-workflow-blueprint.yaml](../templates/human-ai-workflow-blueprint.yaml).
