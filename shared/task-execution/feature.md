# Feature delivery

Status: draft — not yet piloted in a Flutter project.

Use this guide to add or change behavior in a Flutter app. For observed defects, use [bug diagnosis and fix](bug-fix.md). Start after [context loading](../documentation/agent-context-loading.md); use the selected technology modules for implementation details.

## Procedure

1. **Define observable acceptance.** Use the [feature brief](../../templates/feature/feature-brief.md) or an existing issue to describe the user outcome, scope, and criteria. Include relevant failure behavior and target platforms. This step is complete when each criterion describes an outcome that can be checked and material product decisions are resolved.
2. **Trace the affected path.** Follow the user action through the widget, presentation state, and any data or platform boundary it crosses. Identify the current state owner, dependencies, and tests. Finish with a small change plan that names the affected boundaries and selected workflows; keep existing boundaries when they serve the requirement.
3. **Deliver one complete path.** Implement the smallest useful path from user action to visible result using the selected architecture and state-management guidance. Connect real app boundaries or explicitly identify an unavailable integration. A placeholder response does not prove that persistence or a service integration works. Finish with observable behavior that can be exercised through the intended entry point.
4. **Exercise the relevant alternatives.** Use the [coding rules](../coding-rules/README.md) for lifecycle, asynchronous work, user experience, and data safety. Select checks from the changed behavior: for example, a submission may need duplicate-action and retry checks, while a local layout change may need size and semantics checks. Finish when each applicable alternative has an expected outcome and verification evidence or an explicit gap.
5. **Verify and hand off.** Follow the selected testing workflows and the project's established checks. Map results to every acceptance criterion in the [task report](../../templates/task/task-report.md), including integration limits. Review the diff and update affected project documentation. Apply the [shared completion criteria](README.md#evidence-and-handoff).

## Limits

A dependency migration, new primary state tool, or architecture change is a separate decision when the feature does not require it. Resolve that decision through project context before expanding the implementation. If an API contract or platform capability is unknown, investigate that boundary and report the missing decision rather than presenting a simulated integration as a finished feature.
