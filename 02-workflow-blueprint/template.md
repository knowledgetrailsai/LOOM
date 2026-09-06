# Human–AI Workflow Blueprint Template

`Home › 02-workflow-blueprint › Template`

[← Previous: Authority and Evidence](authority-and-evidence.md) · [Contents](../README.md) · [Next: Autonomy Ladder →](../03-progressive-autonomy/autonomy-ladder.md)

Reproduced from [Tools: Workflow and Intelligence Templates §7](https://github.com/knowledgetrailsai/OASIS/blob/main/tools/02-workflow-and-intelligence-templates.md#7-human-ai-workflow-blueprint).

## Schema

```yaml
human_ai_workflow_blueprint:
  workflow_name: ""
  step_sequence:
    - step: ""
      ai_role: ""                  # what the system does at this step
      human_role: ""                # what the human does at this step
      authority: "AI acts | AI recommends, human decides | human acts, AI assists"
      evidence_shown_to_human: []   # list, not a paragraph — each item independently checkable
      interface: ""                 # where/how the human interacts (dashboard, chat, embedded in existing tool)
      approval_required: true|false
      override_mechanism: ""        # exact UI action + required input, not "human can override"
      fallback_if_ai_unavailable: ""
      escalation_trigger: ""        # boolean expression over observable fields, not "when something looks off"
      escalation_target: ""         # named queue or role, not "a human"
  feedback_loop:
    how_human_corrections_are_captured: ""
    how_corrections_feed_back_to_evaluation: ""     # link to Chapter 18 Evaluation Strategy and Dataset
  outcome_event: ""                 # what marks this workflow as complete / successful
```

A copy of this schema, ready to fill in, is in [templates/human-ai-workflow-blueprint.yaml](../templates/human-ai-workflow-blueprint.yaml).

## Worked example: expense-report anomaly detection

Scenario: a model classifies submitted expense line items against policy limits and flags anomalies. Below is the blueprint for the single "classify and route" step, the part of the workflow with the most design risk.

```yaml
human_ai_workflow_blueprint:
  workflow_name: "expense-report-anomaly-detection"
  step_sequence:
    - step: "classify-and-route-line-item"
      ai_role: >
        Classify each submitted expense line item against the policy
        ruleset and produce a flagged/not-flagged decision with a
        confidence score in [0,1]. Flagged items include the specific
        rule ID violated.
      human_role: >
        Review flagged items only. Approve or reject each; unflagged
        items below the auto-approval threshold are never queued for
        human review.
      authority: >
        AI acts — for items with confidence >= 0.9 AND amount < $50
        AND zero policy violations (auto-approve, no human in loop).
        AI recommends, human decides — for all flagged items.
      evidence_shown_to_human:
        - "policy rule violated (rule ID + full rule text)"
        - "line item amount vs. the specific policy limit it exceeds"
        - "employee's flag history, last 90 days (count + categories)"
        - "model confidence score for this classification"
      interface: "embedded review panel inside the existing expense system, not a separate tool"
      approval_required: true   # for flagged items; false for auto-approved items below threshold
      override_mechanism: >
        One-click reject with a required reason code selected from a
        fixed taxonomy (duplicate, missing receipt, out-of-policy category,
        split transaction, other-with-mandatory-freetext). Free-text reject
        with no code is not permitted — it breaks the feedback loop below.
      fallback_if_ai_unavailable: >
        Route 100% of line items to the human review queue. Do not
        auto-approve anything while the classifier is unavailable —
        fail closed, not open.
      escalation_trigger: >
        confidence < 0.6 OR amount > $5000 OR employee has more than
        2 prior flags in the last 90 days
      escalation_target: "team-lead review queue (not the standard reviewer queue)"
  feedback_loop:
    how_human_corrections_are_captured: >
      Every approve/reject decision, plus reason code on reject, is
      logged with the model's original confidence and rule ID against
      a stable line-item ID.
    how_corrections_feed_back_to_evaluation: >
      Reject events with reason code are added to the labeled evaluation
      set (Chapter 18) weekly; reason-code distribution is reviewed
      monthly to detect systematic rule gaps, not just individual misses.
  outcome_event: >
    Expense report status transitions to approved or rejected, with a
    complete audit trail: original classification, confidence, any
    escalation, reviewer identity, decision, and reason code.
```

Read this against [authority-and-evidence.md](authority-and-evidence.md) for the decision rule behind the auto-approve threshold, and [process-risk-classification.md](../05-process-architecture-integration/process-risk-classification.md) for how the $50/100%-compliant cutoff would be derived for a different process.

---

[← Previous: Authority and Evidence](authority-and-evidence.md) · [Contents](../README.md) · [Next: Autonomy Ladder →](../03-progressive-autonomy/autonomy-ladder.md)
