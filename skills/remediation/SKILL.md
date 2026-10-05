---
name: test-gap-remediation
description: Close missing or insufficient executable test evidence identified during implementation review when the current workflow requires that evidence for a durable guarantee, strengthening tests before implementation fixes when appropriate.
---

# Test Gap Remediation

Use this skill when implementation review finds that a durable guarantee required by the current workflow lacks sufficient executable test evidence.

Treat the review finding as a request to restore required durable evidence, not as authority to invent a new requirement or design contract or to promote provisional behavior into a durable guarantee.

## Confirm the gap is already established

Identify the settled requirement or design contract whose evidence is missing or insufficient.

For plan-governed work, remediate the gap here when it corresponds to an already-linked durable required test case.
Return a completion-required durable case missing from the plan-linked definitions to the planning workflow.

A useful test gap for a provisional or intermediate result may be reported as follow-up work.
Do not route it through remediation solely because retained coverage would be useful.
When it is unclear whether the current plan intended the behavior to be durable, return that classification ambiguity to the planning workflow rather than promoting it here.

When requirements or design do not determine the expected result, return the ambiguity to its owning workflow.

## Close evidence gaps before ordinary cleanup

Prioritize the test gap before ordinary cleanup or refactoring, except for prerequisites needed to build or run the required test.

Apply `requirement-driven-testing` when implementing or strengthening the executable test.

When the implementation is incorrect, first add or strengthen a test that demonstrates the missing guarantee, then return the demonstrated defect to the workflow that owns implementation execution.
When the implementation is already correct and only evidence is missing, the remediation test may pass on its first run.

After the gap is closed, use the resulting test as regression protection for the remaining review fixes.

## Preserve repository conventions

Use the repository's established test framework, fixture structure, naming, placement, and traceability conventions.

This skill owns remediation of review-discovered test-evidence gaps.
General implementation review remains with its reviewing workflow.
Behavior-preserving evidence retention belongs to `test-evidence-preservation`.
