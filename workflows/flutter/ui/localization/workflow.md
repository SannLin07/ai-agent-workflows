# Localization and locale behavior workflow

Use this module when `localization` is selected in `flutter.ui` and a task changes translated resources, supported locales, locale selection, or locale-sensitive presentation. Keep an established localization system when it meets the requirement. Adding one translated label does not justify migrating the entire app's resource system.

## Decisions before implementation

Confirm the supported language/script/region combinations, translation owner, fallback behavior, and whether users can override the device locale. Distinguish language from business choices such as currency and time zone. Decide how language changes affect an open screen or draft. Translation quality requires review by someone qualified for the language; successful generation alone is not that review.

## Agent procedure

1. Inspect current resources, root-app locale/delegate configuration, package constraints, and generated-code commands. For a new framework-based setup, consult [package guidance](packages.md). Finish with the actual resource source, generated output location, and locale policy.
2. For Flutter's `gen-l10n` setup, enable generation in the app's `pubspec.yaml`, configure `l10n.yaml`, and keep Application Resource Bundle (ARB) files as the editable input. Run the project's generation command; `flutter gen-l10n` is the framework command. Import the generated source from its configured app location, following the [generation migration guidance](https://docs.flutter.dev/release/breaking-changes/flutter-generate-i10n-source) for the adopted SDK.
3. Add whole messages with translator context and typed placeholders. Use the existing system's plural/select facilities where grammar requires alternatives. Keep localized display strings separate from stored values and API identifiers. Follow the [official internationalization guide](https://docs.flutter.dev/ui/internationalization) for supported resource syntax and app integration.
4. Connect the intended supported locales and delegates to the existing app root without changing its router or state tool. Verify initial locale selection, unsupported-locale fallback, and any user override. If the override persists, use the selected storage boundary and verify the intended behavior after restarting.
5. Check locale-sensitive dates and numbers against product examples. Currency identity and time-zone conversion remain explicit domain decisions, not assumptions inferred from a language. Inspect long translations, glyph rendering, and right-to-left content when supported; use direction-aware layout conventions and selected [adaptive layout](../adaptive-layout/workflow.md) guidance where applicable.
6. Verify generation, analysis, and the changed messages and interactions through selected testing workflows. Include representative plural values, locale changes, and fallback cases relevant to the task. Record which translations received language review and which platform localization checks remain unverified.

## Completion checks

- [ ] Resource inputs, generated output, app delegates, and supported locales agree.
- [ ] Changed text, placeholders, and grammatical alternatives have meaningful verification.
- [ ] Locale selection, fallback, and any persisted override follow the product decision.
- [ ] Relevant formatting, long-text, glyph, and direction cases were checked.
- [ ] Generation and runtime checks are recorded separately from translation review.

## Sources and review

- [Internationalizing Flutter apps](https://docs.flutter.dev/ui/internationalization) — resources, generation, locale integration, and formatting. Verified **2026-10-16**.
- [Generated localization source migration](https://docs.flutter.dev/release/breaking-changes/flutter-generate-i10n-source) — app-source imports and generation configuration. Verified **2026-10-16**; apply migration advice to the consuming SDK version.
- Review trigger: Flutter SDK/generator upgrades, localization dependency changes, or additions to supported locales. Native app metadata and store language declarations require the selected platform release guidance and current vendor checks.

## Shared rules

Use the canonical [coding](../../../../shared/coding-rules/README.md), [error-handling](../../../../shared/error-handling/README.md), [documentation](../../../../shared/documentation/README.md), and [dependency-management](../../../../shared/dependency-management/README.md) rules. See [packages.md](packages.md) before dependency changes.
