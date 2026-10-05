# Google Play Store release workflow

Use this module when `play-store` is selected in the `deployment` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

Android builds are distributed through Google Play testing or production tracks.

## Avoid when

Only Android artifact compilation is needed.

## Agent procedure

1. Verify current target API, account, listing, privacy/data safety, rating, and testing requirements.
2. Upload the signed AAB from the intended environment and confirm package/version metadata.
3. Choose internal/closed/open cohort and rollout size deliberately.
4. Review pre-launch, crash, and policy reports before promotion.
5. Define monitoring, halt, and recovery criteria; record track, artifact, and decision.

## Completion checks

- [ ] Artifact/listing/privacy declarations match the app.
- [ ] Track audience and rollout are intentional.
- [ ] Post-release monitoring has an owner.

## Official references

- [Official reference 1](https://support.google.com/googleplay/android-developer/answer/9845334?hl=en)

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
