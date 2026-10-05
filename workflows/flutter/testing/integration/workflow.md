# Integration testing workflow

Use this module when `integration` is selected in the `testing` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

A critical journey crosses app layers, plugins, navigation, storage, or a controlled backend.

## Avoid when

A slow end-to-end test is used for every branch already covered by unit/widget tests.

## Test scope

| Level | Proves well | Does not prove by itself |
|---|---|---|
| Unit | A focused function, mapper, validator, or state transition. | Flutter rendering, plugin wiring, or a full journey. |
| Widget | Rendering, interaction, and visible states in a controlled widget tree. | Production network behavior or platform integration. |
| Integration | A selected journey through real app layers and plugins/services. | Every edge case or all backend/platform combinations. |

Choose the lowest level that reliably proves the behavior, then add a few higher-level checks for critical wiring.

## Agent procedure

1. Choose a few valuable journeys with explicit setup and cleanup.
2. Use dedicated test environments and non-production accounts.
3. Verify plugin/platform wiring on supported targets.
4. Capture sanitized diagnostics; keep lower-level tests for most branches.

## Completion checks

- [ ] Test data is reset/cleaned safely.
- [ ] At least one claimed critical path crosses real app boundaries.
- [ ] The test environment cannot mutate production.

## Official references

- [Official reference 1](https://docs.flutter.dev/testing/integration-tests)

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
