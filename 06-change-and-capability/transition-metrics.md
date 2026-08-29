# Transition Metrics

`Home › 06-change-and-capability › Transition Metrics`

Measure the transition itself, not just the eventual outcome — these are early signals of whether a workflow is landing, well before the [outcome metrics](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-18-evaluation-and-reliability-engineering.md) move.

## Definitions

**Override rate** (per period, per reviewer or in aggregate):

```
override_rate = overrides / total_AI-assisted_decisions_in_period
```

**Time-to-proficiency**: the elapsed time from workflow launch to the point where an individual reviewer's override-agreement rate with senior-reviewer consensus stabilizes within ±2 percentage points for 2 consecutive weeks. "Stabilizes" means the week-over-week change in agreement rate stays within the ±2pp band for both weeks — a single good week is not proficiency, it can be sampling noise on a small weekly n.

**Workaround behavior**: any observed case of a user completing the task outcome via a path that bypasses the redesigned workflow (e.g., editing the source system directly instead of using the review queue). Track as a count per period, not a rate — even a small nonzero count is a signal worth investigating, since workarounds are usually underreported.

## Worked example: override rate trend, weeks 1–4

| Week | AI-assisted decisions | Overrides | Override rate |
|---|---|---|---|
| 1 | 420 | 76 | 18.1% |
| 2 | 445 | 49 | 11.0% |
| 3 | 460 | 32 | 7.0% |
| 4 | 470 | 28 | 6.0% |

Reading the trend: weeks 1→3 show a steep decline (18.1% → 7.0%), consistent with reviewers and the model both adjusting during the normal ramp period — this is expected and not itself a red flag. Week 3→4 shows a much smaller drop (7.0% → 6.0%, a 1pp change): this is the point to start tracking for a plateau, not further improvement. If week 5 comes in within ±2pp of week 4 (i.e., roughly 4–8%) for two consecutive weeks, that satisfies the proficiency-stabilization definition above and the workflow can be evaluated for promotion consideration against the [promotion-and-demotion-criteria.md](../03-progressive-autonomy/promotion-and-demotion-criteria.md) statistical gate — note that a declining trend by itself is not a promotion criterion, only the Wilson-bound calculation is.

A trend that instead plateaus early (e.g., 18% → 16% → 15% → 15%) without ever approaching the rung's target threshold is a different signal: not "still ramping," but "this configuration of workflow, evidence, and interface has a ceiling above the target" — investigate evidence quality and interface design (see [authority-and-evidence.md](../02-workflow-blueprint/authority-and-evidence.md)) before assuming more time will fix it.

## Full metric set

| Metric | What it signals |
|---|---|
| Time-to-proficiency | See definition above; measured per reviewer, reported as a distribution (median + p90), not a single team-wide number |
| Override rate | Feeds directly into the [promotion/demotion](../03-progressive-autonomy/promotion-and-demotion-criteria.md) Wilson-bound calculation |
| Workaround count | A nonzero count is a stronger signal of a broken design than a low satisfaction score |
| Migration ratio | Exception-queue volume as % of pre-automation manual volume — see [behavioral-signals.md](../04-trust-calibration/behavioral-signals.md) |
| Users' sense of control (survey) | Weakest signal here — self-report; use only as a secondary check against the behavioral signals above, never as a substitute for them |

## Why these come before outcome metrics

Outcome metrics (Chapter 18, Chapter 26) tell you whether the business result improved, but they move slowly and can be confounded by many other factors. Transition metrics move fast and are directly attributable to the workflow redesign itself — a rising override rate or workaround count in week two is actionable long before a quarterly outcome metric would show anything.
