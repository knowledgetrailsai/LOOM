# Process Ownership Model

`Home › 05-process-architecture-integration › Process Ownership Model`

| Principle | What it means in practice |
|---|---|
| The process owner is never the agent | A named human or function owns the end-to-end process outcome regardless of how many steps are agent-executed — the process-level instance of "Human accountable." |
| Agent scope is a subset of process scope | An agent's autonomy is defined at the step level, never inherited automatically across the whole process. |
| Handback points are designed, not incidental | Every process with agentic steps names, in advance, the conditions under which control returns to a human — confidence threshold, policy exception, value threshold — per this repository's [workflow blueprint](../02-workflow-blueprint/template.md). |
| Process change is versioned like system change | A process redesign that changes which steps are agent-executed follows the same release discipline as any production system-behavior change — it is a change to system behavior, not just a documentation update. |

## Why this matters for Loom specifically

A [Human–AI Workflow Blueprint](../02-workflow-blueprint/template.md) is written at the step level. Without an explicit process ownership model sitting above it, it's easy to write a technically excellent blueprint for one step while leaving the overall process owner unclear: the exact ambiguity that turns into a finger-pointing exercise during an incident review.
