# Agent context loading

Use the Flutter project's configuration as an index into this library, not as a reason to load every workflow. A senior-quality change depends on the project's actual SDK constraints, architecture, conventions, and acceptance criteria as well as the selected modules. Load enough context to make a sound decision, then keep unrelated guidance out of the task.

## Load context in this order

1. **Read higher-priority instructions and the task.** Identify the requested behavior, acceptance criteria, constraints, and any applicable system, platform, or user instructions.
2. **Understand the Flutter project.** Read `project.yaml` when present, local `AGENTS.md` or equivalent, and accepted architecture decisions that affect the change. Inspect the relevant parts of `pubspec.yaml`, the lockfile, `analysis_options.yaml`, platform configuration, nearby implementation, and tests when they determine APIs, supported targets, conventions, or verification commands. Report missing configuration or conflicting project decisions instead of inventing defaults.
3. **Load shared rules that apply.** Read the coding rules, then the relevant Git, security, error-handling, logging, documentation, and dependency-management rules. Keep each shared rule in its canonical file; workflow documents link to those rules rather than replacing them.
4. **Resolve selected workflow IDs.** Map each selected ID to `workflows/<platform>/<category>/<slug>/workflow.yaml`. Confirm its category, version, and declared `entrypoint`. Read an entrypoint when its subject affects the task, and recursively load every module named in `requires`.
5. **Load branch-specific references when needed.** Read a module's package list, checklist, test guide, or other nearby reference only when the implementation reaches that topic. For example, consult GetX controller testing guidance when changing a controller test.
   For feature delivery, bug diagnosis or fixes, and release preparation or distribution, use the [task guide index](../task-execution/README.md) to load only the applicable task procedure. For other work, proceed with the relevant shared rules and selected modules.
6. **Compare the implementation with its evidence.** Before finishing, check the change against acceptance criteria and the selected workflows' verification and completion criteria. Report which workflow guidance informed the work and which checks ran or remain unverified.

## Resolve Flutter selections

For a Flutter project, `flutter.state_management` and `flutter.routing` each identify one workflow. Each ID in the architecture, networking, storage, authentication, backend, optional UI, and testing lists identifies a workflow. Translate the category and slug directly to the matching module path. A missing or unknown ID is an unresolved configuration issue; do not substitute a nearby technology silently.

The optional `flutter.ui` list maps each slug to `flutter.ui.<slug>` and `workflows/flutter/ui/<slug>/workflow.yaml`. Omission or an empty list selects no UI modules and keeps existing project configurations valid. Selecting a UI module does not replace the baseline user-experience and accessibility rules in the shared coding guidance.

The project configuration selects possible technologies for the app. It does not mean every selected module is relevant to every task. For a widget-only change, skip authentication and database guidance unless the behavior touches those boundaries. For an authenticated API feature, load the selected architecture, state management, networking, routing, authentication, secure storage, and testing guidance that the feature crosses.

## Check module combinations and versions

- Load every mandatory module named in `requires`, even when the project did not select it separately.
- Treat a pair as a hard conflict when either module names the other in `conflicts_with`.
- Treat `compatible_with` as a positive hint, not a complete compatibility matrix. Check actual module requirements before combining selections that are not listed as compatible.
- Enforce one primary state-management workflow and one routing workflow. If the project selects multiple architecture modules, require an accepted decision that explains how they compose. Combine other list categories only when the project has a concrete use for each module.
- If a project pin differs from the selected module version, use the pinned version when that version is available in the library. If it is unavailable, report the mismatch and ask how to proceed.

## Resolve conflicts openly

Higher-priority system and platform instructions always apply. Within the project, an explicit current user instruction can change a project decision; record the change when it affects durable configuration. Accepted project decisions and local rules constrain implementation, while the project configuration selects technologies.

Global MUST rules and selected workflow MUST rules apply within their stated scope. When one conflicts with another or with an accepted project decision, identify the exact statements and ask for a resolution if the task cannot proceed safely. Adapt SHOULD-level and default guidance only with a clear reason. Do not silently discard a rule.

Security and privacy requirements remain hard constraints. A project rule or user preference cannot make credential exposure or an unsafe access boundary acceptable. Explain the constraint and continue with a safe implementation path.

## Keep context task-sized

Read only the entrypoints that bear on the change, and follow their required modules. A text-only documentation change usually needs no Flutter feature workflows. A layout change may need the selected architecture, state-management, adaptive-layout, accessibility, and widget-testing guidance. A translated form may need selected forms, localization, and relevant testing guidance. A new authenticated API flow may need architecture, state management, networking, routing, secure storage, authentication, the API contract, and relevant tests.

Add detail as the task reaches a boundary, such as package-specific setup, code generation, controller lifecycle, or a platform release step. This keeps the agent's decisions grounded in the project without making it repeat unrelated library instructions.
