---
name: test-evidence-planning
description: Plan or reassess automated or manual verification for settled requirements, design, or diagnostic work. Define cases, expected outcomes, and coverage.
---

# Test Evidence Planning

Plan or reassess the cases and expected outcomes for automated or manual verification, including additions, consolidation, replacement, and retirement. Start from settled requirements and design or the current diagnostic task.

Treat requirements and design as authority, and test definitions as a planning output that makes the required evidence explicit.

When planning additions or expansions to automatically collected tests, apply [`ci-execution-efficiency`](https://github.com/supersovaa/ci-efficiency/blob/main/skills/execution/SKILL.md) to their recurring execution cost, including when CI workflow files stay unchanged.

## Establish the planning scope

Use the settled requirements and design that govern the requested work.

When an implementation plan governs the work, use its settled implementation boundary and completion contract to bound test planning.
Keep required test definitions inside that boundary and preserve its out-of-scope decisions.

When no implementation plan governs the work, use the explicit requested change or review scope as the test-planning boundary.

Requirements take precedence over design.
Return design that conflicts with a settled requirement to the workflow that owns design before planning dependent test evidence.

## Apply lifecycle decisions

Apply [`test-lifecycle`](https://github.com/supersovaa/test-lifecycle/blob/main/SKILL.md) when selecting or reassessing tests, including their classification, CI admission and retention, written accountability, and retirement conditions.
Record the resulting decisions in the test plan before introduction. Use current test design for already introduced tests.
In this skill, ongoing evidence means verification selected for continued manual use or CI protection under those decisions; provisional evidence is a substitute with a planned replacement condition.
Plan implementation-time verification within its completion boundary, including diagnostic work. A continuing product guarantee alone does not select continuing test evidence.

## Select sufficient ongoing evidence

For each guarantee selected for continuing verification under the lifecycle decisions, including required verification examples in that scope, inspect relevant settled test definitions and existing tests or manual procedures, including evidence owned by other plans or components.
For each ongoing test considered for addition or retention in the current scope, including existing tests reused as required or regression evidence, identify the settled guarantee and the concrete violation its assertions can detect on a consumer path or mode required by the settled requirements or design.
Reuse sufficient definitions and evidence by reference; add or retain separate tests only for uncovered cases or distinct behavior within the selected lifecycle and responsibility boundary.
One test may establish multiple guarantees, and multiple tests may together establish one.

Assert required behavior and results on the consumer paths and modes required by the settled requirements or design, including the real input and loading path when that path belongs to the guarantee.
Use those assertions as evidence for the guarantees they actually establish. Executing a path without asserting its guarantee establishes none, and neither does asserting on a path or mode outside those settled consumer contracts.
Treat a handwritten copy of a loaded internal structure as redundant when behavioral evidence already establishes the same guarantee.
Require separate representation or loading checks only for a distinct settled contract and a concrete violation outside that behavioral evidence.
For tests, fixtures, helpers, and CI machinery, prefer consumer tests, review, and bounded change-time checks; select dedicated continuing tests through `test-lifecycle` only for a distinct failure those checks would miss.
Complete test selection when the scoped verification obligations have sufficient automated or manual evidence as selected.

Keeping ongoing evidence does not require executing every test for every change; CI execution selection belongs to `ci-execution-efficiency`.

When a settled test definition fixes incidental details, duplicates sufficient evidence, or prescribes prohibited repetition or unnecessary processing, revise it here against the governing guarantee in the test plan before introduction or the current test design afterward. Keep remaining planning references aligned with that authority.
Treat proposed additional persistent tests discovered during implementation or review as test-planning candidates. Select them only after establishing their governing guarantee, the distinct violation that existing evidence misses, and their fit within the current work boundary; return changes to an implementation plan's settled boundary to its owning planning workflow.
Keep changes to authoritative requirements, design, or completion contracts with their owning workflows.
A settled required test definition remains a pending evidence obligation until its selected verification establishes the specified case and expected outcome or its definition is revised through the owning workflow.

## Define required test cases

Specify the required test cases and expected outcomes at the granularity guaranteed by the governing requirements and design for the defined test conditions.
Fix exact values, counts, positions, sequences, complete collections, names, wording, and representations only when those properties are established by the guarantee and test conditions. Otherwise, constrain expectations to the relevant properties and relationships.
For numeric outcomes, distinguish exact-value guarantees from floating-point results whose rounding can vary with operation order, including parallel reductions. Specify guaranteed invariants or justified absolute and/or relative tolerances based on the required accuracy and value scale; use exact equality when the contract requires it. Specify the treatment of non-finite values when relevant, and keep tolerances narrow enough to detect meaningful numerical violations.
Consider whether a valid refactoring, extension, or rewording preserving the tested guarantee could change an expected outcome. If so, refine the expectation to remain valid under that change without weakening the guarantee being tested.
Define boundary coverage, combinations, regression scope, validation methods, and test-support constraints when they materially affect whether the evidence is sufficient.
For broad verification or exact properties named by a settled completion criterion, require traceability to the governing requirements or design. Return a criterion that lacks that traceability to [`plan-driven-planning`](https://github.com/supersovaa/plan-driven-implementation/blob/main/skills/plan-driven-planning/SKILL.md) for correction before deriving or revising dependent required test definitions.

Use requirement cases for externally meaningful behavior, outcomes, constraints, and other requirement-level guarantees.
Use design cases for APIs, invariants, type guarantees, responsibility boundaries, and other established design contracts.

Keep the definitions about what must be established.
Leave test framework mechanics, fixture implementation, test decomposition, and assertion structure to test implementation unless a settled constraint requires them.

## Prohibit high-volume repetition

Do not plan, retain, implement, or execute high-volume repetition as test evidence. This includes bulk randomized draws or allocations, seed sweeps, repeated save/restore or real connections, and large generated or parameterized case combinations, even inside a single local unit test. A 10,000-allocation loop is prohibited; that example is not a numerical threshold permitting slightly smaller loops.
Apply this rule to temporary, provisional, manual, and CI verification, including definitions already present in a settled plan or current test design. Fast execution, a fixed seed, a timeout, or splitting work across tests, commands, or workers does not authorize the method. Assess the combined repetition across those boundaries.

Select the narrowest sufficient method and a small bounded set of cases by comparing the required guarantee, lighter evidence, and total work. Prefer inspection, deterministic unit or component tests, focused state transitions, controlled results, and reusable evidence; select complete games, simulations, or other end-to-end trials only for a concrete violation that depends on the complete lifecycle or actual integration. Account for case count times repetitions and the setup, allocation, serialization, I/O, and connection work performed within them.
Tie each varied condition to a guarantee or concrete violation. Use representative cases for independent conditions; combine them only when an interaction or boundary creates a distinct violation those cases would miss. For randomized behavior, use controlled draws and deterministic boundary or invariant checks. Verify save/restore and real integration at the scale each guarantee requires. Use controlled results or counting substitutes to check large-count inputs and dispatch behavior without performing that many real operations. Do not add sample counts or statistical acceptance bands merely to gain confidence through repetition.

If a settled requirement or design specifically requires a statistical, load, or scale guarantee that focused checks cannot establish, keep that obligation pending and return the verification decision to the workflow owning that requirement or design before implementation or execution. Do not silently weaken the guarantee or treat the existing definition as an exception to this prohibition.

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

For new verification, settle the required test cases, expected outcomes, evidence lifetimes, and validation scope in the test plan before target implementation begins.
For reassessment of introduced verification, record the revised cases and decisions in the current test design and update references from any affected implementation plan.
Use the repository's established format for required test definitions when one exists.

For plan-governed work, keep the authoritative definitions in repository-persistent documentation and link them from the implementation plan's completion criteria before execution readiness. Resolve those links to the test plan for pending verification and to current test design for introduced verification.

When linking test definitions in implementation plans or editing their planning indexes, follow [`plan-driven-planning`](https://github.com/supersovaa/plan-driven-implementation/blob/main/skills/plan-driven-planning/SKILL.md) for current planning facts and their derived views in those documents.

For new verification without an implementation plan, record a concise test plan in the established work context. Keep plans for continuing tests in repository documentation and use the current work context for bounded temporary verification.

Apply the written-accountability rules in [`test-lifecycle`](https://github.com/supersovaa/test-lifecycle/blob/main/SKILL.md). Test planning owns the explanation before introduction; test implementation establishes the current test design when introducing tests or manual procedures. Keep the plan's remaining references aligned with that handoff.

Record for each guarantee and required verification example in the selected verification scope the sufficient existing tests and supporting coverage, or the uncovered cases, expected outcomes, and required new or expanded tests. For combined conditions, record the distinct interaction or boundary violation that requires the combination.
When existing evidence establishes all of them, record its sufficiency and complete test selection with that evidence.
Record the selected verification role and applicable completion or replacement condition. Apply `test-lifecycle` directly when a test reaches its retirement condition.
Record the selected method, its sufficiency, and the bounded scope in the same test plan or current test design.
Keep each definition traceable to the requirement or design guarantee it establishes.

## Hand off executable work

Hand the settled required test definitions to `test-evidence-implementation` for executable test establishment.

Use `test-evidence-review` to judge whether the implemented evidence sufficiently establishes the settled definitions.
Route review-discovered test-evidence gaps to `test-gap-remediation`.

This skill owns concrete test-evidence planning and reassessment of test definitions, applying lifecycle policy owned by `test-lifecycle`.
Executable test creation, reuse, and retirement belong to `test-evidence-implementation`.
Requirement definition, design definition, implementation planning, implementation execution, and general implementation review remain with their owning workflows.
