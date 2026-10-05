---
name: test-gap-remediation
description: Close missing or insufficient executable test evidence identified during implementation review, strengthening tests before implementation fixes when the missing guarantee is already established.
---

# Test Gap Remediation

Use this skill when implementation review finds that an established requirement or design contract lacks sufficient executable test evidence.

Treat the review finding as a request to restore established evidence, not as authority to invent a new requirement or design contract.

## Confirm the gap is already established

Identify the settled requirement or design contract whose evidence is missing or insufficient.

For plan-governed work, remediate the gap here when it corresponds to an already-linked required test case.
Return a completion-required case missing from the plan-linked definitions to the planning workflow.

When requirements or design do not determine the expected result, return the ambiguity to its owning workflow.

## Close evidence gaps before ordinary cleanup

Prioritize the test gap before ordinary cleanup or refactoring, except for prerequisites needed to build or run the required test.

Apply `requirement-driven-testing` when implementing or strengthening the executable test.

When the implementation is incorrect, first add or strengthen a test that demonstrates the missing guarantee, then fix the implementation.
When the implementation is already correct and only evidence is missing, the remediation test may pass on its first run.

After the gap is closed, use the resulting test as regression protection for the remaining review fixes.

## Preserve repository conventions

Use the repository's established test framework, fixture structure, naming, placement, and traceability conventions.

This skill owns remediation of review-discovered test-evidence gaps.
General implementation review remains with its reviewing workflow.
Behavior-preserving evidence retention belongs to `test-evidence-preservation`.
