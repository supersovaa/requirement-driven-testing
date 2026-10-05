---
name: test-evidence-preservation
description: Preserve the requirement and design guarantees intentionally established by existing tests when behavior-preserving refactoring changes test structure or placement.
---

# Test Evidence Preservation

Use this skill when behavior-preserving refactoring changes tests that already carry established requirement or design evidence.

Treat the guarantee established by a test as the thing to preserve, not the test's current structure.

## Identify established guarantees

Before changing an existing test, identify the requirement or design guarantee it intentionally establishes.
Distinguish authoritative guarantees from incidental assertions or implementation details.

Requirements remain authoritative over design, tests, and implementation.
When an existing test conflicts with settled requirements, return the conflict to the owning workflow instead of preserving the conflicting behavior as authority.

## Preserve equivalent evidence

Keep executable evidence for every still-applicable established guarantee affected by the refactoring.
The test may change framework usage, fixture shape, placement, decomposition, or assertion structure when the resulting evidence remains sufficient.

Reuse an existing replacement test when it already establishes the same guarantee.
Avoid duplicate coverage whose only purpose is to preserve the old test's form.

## Remove evidence only with changed authority

Weaken or remove an established guarantee only when its authoritative settled requirement or design contract has changed so that the guarantee no longer applies.

When the authoritative source is ambiguous, return that ambiguity to its owning workflow before discarding the evidence.

## Preserve repository conventions

Use the repository's established test framework, fixture structure, naming, placement, and traceability conventions.

This skill owns preserving executable test evidence during behavior-preserving refactoring.
Establishing new executable evidence during implementation belongs to `requirement-driven-testing`.
Review-discovered evidence repair belongs to `test-gap-remediation`.
