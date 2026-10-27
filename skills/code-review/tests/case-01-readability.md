---
case: 1
perspective: readability
---

## Input

```python
def p(d, f, x, y, z):
    if d:
        if f:
            if x > 0:
                if y > 0:
                    if z > 0:
                        return x + y + z
                    else:
                        return 0
                else:
                    return 0
            else:
                return 0
        else:
            return 0
    else:
        return 0
```

## Expected Finding

- Perspective: Readability
- Severity: P2
- Location: function `p`
- Issue: non-descriptive name (`p`, `d`, `f`, `x`, `y`, `z`) and five levels of
  nested conditionals that can be flattened/guard-claused.
- Should NOT flag: performance, security, or test-coverage issues for this
  snippet.
