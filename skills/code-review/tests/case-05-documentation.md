---
case: 5
perspective: documentation
---

## Input

```python
def fetch_user(user_id, cache=True):
    """Fetch a user by id. Always hits the database directly."""
    if cache and user_id in _CACHE:
        return _CACHE[user_id]
    user = db.get_user(user_id)
    _CACHE[user_id] = user
    return user
```

## Expected Finding

- Perspective: Documentation
- Severity: P2
- Location: `fetch_user` docstring
- Issue: docstring says "Always hits the database directly" but the
  implementation checks a cache first — documentation contradicts behavior.
- Should NOT flag: the caching logic itself as a bug.
