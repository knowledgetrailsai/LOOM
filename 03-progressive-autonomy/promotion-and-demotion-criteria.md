# Promotion and Demotion Criteria

`Home › 03-progressive-autonomy › Promotion and Demotion Criteria`

[← Previous: Autonomy Ladder](autonomy-ladder.md) · [Contents](../README.md) · [Next: Appropriate Reliance →](../04-trust-calibration/appropriate-reliance.md)

## Promotion rule

Promote a workflow to the next rung of the [autonomy ladder](autonomy-ladder.md) only if both hold:

1. **Sample size**: n ≥ 500 AI-assisted decisions in the current rolling window.
2. **Statistical bound**: the 95% Wilson score upper confidence bound on the override/error rate is below the rung's target threshold.

Do not promote on the point estimate alone. A point estimate of 2% on n=30 carries far more uncertainty than 2% on n=5000. Promoting on a calendar schedule or on the point estimate alone is exactly what produces incidents on rare cases the sample never actually covered.

### Wilson score interval

For observed override rate p̂ = k/n (k overrides in n decisions) and z = 1.96 (95% confidence), the upper bound is:

```
UB = [ p̂ + z²/(2n) + z·sqrt( p̂(1-p̂)/n + z²/(4n²) ) ] / (1 + z²/n)
```

The Wilson interval is preferred over the naive p̂ ± z·sqrt(p̂(1-p̂)/n) normal approximation because it stays well-behaved when p̂ is small and n is finite — exactly the regime override rates live in.

### Worked example

Window: n = 500 decisions, k = 12 overrides. p̂ = 12/500 = 0.024 (2.4%). Target threshold for this rung: 5%.

```
z = 1.96,  z² = 3.8416

z²/(2n)            = 3.8416 / 1000            = 0.0038416
p̂ + z²/(2n)        = 0.024 + 0.0038416        = 0.0278416

p̂(1-p̂)/n           = 0.024 × 0.976 / 500      = 0.000046848
z²/(4n²)           = 3.8416 / 1,000,000       = 0.0000038416
sum under sqrt     = 0.0000506896
sqrt(sum)          = 0.0071196
z × sqrt(sum)      = 1.96 × 0.0071196         = 0.0139544

numerator          = 0.0278416 + 0.0139544    = 0.0417960
denominator         = 1 + z²/n = 1 + 3.8416/500 = 1.0076832

UB = 0.0417960 / 1.0076832 = 0.04148  →  4.15%
```

n = 500 ≥ 500 (sample-size gate passes). UB = 4.15% < 5% target → **promote**.

If the same 2.4% point estimate were observed on n = 60 instead, the Wilson upper bound rises to roughly 12% — well above a 5% target. The sample-size gate would fail regardless. This is the concrete reason the point estimate alone cannot be the promotion criterion.

## Demotion rule

Demote immediately, pending re-evaluation, if either holds:

1. The rolling 7-day override rate's **point estimate** exceeds 2× the rate observed at the time of last promotion (e.g., promoted at 2.4% → demote if the 7-day rate exceeds 4.8%). No confidence-interval calculation is needed here — this is a fast trip-wire, not a statistical test.
2. A policy or model change occurred with unverified downstream effect on this workflow: demote until re-verified against the Chapter 18 evaluation set, independent of the current override rate.

Demotion is not a failure state to be avoided. Treating it as one discourages teams from demoting a workflow when the data calls for it — and that avoidance is itself a trust-calibration risk (see [04-trust-calibration](../04-trust-calibration/behavioral-signals.md)).

## Additional promotion gate

Do not promote if rubber-stamping is detected in trust-calibration monitoring for the current rung (see [behavioral-signals.md](../04-trust-calibration/behavioral-signals.md) for the detection rule) — a low override rate produced by reviewers not actually reviewing is not evidence the AI is reliable, it's an absence of evidence.

## Recording the decision

Every promotion or demotion is recorded against the workflow's [Human–AI Workflow Blueprint](../02-workflow-blueprint/template.md): the `authority` field for the affected step changes, with the n, k, p̂, and UB values that justified it attached as the change record. That change is itself a release, following the same discipline [Helm](https://github.com/knowledgetrailsai/HELM)'s release-management practice applies to any production system-behavior change.
