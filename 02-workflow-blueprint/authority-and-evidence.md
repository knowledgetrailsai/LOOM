# Authority and Evidence

`Home › 02-workflow-blueprint › Authority and Evidence`

[← Previous: Overview](blueprint-overview.md) · [Contents](../README.md) · [Next: Template →](template.md)

The blueprint's most consequential field is **authority**: whether the AI acts, whether it recommends and a human decides, or whether the human acts with AI assistance. This field must resolve to a boolean expression over observable case attributes — not a sentence with "usually" or "typically" in it.

## Decision table: authority mode by case value and model confidence

Bucket each incoming case on two axes: **case value** (the cost of a wrong decision) and **model confidence** (the classifier's own calibrated score for this instance). The cell is the default authority mode; deviate from a cell only with a written justification attached to the blueprint.

| | Low confidence (< 0.6) | Medium confidence (0.6–0.9) | High confidence (≥ 0.9) |
|---|---|---|---|
| **Low value** (e.g. < $50, easily reversible) | AI recommends, human decides | AI recommends, human decides | AI acts |
| **Medium value** (e.g. $50–$5,000, reversible with effort) | Human acts, AI assists | AI recommends, human decides | AI recommends, human decides |
| **High value** (e.g. > $5,000, irreversible or regulated) | Human acts, AI assists | Human acts, AI assists | AI recommends, human decides |

Notes on the table:

- No cell in the high-value row is "AI acts," regardless of confidence; see [process-risk-classification.md](../05-process-architecture-integration/process-risk-classification.md) for why value and reversibility cap the authority mode independent of model performance.
- The low-value/high-confidence cell is the only one where full automation is the default. This is the cell the expense-report example in [template.md](template.md) uses for its $50/100%-compliant auto-approve rule.
- "Confidence" here must be a calibrated score (validated against the Chapter 18 evaluation set), not a raw softmax output. An uncalibrated score makes every cell boundary meaningless.
- Re-derive this table per workflow. The bucket boundaries ($50, $5,000, 0.6, 0.9) are workflow-specific parameters, not universal constants; treat them as configuration reviewed at each promotion/demotion decision (see [promotion-and-demotion-criteria.md](../03-progressive-autonomy/promotion-and-demotion-criteria.md)).

## Two recurring failure patterns

**Leaving authority implicit.** Without an explicit table like the one above, the system accretes more authority than anyone formally granted, usually because no one built a fallback path for timely human intervention, so the default answer to "who decides" quietly becomes "whoever configured the last threshold." Authority must resolve to a named role or a rule, checkable against the table.

**A well-specified AI role with no feedback-loop field filled in.** Every correction a human makes evaporates instead of improving the system. The feedback field links directly into the [Chapter 18 evaluation dataset](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-18-evaluation-and-reliability-engineering.md); a correction that doesn't reach that dataset is a lesson the system re-learns from a future failure of the same shape.

## Frame the AI contribution as cognitive work, not technology

"Uses a language model to draft a response" tells a reviewer nothing about what to check. "Drafts a first-pass response for human review" tells them: verify claims against source, check tone, confirm the recommended action is within policy. Always write the AI-role field as the cognitive function it performs, because that framing is what determines the evidence field below it.

## What evidence must be visible

The evidence field states what source, confidence, and context must be visible to the human at the point of decision: as a list of discrete, independently checkable items (see the expense-report example's four-item evidence list), not a paragraph. This is where [Forge](../../Forge)'s [grounding policy](../../Forge/04-grounding-and-context-quality/grounding-policy.md) and [context quality checklist](../../Forge/04-grounding-and-context-quality/context-quality-checklist.md) become load-bearing: a human cannot exercise real authority over evidence they cannot see, verify, or trace to its source.
