# Responsive and adaptive layouts workflow

Use this module when `adaptive-layout` is selected in `flutter.ui` and the task changes layout across available space, orientation, or input modes. Responsive layout fits content into its space; adaptive layout changes presentation or interaction to suit that space. See [Flutter's overview](https://docs.flutter.dev/ui/adaptive-responsive). It does not select the app's router, architecture, or state-management tool.

## Decisions before implementation

Identify supported windows and targets from project configuration, the content that must remain usable, and the interactions that depend on touch, keyboard, or pointer input. Choose breakpoints from the content and the project's design decisions. Device labels such as phone or tablet alone do not specify the space available to an app window.

## Agent procedure

1. Inspect the current layout and reproduce its limiting conditions. Record the available width and height, text scaling, content length, and input mode that expose the problem. Finish with representative cases, including where a layout changes arrangement.
2. Measure at the boundary that makes the decision. `LayoutBuilder` exposes parent constraints; `MediaQuery.sizeOf(context)` gives the app window size. Use local constraints for a component inside a pane and window size for a window-level decision. Check these APIs against the project's SDK and the [official sizing guidance](https://docs.flutter.dev/ui/adaptive-responsive/general).
3. Choose which elements resize, wrap, scroll, or change arrangement. Define behavior for narrow widths and constrained heights rather than scaling every dimension by a common factor. Respect the project's handling of system insets and the on-screen keyboard so required actions remain reachable.
4. Keep feature state and destination identity stable when switching presentations. For example, a wider list/detail presentation should preserve the selected item and an unfinished edit according to the product contract. Share the relevant state boundary rather than creating independent narrow and wide controllers. Follow the selected router when adapting navigation controls.
5. Exercise each arrangement and resize across its transition while interaction is in progress. Check long and localized text, increased text size, scrolling, and the supported input modes. Use selected [accessibility](../accessibility/workflow.md) or [localization](../localization/workflow.md) guidance for their detailed verification.
6. Use selected widget tests for layout and interaction cases; use device or integration checks for behavior outside the controlled widget tree. Record dimensions and conditions with the results so a passing case can be repeated.

## Completion checks

- [ ] Layout choices use the appropriate available constraints and documented project breakpoints.
- [ ] Content and required actions remain usable in the chosen small and large cases.
- [ ] Resizing preserves selection, edits, and route behavior as intended.
- [ ] Text scaling, long content, keyboard/inset conditions, and applicable input modes were checked.
- [ ] Evidence names the windows and conditions tested; untested targets remain explicit.

## Sources and review

- [Adaptive and responsive design](https://docs.flutter.dev/ui/adaptive-responsive) — scope and terminology. Verified **2026-10-16**.
- [General approach to adaptive apps](https://docs.flutter.dev/ui/adaptive-responsive/general) — local constraints, app window size, and layout branching. Verified **2026-10-16**.
- Review trigger: changes to supported targets, design breakpoints, or Flutter sizing/input APIs after an SDK upgrade.

## Shared rules

Use the canonical [coding](../../../../shared/coding-rules/README.md) and [dependency-management](../../../../shared/dependency-management/README.md) rules. Framework layout tools are the starting point; this module adds no third-party package recommendation.
