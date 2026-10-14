# Flutter logging rules

Use logs to explain meaningful app behavior and help diagnose failures in development and production. Keep diagnostic events separate from user-facing error messages, and use the logging or error-reporting tools already established by the Flutter project. A log is evidence for investigation; it is not the source of truth for security, authorization, or financial decisions.

## Log at useful boundaries

- Record meaningful events at the boundary that owns the operation, such as an app lifecycle transition, repository request, authentication change, or recoverable storage failure.
- Include enough safe context to answer what happened and where: feature or subsystem, operation, outcome, failure code or category, and a non-sensitive correlation identifier when available.
- Emit one useful event for an operation. Coordinate logging between widgets, state objects, repositories, interceptors, and global handlers so the same failure is not repeated at every layer.
- Keep widget `build` methods and frequently repeated render or state-update paths free of routine logging. They can run often and produce noisy records that hide meaningful events.
- Use the project's established severity levels consistently. Keep development-only detail filtered from production according to the app's release configuration.

A useful structured failure event might identify `feature: profile`, `operation: load`, `outcome: failed`, and a safe `failure_code: timeout`, with a correlation identifier if one exists. Keep field names and severity semantics consistent with the project's logging setup.

## Protect user and credential data

- Log only fields that support a concrete diagnostic purpose. Prefer an allowlist of safe fields over logging an entire request, response, model, or exception object.
- Exclude passwords, access and refresh tokens, authorization headers, signing keys, private identifiers, personal data, and sensitive request or response bodies. Treat route parameters, user input, and plugin payloads as potentially sensitive.
- Sanitize exception messages and stack details before sending them to an external crash or error-reporting service. Confirm that the service's collection, access, and retention settings match the product's privacy requirements.
- Keep logs out of decisions that grant access or authorize a sensitive operation. Enforce those decisions at the trusted server boundary.
- Follow the canonical [security and privacy rules](../security/README.md) and [error-handling rules](../error-handling/README.md) when recording failures or security-relevant events.

## Keep logging useful and efficient

- Record state transitions or operation outcomes that a maintainer can act on. Avoid per-frame output, repeated polling messages, and routine success logs that add no diagnostic value.
- Keep payload formatting bounded. Avoid serializing large objects or computing expensive diagnostic strings when the active log level will discard the event.
- Use a correlation identifier to connect related client-side events when the project provides one. Keep it non-sensitive and avoid using credentials or raw personal identifiers for correlation.
- Separate operational diagnostics from product analytics. Apply the app's consent and retention rules to analytics, and keep sensitive values out of both systems.
- Never treat a client-side log as an authoritative audit record for security or financial actions.

## Verify logging behavior

- Check that production configuration filters development-only detail and that the selected logging package follows the project's severity convention.
- When a task changes sensitive logging or redaction, verify that representative credentials, personal data, and payload fields are removed before the log or report is emitted.
- When logging is part of the task's acceptance criteria, use a controlled sink or test logger to assert the event, useful context, and redaction behavior without coupling unrelated tests to log wording.
- Review diagnostic output for duplication across layers, unbounded payloads, and details that should remain private before completing the task.
