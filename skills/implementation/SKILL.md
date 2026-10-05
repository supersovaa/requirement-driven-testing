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
6. Implement any remaining required behavior.
7. Run the focused test and relevant regression tests until they pass.

Apply the same ordering to design tests when an established design contract needs direct executable evidence.

A pre-implementation failure is useful only when the missing target behavior or contract causes it.

## Distinguish test support from production dependencies

When fixtures, builders, deterministic inputs, or other test-support boundaries prevent a required test from being expressed, establish the minimum test support needed first.

When required production behavior is missing and the scenario cannot execute meaningfully, treat that as an implementation dependency and return it to the workflow that owns planning or execution readiness.

## Preserve repository conventions

Use the repository's established test framework, fixture structure, naming, placement, and traceability conventions.
Use an existing documentation or mapping format when it can express the required relationship.

This skill owns executable test establishment during implementation.
Behavior-preserving evidence retention belongs to `test-evidence-preservation`.
Review-discovered evidence repair belongs to `test-gap-remediation`.
Requirement definition, design definition, implementation planning, implementation execution, and implementation review remain with their owning workflows.
