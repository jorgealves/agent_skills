---
case: 1
area: secret_leak
---

## Input

```python
# config/settings.py
AWS_ACCESS_KEY_ID = "AKIAIOSFODNN7EXAMPLE"
AWS_SECRET_ACCESS_KEY = "wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY"
```

## Expected Finding

- Area: Secret leak detection
- Severity: P0
- Location: `config/settings.py`
- Exposure: hardcoded AWS access key and secret key committed to source.
- Mitigation: remove from source, rotate both credentials immediately, move
  to a secret manager or environment variable injected at runtime.
- Must NOT reproduce the full key value in the finding — reference type and
  location only.
