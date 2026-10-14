# Documentation rules

Documentation should help its intended reader understand a decision and act on it without loading unrelated material. Write in a detailed, explanatory style: give the context and reasoning needed to use the guidance, then make the expected actions and checks easy to find.

## Explain decisions and actions

- Introduce the purpose and scope of a document before giving instructions when the reader needs that context to decide whether it applies.
- Explain why a recommendation matters when it affects architecture, security, reliability, or maintenance. Include the relevant tradeoffs and assumptions.
- Put actions in the order they should happen. State the expected result and how to verify completion.
- Describe important failure paths, exceptions, and limits when they change what the reader should do.
- Define unfamiliar terms when they first matter. Use a concrete example when it makes a rule easier to apply.
- Use short paragraphs, descriptive headings, and lists or tables for steps and comparisons. Keep each section focused on one decision or task.
- Keep explanations relevant to the intended reader and task. Link to a canonical rule or deeper reference when more detail is useful.

## Keep guidance Flutter-centered

- Treat Flutter and Dart application work as the primary scope of this library. Describe backend and platform services only where they define an integration boundary or affect the Flutter app's behavior.
- Make recommendations specific to the selected Flutter workflow. Explain relevant effects on widget composition, state ownership, asynchronous work, navigation, persistence, rendering performance, accessibility, or platform integration.
- Explain the tradeoffs a senior engineer needs to evaluate: the project's existing conventions, complexity added, lifecycle ownership, failure behavior, testability, and production impact.
- Ground implementation guidance in the consuming project's Flutter/Dart constraints and established patterns. Add abstractions or dependencies only when they solve a concrete problem in that project.
- Include only the Flutter concerns that affect the current module or task. Link to other selected workflows and shared rules for concerns they own.

## Keep rules canonical

- Store each cross-cutting rule in one canonical file and link to it from dependent workflows or documents.
- Keep a workflow entrypoint focused on its applicability, decisions, ordered actions, verification, and limits. Move branch-specific reference material to a nearby file only when that makes the entrypoint easier to use, and link to the reference.
- Avoid repeating a rule in multiple documents. When a repeated instruction is needed for context, summarize it briefly and link to the canonical explanation.
- Keep `workflow.yaml` aligned with the declared entrypoint and module metadata.

## Show evidence and uncertainty

- Distinguish confirmed behavior from recommendations, assumptions, and unresolved questions. Label uncertainty where it could affect an implementation decision.
- Support package and platform facts with an authoritative source and the date they were verified.
- Identify an owner or review trigger for facts that can change, including package versions, platform requirements, and deployment steps.
- Treat examples as demonstrations of a real convention. Do not add hypothetical incidents or unsupported compatibility claims.

## Keep documentation current

- Update documentation when a change affects setup, user-visible behavior, project decisions, or a workflow's verification criteria.
- Recheck linked instructions and examples when the surrounding behavior or module metadata changes.
- Before finishing, confirm that links resolve, examples match the described configuration, and the document's instructions agree with the canonical rules.
