# Change and migration

Read for replacements or substantial evolution of an existing system, data model, predictive model, API, schema, library, or platform. Clarify what "model" means from context; do not assume machine learning.

## Start from the problem

Identify the highest-impact problems using incidents, latency measurements, support burden, costs, developer friction, or product evidence. Distinguish symptoms from structural limitations. Rank qualitatively when evidence does not support precise scoring.

Compare targeted improvement, compatible extension, and replacement where plausible. Replacement may be justified when fundamental constraints prevent the desired outcome or compatibility costs outweigh its benefit. Age alone is not evidence that a system should be replaced.

## Design the transition

These are prompts, not a mandatory sequence:

- Find a bounded capability or consumer that can move independently and produce useful evidence.
- Identify prerequisites, interface promises, accidental dependencies, data ownership, and mixed-version behavior.
- Specify an intermediate state that remains understandable and operable during coexistence.
- Decide who owns migration and how consumers will be supported. Do not assume every consuming team can absorb an unfunded migration.
- Define success, expansion, pause, and retirement against actual constraints.
- Budget temporary infrastructure and maintenance. Assign removal of adapters, flags, duplicate pipelines, and obsolete code.

Sources: Software Engineering at Google chapters 1, 15, 22, and 24. The mechanisms below are engineering applications, not claims that every mechanism appears in those chapters.

## Match rollout mechanisms to risk

| Mechanism | Useful when | Limitation to evaluate |
|---|---|---|
| Offline comparison or replay | Representative existing cases can compare behavior | Cases may omit recent conditions; do not replay external side effects |
| Shadow execution | Outputs can be compared without controlling live decisions | Extra cost, privacy, unintended writes; isolate effects |
| Small consumer or traffic cohort | Exposure can be bounded during real use | Cohort bias, mixed versions, cross-cohort interactions |
| Compatibility adapter | Consumers need different migration schedules | Maintenance and possible permanent coexistence |
| Expand-and-contract schema change | Old and new application versions must coexist | Backfills, write semantics, constraints, restoration |
| Coordinated cutover | Mixed operation would be unsafe or more complex | Coordination cost and explicit recovery preparation |

## Distinguish rollback from recovery

Changing code back does not undo schema changes, sent messages, payments, deleted data, or model-driven actions. Identify the relevant recovery route: rollback, restore, replay, compensation, or forward repair. Check whether restoration is practical within the tolerated interruption.

For parallel writes, establish the authoritative source and reconciliation behavior. Do not suggest dual writes casually; partial success and ordering can produce divergence.

## Example: replacing a shared internal model

Suppose the current model has confusing validation errors, slow reads, and inconsistent representations. Verify which issue hurts users most. Better diagnostics might be delivered within the existing contract while structural alternatives are evaluated for performance. If a new representation is needed, a bounded consumer can establish evidence about correctness, latency, and migration effort before wider adoption.

Separate useful improvements from unvalidated assumptions. Do not force independent releases when changes are inseparable. Include final removal of the old representation in the estimate.

## Preserve architecture during change

Select properties worth protecting and attach evidence. Examples: compare a defined latency percentile at representative load, verify supported consumers against the contract, or monitor resource cost per completed operation. A threshold is a project decision, not a universal benchmark.

Source: Building Evolutionary Architectures, second edition, available chapter 1. Continuous checks support change; they do not eliminate judgment.
