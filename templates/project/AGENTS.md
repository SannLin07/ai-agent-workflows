# Project agent instructions

Use these instructions for Flutter work in this project. Complete a task when the requested behavior meets its acceptance criteria, project decisions are respected, and verification results are reported accurately.

## Before implementation

1. Record the requested outcome and acceptance criteria as the task's completion target. Read this project's `project.yaml`, local instructions, and accepted architecture decisions that affect the task.
2. Inspect the relevant `pubspec.yaml`, lockfile, `analysis_options.yaml`, platform configuration, nearby implementation, and tests. Finish with the Flutter/Dart constraints, supported targets, established patterns, and project verification commands that apply to the task.
3. Use the agent context-loading guide from the workflow library version adopted by this project. Load its canonical shared rules and only the selected workflow entrypoints that affect the task, following each required module recursively. Finish by identifying the workflow modules that inform the change.
4. Check selected module IDs, version pins, and hard conflicts before making an incompatible choice. Resolve each conflict or report the exact decision that needs clarification before proceeding with an incompatible implementation.

## Implement and verify

- Follow the selected architecture, state-management, and routing decisions and the project's existing Flutter conventions. Apply the canonical coding rules and selected workflow procedures to state ownership, widget lifecycle, asynchronous behavior, accessibility, performance, security, and error handling when those concerns affect the change.
- Keep the implementation focused on the requested behavior. Explain material tradeoffs or assumptions that affect compatibility, data ownership, or user-visible behavior.
- Verify every acceptance criterion with the project's documented commands and the selected workflows' checks when they apply. Report the commands run, their results, and any checks that remain unverified. Update relevant documentation when the change affects setup, behavior, or project decisions.

## Completion criteria

- The requested behavior and acceptance criteria are addressed, or any blocked requirement is identified clearly.
- Relevant module conflicts and project decisions are resolved or reported.
- Verification evidence is accurate, and remaining risks or unverified checks are stated.
