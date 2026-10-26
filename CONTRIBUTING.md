# Contributing

## Adding or updating a skill

1. Create `skills/<skill-name>/SKILL.md` using a lowercase, hyphenated directory name.
2. Add YAML frontmatter with `name` and a `description` that starts with **“Use when...”** and describes when to load the skill.
3. Keep the instructions reusable across projects. Put project-specific procedures in that project's documentation instead.
4. Explain how the skill works with relevant Superpowers skills. Invoke only the skills that apply to the task; do not make unrelated workflows mandatory.
5. Include concrete checks for evidence, safety, and completion where relevant.
6. Update the README skill list and installation guidance when needed.
7. Review the skill against realistic scenarios before considering it ready; verify that the guidance handles missing evidence and pressure to overstate results.

## Pull requests

Describe the use case, trigger conditions, and scenarios used to validate the skill. Do not include credentials, tokens, customer data, or unredacted screenshots/logs.

## Style

- Prefer concise, direct instructions and observable decision criteria.
- Separate facts, user reports, hypotheses, and unknowns.
- Avoid claiming a test passed or a defect is confirmed without evidence.
- Keep skills independent; cross-reference other skills by their discoverable name.
