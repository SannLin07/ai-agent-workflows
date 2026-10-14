# Contributing

This repository maintains reusable workflows for Flutter application work. Add or revise guidance when it addresses a concrete need from a Flutter project. Write for a developer and an AI agent who need enough context to make and verify a sound implementation decision. Follow the detailed, Flutter-centered guidance in [`shared/documentation/README.md`](shared/documentation/README.md).

## Add or change a workflow

1. **Start from a real need.** Define the Flutter project situation the workflow serves and the task branches it covers. Keep a module focused on one coherent decision or capability.
2. **Preserve its identity.** Keep the module's stable ID and path when revising it. A display-name change does not require an ID change.
3. **Keep procedure and metadata aligned.** Include `workflow.yaml` and the file declared by its `entrypoint`. Confirm the metadata ID, category, platform, version, dependencies, and entrypoint agree with the directory and procedure.
4. **Write an actionable procedure.** Explain when the workflow applies and when it does not, the decisions and tradeoffs a Flutter developer must consider, the ordered implementation steps, and the evidence required to complete the task. Include lifecycle, async state, platform, accessibility, performance, or error details when they affect the module.
5. **Use canonical shared rules.** Keep cross-cutting guidance in `shared/` and link to it from the workflow. Use `requires` only for mandatory modules. Use `conflicts_with` only for selections that cannot safely coexist; record compatibility claims only when there is evidence for them.
6. **Keep maturity evidence-based.** Set a new or unpiloted workflow to `status: draft`. Promote it only after a real Flutter project has used the guidance; record concrete gaps and follow-up work from that use.
7. **Update discovery files.** When a module becomes selectable, update the project schema and example configuration. Add it to the root README and document real compatibility constraints where they help project selection.

## Version changes

Start new modules at `0.1.0`. Increase the patch version for clarifications and corrections that do not change expected behavior. Increase the minor version for backward-compatible additions. Increase the major version when the selection contract or required behavior changes incompatibly. Update a consuming project's pins only when it deliberately adopts the new module version.

The root `VERSION` identifies a release of the workflow collection. It does not replace independent module versions and changes only when the collection is released.

## Package and platform facts

Treat package constraints as dated recommendations. For every package recommendation, record the package name, purpose, compatible constraint, direct authoritative source URL, relevant notes, and `verified_on` date. Check the consuming project's Flutter and Dart constraints, supported platforms, release activity, license, and migration guidance before recommending a package or major upgrade.

For platform and deployment instructions, cite the vendor's current documentation and record when the instructions were checked. Add an owner or review trigger when a fact can change. The consuming project's dependency resolver and lockfile determine installed package versions.

## Troubleshooting evidence

Create an incident record only after a problem has been observed and investigated. Include the affected Flutter, Dart, package, and platform versions; exact sanitized evidence; investigation steps; confirmed cause or remaining hypotheses; fix; verification; prevention; and related workflow. Keep secrets, tokens, personal data, and private logs out of the record.

## Review checklist

- Does the workflow address a real Flutter project need and make its scope clear?
- Do its ID, directory, category, platform, `workflow.yaml`, entrypoint, dependencies, and version agree?
- Are the procedure, tradeoffs, verification steps, and completion criteria clear enough to follow and check?
- Are cross-cutting rules linked from their canonical files, with no duplicated policy?
- Are hard conflicts minimal and supported by a concrete incompatibility?
- Are package and platform facts sourced, dated, and paired with a review trigger when they can change?
- Are schema, example configuration, and README discovery updated when a module becomes selectable?
- Does the change describe only tooling and automation that actually exist?
