# Security and Confidentiality

This is a public educational/portfolio repository. Use **synthetic or sanitized lab data only**.

## Never commit

- passwords, tokens, API keys, private keys, certificates, or real secrets
- `.env` files containing credentials
- employer/customer configurations or proprietary documentation
- internal hostnames, IP plans, network diagrams, asset identifiers, or screenshots from protected environments
- personal or customer data
- real vulnerability details that could expose an organization

## Evidence rules

- Prefer reproducible lab output over production screenshots.
- Redact machine-specific or personal information when it adds no technical value.
- Clearly label results as **measured**, **derived**, **simulated**, or **modeled/reference**.
- Use fake credentials and synthetic incidents for security exercises.

## If a secret is committed

Treat it as compromised: revoke/rotate it immediately, remove it from the repository, and rewrite history when necessary. Deleting only the latest copy is not sufficient if the secret remains in Git history.

For non-sensitive repository problems, use a normal GitHub issue. Do **not** publish sensitive security information or credentials in an issue.
