---
name: test-evidence-implementation
description: Establish executable test evidence from settled required test definitions during implementation, reusing sufficient existing coverage and creating meaningful tests before target implementation.
---

# Test Evidence Implementation

Use this skill when implementing executable test evidence for settled required test definitions, including evidence-only additions for behavior that is already correct.

Treat required test definitions as implementation inputs.
Test planning belongs to `test-evidence-planning`.

## Consume settled test definitions

Use the required test cases and expected outcomes settled by `test-evidence-planning`.

When an implementation plan governs the work, implement the required test definitions linked to the current plan boundary.
Apply the settled validation scope, boundary coverage, combinations, regression scope, validation methods, and test-support constraints that govern those definitions.

Return missing required cases, missing expected outcomes, or missing material testing decisions to `test-evidence-planning`.
When a settled test definition conflicts with applicable settled requirements or design, apply the authority rules below and return the definition mismatch to `test-evidence-planning`.
When settled requirements or design do not determine an expected outcome, return that ambiguity to its owning workflow.

## Keep requirement and design evidence distinct

Use requirement tests for cases that establish externally meaningful behavior, outcomes, constraints, and other requirement-level guarantees.
Use design tests for cases that establish APIs, invariants, type guarantees, responsibility boundaries, and other settled design contracts.

Requirements take precedence over design, tests, and implementation.
Return design that conflicts with a settled requirement to the workflow that owns design before relying on it as test authority.

Test internal structures directly only when the settled test definition establishes a design guarantee that requires direct evidence.

## Reuse sufficient evidence

Inspect existing tests before adding a new test.
Use an existing test when it already establishes the required case and expected outcome.
Treat incidental path execution as insufficient when the test does not actually establish that guarantee.

## Establish tests before target implementation

When a required case lacks sufficient executable evidence, establish that evidence before implementing the target behavior when the case can be meaningfully exercised.

For each required case:

1. Select the settled required case.
2. Add or select the executable test that establishes the case.
3. Run it before target implementation.
4. When the required behavior is missing, confirm that the test fails because of that missing behavior.
5. When the test already passes, verify that existing behavior genuinely satisfies the required case instead of manufacturing a failure.
6. Return any remaining target behavior to the workflow that owns implementation execution.
7. After the target implementation is updated, run the focused test and relevant regression tests until they pass.

Apply the same ordering to design cases when a settled design contract needs direct executable evidence.

A pre-implementation failure is useful only when the missing target behavior or contract causes it.

## Use subtractive fixtures for staged implementation

When the current implementation boundary owns only part of a settled case grounded in a concrete source element and the complete source element is not yet executable, prefer a temporary fixture formed by removing only properties, behaviors, or components that are immaterial to the guarantee under test.

Preserve every precondition, interaction, and expected outcome material to the guarantee under test.
Do not add properties, behaviors, or interactions absent from the real source element when they affect the guarantee under test.

Treat the reduced fixture as executable evidence only for guarantees whose material conditions remain after the reduction.
Do not use it as evidence for a guarantee that depends on a removed part.
When such a guarantee enters completion scope, establish its evidence through the real source element.

## Distinguish test support from production dependencies

When fixtures, builders, deterministic inputs, or other test-support boundaries prevent a required test from being expressed, establish the minimum test support permitted by the settled test definitions.

When the current implementation boundary still cannot execute meaningfully with the allowed test support, treat the missing production behavior as an implementation dependency and return it to the workflow that owns planning or execution readiness.

## Preserve repository conventions

Use the repository's established test framework, fixture structure, naming, placement, and traceability conventions.
Use an existing documentation or mapping format when it can express the required relationship.

This skill owns executable test establishment from settled test definitions.
Test-evidence planning belongs to `test-evidence-planning`.
Behavior-preserving evidence retention belongs to `test-evidence-preservation`.
Use `test-evidence-review` when a focused review of test-evidence sufficiency is needed.
Review-discovered evidence repair belongs to `test-gap-remediation`.
Requirement definition, design definition, implementation planning, implementation execution, and general implementation review remain with their owning workflows.
