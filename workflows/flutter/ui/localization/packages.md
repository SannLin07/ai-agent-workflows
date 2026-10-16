# Localization package guidance

Verified against the sources below on **2026-10-16**. Keep the project's established localization system unless a concrete requirement calls for a change. These recommendations describe Flutter's generated-localization path, not mandatory dependencies for every selected localization task.

```yaml
packages:
  - name: flutter_localizations
    purpose: Framework widget translations and locale delegates
    version_constraint: "sdk: flutter"
    official_source: https://docs.flutter.dev/ui/internationalization
    notes: >-
      An SDK dependency, declared as flutter_localizations: {sdk: flutter},
      rather than an independently versioned pub constraint.
      Use the consuming project's adopted Flutter SDK.
    verified_on: 2026-10-16
  - name: intl
    purpose: Locale-sensitive number/date formatting and generated message support
    version_constraint: ^0.20.3
    official_source: https://pub.dev/packages/intl
    notes: >-
      A dated candidate constraint, also present in the checked Flutter stable
      localization dependency declaration. Inspect the consuming SDK's
      flutter_localizations/pubspec.yaml before adoption; an older SDK may
      require a different constraint. Do not use a dependency override to
      bypass that requirement. The project resolver and lockfile decide
      the installed version.
    verified_on: 2026-10-16
```

## Compatibility and review

The checked [Flutter stable localization declaration](https://raw.githubusercontent.com/flutter/flutter/stable/packages/flutter_localizations/pubspec.yaml) uses `intl: ^0.20.3`. The branch is mutable: inspect the local adopted SDK rather than treating that declaration as a constraint for every Flutter release. The [official setup guide](https://docs.flutter.dev/ui/internationalization) explains the SDK dependency and generation setup. Sources checked **2026-10-16**.

Before adding packages, check the project's Flutter/Dart constraints, SDK dependency requirements, target platforms, license, release activity, and migration notes under the [dependency-management rules](../../../../shared/dependency-management/README.md). Review these recommendations whenever the SDK or localization dependencies change. No consumer dependency resolution or runtime validation has been performed for this draft module.
