# Git workflow for Flutter projects

Use Git to keep Flutter project changes reviewable, recoverable, and scoped to the requested work. Follow the repository's existing branch, commit, release, and pull request policies when they are documented. These rules apply to app repositories and to changes in this workflow library.

## Before changing files

1. Inspect the current branch, working tree, and relevant recent history before editing. Identify user changes that were already present and preserve them.
2. Read the repository's contributor guidance and any local Git instructions. Project policy takes precedence over these defaults.
3. Use a short-lived branch when isolation, collaboration, or review is useful or required. A small personal change may stay on the current branch only when repository policy allows it.
4. Keep the requested change focused. Do not include unrelated formatting, generated output, dependency upgrades, or cleanup just because they are nearby.

Do not reset, clean, discard, or overwrite existing work as a shortcut. If a requested operation could remove or rewrite work, first establish exactly what it will affect and obtain the user's authorization when it was not already given.

## Stage and commit changes

Before committing:

1. Review the changed-file list and the complete diff. Check for unrelated edits, accidental deletions, credentials, private user data, and generated or build output that should not be committed.
2. Stage only files that belong to the intended change. Review the staged diff separately; do not assume the whole working tree is yours.
3. For Flutter or Dart dependency changes, inspect `pubspec.yaml`, the lockfile, and any generated files affected by the change. Keep or update generated artifacts according to the repository's policy, and explain material dependency changes in the review summary. See [dependency management](../dependency-management/README.md).
4. Run only the checks appropriate to the change and project instructions. Report what ran and what did not; do not imply that an unrun check passed. See [coding rules](../coding-rules/README.md) for implementation verification.

Keep commits focused and describe their intent with an imperative summary. A commit should be understandable on its own; split unrelated work into separate commits when practical. Do not create a commit unless the user or task explicitly asks for one, or the established workflow clearly requires it.

## Collaboration and shared history

- Use pull requests when review, collaboration, or a durable discussion is useful or required. Describe the user-visible or engineering impact, relevant verification, and any known limitation. Keep the review checklist proportional to the change's risk.
- Do not rewrite shared history or force-push unless the user explicitly requests it and the target branch and consequences are understood.
- Do not push, merge, publish, or change remote state unless the user requested that action or an existing instruction clearly authorizes it.
- When conflicts occur, preserve both the intended project behavior and unrelated user work. Resolve only conflicts whose intent can be established; ask for clarification when the intended result is ambiguous.

## Releases and versioned artifacts

Tag releases and record user-visible changes when the project distributes versioned artifacts, following that project's release process. For workflow-library changes, preserve workflow IDs and update versions according to [contribution guidance](../../CONTRIBUTING.md). Do not invent release steps or claim a release occurred unless it was actually completed.

## Finish with a clear handoff

When reporting completion, state the files or behavior changed, the checks that were run, and any relevant Git state such as the branch or whether changes remain uncommitted. Keep the summary factual and mention blockers or unverified items plainly.
