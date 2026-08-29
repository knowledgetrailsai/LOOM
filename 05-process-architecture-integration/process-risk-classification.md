# Process Risk Classification

`Home › 05-process-architecture-integration › Process Risk Classification`

| Process characteristic | Implication for agent participation |
|---|---|
| Irreversible or high-value step | Confirmation and human approval required before execution. |
| Regulated decision point (credit, employment, benefits eligibility) | Route through the applicable compliance/standards checklist before any agent participation is approved. |
| High-volume, low-variance step | Strongest candidate for higher [autonomy](../03-progressive-autonomy/autonomy-ladder.md) — evaluate against evidence, not intuition. |
| Cross-functional handoff | Requires explicit ownership assignment — ambiguous ownership at a handoff is where agentic processes most often fail silently. |

## Relationship to system-level workflow design

A process map spans potentially many systems and agents; a single system's own harness and orchestration design governs how one agent or workflow executes its portion. Don't duplicate step-level implementation detail in the process map — link to the owning system's design and keep the process map at the process-step and ownership level.
