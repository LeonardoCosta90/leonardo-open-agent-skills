# Leonardo's Open Agent Skills

Reusable skills for AI coding agents, maintained as portable `SKILL.md` files. The skills are intended to work across projects; when a skill is relevant, use it together with applicable Superpowers skills rather than treating either as a replacement for the other.

## Skills

| Skill | Purpose |
|---|---|
| [`conducting-functional-qa`](skills/conducting-functional-qa/SKILL.md) | Guide manual functional QA one step at a time and record only evidence-backed results. |
| [`documenting-evidence-based-issues`](skills/documenting-evidence-based-issues/SKILL.md) | Write actionable bug reports that distinguish observed evidence, code findings, hypotheses, and limits. |

## Install for OpenCode

OpenCode discovers personal skills in `~/.agents/skills/`. Clone this repository and copy the skill directories there:

```sh
git clone https://github.com/LeonardoCosta90/leonardo-open-agent-skills.git
cp -R leonardo-open-agent-skills/skills/* ~/.agents/skills/
```

Alternatively, copy a single skill directory into a project's `.opencode/skills/` directory. Each skill must remain in its own directory and contain a `SKILL.md` file.

After installation, reload OpenCode or start a new session if a newly installed skill is not yet listed.

## Repository layout

```text
skills/
  <skill-name>/
    SKILL.md
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for skill format, quality expectations, and pull request guidance. Keep skills focused, portable, and explicit about when they apply. Do not include secrets, personal data, or project-specific private information.
