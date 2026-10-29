# Judgment lenses

Use only perspectives that could materially change the decision. These are original decision prompts informed by the sources below; examples are applications, not quotations or prescriptions from the authors.

## Outcome and evidence

State the problem before selecting a solution. A complaint about an old model may concern poor diagnostics or slow onboarding rather than an inherently wrong abstraction. Separate observed impact from a proposed remedy.

Ask: What gets better for whom, and what evidence would demonstrate it?

Use a baseline and meaningful signal where measurement is worthwhile. For an internal tool, time to complete a representative task and support burden may matter more than feature count. Consider measurement cost and whether the result would actually change a decision.

Source: Software Engineering at Google (SWE), chapter 7, goals/signals/metrics and measurement triage.

## Lifetime and ability to change

Choose durability proportional to expected lifetime and exposure. An experiment can be disposable; a shared contract accumulates commitments. Adaptability means retaining the capability to make valuable changes, not predicting every future feature.

Ask: Which plausible change becomes costly, and what modest boundary would keep it manageable?

Avoid both speculative extension points and shortcuts that make a known upcoming change impractical.

Source: SWE chapter 1, sustainability, time, and change.

## Total cost and opportunity cost

Compare runtime resources, implementation effort, support, maintenance, coordination, migration, and temporary coexistence. Include the cost of delaying other useful work. Estimate ranges when inputs are uncertain.

Ask: Are savings local to this team while costs increase elsewhere?

A custom component might lower vendor spend while increasing operational ownership. A managed service might be worthwhile at one scale and expensive at another. Revisit when workload or team capacity changes.

Source: SWE chapter 1, tradeoffs and costs.

## Compatibility in practice

Inspect real consumers, persisted data, and failure behavior. Published interfaces do not capture every dependency. Ordering, timing, error shape, or incidental fields may already affect callers.

Ask: What behavior could consumers rely on that the intended contract omits?

Use usage evidence and representative contract tests to distinguish internal refactoring from consumer-visible changes. Do not preserve every accidental behavior forever; make the impact and transition deliberate.

Source: SWE chapter 1, Hyrum's Law.

## Feedback and change size

Evaluate changes by how easily they can be understood, tested, introduced, diagnosed, and recovered. Size includes conceptual scope and coupling, not just lines of code.

Ask: What is the smallest independently useful or informative step?

A preparatory compatibility change can be worthwhile without immediate user-visible value. Splitting changes is counterproductive if it creates unsafe intermediate states; identify those dependencies first.

Sources: SWE chapters 9, 22, 23, and 24.

## Testability and confidence

Choose tests for the behavior and risks at stake. Prefer stable interfaces and meaningful outcomes over reproducing internal call sequences. Review whether a failure reveals a regression or obstructs harmless restructuring.

Ask: Which meaningful failure would this verification catch?

Avoid declaring success from coverage alone or adding a test for every line. Combine narrow tests with relevant integration evidence where boundaries, persistence, or external behavior create risk.

Source: SWE chapter 12, maintainable tests and testing behavior.

## Operating behavior

Trace a critical operation through dependencies and constrained resources. Evaluate slow responses, partial failure, bursts, malformed input, exhausted pools, and recovery. Prioritize credible scenarios rather than an exhaustive hypothetical catalog.

Ask: How does a local problem affect the rest of the service?

Read [Production and AI](production-and-ai.md) for operational questions. Release It! provides the production-design perspective; the available introduction and stability excerpt are partial sources, not the entire book.

## Observability tied to decisions

Choose signals that help someone assess health and decide what to do. Distinguish a reachable component from a successful user operation. Consider telemetry cost and sensitive data.

Ask: Could an engineer distinguish likely failure causes using the evidence available?

Instrumentation should support concrete debugging and rollout decisions. More dashboards are not inherently better visibility.

Source basis: SWE chapter 24 health indicators; further operational prompts are original synthesis.

## Ownership and shared knowledge

Make responsibility for contracts, operation, migration, and eventual removal clear. Document consequential reasoning and constraints that code cannot explain. Spread essential knowledge through review and mentoring.

Ask: Can another engineer safely operate and modify this without the original author?

Do not turn a small change into a documentation project. Capture information whose absence would cause repeated confusion or risky action.

Sources: SWE chapters 3 and 10.

## Protect useful properties during evolution

Identify architectural characteristics worth protecting during change. Select practical checks, such as a dependency rule, latency budget, compatibility check, or operational review. Automate when reliable measurement and recurrence justify it.

Ask: Which important property could quietly degrade during this improvement?

Checks are useful when they measure the intended property and lead to a meaningful response. Passing checks does not prove the whole architecture is appropriate.

Source: Building Evolutionary Architectures, second edition, official chapter 1 excerpt: guided incremental change and architectural fitness functions. Check examples above are original applications.
