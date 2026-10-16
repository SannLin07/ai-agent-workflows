# Flutter task execution

Status: draft — these task guides have not yet been piloted in a Flutter project.

Use a task guide after [loading project context](../documentation/agent-context-loading.md). Technology modules explain how to work within the chosen stack; a task guide orders the work around a requested outcome. These guides are shared procedures, not selectable modules, so they do not add IDs or fields to `project.yaml`.

## Choose the guide for the outcome

| Requested outcome | Read | Working record |
|---|---|---|
| Add or change user-visible behavior | [Feature delivery](feature.md) | [Feature brief](../../templates/feature/feature-brief.md) |
| Investigate or correct observed incorrect behavior | [Bug diagnosis and fix](bug-fix.md) | [Bug report](../../templates/bug-report/bug-report.md) |
| Validate a build candidate or prepare distribution | [Release readiness](release.md) | [Release checklist](../../templates/release/release-checklist.md) |

Read only the guide for the current work. When a task crosses stages, such as a fix followed by release preparation, finish the first stage's evidence before loading the next guide. For documentation-only work, use the [documentation rules](../documentation/README.md) directly.

Use an existing issue, pull request, or project document as the working record when it already holds the needed information. Templates describe useful fields; they do not require extra files for every small task.

## Evidence and handoff

Use the [task report](../../templates/task/task-report.md) to connect each acceptance criterion to its result and evidence. A short task may report these fields directly in the final response. Keep **verified**, **failed**, **not run**, and **not applicable** distinct: a planned command or an unchecked checklist item is not verification. Explain why a check is not applicable; for a check not run, record the missing prerequisite and the next action.

Mark the task complete only when the requested criteria are verified. Use partial or blocked when required evidence or behavior is missing, and name the specific remaining work. A diagnosis-only request can be complete with a supported diagnosis or an evidence-backed account of what remains unknown; it does not imply a fix was made. Release preparation can be complete with a validated candidate; it does not imply publication.

Use [coding rules](../coding-rules/README.md) and selected testing modules for verification scope, [Git rules](../git/README.md) for repository and remote actions, and the [troubleshooting knowledge base](../../troubleshooting/README.md) for recording observed incidents. Each remains the canonical owner of its rules.

## Pilot the upgrade

Choose one real, bounded Flutter task and use its selected module versions with one guide. Record the task reference, guide used, acceptance results, verification limits, and any ambiguous or missing instruction in its task report. Change guidance only from that evidence. A document review alone does not establish that a guide works in a Flutter project; keep each guide draft until its own procedure has been validated through use.
