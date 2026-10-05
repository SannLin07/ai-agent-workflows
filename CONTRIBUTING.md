# Contributing

This repository is maintained to stay useful to one developer and to AI agents. Prefer a small, actionable change over a broad catalog expansion.

## Add or change a workflow

- Keep a stable module ID and path. A renamed display title does not require changing the ID.
- Include `workflow.yaml` plus its declared `entrypoint`. Keep procedures in the entrypoint and disclose branch-specific reference into a nearby file only when it materially helps.
- State purpose, suitable and unsuitable use, ordered actions, verification, and completion criteria.
- Put cross-cutting rules in `shared/`; link to their canonical files.
- Use `requires` for mandatory modules and `conflicts_with` only for combinations that cannot safely coexist. Compatibility claims are advisory and must be evidence-based.
- Use `draft` until the workflow has been applied to a real project. Record concrete gaps for the next revision.

## Version changes

Start new modules at `0.1.0`. Increase patch for corrections and clarifications, minor for compatible additions, and major when the module's selection contract or required behavior changes incompatibly. Update project pins when deliberately adopting a new version. The root `VERSION` changes only for a release of the collection; it does not replace module versions.

## Package and platform facts

Prefer official package registries and vendor documentation. For every package recommendation record its name, purpose, compatible constraint, direct source URL, notes, and `verified_on` date. Recheck volatile platform steps when updating them. Constraints are recommendations, not lockfiles; the consuming project's resolver and lockfile determine installed versions.

## Troubleshooting evidence

Add an incident only after observing it. Record the affected environment, exact error or other evidence, investigation, confirmed root cause or unresolved hypotheses, solution, verification, prevention, and related workflow. Keep secrets, tokens, personal data, and private logs out of the record.

## Review checklist

- Is the module discoverable through the root README and project schema when applicable?
- Do the metadata ID, path, category, entrypoint, dependencies, and version agree?
- Are instructions actionable and scoped to their selected technology?
- Are conflicts explicit and minimal?
- Are factual claims dated and sourced where they can change?
- Is any content duplicated instead of linked to its canonical rule?
- Does the change avoid implying that scripts, a package manager, or an orchestration engine exist?
