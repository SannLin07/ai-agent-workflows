# Unit testing workflow

Use this module when `unit` is selected in the `testing` category and the behavior can be proved without rendering Flutter UI or exercising a real platform integration. Read it with the shared rules and only the other selected workflows that affect the code under test.

## Use this workflow when

- A function, class, mapper, validator, formatter, or domain rule has meaningful behavior.
- A state-management controller, notifier, bloc, or view model makes decisions that can be observed through its public state or outputs.
- A failure is translated at a boundary and callers need a reliable result or state transition.
- A confirmed defect needs regression coverage at the smallest level that reproduces it.

## Choose the right test level

| Level | Proves well | Does not prove by itself |
|---|---|---|
| Unit | Focused logic, transformations, validation, error mapping, and state transitions with controlled dependencies. | Flutter rendering, user interaction, native plugin behavior, or a complete app journey. |
| Widget | Rendering, interaction, semantics, and visible states in a controlled widget tree. | Production network behavior or native platform integration. |
| Integration | A selected journey across real app layers, plugins, navigation, or controlled services. | Every branch, edge case, or supported backend and platform combination. |

Choose the lowest level that gives reliable evidence for the behavior. Add a widget or integration test when the important risk is in the wiring across that boundary. A unit test that replaces the UI or platform boundary cannot establish that the replaced boundary works.

## Agent procedure

1. **Start with the behavior.** Read the acceptance criteria and nearby implementation. Write down the input, observable result, and important edge or failure condition before choosing assertions.
2. **Find the smallest useful seam.** Test a public function or boundary where behavior matters. Avoid exposing private implementation only to make a test possible; introduce a seam only when it clarifies ownership or isolates a dependency that changes independently.
3. **Control external inputs.** Replace network, persistence, clock, random values, platform APIs, and other nondeterministic dependencies with controlled fakes or mocks. Prefer a small fake when the test benefits from realistic behavior; use an interaction expectation when that interaction itself is part of the contract.
4. **Exercise outcomes deliberately.** Cover the main success case and the important boundary and failure cases for the risk. For asynchronous behavior, control completion order and assert that loading, success, cancellation, and failure results are applied only as intended.
5. **Assert observable behavior.** Check returned values, emitted states, transformed data, or meaningful side effects. Keep assertions focused on the contract; avoid tying tests to private fields, incidental call order, or a particular internal helper structure.
6. **Keep each case independent.** Build fresh state or reset shared fixtures for each test. Clean up subscriptions, controllers, timers, and other resources the test owns, following the selected state-management workflow's lifecycle rules.
7. **Run the narrow relevant test first.** Then run the broader project check when required and practical. Use the consuming project's documented commands and SDK constraints; do not invent a test command when the project has not established one.

## Flutter and Dart boundaries

- Keep tests as plain Dart tests when the behavior does not depend on Flutter APIs. Use Flutter test utilities only when the code or project setup needs them.
- Unit tests run without the app's native plugin host. Put plugin calls behind an app-owned adapter or service boundary and replace that boundary in a unit test. Test platform-channel wiring at an appropriate higher level when it is part of the requirement.
- Do not claim that a unit test verifies widget layout, accessibility, navigation integration, native permissions, persistence behavior, or real network behavior when those boundaries were replaced.
- For controller or state-container tests, follow the selected state-management module for construction, dependency registration, asynchronous state, and disposal. Do not mix lifecycle conventions from another state-management tool.
- When testing error translation, assert the stable result or state exposed to the caller. Keep implementation diagnostics out of user-facing outputs and follow the shared error-handling and security rules.

## Test quality checks

- Keep the test name specific enough to explain the behavior and condition being checked.
- Use arrange, act, and assert sections where they improve readability; avoid setup that obscures the scenario.
- Avoid arbitrary delays and dependence on wall-clock timing. Control asynchronous inputs so the test is repeatable.
- Avoid production accounts, credentials, network services, and persistent user data.
- Do not treat line coverage alone as proof that important behavior is tested. Focus on decisions and outcomes that could cause a user-visible or data-integrity failure.
- Add regression coverage only for a confirmed behavior or defect; do not invent incidents or hypothetical bug history.

## Completion checks

- [ ] The test states the expected behavior and covers meaningful success, boundary, or failure outcomes for the risk.
- [ ] External and asynchronous inputs are controlled; the test is repeatable and independent.
- [ ] Assertions cover observable behavior without overfitting to private structure.
- [ ] Plugin, UI, service, and platform claims match the boundaries the test actually exercised.
- [ ] Resources owned by the test are cleaned up, and the selected state-management lifecycle is respected.
- [ ] The reported verification names the commands that ran and clearly identifies any checks that remain unverified.

## Official references

- [Testing Flutter apps](https://docs.flutter.dev/testing/overview) — Flutter's comparison of unit, widget, and integration test scope. Verified 2026-10-09.
- [An introduction to unit testing](https://docs.flutter.dev/cookbook/testing/unit/introduction) — Dart unit-test structure and examples. Verified 2026-10-09.
- [Plugins in Flutter tests](https://docs.flutter.dev/testing/plugins-in-tests) — plugin boundaries and approaches to testing code that calls plugins. Verified 2026-10-09.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
