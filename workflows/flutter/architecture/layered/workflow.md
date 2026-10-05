# Layered Architecture workflow

Use this module when `layered` is selected in the `architecture` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

A project benefits from clear presentation, service/domain, and data responsibilities with a small number of layers.

## Avoid when

Feature work would spread across unrelated horizontal directories or the app is too small to benefit.

## Architecture tradeoffs

- Benefits: familiar separation with low learning cost.
- Costs: features may span many folders and shared layers can become broad.
- Complexity: low to medium.
- Typical size: small/medium apps with relatively uniform capabilities.
- Compatibility: works with all state tools and may combine with feature-based ownership.

## Agent procedure

1. Define a few layers with one dependency direction.
2. Keep UI from owning transport and persistence details.
3. Add abstractions at volatile or test-critical boundaries; avoid an interface for every class.
4. Document justified dependency exceptions and keep shared folders focused.

## Completion checks

- [ ] Each layer has a clear responsibility and direction.
- [ ] Feature code is findable without duplicate directories.
- [ ] External data sources can be replaced at the chosen boundary.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
