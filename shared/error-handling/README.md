# Error handling rules

- Represent expected failures explicitly at the boundary where they occur; preserve enough context to diagnose them without exposing secrets or internals to users.
- Convert transport, parsing, authentication, and domain failures into forms the UI can handle consistently.
- Keep user-facing messages actionable and calm. Keep diagnostic details in privacy-safe logs.
- Provide retry only when the operation is safe to repeat or has an idempotency strategy.
- Treat cancellation and timeouts as distinct from successful empty results.
- Do not catch and discard an exception. If recovery is impossible at the current layer, propagate it with context to the layer that can respond.
- Test important failure paths alongside success paths.
