---
name: security-review
description: Security and compliance review covering PII exposure, HIPAA technical safeguards, general security/compliance posture, and leaked secrets/credentials. Technology-agnostic. Use when auditing code, configs, logs, or datasets for sensitive-data handling and security compliance risks.
---

# Security Review

## Purpose and Intent

Audit code, configuration, logs, or datasets for sensitive-data and compliance risks across four areas, and report only concrete, evidence-based findings. This skill does not assume a specific language, framework, or regulatory jurisdiction beyond what is explicitly in scope.

## Areas

Run each area below against the given scope. Skip an area only if it is clearly inapplicable (e.g. no health data anywhere in the project) and say so explicitly.

1. **PII exposure** — detect personally identifiable information (names, emails, phone numbers, national IDs, financial data, addresses) in logs, datasets, code, or outputs that shouldn't contain it; flag missing redaction/masking.
2. **HIPAA technical safeguards** — only when the scope involves health data (PHI): check for encryption at rest/in transit, access controls, and audit logging consistent with HIPAA's technical safeguard requirements.
3. **Security compliance** — general security posture: insecure defaults, missing authN/authZ checks, unsafe deserialization, injection risks, insecure transport, dependency/license risk flagged as a security concern.
4. **Secret leak detection** — hardcoded credentials, API keys, tokens, private keys in source code, config files, or git history.

## When to Use

- Auditing a repository, PR, or dataset before a release or compliance check.
- Reviewing logs or data exports for accidental sensitive-data leakage.
- As part of a pre-commit or CI security gate.

## When NOT to Use

- Penetration testing or exploit development — this skill reports risks, it does not attempt to exploit them.
- General code-quality review — use the `code-review` skill for readability/tests/performance/best-practices.

## Output Format

For each area, report only actionable findings with:

- Severity (P0–P3)
- File/line or data location
- What was exposed and why it matters
- Concrete mitigation (e.g. redact, encrypt, move to secret manager, rotate credential)

If an area has no findings, say so in one line instead of omitting it silently. Never print the actual secret/PII value found — reference its location and type only.

## Error Conditions and Edge Cases

- No scope provided: ask what to audit rather than guessing.
- Ambiguous whether data is PHI/PII: flag as uncertain and state what confirmation is needed.

## Security and Data-Handling Considerations

- Analysis is local; no code, secrets, or PII are sent externally.
- Findings must redact the sensitive value itself in the report, showing only type/location.
- Any discovered live/active credential should be flagged as P0 and the user advised to rotate it immediately.

## Validation

See [tests/](tests/) for fixture cases (one per area) with a planted issue and
an expected finding. Use them to sanity-check this skill's output before
trusting it on real code.
