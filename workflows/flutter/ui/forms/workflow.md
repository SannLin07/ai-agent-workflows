# Forms and validation workflow

Use this module when `forms` is selected in `flutter.ui` and the task changes data entry, field validation, or submission. Keep the project's selected state-management and data boundaries. A static text display does not need this module, and a form change alone does not justify a form package or a new state tool.

## Decisions before implementation

Identify the editable values, validation rules, submit operation, and state lifetime. Decide whether a draft survives navigation or is discarded, when validation appears, and which server failures can be attached to a field. Distinguish display text from the typed value sent to storage or an API. Client validation improves feedback; authorization and trusted validation remain at the boundary defined by the [security rules](../../../../shared/security/README.md).

## Agent procedure

1. Inspect the existing form and selected state-management conventions. Give field values, validation results, and submission status explicit owners; avoid two independently writable copies of the same draft. Finish with an ownership and submission plan.
2. For framework-managed validation, group relevant fields in a `Form` and use `TextFormField` validators. A validator returns an error string for invalid input and `null` for valid input; `FormState.validate()` runs validation for the fields. Keep a form key stable across rebuilds. These APIs are documented in the [official form recipe](https://docs.flutter.dev/cookbook/forms/validation).
3. Implement required, boundary, and cross-field rules from the product contract. Keep synchronous checks deterministic. Put remote checks and save operations in the selected state/data boundary and define how superseded responses are ignored. Decide whether editing a value clears its previous server error.
4. Define the transition from editing to submitting and then success or failure. Follow the selected state-management module for async ownership and the [coding rules](../../../../shared/coding-rules/README.md) for lifecycle and duplicate actions. Preserve recoverable input and distinguish a rejected field from a failed operation using the [error-handling rules](../../../../shared/error-handling/README.md).
5. Check the full interaction: field labels, input type, focus order, next/submit actions, keyboard visibility, and access to validation feedback. Use selected [accessibility](../accessibility/workflow.md), [adaptive layout](../adaptive-layout/workflow.md), or [localization](../localization/workflow.md) guidance when those concerns are part of the task.
6. Verify through the selected testing workflows. Cover valid submission, invalid input, meaningful boundaries, a failed save followed by retry, and leaving the screen during pending work when applicable. Finish with evidence for the changed behavior and any unverified service or device boundary.

## Completion checks

- [ ] Each input and submit state has one owner and a defined lifetime.
- [ ] Invalid input prevents the relevant operation; valid input reaches the intended data boundary.
- [ ] Errors reach the correct field or form, and recovery preserves the intended draft.
- [ ] Keyboard/focus behavior and submission feedback work for the supported targets.
- [ ] Relevant validation and interaction checks ran, with remaining gaps reported.

## Sources and review

- [Build a form with validation](https://docs.flutter.dev/cookbook/forms/validation) — framework form, key, validator, and validation behavior. Verified **2026-10-16**.
- Review trigger: Flutter SDK upgrades affecting form APIs or a change to the project's form/state-management conventions.

## Shared rules

Use the canonical [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error-handling](../../../../shared/error-handling/README.md), and [dependency-management](../../../../shared/dependency-management/README.md) rules. This module adds no third-party package recommendation.
