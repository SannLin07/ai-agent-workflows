# Agent context loading

Use the project configuration as an index, not as permission to load the whole library.

## Load in this order

1. Read the applicable system, platform, and user instructions.
2. Read the project's `project.yaml`, local `AGENTS.md` or equivalent, and accepted architecture decisions that affect the task.
3. Read the global rules that bear on the change: coding, Git, security, error handling, logging, documentation, and dependency management.
4. Resolve selected workflow IDs to `workflows/<platform>/<category>/<slug>/workflow.yaml`. Read each selected module's `entrypoint` only when it applies to the task; follow its `requires` recursively.
5. Load additional module references only when the task reaches that branch, such as GetX testing guidance when changing a controller test.
6. Before finishing, compare the change with the selected workflow's verification and completion criteria.

For a Flutter task, `flutter.state_management` and `flutter.routing` each identify one workflow. Each ID in the architecture, networking, storage, authentication, backend, and testing lists identifies one workflow. Translate category and slug directly to the matching module path. A missing or unknown ID is an unresolved configuration issue; do not substitute a nearby technology silently.

## Check combinations

- Load mandatory modules named in `requires` even if they were not separately selected.
- Reject pairs named by either module's `conflicts_with`.
- Treat `compatible_with` as a positive hint, never as proof that all unlisted pairings are incompatible.
- Enforce one state-management module and one routing module. If multiple architectures are selected, require an explicit composition decision. For other list categories, inspect actual module constraints rather than assuming every pairing is safe.
- If a project pin differs from the selected module's version, use the project's pinned version when it is available in the library. If unavailable, report the mismatch and ask how to proceed.

## Resolve conflicts openly

Higher-priority platform or system instructions always apply. Within the project, an explicit current user instruction can change a project decision; record the change if it affects durable configuration. Accepted project-specific decisions and rules define local constraints. The project configuration selects technologies. Global MUST rules and selected workflow MUST rules still apply within their stated scope; a conflict between them or with an accepted project decision must be shown to the user. The agent should identify the exact conflicting statements and ask for a resolution when the task cannot proceed safely. It should not silently discard a rule. SHOULD and default guidance can be adapted with a stated reason.

Security and privacy requirements are hard guardrails: a project rule or user preference cannot turn credential exposure or unsafe handling into an acceptable implementation. Explain the constraint and offer a safe implementation.

## Keep context task-sized

Load only the entrypoints related to the task. For example, a text-only change does not need the SQLite or authentication workflows. A new authenticated API feature may need state management, architecture, networking, routing, secure storage, authentication, and relevant testing guidance. Record which modules actually informed the change in the final summary when that helps the developer review it.
