---
name: requirement-driven-testing
description: Establish executable test evidence from settled requirements and design during implementation, consuming plan-linked required test definitions when present, reusing sufficient existing coverage, and creating meaningful tests before target implementation.
---

# Requirement-Driven Testing

Use this skill when establishing executable test evidence during implementation for behavior governed by settled requirements or design, including evidence-only additions for behavior that is already correct.

Treat tests as executable evidence of established requirements and design rather than as a source for inventing them.

## Consume settled testing inputs

When work is governed by an implementation plan, use its linked required test definitions as the completion-required test cases.
Implement executable tests for those cases and use the expected outcomes recorded by the linked definitions.

Apply applicable plan-level decisions for validation scope, boundary coverage, combinations, regression scope, validation methods, and test-support constraints.

Return missing linked definitions, missing completion-required cases, or missing expected outcomes to the planning workflow.
When a linked definition conflicts with applicable settled requirements or design, apply the authority rules below and return any remaining definition mismatch to the planning workflow.
When settled requirements or design do not determine an expected outcome, return that ambiguity to its owning workflow.

When no implementation plan governs the work, derive requirement tests from settled requirements and design tests from settled design.

## Keep requirement and design evidence distinct

Use requirement tests for externally meaningful behavior, outcomes, constraints, and other requirement-level guarantees.
Use design tests for APIs, invariants, type guarantees, responsibility boundaries, and other established design contracts.

Requirements take precedence over design, tests, and implementation.
Return design that conflicts with a settled requirement to the workflow that owns design before relying on it as test authority.

Test internal structures directly only when they carry an established design guarantee.

## Reuse sufficient evidence

Inspect existing tests before adding a new test.
Use an existing test when it already establishes the required guarantee.
Treat incidental path execution as insufficient when the test does not actually establish that guarantee.

## Establish tests before target implementation

When a missing guarantee can be meaningfully tested, establish its executable evidence before implementing the target behavior.

For each required case:

1. Select the plan-linked case, or the smallest observable scenario when no plan governs the work.
2. Add or select the executable test that establishes the case.
3. Run it before target implementation.
4. When the required behavior is missing, confirm that the test fails because of that missing behavior.
5. When the test already passes, verify that existing behavior genuinely satisfies the requirement instead of manufacturing a failure.
6. Return any remaining target behavior to the workflow that owns implementation execution.
7. After the target implementation is updated, run the focused test and relevant regression tests until they pass.

Apply the same ordering to design tests when an established design contract needs direct executable evidence.

A pre-implementation failure is useful only when the missing target behavior or contract causes it.

## Use subtractive fixtures for staged implementation

When the current implementation boundary owns only part of a settled case grounded in a concrete source element and the complete source element is not yet executable, prefer a temporary fixture formed by removing only properties, behaviors, or components that are immaterial to the guarantee under test.

Preserve every precondition, interaction, and expected outcome material to the guarantee under test.
Do not add properties, behaviors, or interactions absent from the real source element when they affect the guarantee under test.

Treat the reduced fixture as executable evidence only for the current implementation boundary.
It does not satisfy the full source element's settled case.
When that full case enters completion scope, establish its evidence through the real source element.

## Distinguish test support from production dependencies

When fixtures, builders, deterministic inputs, or other test-support boundaries prevent a required test from being expressed, establish the minimum test support needed first.

When the current implementation boundary still cannot execute meaningfully with the allowed test support, treat the missing production behavior as an implementation dependency and return it to the workflow that owns planning or execution readiness.

## Preserve repository conventions

Use the repository's established test framework, fixture structure, naming, placement, and traceability conventions.
Use an existing documentation or mapping format when it can express the required relationship.

This skill owns executable test establishment during implementation.
Behavior-preserving evidence retention belongs to `test-evidence-preservation`.
Use `test-evidence-review` when a focused review of test-evidence sufficiency is needed.
Review-discovered evidence repair belongs to `test-gap-remediation`.
Requirement definition, design definition, implementation planning, implementation execution, and general implementation review remain with their owning workflows.
