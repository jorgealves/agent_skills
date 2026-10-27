---
case: 2
perspective: tests
---

## Input

```python
# changed file: pricing.py
def apply_discount(price, percent):
    if percent < 0 or percent > 100:
        raise ValueError("percent must be between 0 and 100")
    return price * (1 - percent / 100)

# changed file: test_pricing.py
def test_apply_discount():
    assert apply_discount(100, 10) == 90
```

## Expected Finding

- Perspective: Tests
- Severity: P2
- Location: `test_pricing.py`
- Issue: no test covers the boundary/invalid cases (`percent < 0`,
  `percent > 100`, `percent == 0`, `percent == 100`) despite the function
  explicitly validating them.
- Should NOT flag: readability of `apply_discount` itself.
