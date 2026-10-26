---
name: conducting-functional-qa
description: Use when guiding a person through manual functional QA in a running application, continuing an existing test plan, collecting UI evidence, or recording pass/fail/blocked results in a QA tracker or wiki.
---

# Conducting Functional QA

## Core principle

The human operator performs the live test. Guide one meaningful action at a time, then record only outcomes they explicitly report or evidence directly establishes. A test plan is not permission to access systems, create data, or make changes.

## Work with Superpowers

Use this skill together with applicable Superpowers skills; this workflow does not replace them. Use `systematic-debugging` before diagnosing an unexpected result or test failure, and `verification-before-completion` before claiming a test, record update, or publication is complete. Use `brainstorming` before inventing or materially changing test scope. Do not invoke implementation/planning skills when only guiding manual execution and recording results.

## Workflow

1. **Read the existing test source and history.** Find the next applicable uncompleted case. Check wiki/test tracker and recent notes first; do not repeat a completed test unless the user requests a retest or new evidence makes it necessary.
2. **Honor scope and exclusions.** Carry forward explicit constraints: blocked environments, excluded modules, known issues not to reopen, skipped cases, user roles, privacy requirements, and limits on direct API/database access. Ask before expanding scope.
3. **Choose a safe, useful next test.** Prefer the next functional case that can be exercised through the available interface. Avoid cases whose prerequisite is blocked. Identify synthetic data and any cleanup requirement before a consequential action.
4. **Guide incrementally.** Present the case ID/name, one small set of clear steps, and the observable expected result. Pause for the operator's evidence before deciding or moving to a consequential next step. Do not ask the operator to infer backend persistence from a transient UI state.
5. **Assess evidence narrowly.** Separate operator report, screenshots, visible UI, API response, persisted state, and code inspection. Point out what is still unverified. A successful click alone does not prove persistence, authorization boundaries, or end-to-end correctness.
6. **Classify accurately.** Use the tracker’s statuses, such as OK, Não OK, Bloqueado, or N/A, only when supported. A test is **OK** only for its stated scope and observed acceptance criteria. Use **Não OK** for a demonstrated mismatch. Use **Bloqueado** when a prerequisite/environment prevents execution. Use **N/A** only with an explicit rationale. A skipped or deferred test remains unmarked unless the tracker has a distinct skipped status and the user approves using it.
7. **Handle failures and issues.** For an unexpected result, preserve sanitized evidence and investigate before claiming cause. Create or update an issue only when asked or already authorized by the ongoing task; search for duplicates first. Do not change product code when the task is test execution/reporting only.
8. **Update records carefully.** Before editing a wiki/tracker, verify the exact case and current contents. Include concise evidence, environment/build/role if known, defect link, and limitations. Do not expose credentials or personal data. Do not commit or publish externally unless that is part of the user's established request.
9. **Verify the update.** Check diff/format, confirm only intended test records changed, and verify publication when publishing was requested. Report the status, evidence basis, any limits, and the next eligible case.

## One-step interaction pattern

At each turn, provide:

1. **Current case:** ID and short title.
2. **Action:** what the operator should do now, using synthetic/non-sensitive data.
3. **Expected observation:** what to report or capture.
4. **Boundary:** relevant caution, prerequisite, or excluded area.

After evidence arrives, summarize what it establishes and what it does not. Ask for the next needed observation only; do not pre-mark results or send a long sequence of unrelated test cases.

## Status decision table

| Status | Apply when | Do not apply when |
|---|---|---|
| OK | All acceptance points in the executed scope are supported by evidence | Only a subset ran, or persistence/security was inferred but not checked |
| Não OK | A reproducible or directly observed result violates expected behavior | A suspicious message has no demonstrated mismatch |
| Bloqueado | A named prerequisite (access, environment, data, permission) prevents a meaningful run | The test is merely inconvenient or intentionally skipped |
| N/A | The case does not apply, with reason approved/documented | The case was simply not run |

Partial evidence should be recorded as partial, not promoted to a full pass. If the test source has no partial status, leave the official status unchanged and add a clearly labeled note only if authorized.

## Safety and rigor checks

- Never ask for passwords, tokens, real patient records, or unredacted sensitive screenshots.
- Do not bypass access controls, probe other tenants, or make destructive/irreversible changes without explicit authorization and a cleanup/rollback plan.
- Do not repeat cases already confirmed complete; distinguish a true retest from a continuation or additional scenario.
- Do not re-open known issues or excluded test areas unless the user directs it.
- Do not claim a security defect from an error, empty list, role difference, or UI affordance alone.
- Do not claim completion, pass, publication, or persistence without checking the relevant evidence.
