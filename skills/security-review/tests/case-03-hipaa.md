---
case: 3
area: hipaa
---

## Input

```python
# patient_records.py — stores PHI
def save_patient_record(record):
    with open(f"/data/patients/{record['id']}.json", "w") as f:
        json.dump(record, f)  # contains diagnosis, SSN, treatment notes

def get_patient_record(patient_id, requester):
    with open(f"/data/patients/{patient_id}.json") as f:
        return json.load(f)  # no check that `requester` is authorized
```

## Expected Finding

- Area: HIPAA technical safeguards
- Severity: P0
- Location: `patient_records.py`
- Exposure: PHI (diagnosis, SSN, treatment notes) written to disk unencrypted,
  and `get_patient_record` has no access control check on `requester`, and no
  audit log of who accessed the record.
- Mitigation: encrypt PHI at rest, enforce an authorization check before
  returning a record, and add audit logging of access events.
