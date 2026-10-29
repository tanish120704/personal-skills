# Production and AI

Use questions appropriate to the workload. The production lens is informed by publicly available Release It! excerpts and the Google book. Detailed mechanisms and AI guidance here are original applications, not summaries of unavailable chapters.

## Follow a real operation

Trace a critical user operation through dependencies. Consider unavailable, slow, malformed, or partially successful responses and how they consume caller resources. A service that stays running while every request fails is not providing useful reliability.

At consequential boundaries, evaluate:

- End-to-end deadlines and time remaining for each dependency.
- Bounded retries, safety of repeated side effects, and retry load during recovery.
- Limits on queues, concurrency, memory, result sizes, and worker or connection pools.
- Isolation of expensive or failing work from shared capacity.
- Degraded responses, rejection, or fallback appropriate for the task.

Do not add every resilience mechanism automatically. Queues create persistence and recovery questions; circuit breakers add state and failure modes. Choose mechanisms for observed or credible failure paths.

Source basis: Release It! introduction and stability antipatterns excerpt. Verify specific implementation guidance against the platform and current documentation.

## Evaluate performance and cost together

Define expected load, bursts, concurrency, payload sizes, and an appropriate latency distribution. Separate observed bottlenecks from guesses. Check whether an optimization reduces one resource while increasing another, affects correctness, or creates operational complexity.

Include engineering effort and steady-state support. For substantial decisions, show assumptions and cost ranges rather than unsupported point estimates. Recalculate when volume, pricing, or team capacity changes.

Source basis: Software Engineering at Google chapter 1; workload prompts are original applications.

## Connect observability to actions

For important operations, consider completion rate, latency, failure categories, resource pressure, and relevant cost. Add correlation across boundaries when it changes debugging effectiveness. Prefer actionable alerts over notifications for every transient event. Do not collect secrets or sensitive input by default.

For a rollout, define evidence permitting expansion and evidence triggering pause or recovery. Verify that telemetry appears and can distinguish unhealthy dependencies from regressions. Consider instrumentation overhead and retention costs.

Source basis: Software Engineering at Google chapter 24 discusses health indicators and staged rollout; diagnostic questions are original synthesis.

## AI-enabled systems

This section extends the engineering perspectives to AI work. It is original guidance, not attributed to the three books.

### Define task success before orchestration

Compare a deterministic baseline, a single model call, retrieval, a defined workflow, and a more autonomous agent only when relevant. Fluent responses and successful API calls do not establish task success.

Use representative evaluations with clear success criteria and known failure cases. Include difficult and changed inputs. Separate model quality, retrieval quality, tool reliability, and task completion so one improvement does not hide other regressions. For stochastic outputs, avoid strong conclusions from a single run.

### Treat prompts, models, tools, and retrieval as changeable dependencies

Version the components needed to reproduce meaningful results. Compare candidates on representative cases before expanded exposure. Check output validity, refusal behavior, tool selection, latency, and cost. Provider aliases and dependency updates can change behavior without application-code changes.

### Bound execution and effects

For tool-using systems, specify permissions and the boundary between proposed and executed actions. Apply stricter controls to irreversible or high-impact effects. Bound execution using appropriate deadlines, tool-call limits, retries, or spend. Prefer idempotent actions or handle duplicate execution explicitly.

Treat retrieved material and tool outputs as untrusted data. Model confidence is not authorization. Use human review where consequence and uncertainty justify it, not as a universal extra step.

### Measure the operated workflow

Consider cost per successfully completed task, relevant latency percentiles, tool failures, invalid outputs, repeated attempts, and human intervention. Identify fallback behavior that preserves the user's goal where possible; a cheaper model or stale cached answer is not automatically safe.

Instrument relevant steps and outcomes with appropriate redaction and retention. Check current model limits, prices, provider behavior, and data handling before relying on them. Do not infer credentials or permission to call a paid API from this skill.
