# Flutter error-handling rules

Handle failures at the boundary that has enough information to classify them, then pass a safe, actionable result to the next layer. In a Flutter app, this keeps widgets and state objects independent from Dio, plugin, parsing, and platform-specific exception details while still allowing the app to recover and diagnose problems. Follow the selected networking, authentication, storage, and state-management workflows for their specific APIs.

## Classify failures where they occur

- Represent expected failures with the project's established typed result or failure model. Add a new shared abstraction only when multiple features need the same contract.
- Preserve useful diagnostic context, such as operation, feature, cause, and retryability, when translating an error at an API, plugin, storage, or domain boundary.
- Keep successful empty data distinct from invalid input, permission denial, authentication failure, connectivity problems, timeout, cancellation, malformed data, and unexpected defects. These outcomes lead to different UI and recovery choices.
- Propagate unexpected failures to the app's established error-reporting boundary with enough context to investigate. Keep stack traces and internal details out of user-facing messages.
- Never catch and discard an exception. When the current layer cannot recover, propagate a meaningful failure to the layer that can respond.

## Carry safe failures through the Flutter app

- Normalize transport, parsing, authentication, plugin, and domain failures at the boundary that understands them. Keep response and platform exception types out of widgets.
- Let the selected state-management boundary represent the states the feature needs. A widget should render the resulting state and forward user intent; it should not infer domain meaning from a raw exception.
- Preserve cancellation and timeout as distinct outcomes. Follow the [Flutter lifecycle and asynchronous rules](../coding-rules/README.md) so disposed objects and superseded requests cannot publish stale failure or success states.
- Keep failure models proportional to the feature. Share a contract when it improves consistency across real boundaries, and keep feature-specific recovery local when the meaning differs.

## Choose a useful user response

| Failure or result | Flutter app response |
|---|---|
| Valid empty result | Show the feature's empty state as successful data. |
| Field validation | Show the relevant validation message and preserve the entered values. |
| Authentication or permission denial | Follow the selected sign-in, authorization, or permission flow; do not retry the protected operation blindly. |
| Connectivity or timeout | Show a recoverable state and offer retry when the operation is safe to repeat. |
| Intentional cancellation or superseded request | Stop the obsolete work and avoid showing a failure message for a cancellation the user expects. |
| Malformed response or unexpected defect | Show a safe general message, preserve recoverable user input, and send sanitized diagnostic context to the established reporting path. |

User-facing messages should explain what the person can do next and follow the app's localization and tone conventions. Keep implementation details, raw server messages, and stack traces in privacy-safe diagnostics rather than in the UI.

## Make recovery safe

- Retry only operations that are idempotent or have an explicit idempotency strategy. Identify which failure categories are retryable and use a bounded retry policy when automatic retries are appropriate.
- Avoid retrying validation, authorization, or permanent client errors without changing the request or session first.
- Preserve valid form input and relevant screen state after recoverable failures. Clear state only when the product flow requires it, such as after a successful submission or sign-out.
- Ensure loading and failure state transitions cannot trigger duplicate submissions, repeated notifications, or repeated writes during widget rebuilds.
- Keep authentication credentials, personal data, and sensitive payloads out of logs and error reports. Follow the canonical [security rules](../security/README.md) and [logging rules](../logging/README.md).

## Verify important failure paths

- Test success, empty data, boundary values, and important failures at the lowest level that proves the behavior. Follow the selected [unit](../../workflows/flutter/testing/unit/workflow.md), [widget](../../workflows/flutter/testing/widget/workflow.md), or [integration](../../workflows/flutter/testing/integration/workflow.md) testing workflow when selected and relevant.
- Use fakes or controlled services to cover cases such as rejected authentication, malformed responses, timeout, cancellation, stale requests, retry, and recovery without production credentials or accounts.
- Assert the user's visible outcome and the recovery behavior. Check that sensitive details are redacted and that a failure does not cause unintended duplicate side effects.
- Add troubleshooting documentation only for an issue that was observed and investigated; keep hypotheses separate from confirmed causes.
