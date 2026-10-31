---
name: test-evidence-implementation
description: Apply settled evidence-lifetime decisions by establishing or reusing ongoing executable evidence, keeping temporary diagnostic verification bounded, replacing provisional evidence, and consolidating incidental or redundant coverage.
---

# Test Evidence Implementation

Use this skill when implementing settled test-evidence decisions, including establishing ongoing evidence, carrying out bounded temporary diagnostic verification, replacing provisional evidence, narrowing incidental assertions, or consolidating redundant tests.

Treat required test definitions as implementation inputs for ongoing and provisional evidence. For temporary diagnostic verification, use its scope and completion boundary from the current work context.
When selecting or executing verification that may launch real complete games, simulations, episodes, or similarly costly end-to-end trials, apply [`test-execution-budget`](../execution/SKILL.md) before selecting commands to determine whether those trials are necessary and to bound justified execution.
Test planning belongs to `test-evidence-planning`.

## Consume settled test definitions

When establishing required evidence, use the test cases, expected outcomes, and evidence-lifetime decisions settled by `test-evidence-planning`.

When establishing required evidence under an implementation plan, implement the required test definitions linked to the current plan boundary.
Keep additions and expansions of persistent executable tests within the settled required definitions and current work boundary. Route any newly discovered need for distinct ongoing coverage to `test-evidence-planning` for selection and recording before implementing it.
Apply the settled validation scope, boundary coverage, combinations, regression scope, validation methods, and test-support constraints that govern those definitions.

Return absent or incomplete settled definitions for required evidence to `test-evidence-planning`.
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

Use exact object equality, metadata collections, ordering, reference identifiers, or other complete comparisons only when the settled guarantee requires those properties. When separate representations describe the same event, compare the common facts and source relationships required by the settled test case. Check representation-specific properties only when that case requires them under their respective settled contracts. A convenient current representation is not authority for additional pass/fail conditions.

Narrow an incidental assertion within the settled test definition before marking the evidence complete. When a stronger guarantee appears necessary, return that decision to `test-evidence-planning` rather than silently expanding the required test.

## Implement according to evidence lifetime

Inspect existing tests before adding ongoing evidence.
Use an existing test when it already establishes the required case and expected outcome.
Treat incidental path execution as insufficient when the test does not actually establish that guarantee.

For ongoing evidence, keep sufficient executable coverage for each continuing guarantee and consolidate redundant tests according to the settled planning decision.
For temporary diagnostic verification, prefer transient commands or scratch artifacts that stay outside the persistent test suite. When the verification needs a repository artifact, keep that artifact scoped to the current work and clear it at the settled completion boundary.
For provisional evidence, keep the substitute only while its settled replacement condition applies, then establish the complete evidence and discharge the pending verification obligation.

Treat defect reproduction as evidence-lifetime neutral: its lifetime comes from the settled guarantee it establishes.
Retire incidental assertions as directed by the settled planning decision.
Return missing lifetime decisions and over-specified required definitions to `test-evidence-planning` before changing their obligations.

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
Keep the repository documentation's identification of ongoing executable evidence aligned with tests added, materially changed, consolidated, replaced, or retired. Use the existing test names, files, or coherent groups to identify evidence at the granularity needed to distinguish its guarantees. Preserve the single authoritative explanation in settled test documentation and use documentation-side references; test source needs only the code and naming required to express the test.

This skill owns executable test establishment and lifecycle handling from settled test definitions and evidence-lifetime decisions.
Test-evidence planning belongs to `test-evidence-planning`.
Behavior-preserving evidence retention belongs to `test-evidence-preservation`.
Use `test-evidence-review` when a focused review of test-evidence sufficiency is needed.
Review-discovered evidence repair belongs to `test-gap-remediation`.
Requirement definition, design definition, implementation planning, implementation execution, and general implementation review remain with their owning workflows.
