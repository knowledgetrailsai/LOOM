# Process Risk Classification

`Home › 05-process-architecture-integration › Process Risk Classification`

[← Previous: Process Ownership Model](process-ownership-model.md) · [Contents](../README.md) · [Next: Change and Capability →](../06-change-and-capability/change-and-capability.md)

## Scoring model

Score every process step on three inputs, 1–3 each:

| Score | Value | Reversibility | Regulatory sensitivity |
|---|---|---|---|
| 1 | Low (e.g. < $50, or no direct cost) | Fully reversible, no cost to undo | Not regulated |
| 2 | Medium (e.g. $50–$5,000) | Reversible with material effort/cost | Internal policy or contractual constraint |
| 3 | High (e.g. > $5,000, or reputational/safety exposure) | Irreversible or effectively so once executed | Regulated decision point (credit, employment, benefits eligibility, healthcare) |

**Risk tier = max(value, reversibility, regulatory_sensitivity)**: use max, not sum, so a single high-severity input (e.g., regulatory sensitivity = 3) cannot be diluted by two low scores elsewhere. Map the combined score to a tier:

| Combined score (max) | Risk tier |
|---|---|
| 1 | Low |
| 2 | Medium |
| 3 | High |

## Permitted autonomy modes by risk tier

| Risk tier | Permitted [autonomy ladder](../03-progressive-autonomy/autonomy-ladder.md) modes | Notes |
|---|---|---|
| Low | Shadow, Recommend, Assist, Approve-to-act, Exception-based, Bounded autonomy | Full ladder available; promote per [promotion-and-demotion-criteria.md](../03-progressive-autonomy/promotion-and-demotion-criteria.md). |
| Medium | Shadow, Recommend, Assist, Approve-to-act, Exception-based | Bounded autonomy requires an explicit risk-acceptance sign-off from the process owner, not just a passing override-rate check. |
| High | Shadow, Recommend, Assist only | Approve-to-act or higher is not permitted without documented Independent Assurance sign-off (an assurance function distinct from the team that built the workflow) — see the [assurance discussion in Chapter 16](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-16-human-ai-workflow-and-experience-engineering.md). Even with sign-off, exception-based and bounded autonomy remain out of scope. |

## Worked example

A credit-limit-increase step: value = 3 (increases can run into thousands of dollars), reversibility = 2 (can be reversed but with customer-relationship cost), regulatory sensitivity = 3 (credit decision, regulated). Risk tier = max(3,2,3) = 3 → **High**. Permitted modes: Shadow, Recommend, Assist only; the workflow can prepare a recommended limit and supporting evidence, but a human must decide and act, and this cannot be promoted to approve-to-act without Independent Assurance sign-off regardless of override-rate history.

## Relationship to system-level workflow design

A process map spans potentially many systems and agents; a single system's own harness and orchestration design governs how one agent or workflow executes its portion. Don't duplicate step-level implementation detail in the process map. Link to the owning system's design and keep the process map at the process-step, risk-tier, and ownership level.
