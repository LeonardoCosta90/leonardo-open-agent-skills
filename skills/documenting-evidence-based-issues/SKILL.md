---
name: documenting-evidence-based-issues
description: Use when investigating or reporting a defect, especially when evidence is partial or a bug report needs diagnosis, reproduction steps, suggested correction, or acceptance criteria.
---

# Documenting Evidence-Based Issues

## Purpose

Produce bug reports that are useful to engineering without turning assumptions into facts. Separate what was observed, what code inspection establishes, and what remains a hypothesis. Preserve uncertainty and avoid overstating security, scope, or test coverage.

## Work with Superpowers

Use this skill together with applicable Superpowers skills; it is not a substitute for them. Use `systematic-debugging` when investigating a technical defect, and `verification-before-completion` before claiming an issue was created, evidence verified, or a report is complete. Use `brainstorming` if the task expands into designing new behavior or a broader solution. Do not invoke implementation skills when the request is only to diagnose or report.

## Workflow

1. **Capture the report context.** Record the environment/build if known, actor/role and tenant or scope if relevant, operation performed, observed result, and user impact. Never include credentials, tokens, real patient data, or other secrets.
2. **Separate evidence from interpretation.** Identify which facts come from user testimony, screenshots, API responses, logs, automated tests, or local source inspection. Do not imply that a screenshot proves persistence, authorization behavior, or backend state unless it actually shows that.
3. **Reproduce safely when authorized and feasible.** Follow the user's scope. Do not make production writes, alter data, or test outside the requested environment. If not reproduced, say so explicitly.
4. **Investigate before asserting root cause.** Trace the relevant UI, API, and persistence paths as needed. Cite repository-relative file paths and line ranges where available. Distinguish confirmed code behavior from the deployed build; local code does not prove which code is running in STG/production.
5. **Classify the finding narrowly.** Distinguish UI/message defects, functional defects, data-integrity defects, and authorization/security defects. A suspicious symptom is not proof of a security incident. State what the evidence does and does not demonstrate.
6. **Write an actionable report.** Include concise reproduction steps, expected and actual behavior, evidence, diagnosis (or explicitly say root cause is unconfirmed), a proposed direction rather than an unrequested implementation, and testable acceptance criteria.
7. **State boundaries.** Mention untested cases, missing build/request/log/database evidence, and whether code or data was changed. Never mark a test passed based only on assumptions.
8. **Check for duplicates and publish only when requested.** Search the relevant repository's open and closed issues. If creating an issue was not requested, prepare a draft rather than publishing. Do not modify application code when the request is only to report a bug.

## Evidence language

Prefer explicit labels:

- **Observed:** directly visible or returned in the provided/tested evidence.
- **Confirmed by code inspection:** behavior present in the inspected local source; deployed version may differ.
- **Reported by user:** information the user supplied but that was not independently verified.
- **Hypothesis / risk to investigate:** plausible implication not yet reproduced or proven.
- **Not tested / unknown:** required evidence or scenario is absent.

Use calibrated conclusions: “is consistent with,” “suggests,” or “was not demonstrated” when evidence is incomplete. Reserve “confirmed cause,” “data leak,” and “reproduced” for cases with supporting evidence.

## Suggested issue structure

```markdown
## Problema
<Observed behavior and impact; avoid speculative cause.>

## Reprodução
1. <Minimal, safe, deterministic steps>

## Evidência
<Source of evidence, sanitized response/logs, environment/build if known.>
<State what the evidence does not establish.>

## Diagnóstico no código (if inspected)
- <path:line-range — confirmed local behavior>
- <Separate deployment/version uncertainty and unconfirmed hypotheses.>

## Esperado
- <User-visible and system behavior>

## Sugestão de correção (optional)
1. <Direction that preserves security/data integrity; do not prescribe an unverified root-cause fix.>

## Critérios de aceite
- [ ] <Observable, testable outcomes, including relevant regressions and edge cases>

## Limites
<Not reproduced, build/request/log/database unknown, scenarios not tested, and whether code/data changed.>
```

Adapt or omit sections when they do not apply. Keep the issue proportional to the defect; do not pad it with generic criteria.

## Safety and rigor checks

Before publishing, verify:

- Does every factual claim have a stated source?
- Are user-reported behavior, direct evidence, source inspection, and hypotheses clearly distinguished?
- Could a 404, empty list, or generic error have multiple explanations? Do not collapse them into one without evidence.
- Does the report avoid claiming authorization failure or data exposure unless unauthorized data access is demonstrated?
- Are acceptance criteria testable and do they cover the security boundary without prescribing insecure shortcuts?
- Are privacy-sensitive examples synthetic and sanitized?
- Is the issue scoped to the user's request, with no fix implemented unless separately requested?

If a root cause is unknown, title and describe the issue by its observed symptom, and label diagnosis as unconfirmed rather than inventing certainty.
