---
name: test-evidence-planning
description: Define the test cases, expected outcomes, coverage boundaries, combinations, regression scope, evidence retention, validation methods, and test-support constraints required to establish executable evidence for settled requirements and design.
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
Decide separately whether verification is needed for the current work and whether the guarantee requires ongoing executable evidence afterward.
Base continued evidence on the guarantee's applicability and sufficient equivalent coverage, rather than on whether a test helped diagnose a defect.

Specify the required test cases and expected outcomes at the granularity guaranteed by the governing requirements and design for the defined test conditions.
Fix exact values, counts, positions, sequences, and complete collections when those properties are established by the guarantee and test conditions. Otherwise, constrain expectations to the relevant properties and relationships.
Consider whether a valid extension preserving the tested guarantee could change an expected outcome. If so, refine the expectation to remain valid under that extension without weakening the guarantee being tested.
Define validation scope, boundary coverage, combinations, regression scope, validation methods, and test-support constraints when they materially affect whether the evidence is sufficient.

Use requirement cases for externally meaningful behavior, outcomes, constraints, and other requirement-level guarantees.
Use design cases for APIs, invariants, type guarantees, responsibility boundaries, and other established design contracts.

Keep the definitions about what must be established.
Leave test framework mechanics, fixture implementation, test decomposition, and assertion structure to test implementation unless a settled constraint requires them.

When a provisional test stands in for a complete test during staged implementation, first define the corresponding complete test case and expected outcome, then derive the provisional test from that definition.
Keep the complete test definition as the target for eventual executable evidence.
Treat temporary diagnostic checks that establish no settled guarantee as bounded verification for the current work, rather than permanent required test cases.

For a guarantee that applies only during an intermediate stage, a reduced source element may be used when the removed parts are immaterial to that guarantee.
For the source element's own completion, plan evidence using its complete form.

When full verification of a complete source element depends on another unfinished element, prefer waiting for that dependency to be completed before treating the source element as complete.
When waiting is not feasible, plan completion with provisional test evidence using the complete source element and retain its complete test as a pending verification obligation after the dependency is completed.
Keep provisional evidence distinct from evidence for the complete test.
Define when temporary diagnostic checks end and when provisional tests can be replaced, retaining pending full-verification obligations until sufficient evidence is established.

Keep the complete test definition with the source element and hand the pending verification obligation to implementation planning.
When the unfinished dependency's completion scope includes the required integration verification, have implementation planning link to that definition from the dependency's completion criteria.
Otherwise, have implementation planning assign the verification to follow-up work after the dependency's completion.
Refer to the complete test definition from its owner rather than duplicating it.

## Reuse sufficient evidence and bound verification cost

Before adding required cases, compare the guarantees in the current scope with relevant settled test definitions and existing executable tests, including evidence owned by other plans or components.
Reuse a definition or existing executable evidence when it establishes the same guarantee under the applicable conditions; reference its owner instead of duplicating it.
A planned but unimplemented definition does not yet provide executable evidence, and incidental execution of a code path does not establish an unchecked guarantee.
One test may establish multiple guarantees, and several tests may jointly establish one.
Keep distinct new guarantees at the current responsibility or integration boundary explicit even when reusing lower-level evidence.

For uncovered guarantees, select the narrowest practical validation scope that can detect a violation.
Prefer focused, deterministic verification for independently observable behavior, contracts, and state boundaries; require broader integration or end-to-end execution when the guarantee depends on those parts working together.
Select combinations for material interactions and boundary differences instead of multiplying independent dimensions by default.
Where earlier evidence establishes component behavior, verify the new connection without repeating that behavior's full validation unless the integrated guarantee requires it.

Distinguish maintaining ongoing executable evidence from rerunning every test for each change.
Define regression obligations from affected guarantees, dependencies, and integration paths, retaining broad runs when settled completion criteria require them or the impact cannot be bounded reliably.
CI job selection and execution frequency belong to `ci-execution-efficiency`; executable test construction and consolidation belong to `test-evidence-implementation`.

## Keep definitions grounded

Derive every required case and expected outcome from settled requirements or design and the specified test conditions.
Distinguish guaranteed properties from incidental details of the current implementation or test scenario.
When those sources do not determine an expected outcome or another material testing decision, return the ambiguity to its owning workflow.

Do not use current implementation behavior as authority for an expected outcome.
Use repository state to understand available validation surfaces and existing conventions.

## Record the planning result

Use the repository's established format for required test definitions when one exists.

For plan-governed work, record the complete required test definitions in repository-persistent documentation and link them from the implementation plan's completion criteria before execution readiness.

When linking test definitions in implementation plans or editing their planning indexes, follow [`plan-driven-planning`](https://github.com/supersovaa/plan-driven-implementation/blob/main/skills/plan-driven-planning/SKILL.md) for current planning facts and their derived views in those documents.

For work without an implementation plan, make the settled test definitions explicit in the current work context and persist them when the surrounding workflow requires durable planning state.

Record whether planned required evidence is ongoing or provisional and the replacement condition for provisional evidence.
Keep each definition traceable to the requirement or design guarantee it establishes.

## Hand off executable work

Hand the settled required test definitions to `test-evidence-implementation` for executable test establishment.

Use `test-evidence-review` to judge whether the implemented evidence sufficiently establishes the settled definitions.
Route review-discovered test-evidence gaps to `test-gap-remediation`.

This skill owns test-evidence planning.
Executable test creation and reuse belong to `test-evidence-implementation`.
Requirement definition, design definition, implementation planning, implementation execution, and general implementation review remain with their owning workflows.
