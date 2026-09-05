# Behavioral Signals

`Home › 04-trust-calibration › Behavioral Signals`

Trust calibration is behavioral. Measure it with detection algorithms against logged event data, not by self-report or survey.

## Rubber-stamping

**Flag reviewer-day *d* for reviewer *r* if both:**

```
median(review_time[r, d]) < percentile_10(review_time_history[r])
   AND
approval_rate[r, d] > 0.98
```

`review_time_history[r]` is that reviewer's own historical distribution (e.g., trailing 90 days), not a cross-reviewer benchmark — reviewers legitimately differ in baseline speed, so the comparison must be against the reviewer's own norm. The condition requires *both* unusually fast review times *and* near-universal approval on the same day; either alone is weaker evidence (a fast day with normal approval variance can be a genuinely easy case mix).

Action on flag: sample 5 of the flagged day's approvals for independent re-review before the next promotion decision for that workflow.

## Automation bias

Build a calibration plot: bin AI confidence scores into deciles (0.0–0.1, 0.1–0.2, ..., 0.9–1.0) and compute the human agreement rate (fraction of AI outputs approved as-is) within each bin.

**Automation bias is indicated when the human agreement rate stays flat and near 100% across bins that should show a declining agreement rate as confidence drops** — i.e., agreement rate is not tracking confidence.

Concrete example:

| Confidence bin | n | Human approval rate |
|---|---|---|
| 0.5–0.6 | 340 | 97% |
| 0.6–0.7 | 410 | 96% |
| 0.7–0.8 | 890 | 98% |
| 0.8–0.9 | 1,650 | 99% |
| 0.9–1.0 | 4,200 | 99% |

A 97% approval rate in the 0.5–0.6 bin — where the model itself is telling you it is close to a coin flip — with no meaningful drop relative to the 0.9–1.0 bin is the signal: reviewers are not discriminating between cases the model is unsure about and cases it is confident about. If oversight were functioning, the low-confidence bins should show materially lower approval rates (more edits, more rejects) than the high-confidence bins.

## Workload migrated into exception handling

Track exception-queue volume as a percentage of the pre-automation manual-review volume, over time.

```
migration_ratio = exception_queue_volume_now / manual_review_volume_before_automation
```

Example: automation was projected to eliminate 80% of manual review (leaving 20% as expected exceptions). If `migration_ratio` comes back at 75% instead of the expected 20%, only 5 percentage points of the projected 80% reduction actually disappeared; the rest moved from "manual review" to "exception review," which is a relabeling, not a reduction. Report the ratio explicitly in transition metrics (see [transition-metrics.md](../06-change-and-capability/transition-metrics.md)); don't report only the review-volume reduction, since that number alone can't distinguish elimination from migration.

## Why this connects to the autonomy ladder

These are exactly the signals [promotion-and-demotion-criteria.md](../03-progressive-autonomy/promotion-and-demotion-criteria.md) uses as a promotion gate. Rubber-stamping detected at the assist rung blocks promotion to approve-to-act regardless of a favorable Wilson-bound override rate. A low override rate produced by reviewers not actually reviewing is not evidence the AI is reliable.
