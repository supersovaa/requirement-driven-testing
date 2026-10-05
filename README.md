# Requirement-Driven Testing Skills

A lightweight four-skill set for treating tests as executable evidence of already-settled requirements and design.

## Core idea

Tests establish evidence for requirements and design contracts.
They do not define those requirements or contracts.

The workflow separates ordinary test establishment, preservation during behavior-preserving refactoring, review of evidence sufficiency, and repair of identified evidence gaps.

## Skills

- `requirement-driven-testing` — establish or reuse executable test evidence during implementation, including plan-linked required test cases and pre-implementation test execution.
- `test-evidence-preservation` — preserve still-applicable requirement and design guarantees when behavior-preserving refactoring changes tests.
- `test-evidence-review` — review whether settled requirements and design contracts have sufficient executable test evidence and identify evidence gaps.
- `test-gap-remediation` — close missing or insufficient executable evidence identified by test-evidence review.

## Responsibility boundaries

For plan-governed work, implementation planning owns the complete set of test cases and expected outcomes required for plan completion.
Requirement and design workflows own the authoritative behavior and contracts.
`test-evidence-review` owns judging whether the applicable settled guarantees have sufficient executable evidence.
General implementation review owns findings outside test-evidence sufficiency.
These testing skills establish, preserve, review, or restore executable evidence without taking ownership of upstream requirement, design, or planning decisions.

## Files

- `skills/implementation/SKILL.md` — `requirement-driven-testing`.
- `skills/preservation/SKILL.md` — `test-evidence-preservation`.
- `skills/review/SKILL.md` — `test-evidence-review`.
- `skills/remediation/SKILL.md` — `test-gap-remediation`.
- `README.md` — repository-level responsibility map.
- `LICENSE` — MIT License.
