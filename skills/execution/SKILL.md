---
name: test-execution-budget
description: Decide whether real end-to-end simulations or trials are needed for verification, then bound necessary runs, including indirect and automated test execution.
---

# Test Execution Budget

Use this skill before running or rerunning a real complete game, simulation, episode, or similarly costly end-to-end trial for verification. Apply it to direct commands and test runners that launch such work indirectly, including a single trial.

## Establish whether real trials are necessary

Identify the specific settled guarantee or diagnostic question, the failure to detect, and relevant existing evidence. Compare real trials with source or contract inspection, compilation, deterministic unit or component tests, controlled fixtures, injected results, and reusable verified evidence.

**Choose zero complete trials** when a lighter method establishes the same guarantee. For example, verify large trial-count inputs, dispatch counts, progress reporting, aggregation, and stop handling using controlled results or a counting substitute when these establish the contract.

Select real trials when the outstanding guarantee depends on actual game-state transitions, full-path interactions, or statistical behavior that requires real sampling. For every selected real trial, identify the evidence that a zero-trial method leaves uncovered. Existing loops, a broad test command, and a large number in an example are prompts to examine the assertions and the owning guarantee, rather than sufficient evidence of the need to run games.

Treat settled required test definitions as obligations. When a required definition prescribes real trials but an equivalent lighter method appears sufficient, return the proposed change to `test-evidence-planning` for reassessment; preserve the original requirement as pending until revised or verified. Keep requirement or design changes with their owning workflow.

## Bound the necessary execution

Inspect selected commands, test definitions, runners, and configuration to determine the maximum number of complete trials. Include loops inside tests, multiple targets, parameterized cases, parallel workers, retries, and trials already performed for the current work unit.

Use **10 complete end-to-end trials per work unit** as the default cumulative autonomous execution ceiling, applied only after the need for real trials is established. Choose the smallest number sufficient for the identified guarantee, starting with a single targeted trial when appropriate. Count each complete game or equivalent end-to-end trial once, regardless of how many test processes launch it.

Choose commands that stay within the remaining authorized trial budget. Resolve uncertain counts by inspecting source or configuration, listing tests, or using a dry run before execution. Use trial caps and timeouts supported by the runner.

Reuse previously successful evidence when its inputs and guarantees remain applicable. Count diagnostic reruns and retries against the same budget.

## Escalate justified large runs

For verification requiring more than the remaining autonomous budget, identify the governing guarantee, explain the additional evidence supplied by actual trials beyond lighter checks, and state the proposed total trial count and estimated resource or time cost when available. Obtain explicit user authorization for the bounded run.

A requirement, design example, implementation plan, or generated test specifying a large count establishes a potential verification obligation; explicit authorization governs autonomous spending beyond the default ceiling. Reuse existing user authorization when its scope and bound cover the proposed run.

When authorization or reassessment is pending, report completed lighter evidence and the outstanding verification separately. Treat a required real-trial verification as complete when sufficient executable evidence has been established.

## Responsibility boundary

This skill governs the necessity decision before trial execution and the budget for justified trials. `test-evidence-planning` owns required coverage, validation methods, and reassessment of settled test definitions; `test-evidence-implementation` owns executable test establishment; `ci-execution-efficiency` owns CI selection and configuration.

Skill guidance constrains agent decisions. For unattended or automatically triggered execution needing a mechanically enforced ceiling, implement the corresponding limit in the test runner, script, or CI configuration through its owning implementation workflow.
