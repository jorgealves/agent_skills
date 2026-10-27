---
case: 6
perspective: best_practices
---

## Input

```python
def load_config(path):
    try:
        with open(path) as f:
            return json.load(f)
    except Exception:
        pass
```

## Expected Finding

- Perspective: Best practices
- Severity: P1
- Location: `load_config`
- Issue: bare `except Exception: pass` silently swallows all errors
  (missing file, invalid JSON, permissions) and returns `None` with no
  logging or signal to the caller — inconsistent with proper error handling.
- Should NOT flag: readability of the function name/structure.
