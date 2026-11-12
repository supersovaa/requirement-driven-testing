---
name: test-gap-remediation
description: Close missing or insufficient executable test evidence identified during review, applying settled test definitions and coordinating evidence repair with implementation fixes.
---

# Test Gap Remediation

Use this skill when review finds that a settled required test case lacks sufficient executable evidence.

Treat the review finding as a request to restore settled evidence, not as authority to plan a new test case or invent a new requirement or design contract.

## Confirm the gap is already settled

Identify the settled required test case and its expected outcome.

When the finding requires a case or material testing decision that is absent from the settled test definitions, return it to `test-evidence-planning`.

When requirements or design do not determine the expected result, return the ambiguity to its owning workflow.

## Close evidence gaps before ordinary cleanup

Prioritize the test gap before ordinary cleanup or refactoring, except for prerequisites needed to build or run the required test.

Apply [`test-evidence-implementation`](../implementation/SKILL.md) when implementing or strengthening the executable test, including its [sequencing rules](../implementation/SKILL.md#establish-executable-evidence-from-the-test-plan).

When the implementation is incorrect, return the defect and its settled required case to the workflow that owns implementation execution, and coordinate the fix with executable evidence establishment.
When the implementation is already correct and only evidence is missing, the remediation test may pass on its first run.

After the gap is closed, use the resulting test as regression protection for the remaining review fixes.

## Preserve repository conventions

Use the repository's established test framework, fixture structure, naming, placement, and traceability conventions.

This skill owns remediation of review-discovered executable evidence gaps for settled required cases.
Test-evidence planning belongs to `test-evidence-planning`.
Use `test-evidence-review` when a focused review of test-evidence sufficiency is needed.
General implementation review remains with its reviewing workflow.
Behavior-preserving evidence retention belongs to `test-evidence-preservation`.
