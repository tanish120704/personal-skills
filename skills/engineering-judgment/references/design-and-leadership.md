# Design and leadership

These are general engineering decision prompts. Book-specific claims require reading available source passages; the linked extracts do not cover either complete book.

## Complexity and interfaces

Trace a representative caller's task. Evaluate how much knowledge, ordering, configuration, and cross-component coordination it requires. Count conceptual obligations and failure paths, not just files or lines.

Ask whether an abstraction hides implementation detail or merely relocates it. Similar-looking code may encode different semantics. Shared abstractions are more persuasive when consumers have stable common behavior; separate implementations can be preferable when ownership and change cadence differ.

Avoid speculative extension points. Conversely, preserve a modest boundary when an evidenced upcoming change would otherwise be expensive. Compare the cost of a boundary against the change it makes easier.

Ask: What must a caller know, and which details can the component safely own?

Read the author-provided A Philosophy of Software Design extract for the topics it actually contains, including deciding what matters and general-purpose modules. Do not attribute the full guidance above to unread chapters.

## Leading technical work

Identify the stakeholders, decision owners, affected teams, and people who will operate the result. Understand how the proposed change connects to organizational goals and competing work. Titles do not establish that an argument is correct.

Make dependencies concrete: required contribution, owner, timing, and what happens if it does not arrive. Before choosing a design that depends on many teams changing together, evaluate whether a compatibility boundary or different sequencing can reduce coordination.

Distinguish disagreement over facts, goals, constraints, and preferences; seek evidence or a decision at the appropriate level. Record consequential reasoning and uncertainty so later engineers can revisit it without reconstructing the conversation.

Ask: What needs to be true across the organization for this design to become useful and remain supported?

The linked Staff Engineer's Path preview and author companion resource list provide partial reading material and topic navigation. They do not establish access to all project execution or leadership chapters. Use Software Engineering at Google chapters 3, 5, 6, and 10 as available full-text sources for related questions.
