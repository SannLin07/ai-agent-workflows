# Feature-based architecture workflow

Use this module when `feature-based` is selected in the `architecture` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The app has multiple product areas that should be changed and understood independently.

## Avoid when

A tiny prototype would get empty feature folders, or an established structure already works.

## Architecture tradeoffs

- Benefits: changes stay near the capability owner.
- Costs: duplicated helpers and inconsistent conventions need review.
- Complexity: low to medium; mostly ownership discipline.
- Typical size: apps with several features through large apps; tiny apps can stay flat.
- Compatibility: composes with any state tool and clean layers inside a feature.

## Agent procedure

1. Group code by user capability or domain feature; reserve app/core for genuinely cross-feature concerns.
2. Keep each feature's view and presentation behavior near its owner; add domain/data subfolders only when needed.
3. Keep shared code small and promote components only after another feature has a real use.
4. Define clear contracts for cross-feature calls.

## Completion checks

- [ ] Feature code is discoverable by capability name.
- [ ] Cross-feature imports have clear ownership.
- [ ] Folders reflect existing code rather than anticipated scale.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
