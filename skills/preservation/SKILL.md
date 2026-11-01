---
name: test-evidence-preservation
description: Preserve the requirement and design guarantees intentionally established by existing tests when behavior-preserving refactoring changes test structure or placement.
---

# Test Evidence Preservation

Use this skill when behavior-preserving refactoring changes tests that already carry established requirement or design evidence.

Treat the guarantee established by a test as the thing to preserve, not the test's current structure.
When selecting or executing verification that may launch real complete games, simulations, episodes, or similarly costly end-to-end trials, apply [`test-execution-budget`](../execution/SKILL.md) before selecting commands to determine whether those trials are necessary and to bound justified execution.

## Identify established guarantees

Before changing an existing test, identify the requirement or design guarantee it intentionally establishes.
Distinguish authoritative guarantees from incidental assertions or implementation details using the [ongoing-evidence selection criteria](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/planning/SKILL.md#select-sufficient-ongoing-evidence).

Requirements remain authoritative over design, tests, and implementation.
When an existing test disagrees with a settled requirement, treat the conflicting expectation as non-authoritative.
If aligning the test with the requirement exposes an implementation defect, return that defect to the workflow that owns implementation execution rather than treating the change as behavior-preserving refactoring.
When settled design disagrees with a settled requirement, return the design issue to the workflow that owns design.

## Preserve equivalent evidence

Keep executable evidence for every still-applicable established guarantee affected by the refactoring.
Keep the repository documentation's identification of that evidence current when tests move, merge, split, or are replaced; retain shared guarantee-level explanations when they remain accurate.
The test may change framework usage, fixture shape, placement, decomposition, or assertion structure when the resulting evidence remains sufficient.

Reuse an existing replacement test when it already establishes the same guarantee.
Retire incidental assertions and redundant tests while retaining sufficient evidence for the applicable guarantees.
When a settled test definition itself fixes the incidental detail or requires redundant evidence, return that definition to `test-evidence-planning` for reassessment before changing its obligation.

## Verify discovered test evidence

When refactoring moves, splits, merges, or re-registers test files and modules, compare the tests actually discovered by the project's test runner for the affected targets and configurations before and after the change. Use the runner's collection or list mode where available, and trace test module registration, imports, feature gates, and target inclusion.

For each still-applicable established guarantee, identify the discovered executable test or tests that now establish it. Treat source-level test annotations, file counts, test names, and total counts as signals for investigation. Judge preservation by executable evidence for the guarantees, allowing equivalent renamed, combined, or replacement tests. When a previous discovered inventory is available, use it to identify evidence that may have become disconnected.

Restore the required test registration or equivalent executable evidence where discovery reveals a gap, then re-check the affected test inventory. Use the repository's verification workflow to establish that the discovered tests still exercise their intended assertions. Apply `test-execution-budget` when this verification may launch costly complete trials.

## Keep guarantee changes with their owner

Weaken or remove an established guarantee only when its authoritative settled requirement or design contract has changed so that the guarantee no longer applies.

When the authoritative source is ambiguous, return that ambiguity to its owning workflow before discarding the evidence.

## Preserve repository conventions

Use the repository's established test framework, fixture structure, naming, placement, and traceability conventions.

This skill owns preserving executable test evidence during behavior-preserving refactoring.
Establishing new executable evidence during implementation belongs to `test-evidence-implementation`.
Use `test-evidence-review` when a focused review of test-evidence sufficiency is needed.
Review-discovered evidence repair belongs to `test-gap-remediation`.
Test-evidence planning belongs to `test-evidence-planning`.
