# Android closed testing workflow

Use this module when `closed-testing` is selected in the `testing` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

A release candidate needs validation by an invited limited group through Google Play.

## Avoid when

Closed distribution is confused with automated coverage or public access.

## Agent procedure

1. Use an internal or closed track suitable for the cohort and current console rules.
2. Record build, cohort, feedback window, crash signals, and promotion criteria.
3. Give testers focused tasks and a safe feedback path.
4. Check install/update, auth, permissions, purchase, and recovery as relevant.
5. Recheck current Play Console requirements for each release.

## Completion checks

- [ ] Only intended testers access the build.
- [ ] Feedback and crash signals are reviewed before promotion.
- [ ] Distribution supplements automated tests.

## Official references

- [Official reference 1](https://support.google.com/googleplay/android-developer/answer/9845334?hl=en)

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
