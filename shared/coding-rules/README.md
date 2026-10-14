# Flutter coding rules

These rules apply to Flutter and Dart changes across the library. They describe the shared engineering approach; the project's selected architecture, state-management, routing, clean codes, and feature workflows provide the specific patterns for each app. Preserve deliberate project decisions and use existing code as evidence of local conventions before introducing a new pattern.

## Understand the project before changing code

- Read the task's acceptance criteria, project instructions, `project.yaml` when present, and the selected workflows that affect the change. This identifies the app's supported platforms, architectural boundaries, and verification expectations.
- Inspect nearby implementation and tests before editing. Trace the affected behavior from the widget through state and data boundaries to any API, plugin, or platform service so the change preserves ownership and failure behavior across the full path.
- Check the consuming project's Flutter and Dart constraints, package versions, and established commands before relying on an API or adding a dependency. Treat this library's package constraints as dated recommendations, not as the project's resolved versions.
- Identify assumptions that could change user-visible behavior, data ownership, security, or compatibility. Resolve material uncertainty before choosing an implementation; state smaller assumptions in the final report.

## Choose boundaries that match the selected architecture

- Keep each change focused on the requested behavior and the architecture already selected by the project. A refactor belongs in the task only when it is needed to make the requested behavior safe, testable, or maintainable.
- Keep widgets responsible for rendering and forwarding user intent. Place feature decisions and presentation state in the selected state-management boundary, and keep transport, persistence, and platform calls behind the project's established data or service boundary.
- Give each piece of state a clear owner and lifetime. Keep transient screen state near its screen or feature; share state only when multiple parts of the product need the same source of truth.
- Follow the selected state-management and routing workflows. Do not introduce a second primary state tool or router for convenience; a deliberate migration or bounded integration needs an explicit project decision.
- Add an abstraction when it clarifies ownership, isolates a dependency that changes independently, or makes an important behavior testable. Keep simple code direct when another layer would only forward a call.

## Make Flutter lifecycle and asynchronous behavior explicit

- Keep `build` methods focused on describing UI. Start requests, subscriptions, timers, and other side effects from an explicit action or lifecycle boundary, not as a consequence of rebuilding a widget.
- Match controllers, focus nodes, animation controllers, stream subscriptions, timers, and other owned resources to the lifecycle of the object that creates them. Dispose or cancel owned resources at that boundary, and avoid disposing an object twice when a framework or dependency container owns it.
- After an asynchronous gap, confirm that a widget or context is still valid before using it. Prevent superseded requests from applying stale results, and define cancellation or timeout behavior when it affects the user flow.
- Represent asynchronous outcomes explicitly when the UI needs to distinguish loading, data, empty results, and failure. Preserve valid input and recoverable state after an error when the user can retry or correct the request.
- Put error translation at the boundary that understands the failure. Keep user messages actionable and diagnostic details safe; follow the canonical [error-handling rules](../error-handling/README.md).

## Protect user experience and production quality

- Preserve accessibility semantics, useful focus and interaction behavior, and responsive layouts across the supported targets. Do not rely on color or visual position alone to communicate meaning.
- Provide meaningful loading, empty, success, and failure states where a user-facing flow needs them. Match retry behavior to the operation's safety and avoid losing user input on recoverable failures.
- Keep rendering work proportional to visible content. Use lazy construction for large collections and keep reactive rebuilds near the state they display. Profile real performance problems before adding caching, isolates, or complex optimization layers.
- Validate and authorize sensitive operations at the trusted boundary. Keep credentials and private user data out of source, logs, routes, and ordinary preferences; follow the canonical [security and privacy rules](../security/README.md).
- Log behavior that helps diagnose meaningful events without producing noisy output or exposing secrets. Follow the canonical [logging rules](../logging/README.md).
- Add or upgrade dependencies only to meet a concrete requirement. Check compatibility, platform support, maintenance, license, and migration guidance; follow the canonical [dependency-management rules](../dependency-management/README.md).

## Verify behavior and report evidence

- Choose verification that proves the changed behavior at the lowest useful level: unit tests for focused decisions, widget tests for rendering and interaction, and integration tests for critical paths across real app boundaries.
- Cover important success, empty, boundary, and failure outcomes. Use fakes or controlled services for most tests; do not let routine tests depend on production accounts or credentials.
- Run the consuming project's documented formatter, analyzer, and relevant test commands when they are available and appropriate to the task. Report exactly what ran, what passed, and what remains unverified; do not claim checks that were not run.
- Review the final diff for unrelated edits, accidental changes to generated code, new dependencies, accessibility regressions, and documentation needed for changed behavior.
- Update setup, user-facing behavior, project decisions, or verification guidance when the implementation changes them. Follow the canonical [documentation rules](../documentation/README.md).
