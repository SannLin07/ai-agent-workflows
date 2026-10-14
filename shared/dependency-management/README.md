# Flutter dependency-management rules

Choose a dependency to solve a concrete requirement in the Flutter project. A package affects the app's supported SDKs, platforms, build, security surface, and future upgrades, so check the project before recommending or adding one. Use the selected workflow's package guidance as a dated starting point, then verify the consuming project's actual constraints and resolution.

## Decide whether a package is needed

1. Define the capability the feature requires and check whether Flutter, Dart, or an existing project dependency already provides it.
2. Compare only packages that meet the required behavior. Prefer the smallest maintained option that supports the project's Flutter and Dart constraints and every target platform the feature must support.
3. Review the package's official registry entry, documentation, release activity, license, transitive dependencies, permissions, and migration notes. Check provenance and privacy implications when the package handles credentials, personal data, networking, or platform APIs.
4. Explain the choice in terms of the feature's needs and relevant tradeoffs, such as platform support, setup complexity, generated code, maintenance, or migration cost.

Avoid adding a package for a capability the project already has. Use one dependency for one clear responsibility; overlapping HTTP clients, storage packages, or state-management tools need a concrete project decision and boundary.

## Resolve versions in the consuming project

- Check the project's `environment` constraints, `pubspec.yaml`, and `pubspec.lock` before choosing a version. The resolver and lockfile determine the version the app actually uses.
- Use a constraint compatible with the consuming project and its other dependencies. A newer release is not automatically the right upgrade when it changes SDK support, APIs, generated code, platform setup, or migration work.
- Treat this library's `packages.md` constraints as dated recommendations, not as lockfile entries or guarantees about the resolved version.
- Before a major upgrade, review the package changelog and migration guide, inspect affected APIs and transitive dependencies, and check the app's supported Flutter and Dart versions.
- Follow the consuming project's lockfile policy. Application projects generally need reproducible resolved versions; reusable packages may follow a different repository policy.

## Manage generated code and package changes

- Run code generation only with the consuming project's documented command and compatible generator versions. After changing annotations or generator inputs, regenerate the outputs and review the complete diff.
- Treat generated files according to the project's source-control policy. Keep generation reproducible and make changes in source annotations or inputs rather than editing generated output by hand.
- When removing or replacing a dependency, check imports, platform configuration, generated files, build settings, tests, and setup documentation. Remove obsolete configuration with the package.
- Update user-facing setup instructions when a package choice changes installation, permissions, initialization, or supported platforms.

## Record package recommendations in this library

Every package recommendation belongs in the workflow's `packages.md`. Record the package name, purpose, compatible constraint, direct authoritative source URL, relevant notes, and `verified_on` date. Recheck volatile facts when updating the recommendation and use the package registry or vendor documentation as the source. Follow [`CONTRIBUTING.md`](../../CONTRIBUTING.md#package-and-platform-facts) for the full documentation requirements.

## Verify dependency changes

- Resolve dependencies using the consuming project's documented package command and inspect the resulting lockfile changes.
- Run the project's formatter, analyzer, and relevant tests when they apply to the package change. For platform plugins, verify the affected build targets and setup steps as well.
- Review the final diff for unexpected version changes, duplicate capabilities, generated-code churn, exposed secrets, new permissions, license concerns, and unsupported targets.
- Report the package and resolved version, the compatibility evidence checked, and any build or test checks that were not run.
