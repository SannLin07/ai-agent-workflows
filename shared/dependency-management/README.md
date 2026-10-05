# Dependency management rules

- Add the smallest maintained dependency that meets a concrete requirement; check whether the platform or current project already provides the capability.
- Use compatible constraints in package manifests and commit the consuming project's lockfile when its ecosystem expects one.
- Treat `packages.md` constraints in this library as dated recommendations, not installed-version guarantees.
- Check the official registry, supported platform range, release activity, license, and migration notes before adoption or a major upgrade.
- Prefer one dependency for one clear capability; avoid overlapping clients or state tools without an explicit reason.
- Regenerate code only with the repository's documented generator command and review generated changes.
- Remove unused dependencies and update setup instructions when a dependency changes.
