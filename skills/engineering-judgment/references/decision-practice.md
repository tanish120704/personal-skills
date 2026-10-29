# Decision practice

These are original decision aids, not quotations or a claim that every book teaches the same framework. Use judgment to select relevant questions. A small reversible change rarely needs a formal options analysis.

## Frame the decision

Describe the affected user or operator, observed problem, desired outcome, and consequences of doing nothing. Separate requirements from a proposed solution. Establish what must be decided now and what can remain open.

Distinguish hard constraints from habits and preferences. Examples include contractual behavior, data semantics, staffing, deadlines, latency, operating budget, and adoption capacity. Do not invent numerical targets or treat all desired properties as equally important. Understand what currently works and deserves preservation.

## Compare credible alternatives

Include the simplest plausible intervention and a serious alternative when the stakes justify it. Deferral or no change can be a legitimate baseline. Compare against the same outcomes and constraints. Avoid straw-man alternatives that guarantee the preferred design wins.

Account for implementation, runtime cost, maintenance, support, integration, migration, coordination, security where relevant, and eventual retirement. Identify who pays each cost. A local simplification can impose work elsewhere. Use ranges and explicit uncertainty rather than arbitrary weighted scores.

For build-versus-buy, evaluate the actual differentiating requirement, integration fit, operating responsibility, recurring cost at plausible usage, data portability, and exit cost. Existing team expertise is evidence about execution risk, not an automatic veto of unfamiliar tools.

## Find the uncertainty that matters

Identify which assumption could reverse the recommendation. Seek evidence proportionate to the impact: inspect code, trace a workflow, benchmark a representative workload, review incidents, or trial a bounded consumer. An experiment needs a question and a result that changes the next action.

Do not confuse testing implementation correctness with validating usefulness, workload assumptions, or adoption. Prefer learning before irreversible commitments. Do not delay a low-cost reversible decision for information whose acquisition costs more than the likely mistake.

## Design delivery and operation

Look for a useful or informative first slice and evaluate whether intermediate states are operable. Identify coupled changes that genuinely need coordination. Temporary scaffolding may be worthwhile; give it an owner and a removal condition.

Where relevant, specify data authority, failure behavior, compatibility, exposure limits, success signals, recovery, and ongoing ownership. Read the migration or production reference for details. Developer training, support load, and dependent-team schedules are part of delivery effort.

## Make and revisit the decision

Give a recommendation with the dominant reason, cost accepted, important assumption, and next useful action. State what evidence would change the recommendation. Revisit on meaningful triggers such as workload growth, recurring incidents, a failed trial, or changed business constraints; do not invent recurring review ceremonies by default.

For a substantial proposal, a concise decision record may capture context, options, choice, consequences, validation, and revisit trigger. Scale the artifact to the decision rather than require every field in every answer.

## Help the user build judgment

For a lesson, explain:

- Principle: the decision heuristic.
- Mechanism: why it helps and which failure it prevents.
- Boundary: when the opposite choice could be better.
- Evidence: what to look for in the user's actual system.

Avoid inferring competence, motives, or personality from title or a single project outcome. Compare approaches and constraints. Retrospective success does not establish that the choice was obvious from information available at the time.

## Contrasting applications

- A shared platform needs a new configuration source: investigate a compatible consumer change, authoritative data ownership, and phased migration before assuming a complete replacement is necessary.
- A component cannot meet a mandatory requirement: replacement or coordinated cutover may be appropriate when coexistence introduces greater danger or cost. Establish why local changes are insufficient.
- A one-week prototype has no committed consumers: favor quick learning over a reusable platform; identify what must change before production use.
- A team proposes a shared abstraction: compare actual semantics, ownership, and change cadence. Similar syntax alone is insufficient evidence for common behavior.
- A production service retries failing requests: inspect timeout budgets, idempotency, and load amplification before recommending more retries.

Source basis: Software Engineering at Google chapters 1, 7, 10, 15, 22, and 24 inform costs, measurement, documentation, retirement, change, and delivery. Broader decision framing, build-versus-buy, and teaching exercises above are original synthesis. See sources.md for availability and limits.
