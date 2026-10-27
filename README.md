# Test Evidence Skills

A lightweight six-skill set for planning, implementing, preserving, reviewing, and repairing executable evidence of already-settled requirements and design, plus selecting verification that may involve costly end-to-end trials.

## Core idea

Requirements and design define the guarantees.
Test planning selects sufficient executable evidence and reassesses its retention as coverage changes.
Executable tests establish those guarantees while leaving incidental implementation choices free to change. Their pass/fail assertions must also accept outcomes permitted by the settled contracts.
Verification that may launch real end-to-end trials first receives an evidence-based necessity decision; justified runs use explicit bounds sized to the remaining guarantee and available resources.

The workflow separates test-evidence planning, executable test implementation, preservation during behavior-preserving refactoring, focused review of evidence sufficiency and assertion scope, and repair of identified evidence gaps.

## Skills

- [`test-evidence-planning`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/planning/SKILL.md) — plan or reassess sufficient required evidence, reuse established coverage, decide retention and retirement, and distinguish ongoing guarantees, provisional substitutes, and temporary diagnostic checks.
- [`test-evidence-implementation`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/implementation/SKILL.md) — establish executable evidence with assertions bounded by settled guarantees, retire incidental checks, and consolidate redundant coverage.
- [`test-execution-budget`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/execution/SKILL.md) — before selecting verification commands that may launch real game or simulation trials, prefer zero-trial evidence when sufficient and bound necessary runs by evidence need and resource cost.
- [`test-evidence-preservation`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/preservation/SKILL.md) — preserve still-applicable requirement and design guarantees when behavior-preserving refactoring changes tests.
- [`test-evidence-review`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/review/SKILL.md) — judge both evidence sufficiency and whether executable assertions impose requirements beyond settled test definitions.
- [`test-gap-remediation`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/remediation/SKILL.md) — close missing or insufficient executable evidence identified during review.

## Responsibility boundaries

`test-evidence-planning` owns deciding and reassessing what evidence is required long-term, what may provisionally stand in for it, and what is only a temporary diagnostic check.
`test-evidence-implementation` owns establishing executable tests from settled definitions, replacing provisional tests, and retiring temporary, incidental, or redundant artifacts while retaining sufficient required evidence.
`test-execution-budget` owns the necessity gate and bounded execution of justified real trials; the selection and reassessment of required test evidence remain with test planning, and recurring CI execution with `ci-execution-efficiency`.

Implementation planning owns the implementation boundary and completion contract.
For plan-governed work, required test definitions are bounded by that contract and linked from the implementation plan before execution readiness.
Requirement and design workflows own the authoritative behavior and contracts.

`test-evidence-review` checks coverage sufficiency and unsupported assertion restrictions within another review workflow's existing scope.
The surrounding review workflow continues to own its review scope, acceptance decisions, and findings outside this focused concern.

These testing skills plan, establish, preserve, review, or restore executable evidence without taking ownership of requirement definition, design definition, implementation execution, or general implementation review.

## Setup

For each work type, link the needed public `SKILL.md` definitions above directly from its existing guidance entry point, such as `AGENTS.md` or a task-specific `SKILL.md`.
Read and apply the linked skills when that work begins.
Keep local guidance focused on activation and responsibility; the public skill definitions in this repository remain the authority for the detailed rules.

## Files

- `skills/planning/SKILL.md` — `test-evidence-planning`.
- `skills/implementation/SKILL.md` — `test-evidence-implementation`.
- `skills/execution/SKILL.md` — `test-execution-budget`.
- `skills/preservation/SKILL.md` — `test-evidence-preservation`.
- `skills/review/SKILL.md` — `test-evidence-review`.
- `skills/remediation/SKILL.md` — `test-gap-remediation`.
- `README.md` — repository-level responsibility map.
- `LICENSE` — MIT License.
