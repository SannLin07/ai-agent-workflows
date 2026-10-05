# Testing GetX features

## Controller unit tests

- Construct the controller with fakes for repositories and services where possible.
- Verify initial state, success, empty result, failure, validation, retry, and duplicate-submit behavior that matters to the feature.
- Assert observable state after actions; avoid testing GetX internals or implementation-only call counts.
- Test worker behavior only when debounce/reaction timing is part of the feature contract; use controlled time and cancel workers.
- Close controllers and dispose subscriptions/timers created by the test.

## Binding and widget tests

- Register route dependencies in the test scope and remove them after each test. Keep test registrations isolated to avoid global GetX state leaking between cases.
- Render the smallest widget subtree that proves the user-visible behavior. Verify loading, empty, error, and success states as applicable.
- Interact through labels and controls a user can reach. Avoid brittle tests that depend on private controller fields.

## Integration tests

Exercise a small number of valuable cross-layer paths with realistic navigation and service boundaries. Use a controlled backend/test account and clean test data. Never place production credentials in tests.

## Completion check

A GetX change is covered when its important state transitions and user-visible outcomes are asserted, resources are cleaned up, and the test suite has no dependence on leaked registrations from another test.
