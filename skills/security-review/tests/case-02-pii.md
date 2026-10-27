---
case: 2
area: pii
---

## Input

```text
# app.log
2026-10-27 10:02:14 INFO checkout completed name=Jane Doe email=jane.doe@example.com card=4111111111111111 total=59.99
```

## Expected Finding

- Area: PII exposure
- Severity: P1
- Location: `app.log` line 1
- Exposure: customer name, email, and a full payment card number logged in
  plaintext.
- Mitigation: redact/mask PII and card data before writing to logs (e.g. log
  only a masked card suffix, hash or omit email/name).
- Must NOT reproduce the full card number or email in the finding.
