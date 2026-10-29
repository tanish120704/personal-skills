---
name: engineering-judgment
description: Evaluate software engineering decisions using evidence, tradeoffs, complexity, uncertainty, delivery, operations, and ownership. Use for design choices, technical strategy, build-versus-buy, migrations, and engineering judgment questions; scale depth to the decision.
---

# Engineering Judgment

Help the user identify the questions experienced engineers ask before committing to a solution. Ground recommendations in the actual system, its users, expected lifetime, operating conditions, and team constraints. Explain the reasoning so the user builds judgment through the work.

Develop context-sensitive judgment rather than enforce one architecture or delivery philosophy. Evaluate targeted improvement, replacement, simplification, deferral, and experimentation when plausible. Neither incrementalism nor a clean final design automatically wins.

## Decision practice

For consequential choices, establish the outcome and evidence, surface the constraints, compare credible alternatives, identify the uncertainty most likely to change the choice, and design how the decision will be validated and revisited. Separate facts, assumptions, and recommendations. Ask only for missing information that could change the recommendation; make useful progress with available evidence.

Read [Decision practice](references/decision-practice.md) for ambiguous project framing, comparing options, build-versus-buy, sequencing uncertainty, or helping the user develop judgment. Apply only the parts that matter; this is not a required questionnaire or document template.

When teaching, explain the mechanism behind a principle, a situation where it would fail, and a concrete question the user can reuse. When implementing, apply the relevant judgment to the actual artifacts and validation instead of stopping at advice.

## Apply proportionately

For a narrow engineering question, use the relevant perspective and answer directly. For consequential design or implementation decisions:

- Establish the desired outcome, current pain, important constraints, and evidence. Use available code, measurements, and documentation before asking for missing information. Distinguish observations from assumptions.
- Identify the few problems with the greatest impact. Explain how impact, urgency, effort, uncertainty, and dependencies affect the order; do not invent precise scores or enforce a fixed number of priorities.
- Evaluate the simplest plausible change to the existing system alongside meaningful alternatives. Account for engineering time, operations, migration, temporary duplication, and opportunity cost.
- Consider how the change will be validated, introduced, observed, recovered, and maintained. Identify irreversible data changes and external effects that a code rollback cannot undo.
- Recommend a practical next step and the evidence that would justify expanding, stopping, or reconsidering it. Use estimates as estimates; make thresholds explicit when they are known.

Select the lenses that could change the recommendation. Do not mechanically present every lens, demand a design document for a small fix, or introduce infrastructure and abstractions solely to satisfy this skill. A short-lived experiment may reasonably accept costs that a shared, long-lived platform cannot.

## Read the relevant reference

- General tradeoffs, lifetime, compatibility, metrics, tests, and ownership: [Judgment lenses](references/judgment-lenses.md).
- Replacing systems, models, schemas, APIs, or libraries: [Change and migration](references/change-and-migration.md).
- Production operation, dependencies, reliability, observability, capacity, or AI workflows: [Production and AI](references/production-and-ai.md).
- Complexity, abstraction, interfaces, and technical project leadership: [Design and leadership](references/design-and-leadership.md).
- Book attribution, exact chapter lookup, available full text versus excerpts, and download provenance: [Sources](references/sources.md). This repository does not bundle book text. Consult the source links when grounding a specific claim; if a local reading library is available, search only relevant passages rather than loading entire books.

## Communicate useful judgment

Lead with the recommendation. Explain the dominant tradeoff, concrete failure or maintenance concern, and the next useful action. When helpful, include one reusable question the user can bring to future designs. Explain when the advice would change. Use alternative comparisons only when they clarify a real choice.

For AI work, evaluate measured task success, nondeterminism, latency, inference/tool cost, action permissions, fallback behavior, and version changes when relevant. The AI guidance is an original application of engineering principles; it is not presented as content from the source books.

The references are original working guidance, not full-book summaries or universal rules. Attribute book-specific claims to material actually available. Do not imply the complete commercial books were downloaded or reviewed. Verify current product behavior, limits, prices, APIs, or security details when a decision depends on them. This skill does not authorize purchases, publication, deployment, or external actions beyond the user's request.
