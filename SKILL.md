---
name: requirement-driven-testing
description: Derive and preserve executable test evidence from settled requirements and design, consuming plan-linked required tests when they govern the work, establishing missing executable evidence before target implementation when meaningfully testable, distinguishing requirement behavior from design contracts, and prioritizing test gaps found in implementation review.
---

# Requirement-driven testing

Use this skill when implementing or changing behavior governed by settled requirements or design, when behavior-preserving refactoring changes tests that carry established evidence, and when implementation review finds missing or insufficient tests.

Treat tests as executable evidence of established requirements and design rather than as a source for inventing them.

## Consume plan-linked required tests

When a selected implementation plan links required tests, read every linked required test together with the relevant requirements, design, and settled plan-level testing decisions before implementing executable tests.
Treat the linked required tests as the planning-time definition of the completion cases for that plan.
Requirements and design remain authoritative for guarantees and expected behavior.

Implement executable tests that realize the linked required tests within the selected plan boundary.
Use plan-level validation scope, boundary coverage, combinations, regression scope, validation methods, and test-support constraints when choosing executable structure and coverage.
Do not independently add a new completion case to a plan-governed implementation.

When executable-test work reveals that a linked required test is missing, ambiguous, inconsistent with canon, or insufficient to express a completion obligation, return that issue to the planning workflow instead of silently redefining or extending the required-test set.
When no plan-linked required-test set governs the work, derive executable evidence directly from settled requirements and design under the rules below.

## Keep requirement and design tests distinct

For plan-governed work, implement requirement-backed and design-backed tests from the linked required-test set while preserving their canonical provenance.
When no linked required-test set governs the work, derive requirement tests from settled requirements and design tests from settled design.

Use requirement tests to verify externally meaningful behavior, outcomes, constraints, and other requirement-level guarantees.
Use design tests when APIs, invariants, type guarantees, responsibility boundaries, or other design contracts need executable verification.

Requirements take precedence over design, tests, and implementation.
When settled design conflicts with a settled requirement, do not preserve or test the conflicting design.
Return the conflict to the workflow that owns design so the design can be aligned with the requirement before relying on it for implementation or design tests.
Leave requirement changes to the workflow that owns requirements.

Do not test implementation details merely because they exist.
Test an internal type, structure, or procedure directly only when it carries an established design guarantee.

## Reuse sufficient coverage

Before adding a test, inspect existing tests for the guarantee being established.

When an existing test already provides sufficient evidence for the requirement or design contract, use that evidence instead of adding a duplicate test.
Do not treat incidental execution of a path as sufficient coverage unless the test actually establishes the relevant guarantee.

## Preserve established test evidence

When changing tests during behavior-preserving refactoring, preserve the requirement and design guarantees that the existing tests intentionally established.

Tests may change structure with the implementation.
An established guarantee may be weakened or removed only when its authoritative settled requirement or design contract has changed so that the guarantee no longer applies.

## Establish tests before target implementation

Establish missing executable tests before the target implementation when the guarantee can be meaningfully tested.
Defer test creation only when a required production dependency prevents the scenario from executing meaningfully, or when the guarantee is not reasonably executable as a test.

For a new or changed requirement-level behavior:

1. When a plan-linked required-test set governs the work, select the applicable linked required test and its canonical requirement source. Otherwise, identify the smallest observable scenario that demonstrates the requirement.
2. Add or select the executable test that realizes that case.
3. Run it before the target implementation.
4. If the required behavior is not already satisfied, confirm that the test fails because that behavior is missing.
5. If the test already passes, verify that the existing behavior genuinely satisfies the requirement instead of manufacturing a failure.
6. Implement any remaining required behavior.
7. Run the requirement test and relevant regression tests until they pass.

Apply the same ordering to design tests when an established design contract needs direct executable evidence.

A failure is useful pre-implementation evidence only when it is caused by the missing target behavior or contract.

## Distinguish test-support gaps from implementation dependencies

When a test cannot be expressed because test fixtures, builders, deterministic inputs, or other test-support boundaries are missing, establish the minimum test support needed before the target implementation.

Do not use test support to fake a missing production dependency or predecessor behavior.
When the target scenario cannot meaningfully execute because required production behavior is not yet available, treat that as an implementation dependency and return it to the workflow that owns planning or execution readiness.

When a settled requirement does not determine an expected result, do not invent one in a test.
Return the ambiguity to the workflow that owns the requirement.

## Prioritize review-discovered test gaps

When implementation review finds that an established requirement or design contract lacks sufficient executable test evidence, close that executable-evidence gap before ordinary cleanup or refactoring, except for prerequisites needed to build or run the tests.

For plan-governed work, first distinguish an executable-evidence gap from a missing completion case.
When the linked required-test set already contains the completion case, add or strengthen executable evidence here.
When the completion case itself is absent from the linked required-test set, return it to the planning workflow before adding it as a plan completion obligation.

When the implementation is incorrect and the applicable completion case is already established, first add or strengthen a test that demonstrates the missing guarantee, then fix the implementation.

When the implementation is already correct and only the evidence is missing, a newly added review-remediation test may pass on its first run.

After closing the gap, use the resulting tests as regression protection for the remaining review fixes.

## Preserve repository conventions

Use the repository's established test framework, fixture structure, naming, placement, and traceability conventions.
Do not introduce a new documentation or mapping format when the repository already has one that can express the required relationship.

This skill owns deriving, implementing, preserving, and restoring executable test evidence from settled requirements and design, consuming plan-linked required tests and plan-level testing decisions when they govern the work.
Requirement definition, design definition, implementation planning, implementation execution, and implementation review remain with their owning workflows.
