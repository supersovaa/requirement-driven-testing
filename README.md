# Test Evidence Skills

A lightweight six-skill set for planning, implementing, preserving, reviewing, and repairing automated or manual evidence of already-settled requirements and design, plus selecting verification that may involve costly end-to-end trials.

## Core idea

Requirements and design define the guarantees.
Test planning applies [test-lifecycle](https://github.com/supersovaa/test-lifecycle/blob/main/SKILL.md) to select the verification role, then settles concrete cases, expected outcomes, and validation scope before target implementation begins.
Selected automated tests and manual procedures establish those cases while leaving incidental implementation choices free to change. The test plan explains verification before introduction, and the current test design explains it afterward, following `test-lifecycle`.
Verification that may launch real end-to-end trials first receives an evidence-based necessity decision; justified runs use explicit bounds sized to the remaining guarantee and available resources.
Test planning owns verification-method selection and the prohibition on high-volume repetition. Implementation, execution, preservation, review, and remediation apply that rule to both new and previously settled verification.

Continuing verification follows lifecycle decisions. During refactoring, preservation checks actual test discovery for retained automated evidence. Staged implementation keeps complete verification obligations explicit while substitute evidence is in use.

The workflow separates test-evidence planning, executable test implementation, preservation during behavior-preserving refactoring, focused review of evidence sufficiency, assertion scope, and processing cost, and repair of identified evidence gaps.

## Skills

- [`test-evidence-planning`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/planning/SKILL.md) — plan or reassess concrete verification for settled guarantees or current diagnostic work, applying `test-lifecycle` for classification and retention.
- [`test-evidence-implementation`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/implementation/SKILL.md) — implement selected automated or manual verification and its test design, including temporary checks, provisional evidence, consolidation, and retirement.
- [`test-execution-budget`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/execution/SKILL.md) — use when selecting or running verification for games, simulators, episode-based systems, or other work that may run costly end-to-end trials. If complete trials are possible, assess necessity and bound justified runs.
- [`test-evidence-preservation`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/preservation/SKILL.md) — preserve still-applicable requirement and design guarantees and verify discovered executable tests when behavior-preserving refactoring restructures tests.
- [`test-evidence-review`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/review/SKILL.md) — review automated or manual evidence against the test plan or current test design for sufficient coverage, unsupported pass/fail restrictions, prohibited repetition, and unnecessary processing cost.
- [`test-gap-remediation`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/remediation/SKILL.md) — close missing or insufficient automated or manual evidence identified during review.

## Responsibility boundaries

[test-lifecycle](https://github.com/supersovaa/test-lifecycle/blob/main/SKILL.md) owns lifecycle classification, written accountability, CI admission and retention, and retirement conditions.
`test-evidence-planning` owns concrete cases and expected outcomes within the selected verification role.
`test-evidence-implementation` owns implementing that verification, establishing and maintaining its test design, and performing the selected cleanup.
`test-execution-budget` owns the necessity gate and bounded execution of justified real trials; the selection and reassessment of required test evidence remain with test planning, and CI selection and configuration with `ci-execution-efficiency`.

Implementation planning owns the implementation boundary, completion contract, and dependency-based ordering of implementation and executable test establishment.
For plan-governed work, required test definitions are bounded by that contract and linked from the implementation plan before execution readiness.
Requirement and design workflows own the authoritative behavior and contracts.

`test-evidence-preservation` owns retaining executable evidence and confirming that affected tests remain discoverable through refactoring. The implementation workflow owns restructuring and the resulting code changes.
`test-evidence-review` checks coverage sufficiency, unsupported assertion restrictions, prohibited repetition, and unnecessary processing cost within another review workflow's existing scope.
The surrounding review workflow continues to own its review scope, acceptance decisions, and findings outside this focused concern.

These testing skills plan, establish, preserve, review, or restore selected automated or manual evidence without taking ownership of requirement definition, design definition, implementation execution, or general implementation review.

## Setup

For each work type, link the needed public `SKILL.md` definitions above directly from its existing guidance entry point, such as `AGENTS.md` or a task-specific `SKILL.md`.
Read and apply the linked skills when that work begins, including `test-lifecycle` at the planning, implementation, preservation, review, and remediation entry points that reference it.
At each repository planning, implementation, testing, and review guidance entry point, directly link [`ci-execution-efficiency`](https://github.com/supersovaa/ci-efficiency/blob/main/skills/execution/SKILL.md) and activate it for additions or expansions to automatically collected tests, including when CI workflow files stay unchanged. Use its existing rules to assess recurring execution cost.
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
