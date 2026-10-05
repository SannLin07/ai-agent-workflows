# GetX routing workflow

Use this module when `getx` is selected in the `routing` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The project selects GetX named navigation, route definitions, bindings, and guards.

## Avoid when

GoRouter is selected or deep-link/restoration needs favor an explicit Router API.

## Agent procedure

1. Centralize route names and page definitions.
2. Attach route-scoped registrations through bindings and align them to route lifetime.
3. Pass small validated IDs/arguments and fetch durable data through the feature boundary.
4. Guard routes from selected auth/session state and preserve only validated return destinations.
5. Use one navigation API in a flow; verify platform deep-link setup from current vendor guidance.

## Completion checks

- [ ] Routes, parameters, back behavior, and auth denial are covered.
- [ ] Route dependencies are released appropriately.
- [ ] Supported deep links reach the expected route.

## Package guidance

See [packages.md](packages.md). Verify SDK compatibility, supported platforms, license, and resolver output in the consuming project.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
