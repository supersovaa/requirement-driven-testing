---
name: test-evidence-review
description: Review automated or manual test evidence against the test plan or current test design for sufficient coverage, unsupported pass/fail restrictions, prohibited repetition, and unnecessary processing cost.
---

# Test Evidence Review

Use this skill when a review needs to judge automated or manual test evidence against the test plan or current test design for sufficient coverage, unsupported pass/fail restrictions, prohibited repetition, and unnecessary processing cost.
Apply it within the surrounding review workflow's existing scope when another review workflow already governs the work.

Apply [`test-lifecycle`](https://github.com/supersovaa/test-lifecycle/blob/main/SKILL.md) when reviewing lifecycle decisions, documentation ownership, and retirement in the current scope.
Treat settled product requirements and design contracts as authority, the test plan as the contract for pending verification, and current test design as the contract for introduced verification.
When independently selecting or executing verification, apply the [prohibition on high-volume repetition](../planning/SKILL.md#prohibit-high-volume-repetition), including for unchanged tests reused as evidence. For verification that may launch real complete games, simulations, episodes, or similarly costly end-to-end trials, also apply [`test-execution-budget`](../execution/SKILL.md) before selecting commands.

## Establish the review authority

Use the settled test plan for pending verification and the current test design for introduced tests or manual procedures within the review scope.

When work is governed by an implementation plan, use the required test definitions linked to that plan boundary.

Return missing planning decisions to `test-evidence-planning` and missing current test design to `test-evidence-implementation`.
When a settled test definition conflicts with applicable settled requirements or design, apply the authority rules below and return the definition mismatch to `test-evidence-planning`.

Requirements take precedence over design, tests, and implementation.
Return design that conflicts with a settled requirement to the workflow that owns design.
When settled requirements or design do not determine an expected outcome, return that ambiguity to its owning workflow rather than treating it as a test-evidence gap.

## Review evidence sufficiency

For each required case, identify the selected automated or manual evidence intended to establish it.
For tests added or materially changed in the review scope, confirm that planning selected their verification role within the applicable work boundary and that their explanations meet `test-lifecycle`. Route missing planning decisions to `test-evidence-planning`, and missing or stale test design to `test-evidence-implementation`.

Treat the evidence as sufficient only when the automated assertions or manual execution actually establish the case and expected outcome.
Incidental execution of a code path is not evidence for a guarantee the test does not verify, and an assertion on a path or mode outside the settled consumer contracts is not evidence for any guarantee.

Accept combined or shared tests when they collectively establish the required cases.
Apply the [selection and retention criteria](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/planning/SKILL.md#select-sufficient-ongoing-evidence) before requesting additional or restored tests.
Return over-specified or redundant required test definitions to `test-evidence-planning`, identifying the governing guarantee and the existing evidence that remains sufficient.

Apply the settled validation scope, boundary coverage, combinations, regression scope, validation methods, and test-support constraints that govern the reviewed definitions.

Identify evidence as missing or insufficient when a currently required case lacks the selected verification strong enough to detect its violation. Apply settled retirement conditions without demanding replacement coverage or a deletion rationale for tests whose role has ended.

## Review repetition and processing cost

Apply the [prohibition on high-volume repetition](../planning/SKILL.md#prohibit-high-volume-repetition) to added or changed tests and their governing definitions, even when the implementation exactly follows a settled plan. Inspect loops, generated cases, seed sweeps, and repeated fixture, save/restore, and connection work across the affected tests; test count and passing results do not establish proportionate verification.
Return prohibited repetition or unnecessary processing prescribed by the test plan or current test design to `test-evidence-planning`, identifying the guarantee and the focused evidence that can replace it, or the unresolved verification decision. Route excess work introduced only by fixtures, helpers, or test implementation to `test-evidence-implementation` for correction within the selected scope. Keep any guarantee not yet established visible as pending.
When reviewing additions or expansions to automatically collected tests, apply [`ci-execution-efficiency`](https://github.com/supersovaa/ci-efficiency/blob/main/skills/execution/SKILL.md) to recurring execution cost, including when CI workflow files stay unchanged. Keep acceptance decisions and the applicable blocking threshold with the surrounding review workflow.

## Review assertion scope as well as sufficiency

For tests added or changed within the review scope, inspect whether their pass/fail assertions also reject behavior permitted by the settled requirement, design, and required test case. Compare them with the documented permissible variations and request narrower assertions when valid changes would be rejected. A passing test can still contain an unjustified stronger expectation.

Check complete equality of separate data formats, execution paths, metadata, shared tables, ordering, and internal identifiers against the actual guarantee and the uses each path's settled consumer contract requires. When the settled test case requires only common meaning or a source relationship, assess assertions against those facts. Require representation-specific checks only when that case also includes those guarantees under the corresponding settled contracts. Treat unsupported restrictions as test correctness findings and request their removal or narrowing in the current change before accepting its tests as evidence.
For numeric assertions, including floating-point calculations affected by parallel reductions, verify that exact comparisons, invariants, tolerances, and non-finite handling follow the [planned numeric expectations](../planning/SKILL.md#define-required-test-cases) and still detect meaningful numerical violations.

When the required test definition itself contains the unsupported restriction, refer that definition to `test-evidence-planning`. Keep the surrounding review workflow responsible for acceptance and the applicable blocking threshold.

## Keep findings in their owning workflow

Report each test-evidence gap with the settled required case, the concrete guarantee violation the current evidence would miss, and why that evidence is insufficient.

Route an established test-evidence gap to `test-gap-remediation`.
When sufficient evidence instead exposes incorrect implementation behavior, return that defect to the workflow that owns implementation review or execution.

This skill provides focused criteria for reviewing executable evidence sufficiency, assertion scope, repetition, and processing cost.
Test-evidence planning belongs to `test-evidence-planning`.
The surrounding review workflow retains ownership of its review scope, acceptance decisions, and other findings.
This skill does not define requirements or design, plan required test cases, repair tests, implement production behavior, or replace general implementation review.
