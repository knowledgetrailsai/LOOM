# Interface Design Levers

`Home › 04-trust-calibration › Interface Design Levers`

Interfaces are the primary lever for correcting over-reliance or under-use. A workflow's [Human–AI Workflow Blueprint](../02-workflow-blueprint/template.md) "interface" and "evidence shown to human" fields are where these levers get specified concretely.

| Lever | What it does |
|---|---|
| Source quality display | Shows the reviewer where evidence came from and how authoritative it is — depends on [Forge](../../Forge)'s [readiness assessment](../../Forge/03-readiness-assessment/readiness-dimensions.md) actually being populated |
| Uncertainty display | Surfaces model confidence or ambiguity rather than presenting every output with uniform, unearned confidence |
| Limitations statement | States what the system is and isn't good at for this specific decision, not a generic disclaimer |
| Action scope | Makes the blast radius of the proposed action visible before approval — a small edit vs. an irreversible transaction should not look the same |
| Consequence framing | States what approving actually commits the approver to |

## Design discipline

Visible "where a reviewer will see it" is doing real work in this list — a limitations statement in a help page nobody reads does not calibrate trust in the moment a decision is made. Put these levers in the reviewer's direct line of sight at the point of decision, not one click away.
