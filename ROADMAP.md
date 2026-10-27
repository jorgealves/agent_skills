# Roadmap

This repo favors a small number of broad, technology-agnostic skills over a large catalog. New skills should only be added when an existing one genuinely can't be extended to cover the need.

## Active

- [x] `code-review` skill — readability, tests, performance, security, documentation, best practices
- [x] `security-review` skill — PII, HIPAA, security compliance, secret leaks
- [x] `code-reviewer` subagent — uses `code-review`
- [x] `security-reviewer` subagent — uses `security-review`
- [x] Test fixtures per skill (`skills/*/tests/`) to validate findings before trusting output on real code

## Next

- [ ] Run each skill's fixture cases and confirm findings match before relying on them on real PRs.
- [ ] Try both subagents on a real PR/branch and tune the SKILL.md instructions based on actual output quality.
- [ ] Decide if a third skill is genuinely needed (e.g. architecture/design review) before adding one.
