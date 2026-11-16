---
name: test-evidence-implementation
description: Implement settled automated or manual test verification and its test design, including temporary checks, provisional evidence, consolidation, and retirement under selected lifecycle decisions.
---

# Test Evidence Implementation

Use this skill when implementing settled automated or manual test verification and its test design, including temporary checks, provisional evidence, consolidation, and retirement under selected lifecycle decisions.

Apply [`test-lifecycle`](https://github.com/supersovaa/test-lifecycle/blob/main/SKILL.md) when introducing, changing, or retiring tests and their test design.
Use the test plan for new verification and the current test design for introduced tests. Consume their selected role and completion or replacement condition.
When selecting or executing verification that may launch real complete games, simulations, episodes, or similarly costly end-to-end trials, apply [`test-execution-budget`](../execution/SKILL.md) before selecting commands to determine whether those trials are necessary and to bound justified execution.
Test planning belongs to `test-evidence-planning`.

When adding or expanding automatically collected tests, apply [`ci-execution-efficiency`](https://github.com/supersovaa/ci-efficiency/blob/main/skills/execution/SKILL.md), including when CI workflow files stay unchanged.

## Consume settled test definitions

Use settled cases, expected outcomes, and lifecycle decisions from the test plan for pending verification or from current test design for introduced verification, applying the [prohibition on high-volume repetition](../planning/SKILL.md#prohibit-high-volume-repetition) before implementation or execution.

When establishing required evidence under an implementation plan, implement the required test definitions linked to the current plan boundary.
Keep additions and expansions of persistent tests or manual procedures within the settled required definitions and current work boundary. Route any newly discovered need for distinct ongoing coverage to `test-evidence-planning` for selection and recording before implementing it.
Apply the settled validation scope, boundary coverage, combinations, regression scope, validation methods, and test-support constraints that govern those definitions. Keep fixtures and helpers within the selected bounded scope.

Return absent or incomplete planning decisions and definitions prescribing prohibited repetition or unnecessary processing to `test-evidence-planning` before implementing or executing their verification. Restore missing current test design under `test-lifecycle` before maintaining introduced verification.
Treat identification of additional required cases, expected outcomes, or material testing decisions as `test-evidence-planning` work.
When a settled test definition conflicts with applicable settled requirements or design, apply the authority rules below and return the definition mismatch to `test-evidence-planning`.
When settled requirements or design do not determine an expected outcome, return that ambiguity to its owning workflow.

## Keep requirement and design evidence distinct

Use requirement tests for cases that establish externally meaningful behavior, outcomes, constraints, and other requirement-level guarantees.
Use design tests for cases that establish APIs, invariants, type guarantees, responsibility boundaries, and other settled design contracts.

Requirements take precedence over design, tests, and implementation.
Return design that conflicts with a settled requirement to the workflow that owns design before relying on it as test authority.

Choose assertions using the [ongoing-evidence selection criteria](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/planning/SKILL.md#select-sufficient-ongoing-evidence) settled by `test-evidence-planning`.

## Keep pass/fail assertions within the settled guarantee

For each new or modified assertion that determines whether the tested behavior passes, identify the settled test case and requirement or design guarantee it establishes. Check both that the assertion detects the intended violation and that contract-valid outcomes remain accepted.

Use exact object equality, metadata collections, ordering, reference identifiers, or other complete comparisons only when the settled guarantee requires those properties. When separate representations or execution paths serve the same contract, compare the common facts and source relationships required by the settled test case, on each path only for the uses its settled consumer contract requires. Check representation- or path-specific properties only when that case requires them under their respective settled contracts. A convenient current representation is not authority for additional pass/fail conditions.
For numeric pass/fail assertions, follow the [planned numeric expectations](../planning/SKILL.md#define-required-test-cases) for ongoing and provisional evidence, or the current verification purpose and conditions for temporary diagnostics. Apply exact comparisons, invariants, tolerances, and non-finite handling as appropriate to floating-point rounding and operation-order variation, including parallel reductions.

Narrow an incidental assertion within the settled test definition before marking the evidence complete. When a stronger guarantee appears necessary, return that decision to `test-evidence-planning` rather than silently expanding the required test.

## Implement the selected verification role

Inspect existing tests or manual procedures and reuse sufficient evidence for the selected case and expected outcome.
Treat incidental path execution as insufficient when it does not establish the guarantee.
Apply the classification and retirement decisions from [`test-lifecycle`](https://github.com/supersovaa/test-lifecycle/blob/main/SKILL.md); implement manual procedures as manual verification and CI tests as ongoing automated protection.
For temporary verification, prefer transient commands or scratch artifacts and clear repository artifacts at their settled completion boundary.
For provisional evidence, establish the complete verification when its replacement condition is met, then discharge the pending obligation and remove the substitute.
Return missing material planning decisions to `test-evidence-planning`. Execute an already-settled retirement condition directly.

## Establish executable evidence from the test plan

For new verification, use the [required test definitions settled before target implementation](../planning/SKILL.md#record-the-planning-result). For introduced verification, use the current test design, including subsequent settled revisions.
Follow the governing implementation plan and dependencies to sequence executable test establishment and target implementation. For work without an implementation plan, coordinate that order with the implementation workflow within the current work boundary.

For each required case, add or reuse the selected automated test or manual procedure and assess its result against the settled expected outcome. When a test runs before the required behavior exists, confirm that its failure identifies the missing behavior or contract. When it passes on its first run, confirm that it genuinely establishes the required case.
Return implementation defects or remaining target behavior to the workflow that owns implementation execution.

Run the selected automated verification against the completed target implementation and carry out or obtain the required manual verification. Treat the evidence as complete when it satisfies the settled test definitions for the current work boundary, applying the planned provisional-evidence conditions for staged work.

## Use subtractive fixtures for staged implementation

When the current implementation boundary owns only part of a settled case grounded in a concrete source element and the complete source element is not yet executable, prefer a reduced fixture formed by removing only properties, behaviors, or components that are immaterial to the guarantee under test.

Preserve every precondition, interaction, and expected outcome material to the guarantee under test.
Do not add properties, behaviors, or interactions absent from the real source element when they affect the guarantee under test.

Treat the reduced fixture as executable evidence only for guarantees whose material conditions remain after the reduction.
Do not use it as evidence for a guarantee that depends on a removed part.
When such a guarantee enters completion scope, establish its evidence through the real source element.

## Distinguish test support from production dependencies

When fixtures, builders, deterministic inputs, or other test-support boundaries prevent a required test from being expressed, establish the minimum test support needed within any settled test-support constraints.

When the current implementation boundary still cannot execute meaningfully with the allowed test support, treat the missing production behavior as an implementation dependency and return it to the workflow that owns planning or execution readiness.

## Organize test files from the outset

When establishing new tests, organize distinct testing responsibilities or behavior groups into separate files from the start rather than waiting for files to grow.
Keep cases belonging to one coherent group together. A single file is sufficient for one coherent group; a file per test case is unnecessary.
Extract shared fixtures and helpers when multiple test files actually need them, within settled test-support constraints.

## Preserve repository conventions

Use the repository's established test framework, fixture structure, naming, placement, and traceability conventions.
Follow explicit repository conventions governing test-file grouping; otherwise apply the responsibility-based initial grouping above.
Use an existing documentation or mapping format when it can express the required relationship.
When introducing tests or manual procedures, establish their current test design under `test-lifecycle` and transfer explanatory responsibility from the test plan. Keep that design aligned with retained verification and remove obsolete references during retirement.

This skill owns implementing selected verification, establishing and maintaining its test design, and performing cleanup under lifecycle decisions owned by `test-lifecycle`.
Test-evidence planning belongs to `test-evidence-planning`.
Behavior-preserving evidence retention belongs to `test-evidence-preservation`.
Use `test-evidence-review` when a focused review of test-evidence sufficiency is needed.
Review-discovered evidence repair belongs to `test-gap-remediation`.
Requirement definition, design definition, implementation planning, implementation execution, and general implementation review remain with their owning workflows.
