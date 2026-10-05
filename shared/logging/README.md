# Logging rules

- Log events that help explain meaningful system behavior, failures, and security-relevant actions.
- Include useful context such as operation, feature, and correlation identifier when available; avoid noisy per-frame or repeated logs.
- Redact secrets, authentication headers, personal data, and sensitive payloads before logging.
- Use the project's established logging package and severity convention. Keep debug-only output out of production by default.
- Never rely on a client log as the authoritative record for security or financial decisions.
