# Test Evidence Skills

A lightweight six-skill set for planning, implementing, preserving, reviewing, and repairing executable evidence of already-settled requirements and design, plus selecting verification that may involve costly end-to-end trials.

## Core idea

Requirements and design define the guarantees.
Test planning classifies verification by lifetime and selects sufficient executable evidence for continuing guarantees.
Executable tests establish those guarantees while leaving incidental implementation choices free to change. Their pass/fail assertions must also accept outcomes permitted by the settled contracts. Repository test documentation records the guarantee, permissible variations, and motivating problem or evidence gap at a useful guarantee, group, or case level, identifying relevant executable evidence from the documentation side.
Verification that may launch real end-to-end trials first receives an evidence-based necessity decision; justified runs use explicit bounds sized to the remaining guarantee and available resources.

Ongoing evidence remains with continuing requirements and design guarantees. Temporary diagnostic verification ends with the current investigation or repair. Provisional evidence stands in until complete evidence becomes executable.

The workflow separates test-evidence planning, executable test implementation, preservation during behavior-preserving refactoring, focused review of evidence sufficiency and assertion scope, and repair of identified evidence gaps.

## Skills

- [`test-evidence-planning`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/planning/SKILL.md) — plan or reassess executable verification for settled guarantees or current diagnostic work, classifying it as ongoing, temporary diagnostic, or provisional.
- [`test-evidence-implementation`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/implementation/SKILL.md) — apply settled evidence lifetimes by establishing ongoing evidence, carrying out bounded temporary verification, replacing provisional evidence, and consolidating incidental or redundant coverage.
- [`test-execution-budget`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/execution/SKILL.md) — before selecting verification commands that may launch real game or simulation trials, prefer zero-trial evidence when sufficient and bound necessary runs by evidence need and resource cost.
- [`test-evidence-preservation`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/preservation/SKILL.md) — preserve still-applicable requirement and design guarantees when behavior-preserving refactoring changes tests.
- [`test-evidence-review`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/review/SKILL.md) — judge both evidence sufficiency and whether executable assertions impose requirements beyond settled test definitions.
- [`test-gap-remediation`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/remediation/SKILL.md) — close missing or insufficient executable evidence identified during review.

## Responsibility boundaries

`test-evidence-planning` owns the lifetime classification of verification and the sufficient evidence required for continuing guarantees.
`test-evidence-implementation` owns applying that classification: establishing ongoing evidence, completing temporary diagnostic verification at its boundary, replacing provisional evidence, and consolidating incidental or redundant artifacts.
`test-execution-budget` owns the necessity gate and bounded execution of justified real trials; the selection and reassessment of required test evidence remain with test planning, and CI selection and configuration with `ci-execution-efficiency`.

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
