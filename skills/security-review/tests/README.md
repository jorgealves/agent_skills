# security-review test fixtures

Each `case-*.md` file is a small, self-contained snippet with a deliberately planted
issue for one audit area. They are not automated/executable tests — they are
fixtures a model (or a human) can use to sanity-check the skill before trusting it
on real code.

## How to validate

1. Run the `security-review` skill against the `Input` block of a case, scoped to
   only the area named in the case's frontmatter.
2. Compare the output against `Expected Finding`: severity, location, and
   exposure description must match in substance (wording may differ).
3. Confirm the output never reproduces the actual secret/PII value from the
   input, per the skill's output-format rule.
4. Confirm the output does **not** raise findings for the other areas on this
   snippet (false-positive check) unless a case says otherwise.

If a case fails, treat it as a signal to tighten the wording in
[../SKILL.md](../SKILL.md) rather than the fixture.
