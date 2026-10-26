---
name: test-execution-budget
description: Choose verification for work that may exercise games, simulators, episodes, or costly end-to-end trials, assess whether real trials are necessary, and bound justified executions.
---

# Test Execution Budget

Use this skill when selecting or running verification for a game, simulator, episode, or other workflow that may launch costly complete end-to-end trials. Inspect broad test commands and indirect test runners before choosing an execution command, including when a single trial is proposed.

## Establish whether real trials are necessary

Identify the specific settled guarantee or diagnostic question, the failure to detect, and relevant existing evidence. Compare complete trials with source or contract inspection, compilation, deterministic unit or component tests, focused state-transition tests, controlled fixtures, injected results, and reusable verified evidence.

**Choose zero complete trials** when a lighter method establishes the same guarantee. For example, verify large trial-count inputs, dispatch counts, progress reporting, aggregation, and stop handling using controlled results or a counting substitute when these establish the contract.

Select complete real trials when the outstanding guarantee specifically depends on the complete game or episode lifecycle, an actual end-to-end integration path, or statistical observations requiring real sampling. Verify individual game-state transitions through focused tests when those establish the guarantee. For every selected complete trial, identify the evidence that a zero-trial method leaves uncovered. Existing loops, a broad test command, and a large number in an example prompt examination of the assertions and owning guarantee.

Treat settled required test definitions as obligations. When a required definition prescribes real trials but an equivalent lighter method appears sufficient, return the proposed change to `test-evidence-planning` for reassessment; preserve the original requirement as pending until revised or verified. Keep requirement or design changes with their owning workflow.

## Bound the necessary execution

Inspect candidate commands, test definitions, runners, and configuration to determine the maximum number of complete trial attempts they could start. Include loops inside tests, multiple targets, parameterized cases, parallel workers, automatic retries, and attempts already started for the same requested task or PR verification, including by other workers or agents.

Use **10 started end-to-end trial attempts per requested task or PR verification** as the default cumulative autonomous execution ceiling, applied only after the need for real trials is established. Choose the smallest number sufficient for the identified guarantee, starting with a single targeted trial when appropriate. Count each started attempt, including failed, interrupted, and timed-out runs, once.

Choose commands that stay within the remaining authorized trial budget across all selected runners and workers. Resolve uncertain attempt counts by inspecting source or configuration, listing tests, or using a dry run before execution. Use trial caps and timeouts supported by the runner.

Reuse previously successful evidence when its inputs and guarantees remain applicable. Count diagnostic reruns and retries against the same budget.

## Escalate justified large runs

For verification requiring more than the remaining autonomous budget, identify the governing guarantee, explain the additional evidence supplied by actual trials beyond lighter checks, and state the proposed total trial count and estimated resource or time cost when available. Obtain explicit user authorization for the bounded run.

A requirement, design example, implementation plan, or generated test specifying a large count establishes a potential verification obligation; explicit authorization governs autonomous spending beyond the default ceiling. Reuse existing user authorization when its scope and bound cover the proposed run.

When authorization or reassessment is pending, report completed lighter evidence and the outstanding verification separately. Treat a required real-trial verification as complete when sufficient executable evidence has been established.

## Responsibility boundary

This skill governs the necessity decision before trial execution and the budget for justified trials. `test-evidence-planning` owns required coverage, validation methods, and reassessment of settled test definitions; `test-evidence-implementation` owns executable test establishment; `ci-execution-efficiency` owns CI selection and configuration.

Skill guidance constrains agent decisions. For unattended or automatically triggered execution needing a mechanically enforced ceiling, implement the corresponding limit in the test runner, script, or CI configuration through its owning implementation workflow.
