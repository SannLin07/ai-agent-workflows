# Accessibility verification workflow

Use this module when `accessibility` is selected in `flutter.ui` and the task adds or changes interactive UI, semantic information, or an accessibility defect. It provides a focused implementation and verification procedure. The baseline accessibility obligations in the [coding rules](../../../../shared/coding-rules/README.md) apply even when this optional module is not selected.

## Decisions before implementation

Identify the changed user journey and supported platforms/input modes. Record applicable project accessibility criteria and which assistive technologies can be tested. Define what a person must be able to discover, understand, activate, and recover from in that journey. Keep an automated check, a device observation, and a formal conformance assessment distinct; each supports a different claim.

## Agent procedure

1. Trace the journey through its controls, content, loading states, and errors. Inspect the existing semantic representation as well as the visual layout. Finish with the actions and information that need verification.
2. Prefer the project's established framework controls where they provide the required behavior. For custom UI, inspect labels, roles, values, states, and available actions; correct the semantic representation where it fails to describe the interaction. Avoid duplicate announcements caused by labeling both a composite control and its redundant children.
3. Check reading and focus order through the changed journey. Include opening and dismissing transient UI, returning to the originating control, and exposing validation or operation results. Where keyboard input is supported, exercise reaching and activating every required control without relying on a pointer.
4. Check the journey under increased text size and relevant contrast settings. Verify that meaning and status remain available through the baseline [coding rules](../../../../shared/coding-rules/README.md). Use selected [adaptive layout](../adaptive-layout/workflow.md) guidance if the correction changes layout behavior.
5. Add meaningful semantic/interaction checks through the selected testing workflow. Flutter's Accessibility Guideline API checks target size, target labels, and text contrast; choose checks applicable to the supported platform. Follow the [official testing guide](https://docs.flutter.dev/ui/accessibility/accessibility-testing), rather than copying fixed thresholds into this module.
6. Exercise the changed journey with the relevant platform screen reader or other required assistive technology. Record platform, tool, build, and observed behavior. If the environment is unavailable, report the specific manual check as not run; passing widget checks alone do not establish the real assistive-technology experience.

## Completion checks

- [ ] Required actions and information are represented accurately without redundant announcements.
- [ ] Reading/focus order and return paths work for the changed journey.
- [ ] Supported keyboard interaction and increased text size were checked.
- [ ] Automated and manual results are reported separately, with platform coverage and gaps.
- [ ] The completion claim matches the checks performed and the project's stated criteria.

## Sources and review

- [Flutter accessibility](https://docs.flutter.dev/ui/accessibility) — framework accessibility scope and release considerations. Verified **2026-10-16**.
- [Accessibility testing](https://docs.flutter.dev/ui/accessibility/accessibility-testing) — guideline API and platform inspection approaches. Verified **2026-10-16**.
- Review trigger: Flutter SDK or supported OS/browser upgrades affecting semantics, new interaction patterns, or changes to project accessibility criteria.

## Shared rules

Use the canonical [coding](../../../../shared/coding-rules/README.md), [error-handling](../../../../shared/error-handling/README.md), and [dependency-management](../../../../shared/dependency-management/README.md) rules. This module adds no third-party package recommendation.
