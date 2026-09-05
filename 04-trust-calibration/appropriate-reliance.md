# Appropriate Reliance

`Home › 04-trust-calibration › Appropriate Reliance`

The objective is appropriate reliance, not maximum trust. A user who defers to every AI recommendation looks efficient until the recommendation is wrong. A user who quietly re-does the AI's work looks diligent until you realize the redesign delivered no benefit.

Both failure modes look identical from a naive productivity metric — throughput looks fine either way — which is exactly why trust calibration needs its own deliberate measurement rather than being inferred from output volume.

## Interfaces are the primary lever

Interfaces should reveal:

- Source quality
- Uncertainty
- Limitations
- The scope of the proposed action
- The consequence of approving it

All of this should be visible where a reviewer will actually see it, not buried in a tooltip. See [interface-design-levers.md](interface-design-levers.md).

## Correction and escalation need to be genuinely easy

If the override path is not genuinely easy to use, it will not get used when it matters. A friction-heavy override mechanism produces the appearance of a well-governed workflow (an override path exists) while quietly failing its actual purpose (the override path is used when needed).
