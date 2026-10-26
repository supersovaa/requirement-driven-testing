---
name: test-evidence-review
description: Provide focused review criteria for whether settled required test definitions have sufficient executable evidence, identifying evidence gaps without planning new test cases or repairing the tests.
---

# Test Evidence Review

Use this skill when a review needs to judge whether settled required test definitions have sufficient executable test evidence.
Apply it within the surrounding review workflow's existing scope when another review workflow already governs the work.

Treat settled requirements and design contracts as authority, required test definitions as the review contract, and executable tests as evidence.
When independently executing or rerunning tests that launch repeated complete games, simulations, episodes, or other end-to-end trials, apply [`test-execution-budget`](../execution/SKILL.md).

## Establish the review authority

Use the settled required test definitions produced by `test-evidence-planning` that fall within the current review scope.

When work is governed by an implementation plan, use the required test definitions linked to that plan boundary.

Return missing required test definitions, missing expected outcomes, or incomplete material testing decisions to `test-evidence-planning`.
When a settled test definition conflicts with applicable settled requirements or design, apply the authority rules below and return the definition mismatch to `test-evidence-planning`.

Requirements take precedence over design, tests, and implementation.
Return design that conflicts with a settled requirement to the workflow that owns design.
When settled requirements or design do not determine an expected outcome, return that ambiguity to its owning workflow rather than treating it as a test-evidence gap.

## Review evidence sufficiency

For each required case, identify the executable test evidence intended to establish it.

Treat the evidence as sufficient only when the relevant test behavior and assertions actually establish the case and expected outcome.
Incidental execution of a code path is not evidence for a guarantee the test does not verify.

Accept combined or shared tests when they collectively establish the required cases.
Apply the [selection and retention criteria](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/planning/SKILL.md#select-and-retain-sufficient-evidence) before requesting additional or restored tests.
Return over-specified or redundant required test definitions to `test-evidence-planning`, identifying the governing guarantee and the existing evidence that remains sufficient.

Apply the settled validation scope, boundary coverage, combinations, regression scope, validation methods, and test-support constraints that govern the reviewed definitions.

Identify evidence as missing or insufficient when a settled required case lacks executable coverage strong enough to detect a violation.

## Keep findings in their owning workflow

Report each test-evidence gap with the settled required case, the concrete guarantee violation the current evidence would miss, and why that evidence is insufficient.

Route an established test-evidence gap to `test-gap-remediation`.
When sufficient evidence instead exposes incorrect implementation behavior, return that defect to the workflow that owns implementation review or execution.

This skill provides dedicated criteria for review of executable test-evidence sufficiency.
Test-evidence planning belongs to `test-evidence-planning`.
The surrounding review workflow retains ownership of its review scope, acceptance decisions, and other findings.
This skill does not define requirements or design, plan required test cases, repair tests, implement production behavior, or replace general implementation review.
