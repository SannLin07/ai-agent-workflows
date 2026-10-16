# Bug diagnosis and fix

Status: draft — not yet piloted in a Flutter project.

Use this guide for observed incorrect behavior, exceptions, or performance regressions in a Flutter app. It supports diagnosis-only and fix requests. Start after [context loading](../documentation/agent-context-loading.md) and keep the investigation record in the [bug report](../../templates/bug-report/bug-report.md) or an existing issue.

## Procedure

1. **Establish the observation.** Record expected and actual behavior, affected build and environment, reproduction steps, frequency, impact, and sanitized evidence. Separate supplied reports from observations made during this task. Finish with a reproducible case or a precise account of what could not be reproduced and which evidence is missing.
2. **Locate the failing boundary.** Trace the affected path through the relevant widget, state, data, or platform boundary. For a performance issue, collect measurements under stated conditions before changing the code. Record plausible causes as hypotheses, each with a check that can distinguish it from alternatives. Finish with an investigation plan grounded in the observed failure.
3. **Test the explanation.** Run focused checks and record their results. Change one relevant factor at a time when practical so a result can support or reject a hypothesis. A disappearing symptom alone does not confirm a cause. Finish with an explanation supported by evidence, or an explicit unresolved diagnosis and the next discriminating check. For a diagnosis-only request, report that result without silently expanding into a fix.
4. **Correct the supported cause.** For an authorized fix, make the smallest change that addresses the supported explanation and preserves surrounding behavior. Add regression coverage at the boundary that demonstrates the defect when practical; establish that it detects the original behavior before relying on it. If automation cannot reproduce the issue, record a repeatable manual comparison and its limits. Finish with evidence connecting the change to the original failure.
5. **Verify recovery and adjacent behavior.** Repeat the original reproduction on the corrected build, then run the affected checks required by the selected modules and project. Compare performance under equivalent conditions when relevant. Record results in the [task report](../../templates/task/task-report.md) and apply the [shared completion criteria](README.md#evidence-and-handoff). Add a reusable incident record only under the [knowledge-base rules](../../troubleshooting/README.md).

## When evidence is unavailable

Continue useful read-only investigation while a device, account, log, or environment is unavailable. Distinguish a suspected fix from a verified correction. Report the exact prerequisite for further verification and preserve the unresolved diagnosis in the working record; do not convert a hypothesis into a confirmed incident.
