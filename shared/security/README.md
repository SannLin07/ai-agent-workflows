# Flutter security and privacy rules

Treat every Flutter client as a public, user-controlled environment. A user can inspect an installed app, change its local state, replay requests, and supply values through links or platform callbacks. Client-side checks improve the user experience; trusted backend services and platform security boundaries must enforce access to protected resources. Apply the selected authentication, storage, networking, and deployment workflows for their implementation details.

## Protect secrets and configuration

- Keep passwords, private API credentials, signing keys, service-account files, and privileged backend keys out of Dart code, committed configuration, client bundles, logs, screenshots, and troubleshooting records.
- Assume any value shipped in a Flutter app can be extracted. Treat a value as public only when its provider explicitly documents it as safe for client applications, and keep authorization enforced by trusted services.
- Load development, staging, and production configuration through the project's approved configuration process. Keep environments separate and confirm the target before building or releasing.
- Use clearly fake placeholders in examples. Protect signing certificates, profiles, passwords, and release credentials through the project's approved secret store and build process.

## Enforce identity and authorization

- Authenticate users through the selected identity or session workflow. Enforce authorization for every protected operation at the trusted server or service boundary; hiding a button or guarding a Flutter route is only a user-experience measure.
- Validate ownership, role, and requested action for sensitive resources on the trusted boundary. Never authorize from client-controlled state or from claims decoded only by the app.
- Request the least permission and data scope that supports the feature. Handle denial, expiry, reauthentication, sign-out, account switching, and deletion according to the selected authentication workflow.
- Treat deep links, route parameters, OAuth callbacks, and values received from platform plugins as untrusted input. Validate them before they affect navigation, account state, or a privileged request.

## Minimize and protect user data

- Collect only the personal data needed for the feature. Explain sensitive collection through the product's established flow, and define retention, deletion, and export behavior where relevant.
- Use TLS for network traffic. Do not place credentials or sensitive values in URLs, navigation arguments, analytics events, crash reports, or ordinary logs.
- Keep short-lived credentials in memory when practical. Store credentials that must persist only through the project's platform-backed secure-storage boundary; ordinary preferences and local databases are not secret stores.
- Separate credentials from cached or user-authored data. Review offline caches, backups, account switching, sign-out, and account deletion so sensitive data does not remain available to the wrong user.
- Redact tokens, personal data, and sensitive request or response content before logging or error reporting. Follow the canonical [logging rules](../logging/README.md) and [error-handling rules](../error-handling/README.md).

## Review platform and dependency exposure

- Request runtime permissions only when a feature needs them. Explain the purpose at the point of use, handle denial, and review the actual Android and iOS declarations for the selected targets.
- Review a package's provenance, supported platforms, permissions, maintenance, and license before adding or upgrading it. Follow the canonical [dependency-management rules](../dependency-management/README.md).
- Keep signing material and production environment configuration out of source and ordinary build artifacts. Verify the selected deployment workflow's signing, bundle, and environment checks before release.

## Verify security behavior

- Test both allowed and denied access for protected operations at the trusted boundary. A passing client-side route or widget test does not prove server authorization.
- Test relevant session paths, including expiry, refresh rejection, sign-out, and account switching. Confirm that credentials are cleared or replaced at the intended boundary.
- Use test environments, fake accounts, and synthetic data. Keep production credentials and personal data out of routine tests and diagnostics.
- Review route inputs, permission requests, logs, error reports, local persistence, and build configuration for sensitive values as part of the task's verification.
- If a requested change would expose a credential or weaken an access boundary, stop that implementation path, explain the specific risk, and continue with a safe alternative.
