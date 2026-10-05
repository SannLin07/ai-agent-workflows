# iOS release build workflow

Use this module when `ios` is selected in the `deployment` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The project produces iOS artifacts for internal validation or App Store release.

## Avoid when

App Store listing and testing cohort tasks are needed.

## Agent procedure

1. Check current Flutter/Xcode/iOS/CocoaPods/signing requirements before upgrades.
2. Protect certificates, profiles, API keys, and signing credentials.
3. Review bundle ID, entitlements, privacy prompts, associated domains, and environment config.
4. Record version/build, commit, and signing setup.
5. Install on supported devices and verify permission, links, session, and critical flows.

## Completion checks

- [ ] Signing/entitlements match target.
- [ ] Privacy prompts match real behavior.
- [ ] Release-signed build installs and passes critical-flow checks.

## Official references

- [Official reference 1](https://docs.flutter.dev/deployment/ios)

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
