# Widget testing workflow

Use this module when `widget` is selected in the `testing` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

Behavior depends on Flutter rendering, interaction, accessibility semantics, or visible states.

## Avoid when

Tests use production networks or replace focused business-logic coverage.

## Test scope

| Level | Proves well | Does not prove by itself |
|---|---|---|
| Unit | A focused function, mapper, validator, or state transition. | Flutter rendering, plugin wiring, or a full journey. |
| Widget | Rendering, interaction, and visible states in a controlled widget tree. | Production network behavior or platform integration. |
| Integration | A selected journey through real app layers and plugins/services. | Every edge case or all backend/platform combinations. |

Choose the lowest level that reliably proves the behavior, then add a few higher-level checks for critical wiring.

## Agent procedure

1. Render the smallest useful widget tree and add app/router/providers only when needed.
2. Interact through accessible user-facing labels and controls.
3. Assert visible outcomes and relevant semantics.
4. Use fakes, pump deliberately around async work, and test responsive sizes only when required.

## Completion checks

- [ ] Important interactions and visible states are asserted.
- [ ] No production network or credentials are used.
- [ ] Expectations represent user behavior, not private widget structure.

## Official references

- [Official reference 1](https://docs.flutter.dev/testing/overview)

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
