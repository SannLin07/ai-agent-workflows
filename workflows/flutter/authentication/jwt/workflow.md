# JWT-backed API sessions workflow

Use this module when `jwt` is selected in the `authentication` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

A trusted backend issues signed access tokens for the client to attach to requests.

## Avoid when

The client is expected to mint tokens or authorize itself with decoded claims.

## Agent procedure

1. Validate signature, issuer, audience, expiry, and claims on the trusted server for every protected operation.
2. Never trust client-decoded claims for authorization.
3. Keep access tokens in memory where practical; store refresh credentials only in secure storage under backend rotation policy.
4. Attach credentials through selected networking, redact logs, and clear on sign-out/account switch.
5. Coordinate refresh and retry only safe requests; end the session on refresh rejection.

## Completion checks

- [ ] Server authorization does not rely on client token decoding.
- [ ] Expiry, refresh, rejection, and logout paths are covered.
- [ ] Tokens never appear in logs, URLs, or ordinary preferences.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
