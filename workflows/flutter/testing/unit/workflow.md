# Unit testing workflow

Use this module when `unit` is selected in the `testing` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

Business decisions, validation, mapping, state, or errors can be tested without rendering the app.

## Avoid when

A unit test is used to claim platform integration or rendered UI works.

## Test scope

| Level | Proves well | Does not prove by itself |
|---|---|---|
| Unit | A focused function, mapper, validator, or state transition. | Flutter rendering, plugin wiring, or a full journey. |
| Widget | Rendering, interaction, and visible states in a controlled widget tree. | Production network behavior or platform integration. |
| Integration | A selected journey through real app layers and plugins/services. | Every edge case or all backend/platform combinations. |

Choose the lowest level that reliably proves the behavior, then add a few higher-level checks for critical wiring.

## Agent procedure

1. Assert observable behavior rather than private implementation.
2. Use fakes for external boundaries and control time, randomness, and async completion.
3. Cover important success, boundary, and failure cases according to risk.
4. Add regression coverage for confirmed bugs and clean test-owned resources.

## Completion checks

- [ ] Tests run without production services or credentials.
- [ ] Assertions prove behavior and failure paths.
- [ ] Tests are independent and deterministic.

## Official references

- [Official reference 1](https://docs.flutter.dev/testing/overview)

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
