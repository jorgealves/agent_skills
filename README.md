# agent_skills

My personal library of AI agent skills and subagent profiles, kept intentionally small and technology-agnostic.

## Structure

```text
skills/              # few, broad, technology-agnostic skills
  code-review/
    SKILL.md
    skill.yaml
    tests/            # fixture cases to validate the skill's output
  security-review/
    SKILL.md
    skill.yaml
    tests/
.codex/
  config.toml        # registers available subagents
  agents/             # subagent profiles, each backed by one or more skills
    code-reviewer.toml
    security-reviewer.toml
```

## Philosophy

- **Few skills, broad scope**: instead of one skill per language/framework, each skill covers a problem area (e.g. code review) across multiple perspectives.
- **Technology-agnostic**: code-related skills must work regardless of language or stack.
- **Subagents compose skills**: a subagent is a thin profile that points to the skill(s) it uses — it does not duplicate review logic inline.

## Current skills

| Skill | Purpose |
| --- | --- |
| [code-review](skills/code-review/SKILL.md) | Readability, tests, performance, security, documentation, best practices |
| [security-review](skills/security-review/SKILL.md) | PII exposure, HIPAA safeguards, security compliance, secret leaks |

## Current subagents

| Subagent | Uses skill |
| --- | --- |
| `code-reviewer` | `code-review` |
| `security-reviewer` | `security-review` |

See [AGENTS.md](AGENTS.md) for the rules governing how skills and subagents are created in this repo, and [ROADMAP.md](ROADMAP.md) for what's next.
