# Release readiness

Status: draft — not yet piloted in a Flutter project.

Use this guide to validate a Flutter build candidate or prepare distribution. Start after [context loading](../documentation/agent-context-loading.md). Platform build details belong to the selected deployment modules; tester access belongs to selected release-channel modules. This guide connects their evidence to a release decision.

## Procedure

1. **Identify the candidate and requested action.** Record the app version/build, source commit and any local changes included, target platforms, environment, intended audience, and whether the request covers preparation or distribution. Use the [release checklist](../../templates/release/release-checklist.md). Finish with one identifiable candidate and an explicit action scope.
2. **Load the applicable release boundaries.** Read selected platform, distribution, and release-channel entrypoints with their required modules. For example, an Android build, a Play Store upload, and closed tester access involve different selected modules. Verify mutable package and platform requirements using the authoritative references in those modules and record the check date. If a requested store or target has no library module, use the project's approved procedure and current vendor guidance, or report the coverage gap before the unsupported step. Finish with the procedures and requirements that actually apply to this candidate.
3. **Collect candidate-specific evidence.** Follow the selected modules and project checks. Associate each result with the build tested, device or environment, command or manual action, and observed result. Record required checks that cannot run and their missing prerequisites. If code or build configuration changes, identify the new candidate and reassess which earlier evidence remains valid. Finish when the checklist makes all remaining readiness gaps visible.
4. **Make the readiness decision.** Record go/no-go, known limitations, decision owner, and the applicable recovery and monitoring arrangements. Keep readiness distinct from permission to distribute; follow the canonical [Git and remote-action rules](../git/README.md) and the user's requested scope. Preparation finishes with the candidate, evidence, and remaining distribution action recorded.
5. **Perform and verify distribution when authorized.** Follow the selected distribution procedure. Record the actual artifact, destination, audience, and observed result. Distinguish upload, review, tester availability, and public availability using evidence from the destination; one does not establish the others. Hand off monitoring to the named owner and report the result through the [task report](../../templates/task/task-report.md), using the [shared completion criteria](README.md#evidence-and-handoff).

## Limits

A successful build alone does not verify install, upgrade, or a user journey. Missing signing access, store permissions, hardware, or an approved distribution procedure is a specific release gap; record what remains possible and what requires that prerequisite. Keep current store requirements in sourced platform guidance rather than copying numeric thresholds into this shared guide.
