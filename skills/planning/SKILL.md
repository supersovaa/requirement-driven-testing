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

When planning a temporary test, first define the corresponding complete test case and expected outcome, then derive the temporary test from that definition.
Keep the complete test definition as the target for eventual executable evidence.

For a temporary guarantee, a reduced source element may be used when the removed parts are immaterial to that guarantee.
For the source element's own completion, plan evidence using its complete form.

When full verification of a complete source element depends on another unfinished element, prefer waiting for that dependency to be completed before treating the source element as complete.
When waiting is not feasible, plan completion with temporary test evidence using the complete source element and retain its complete test as a pending verification obligation after the dependency is completed.
Keep temporary evidence distinct from evidence for the complete test.

Keep the complete test definition with the source element and hand the pending verification obligation to implementation planning.
When the unfinished dependency's completion scope includes the required integration verification, have implementation planning link to that definition from the dependency's completion criteria.
Otherwise, have implementation planning assign the verification to follow-up work after the dependency's completion.
Refer to the complete test definition from its owner rather than duplicating it.

## Keep definitions grounded

Derive every required case and expected outcome from settled requirements or design.
When those sources do not determine an expected outcome or another material testing decision, return the ambiguity to its owning workflow.

Do not use current implementation behavior as authority for an expected outcome.
Use repository state to understand available validation surfaces and existing conventions.

## Record the planning result

Use the repository's established format for required test definitions when one exists.

For plan-governed work, record the complete required test definitions in repository-persistent documentation and link them from the implementation plan's completion criteria before execution readiness.

When linking test definitions in implementation plans or editing their planning indexes, use the existing authoritative plan-state and wave-assignment records for current progress information.
Represent progress counts, completed-plan lists, and wave status by references to or derived views of those records rather than maintaining independent copies in test-planning documents.

For work without an implementation plan, make the settled test definitions explicit in the current work context and persist them when the surrounding workflow requires durable planning state.

Keep each definition traceable to the requirement or design guarantee it establishes.

## Hand off executable work

Hand the settled required test definitions to `test-evidence-implementation` for executable test establishment.

Use `test-evidence-review` to judge whether the implemented evidence sufficiently establishes the settled definitions.
Route review-discovered test-evidence gaps to `test-gap-remediation`.

This skill owns test-evidence planning.
Executable test creation and reuse belong to `test-evidence-implementation`.
Requirement definition, design definition, implementation planning, implementation execution, and general implementation review remain with their owning workflows.
