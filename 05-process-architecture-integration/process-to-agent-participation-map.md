# Process-to-Agent Participation Map

`Home › 05-process-architecture-integration › Process-to-Agent Participation Map`

[← Previous: Behavioral Signals](../04-trust-calibration/behavioral-signals.md) · [Contents](../README.md) · [Next: Process Ownership Model →](process-ownership-model.md)

Adapted from [Architecture Perspective 3: Process Architecture §1](https://github.com/knowledgetrailsai/OASIS/blob/main/architecture/perspective-03-process-architecture.md#1-process-to-agent-participation-map).

Chapter 16 (this repository) addresses human–AI workflow design at the level of a single interaction: how a human and an agent hand off a task, when to interrupt for approval, how to design for override. Process Architecture takes the wider view a process owner needs: a business process (claims intake through settlement; a hire from requisition through onboarding) is usually longer, more branched, and touches more systems than any single agent's scope. An agent typically owns one or a few steps within a process it does not own end-to-end.

## Representation: a directed graph

Model the process as a directed graph. Nodes are steps, edges are transitions.

```yaml
# node schema
step:
  step_id: string            # stable, unique within the process
  executor: "human | task_agent | specialist_agent"
  authority: "AI acts | AI recommends, human decides | human acts, AI assists"
  handback_trigger: string   # condition that returns control to the process owner or a human
  process_owner: string      # named role accountable for this step

# edge schema
transition:
  from_step: string          # step_id
  to_step: string            # step_id
  condition: string          # boolean expression over step outputs; "default" for the unconditional edge
```

## Worked example: claims intake to settlement

```yaml
process: "claims-intake-to-settlement"
steps:
  - step_id: "intake"
    executor: "task_agent"
    authority: "AI acts"
    handback_trigger: "required fields missing after 2 automated retries"
    process_owner: "claims-ops-lead"

  - step_id: "classification"
    executor: "task_agent"
    authority: "AI recommends, human decides"
    handback_trigger: "classification confidence < 0.7"
    process_owner: "claims-ops-lead"

  - step_id: "routing"
    executor: "task_agent"
    authority: "AI acts"
    handback_trigger: "claim value > $25,000 OR flagged line of business (workers-comp, liability)"
    process_owner: "claims-ops-lead"

  - step_id: "adjuster-review"
    executor: "human"
    authority: "human acts, AI assists"
    handback_trigger: "n/a — terminal human step; escalates to senior-adjuster queue if coverage dispute detected"
    process_owner: "senior-adjuster"

  - step_id: "settlement"
    executor: "specialist_agent"
    authority: "AI recommends, human decides"
    handback_trigger: "settlement amount exceeds adjuster's approval limit"
    process_owner: "claims-ops-lead"

transitions:
  - from_step: "intake"
    to_step: "classification"
    condition: "required fields present"
  - from_step: "classification"
    to_step: "routing"
    condition: "confidence >= 0.7"
  - from_step: "classification"
    to_step: "adjuster-review"
    condition: "confidence < 0.7"
  - from_step: "routing"
    to_step: "adjuster-review"
    condition: "default"
  - from_step: "adjuster-review"
    to_step: "settlement"
    condition: "adjuster approves coverage"
```

Without this graph it becomes unclear where an agent's authority starts and stops relative to the surrounding human-owned process, and process owners lose visibility into how much of "their" process now runs through agentic components they did not design.

The fillable version is in [templates/](../templates/human-ai-workflow-blueprint.yaml).

---

[← Previous: Behavioral Signals](../04-trust-calibration/behavioral-signals.md) · [Contents](../README.md) · [Next: Process Ownership Model →](process-ownership-model.md)
