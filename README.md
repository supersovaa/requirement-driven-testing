# Requirement-Driven Testing Skills

A lightweight three-skill set for treating tests as executable evidence of already-settled requirements and design.

## Core idea

Tests establish evidence for requirements and design contracts.
They do not define those requirements or contracts.

The workflow separates ordinary test establishment, preservation during behavior-preserving refactoring, and repair of evidence gaps found by review.

## Skills

- `requirement-driven-testing` — establish or reuse executable test evidence during implementation, treating plan-linked durable required tests as completion-required while allowing provisional validation to remain non-durable.
- `test-evidence-preservation` — preserve still-applicable requirement and design guarantees when behavior-preserving refactoring changes tests.
- `test-gap-remediation` — close missing or insufficient executable evidence reported by implementation review.

## Responsibility boundaries

For plan-governed work, implementation planning owns the complete set of test cases and expected outcomes required for durable guarantees.
Provisional or intermediate results may use temporary tests or other sufficient validation without automatically becoming completion-required regression guarantees.
Requirement and design workflows own the authoritative behavior and contracts.
Implementation review owns identifying review findings.
These testing skills establish, preserve, or restore executable evidence without taking ownership of those upstream decisions.

## Files

- `skills/implementation/SKILL.md` — `requirement-driven-testing`.
- `skills/preservation/SKILL.md` — `test-evidence-preservation`.
- `skills/remediation/SKILL.md` — `test-gap-remediation`.
- `README.md` — repository-level responsibility map.
- `LICENSE` — MIT License.
