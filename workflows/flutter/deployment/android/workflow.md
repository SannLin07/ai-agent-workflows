# Android release build workflow

Use this module when `android` is selected in the `deployment` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The project produces Android artifacts for validation or release.

## Avoid when

Store listing and tester-track work alone; those belong to Play Store workflow.

## Agent procedure

1. Use supported Flutter/Gradle/AGP/Kotlin versions and check official compatibility guidance before upgrades.
2. Keep signing keys/passwords outside source in protected build configuration.
3. Review environment IDs, permissions, exported components, links, target SDK, and release shrinking.
4. Record artifact, version/build, commit, and validation evidence.
5. Install/update the signed candidate on supported Android versions.

## Completion checks

- [ ] Release uses intended non-debug key with protected secrets.
- [ ] Version, app ID, permissions, and production endpoints are correct.
- [ ] Install/update and critical flows work.

## Official references

- [Official reference 1](https://docs.flutter.dev/deployment/android)

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
