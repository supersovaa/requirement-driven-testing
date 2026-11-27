---
name: test-gap-remediation
description: Repair missing or insufficient automated or manual evidence found in review for a settled test case. Coordinate the repair with any implementation fix.
---

# Test Gap Remediation

When review finds insufficient automated or manual evidence for a settled case, restore the evidence that case requires. The review finding does not authorize a new case, requirement, or design contract.

## Confirm the gap is already settled

Apply [`test-lifecycle`](https://github.com/supersovaa/test-lifecycle/blob/main/SKILL.md) to confirm that the case remains a current verification obligation.
Identify its expected outcome from the test plan before introduction or the current test design afterward.

When the finding requires a case or material testing decision that is absent from the settled test definitions, return it to `test-evidence-planning`.

When requirements or design do not determine the expected result, return the ambiguity to its owning workflow.

## Close evidence gaps before ordinary cleanup

Prioritize the test gap before ordinary cleanup or refactoring, except for prerequisites needed to build or run the required test.

Apply [`test-evidence-implementation`](../implementation/SKILL.md) when implementing, strengthening, or executing the selected automated test or manual procedure, including its validation of permitted verification methods and its [sequencing rules](../implementation/SKILL.md#establish-executable-evidence-from-the-test-plan).
For a missing manual result, carry out or obtain the required manual verification and assess its result against current test design; keep the obligation pending until that result is available.

When the implementation is incorrect, return the defect and its settled required case to the workflow that owns implementation execution, and coordinate the fix with the selected automated or manual verification.
When the implementation is already correct and only evidence is missing, the remediation test may pass on its first run.

After the gap is closed, use the resulting test for the remaining review fixes within its selected lifetime. Apply `test-lifecycle` to its continuing role and retirement.

## Preserve repository conventions

Use the repository's established test framework, fixture structure, naming, placement, and traceability conventions.

This skill owns remediation of review-discovered automated or manual evidence gaps for settled required cases.
Test-evidence planning belongs to `test-evidence-planning`.
Use `test-evidence-review` when a focused review of test-evidence sufficiency is needed.
General implementation review remains with its reviewing workflow.
Behavior-preserving evidence retention belongs to `test-evidence-preservation`.
