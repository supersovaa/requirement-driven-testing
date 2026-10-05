---
name: test-evidence-review
description: Provide focused review criteria for whether settled requirements and design contracts have sufficient executable test evidence, identifying evidence gaps without inventing new behavior or repairing the tests.
---

# Test Evidence Review

Use this skill when a review needs to judge whether behavior governed by settled requirements or design has sufficient executable test evidence.
Apply it within the surrounding review workflow's existing scope when another review workflow already governs the work.

Treat requirements and design contracts as authority and tests as evidence of that authority.

## Establish the review authority

When work is governed by an implementation plan, use the linked required test definitions and expected outcomes that fall within the current review scope as the applicable review set.

Within that scope, return missing linked definitions, missing completion-required cases, or missing expected outcomes to the planning workflow.
When a linked definition conflicts with applicable settled requirements or design, apply the authority rules below and return any remaining definition mismatch to the planning workflow.

When no implementation plan governs the work, derive the review set from settled requirements and design within the current review scope.

Requirements take precedence over design, tests, and implementation.
Return design that conflicts with a settled requirement to the workflow that owns design.
When settled requirements or design do not determine an expected outcome, return that ambiguity to its owning workflow rather than treating it as a test-evidence gap.

## Review evidence sufficiency

For each applicable guarantee, identify the executable test evidence intended to establish it.

Treat the evidence as sufficient only when the relevant test behavior and assertions actually establish the guarantee.
Incidental execution of a code path is not evidence for a guarantee the test does not verify.

Consider multiple tests together when they collectively establish the guarantee.
Do not require duplicate tests or a one-to-one mapping between guarantees and test functions.

Apply plan-level decisions for validation scope, boundary coverage, combinations, regression scope, validation methods, and test-support constraints when they govern the work.

Identify evidence as missing or insufficient when an established guarantee lacks executable coverage strong enough to detect a violation.

## Keep findings in their owning workflow

Report each test-evidence gap with the established guarantee it concerns and why the current evidence is insufficient.

Route an established test-evidence gap to `test-gap-remediation`.
When sufficient evidence instead exposes incorrect implementation behavior, return that defect to the workflow that owns implementation review or execution.

This skill provides dedicated criteria for review of executable test-evidence sufficiency.
The surrounding review workflow retains ownership of its review scope, acceptance decisions, and other findings.
This skill does not define requirements or design, repair tests, implement production behavior, or replace general implementation review.
