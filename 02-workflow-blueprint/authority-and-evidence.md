# Authority and Evidence

`Home › 02-workflow-blueprint › Authority and Evidence`

The blueprint's most consequential field is **authority** — whether the AI acts, whether it recommends and a human decides, or whether the human acts with AI assistance.

## Two recurring failure patterns

**A common failure is leaving authority implicit.** The system ends up with more authority than anyone formally granted, simply because no one built a fallback path for timely human intervention. Authority deserves explicit discipline: "who may decide" should resolve to a named role or rule, not "the AI, usually."

**An equally common failure is a well-designed AI role with no feedback-loop field filled in**, so every correction a human makes evaporates instead of improving the system. The feedback field links directly into the [Chapter 18 evaluation dataset](https://github.com/knowledgetrailsai/OASIS/blob/main/methodology/chapter-18-evaluation-and-reliability-engineering.md) — a correction that doesn't reach that dataset is a lesson the system will need to relearn from a future failure.

## Frame the AI contribution as cognitive work

It is tempting to describe the AI contribution in terms of technology ("uses a language model to draft a response") rather than the cognitive work it replaces ("drafts a first-pass response for human review"). The second framing tells you:

- What evidence a reviewer needs to do their part of the work.
- What authority the human keeps by reviewing first, rather than rubber-stamping.

## What evidence must be visible

The evidence field states what source, confidence, and context must be visible to the human at the point of decision. This is where [Forge](../../Forge)'s [grounding policy](../../Forge/04-grounding-and-context-quality/grounding-policy.md) and [context quality checklist](../../Forge/04-grounding-and-context-quality/context-quality-checklist.md) become load-bearing for workflow design: a human cannot exercise real authority over evidence they cannot see, verify, or trace to its source.
