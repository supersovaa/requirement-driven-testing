# Test Evidence Skills

A lightweight five-skill set for planning, implementing, preserving, reviewing, and repairing executable evidence of already-settled requirements and design.

## Core idea

Requirements and design define the guarantees.
Test planning defines the executable evidence required to establish those guarantees.
Executable tests implement that settled evidence contract.

The workflow separates test-evidence planning, executable test implementation, preservation during behavior-preserving refactoring, focused review of evidence sufficiency, and repair of identified evidence gaps.

## Skills

- `test-evidence-planning` — define required test cases, expected outcomes, coverage decisions, regression scope, validation methods, and test-support constraints from settled requirements and design.
- `test-evidence-implementation` — establish or reuse executable test evidence for settled required test definitions, including pre-implementation test execution.
- `test-evidence-preservation` — preserve still-applicable requirement and design guarantees when behavior-preserving refactoring changes tests.
- `test-evidence-review` — judge whether settled required test definitions have sufficient executable test evidence.
- `test-gap-remediation` — close missing or insufficient executable evidence identified during review.

## Responsibility boundaries

`test-evidence-planning` owns deciding what test evidence is required.
`test-evidence-implementation` owns turning those settled definitions into executable tests or reusing existing evidence that already satisfies them.

Implementation planning owns the implementation boundary and completion contract.
For plan-governed work, required test definitions are bounded by that contract and linked from the implementation plan before execution readiness.
Requirement and design workflows own the authoritative behavior and contracts.

`test-evidence-review` provides dedicated criteria for judging executable test-evidence sufficiency and may be applied within another review workflow's existing scope.
The surrounding review workflow continues to own its review scope, acceptance decisions, and findings outside this focused concern.

These testing skills plan, establish, preserve, review, or restore executable evidence without taking ownership of requirement definition, design definition, implementation execution, or general implementation review.

## Files

- `skills/planning/SKILL.md` — `test-evidence-planning`.
- `skills/implementation/SKILL.md` — `test-evidence-implementation`.
- `skills/preservation/SKILL.md` — `test-evidence-preservation`.
- `skills/review/SKILL.md` — `test-evidence-review`.
- `skills/remediation/SKILL.md` — `test-gap-remediation`.
- `README.md` — repository-level responsibility map.
- `LICENSE` — MIT License.
