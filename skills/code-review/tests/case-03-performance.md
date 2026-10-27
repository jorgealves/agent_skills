---
case: 3
perspective: performance
---

## Input

```python
def get_order_totals(order_ids, db):
    totals = []
    for order_id in order_ids:
        order = db.query(f"SELECT * FROM orders WHERE id = {order_id}")
        totals.append(order.total)
    return totals
```

## Expected Finding

- Perspective: Performance
- Severity: P1
- Location: `get_order_totals`
- Issue: N+1 query pattern — one DB round-trip per `order_id` instead of a
  single batched query.
- Should ALSO flag (security): string-interpolated SQL is an injection risk —
  acceptable as a cross-perspective note, but the primary expected perspective
  is performance.
