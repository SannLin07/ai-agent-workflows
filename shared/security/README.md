# Security and privacy rules

- Never put credentials, signing keys, private tokens, or production secrets in source code, committed configuration, logs, screenshots, or troubleshooting records.
- Load secrets from the project's approved secret store or environment-specific secure configuration. Keep only clearly fake placeholders in examples.
- Validate and authorize sensitive operations on the trusted server boundary; client-side checks improve UX but do not grant access.
- Request only the personal data and permissions the feature needs. Explain sensitive collection and retention in the product's established way.
- Use TLS for network traffic and secure platform storage for credentials or refresh tokens. Do not treat ordinary preferences or local databases as secret stores.
- Redact tokens, personal data, and sensitive request bodies from logs and error reports.
- Review dependency provenance and platform permissions when introducing a package or integration.
- If a task would expose a credential or weaken an access boundary, stop that implementation path, explain the risk, and propose a safe alternative.
