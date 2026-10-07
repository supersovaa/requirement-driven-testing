---
name: test-evidence-planning
description: Define the test cases, expected outcomes, coverage boundaries, combinations, regression scope, validation methods, and test-support constraints required to establish executable evidence for settled requirements and design.
---

# Test Evidence Planning

Use this skill when deciding what executable test evidence must exist for settled requirements or design before test implementation or evidence review.

Treat requirements and design as authority, and test definitions as a planning output that makes the required evidence explicit.

## Establish the planning scope

Use the settled requirements and design that govern the requested work.

When an implementation plan governs the work, use its settled implementation boundary and completion contract to bound test planning.
Keep required test definitions inside that boundary and preserve its out-of-scope decisions.

When no implementation plan governs the work, use the explicit requested change or review scope as the test-planning boundary.

Requirements take precedence over design.
Return design that conflicts with a settled requirement to the workflow that owns design before planning dependent test evidence.

## Define required test evidence

For each applicable requirement or design guarantee, define the executable evidence required to establish it.

Specify the required test cases and expected outcomes.
Define validation scope, boundary coverage, combinations, regression scope, validation methods, and test-support constraints when they materially affect whether the evidence is sufficient.

Use requirement cases for externally meaningful behavior, outcomes, constraints, and other requirement-level guarantees.
Use design cases for APIs, invariants, type guarantees, responsibility boundaries, and other established design contracts.

Keep the definitions about what must be established.
Leave test framework mechanics, fixture implementation, test decomposition, and assertion structure to test implementation unless a settled constraint requires them.

## Keep definitions grounded

Derive every required case and expected outcome from settled requirements or design.
When those sources do not determine an expected outcome or another material testing decision, return the ambiguity to its owning workflow.

Do not use current implementation behavior as authority for an expected outcome.
Use repository state to understand available validation surfaces and existing conventions.

## Record the planning result

Use the repository's established format for required test definitions when one exists.

For plan-governed work, record the complete required test definitions in repository-persistent documentation and link them from the implementation plan's completion criteria before execution readiness.

For work without an implementation plan, make the settled test definitions explicit in the current work context and persist them when the surrounding workflow requires durable planning state.

Keep each definition traceable to the requirement or design guarantee it establishes.

## Hand off executable work

Hand the settled required test definitions to `test-evidence-implementation` for executable test establishment.

Use `test-evidence-review` to judge whether the implemented evidence sufficiently establishes the settled definitions.
Route review-discovered implementation gaps to `test-gap-remediation`.

This skill owns test-evidence planning.
Executable test creation and reuse belong to `test-evidence-implementation`.
Requirement definition, design definition, implementation planning, implementation execution, and general implementation review remain with their owning workflows.
