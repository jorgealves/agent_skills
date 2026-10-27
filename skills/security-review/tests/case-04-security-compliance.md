---
case: 4
area: security_compliance
---

## Input

```python
import pickle

def load_session(raw_bytes):
    return pickle.loads(raw_bytes)  # raw_bytes comes from an HTTP cookie
```

## Expected Finding

- Area: Security compliance
- Severity: P0
- Location: `load_session`
- Exposure: unsafe deserialization of untrusted, attacker-controlled input
  (`pickle.loads` on a value sourced from a cookie) can lead to arbitrary code
  execution.
- Mitigation: replace `pickle` with a safe serialization format (e.g. signed
  JSON) for any data crossing a trust boundary.
- Must NOT include a working exploit/payload — mitigation only.
