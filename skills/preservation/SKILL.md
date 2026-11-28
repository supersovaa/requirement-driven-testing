---
name: test-evidence-preservation
description: Use during behavior-preserving refactoring to account for existing test evidence.
---

# Test Evidence Preservation

Apply the preservation checks below when the refactor moves or restructures tests that carry existing requirement or design evidence. Determine which tests still merit retention, then preserve their selected guarantees.

Apply [`test-lifecycle`](https://github.com/supersovaa/test-lifecycle/blob/main/SKILL.md) to assess which tests still need retention before preserving their evidence.
For retained tests, preserve their selected guarantees using methods allowed by the [prohibition on high-volume repetition](../planning/SKILL.md#prohibit-high-volume-repetition), applying it before retaining or executing the affected tests.
When selecting or executing verification that may launch real complete games, simulations, episodes, or similarly costly end-to-end trials, apply [`test-execution-budget`](../execution/SKILL.md) before selecting commands to determine whether those trials are necessary and to bound justified execution.

## Identify established guarantees

Before changing an existing test, identify the requirement or design guarantee it intentionally establishes.
Distinguish authoritative guarantees from incidental assertions or implementation details using the [ongoing-evidence selection criteria](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/planning/SKILL.md#select-sufficient-ongoing-evidence).

Requirements remain authoritative over design, tests, and implementation.
When an existing test disagrees with a settled requirement, treat the conflicting expectation as non-authoritative.
If aligning the test with the requirement exposes an implementation defect, return that defect to the workflow that owns implementation execution rather than treating the change as behavior-preserving refactoring.
When settled design disagrees with a settled requirement, return the design issue to the workflow that owns design.

## Preserve equivalent evidence

Keep executable evidence for every guarantee still selected for automated verification under the current lifecycle decisions and affected by the refactoring. Preserve selected manual procedures through their current test design.
Keep the current test design's identification of that evidence aligned when tests move, merge, split, or are replaced; retain shared explanations when they remain accurate.
The test may change framework usage, fixture shape, placement, decomposition, or assertion structure when the resulting evidence remains sufficient.

Reuse an existing replacement test when it already establishes the same guarantee.
Retire incidental assertions and redundant tests while retaining sufficient evidence for the selected continuing verification.
When a settled test definition fixes incidental details, requires redundant evidence, or prescribes prohibited repetition or unnecessary processing, return it to `test-evidence-planning` before retaining or executing that method. Keep the guarantee pending until sufficient permitted evidence is established or its obligation is revised by the owning workflow.

## Verify discovered test evidence

When refactoring moves, splits, merges, or re-registers test files and modules, inspect the tests actually discovered by the project's test runner for the affected targets and configurations. Compare with a pre-refactor discovered inventory when available. Use the runner's collection or list mode where supported, and trace test module registration, imports, feature gates, and target inclusion.

For each guarantee still selected for automated verification, identify the discovered executable test or tests that now establish it. Treat source-level test annotations, file counts, test names, and total counts as signals for investigation. Judge preservation by executable evidence for the guarantees, allowing equivalent renamed, combined, or replacement tests.

When discovery reveals missing required evidence, route its registration or equivalent evidence repair to the owning implementation workflow, or to `test-gap-remediation` for a review-discovered gap. Re-check the affected test inventory after correction. Use the repository's verification workflow to establish that the discovered tests still exercise their intended assertions. Apply `test-execution-budget` when this verification may launch costly complete trials.

## Keep guarantee changes with their owner

Product requirements and design workflows own changes to the product guarantee.
Test retention follows `test-lifecycle`; retiring a test whose protective role has ended does not remove the product guarantee.
When the expected product behavior is ambiguous, return that ambiguity to its owning workflow.

## Preserve repository conventions

Use the repository's established test framework, fixture structure, naming, placement, and traceability conventions.

This skill owns preserving executable test evidence during behavior-preserving refactoring.
Establishing new executable evidence during implementation belongs to `test-evidence-implementation`.
Use `test-evidence-review` when a focused review of test-evidence sufficiency is needed.
Review-discovered evidence repair belongs to `test-gap-remediation`.
Test-evidence planning belongs to `test-evidence-planning`.
