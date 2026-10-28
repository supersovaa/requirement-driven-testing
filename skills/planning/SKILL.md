---
name: test-evidence-planning
description: Plan or reassess executable verification for settled requirements and design or current diagnostic work, including evidence lifetime, required cases, expected outcomes, coverage, regression scope, validation methods, and test-support constraints.
---

# Test Evidence Planning

Use this skill when deciding or reassessing executable verification for settled requirements and design or current diagnostic work, including evidence lifetime, addition, consolidation, replacement, and retirement.

Treat requirements and design as authority, and test definitions as a planning output that makes the required evidence explicit.

## Establish the planning scope

Use the settled requirements and design that govern the requested work.

When an implementation plan governs the work, use its settled implementation boundary and completion contract to bound test planning.
Keep required test definitions inside that boundary and preserve its out-of-scope decisions.

When no implementation plan governs the work, use the explicit requested change or review scope as the test-planning boundary.

Requirements take precedence over design.
Return design that conflicts with a settled requirement to the workflow that owns design before planning dependent test evidence.

## Classify evidence by lifetime

Classify planned verification by whether it establishes a continuing settled guarantee and, when it does, whether complete evidence is currently executable:

- **Ongoing evidence** establishes a settled requirement or design guarantee that continues to apply after the current work. Keep sufficient executable evidence for that guarantee in the repository.
- **Temporary diagnostic verification** serves the current reproduction, isolation, or repair confirmation only. Keep it outside required test definitions, bound it to the current work, and define when its purpose is complete.
- **Provisional evidence** temporarily establishes part or a substitute of a continuing guarantee because complete evidence cannot yet be executed. Keep the complete test definition as the target and define the condition that replaces the provisional evidence.

Base the classification on the continuing guarantee and current executability rather than on how a check was discovered or how useful it was during debugging.
Classify a defect reproduction as ongoing evidence when it establishes a continuing settled guarantee that lacks sufficient equivalent coverage.

## Select sufficient ongoing evidence

For each applicable requirement or design guarantee, including any required verification examples, inspect relevant settled test definitions and existing executable tests, including evidence owned by other plans or components.
For each ongoing test considered for addition or retention in the current scope, identify the settled guarantee and the concrete violation its assertions can detect.
Reuse sufficient definitions by reference and executable evidence when it establishes the guarantee; add or retain separate tests only for uncovered guarantees or distinct behavior at the current responsibility or integration boundary.
One test may establish multiple guarantees, and multiple tests may together establish one.

Prefer assertions on required behavior and results through the real input and loading path when that path belongs to the guarantee.
Use those assertions as evidence for the loading and data-interpretation guarantees they actually establish; incidental code-path execution remains insufficient.
Treat a handwritten copy of a loaded internal structure as redundant when behavioral evidence already establishes the same guarantee.
Require separate representation or loading checks only for a distinct settled contract and a concrete violation outside that behavioral evidence.
For tests, fixtures, helpers, and CI machinery, prefer consumer tests, review, and bounded change-time checks; add or retain dedicated tests only for a distinct continuing guarantee and a concrete failure those checks would miss.
Complete test expansion when the scoped continuing guarantees have sufficient executable evidence.

Keeping ongoing evidence does not require executing every test for every change; CI execution selection belongs to `ci-execution-efficiency`.

When a settled test definition fixes incidental details or duplicates sufficient evidence, revise it here against the governing guarantee and update its planning references.
Keep changes to authoritative requirements, design, or completion contracts with their owning workflows.
A settled required test definition remains a pending evidence obligation until sufficient executable tests establish its specified case and expected outcome or its definition is revised through the owning workflow.

## Define required test cases

Specify the required test cases and expected outcomes at the granularity guaranteed by the governing requirements and design for the defined test conditions.
Fix exact values, counts, positions, sequences, complete collections, names, wording, and representations only when those properties are established by the guarantee and test conditions. Otherwise, constrain expectations to the relevant properties and relationships.
Consider whether a valid refactoring, extension, or rewording preserving the tested guarantee could change an expected outcome. If so, refine the expectation to remain valid under that change without weakening the guarantee being tested.
Select the narrowest validation scope sufficient to detect a violation. Before selecting complete games, simulations, episodes, or other costly end-to-end trials as required evidence, identify the guarantee that depends on complete trial execution and the concrete violation it would detect. Prefer inspection, deterministic unit, component, or focused state-transition tests, controlled results, and reusable evidence when they establish the same guarantee; choose complete trials when the guarantee specifically depends on the complete lifecycle, actual end-to-end integration, or statistical observations that require real sampling.
Define boundary coverage, combinations, regression scope, validation methods, and test-support constraints when they materially affect whether the evidence is sufficient.
For each varied condition, tie its variation to a guarantee or concrete violation the evidence must distinguish.
Combine conditions when their interaction or boundary creates a distinct violation that representative cases for the individual conditions would miss; use representative cases for independent conditions whose combinations establish the same guarantee.
Preserve broad verification explicitly required by settled completion criteria when it is grounded in the governing requirements or design. When a completion criterion instead fixes an incidental property that those authorities do not establish, return that criterion to [`plan-driven-planning`](https://github.com/supersovaa/plan-driven-implementation/blob/main/skills/plan-driven-planning/SKILL.md) for correction before deriving or revising dependent required test definitions.

Use requirement cases for externally meaningful behavior, outcomes, constraints, and other requirement-level guarantees.
Use design cases for APIs, invariants, type guarantees, responsibility boundaries, and other established design contracts.

Keep the definitions about what must be established.
Leave test framework mechanics, fixture implementation, test decomposition, and assertion structure to test implementation unless a settled constraint requires them.

## Plan provisional evidence for staged implementation

When a provisional test stands in for complete evidence during staged implementation, first define the corresponding complete test case and expected outcome, then derive the provisional test from that definition.
Keep the complete test definition as the target for eventual executable evidence.

For a guarantee that applies only during an intermediate stage, a reduced source element may be used when the removed parts are immaterial to that guarantee.
For the source element's own completion, plan evidence using its complete form.

When full verification of a complete source element depends on another unfinished element, prefer waiting for that dependency to be completed before treating the source element as complete.
When waiting is not feasible, plan completion with provisional evidence using the complete source element and retain its complete test as a pending verification obligation after the dependency is completed.
Keep provisional evidence distinct from evidence for the complete test and define its replacement condition.

Keep the complete test definition with the source element and hand the pending verification obligation to implementation planning.
When the unfinished dependency's completion scope includes the required integration verification, have implementation planning link to that definition from the dependency's completion criteria.
Otherwise, have implementation planning assign the verification to follow-up work after the dependency's completion.
Refer to the complete test definition from its owner rather than duplicating it.

## Keep definitions grounded

Derive every required case and expected outcome from settled requirements or design and the specified test conditions.
Distinguish guaranteed properties from incidental details of the current implementation or test scenario.
When those sources do not determine an expected outcome or another material testing decision, return the ambiguity to its owning workflow.

Use settled requirements and design as expectation authority, and repository state to understand available validation surfaces and existing conventions.

## Record the planning result

Use the repository's established format for required test definitions when one exists.

For plan-governed work, record the complete required test definitions in repository-persistent documentation and link them from the implementation plan's completion criteria before execution readiness.

When linking test definitions in implementation plans or editing their planning indexes, follow [`plan-driven-planning`](https://github.com/supersovaa/plan-driven-implementation/blob/main/skills/plan-driven-planning/SKILL.md) for current planning facts and their derived views in those documents.

For work without an implementation plan, make the settled test definitions explicit in the current work context and persist them when the surrounding workflow requires durable planning state.

Record for each applicable guarantee and required verification example the sufficient existing tests and supporting coverage, or the uncovered cases, expected outcomes, and required new or expanded tests. For combined conditions, record the distinct interaction or boundary violation that requires the combination.
When existing evidence establishes all of them, record its sufficiency and complete test selection with that evidence.
Record ongoing evidence with the continuing guarantee it establishes, and provisional evidence with its complete target and replacement condition. Keep temporary diagnostic verification in the current work context with its completion boundary.
For consolidation or retirement, identify the incidental assertions or redundant tests to remove and the sufficient ongoing evidence retained for continuing guarantees.
Keep each definition traceable to the requirement or design guarantee it establishes.

## Hand off executable work

Hand the settled required test definitions to `test-evidence-implementation` for executable test establishment.

Use `test-evidence-review` to judge whether the implemented evidence sufficiently establishes the settled definitions.
Route review-discovered test-evidence gaps to `test-gap-remediation`.

This skill owns test-evidence planning, evidence-lifetime classification, and reassessment of test definitions.
Executable test creation, reuse, and retirement belong to `test-evidence-implementation`.
Requirement definition, design definition, implementation planning, implementation execution, and general implementation review remain with their owning workflows.
