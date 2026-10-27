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

Inspect candidate commands, test definitions, runners, and configuration to determine the maximum number of complete trial attempts they could start. Include loops inside tests, multiple targets, parameterized cases, parallel workers, automatic retries, and attempts already started when assessing remaining evidence, including attempts by other workers or agents.

For each outstanding guarantee, choose a bounded run sized to the evidence still needed and its expected resource cost. Set an explicit maximum of started attempts, concurrency, and supported timeouts before execution; estimate runtime and compute cost from available evidence when possible. Start with the smallest number sufficient for the guarantee, often one targeted trial. A distinct remaining integration guarantee may warrant its own bounded run even after previous trials for the same task or PR.

Count each started attempt, including failed, interrupted, and timed-out runs, against the selected run's bound. Allocate attempt quotas across workers or subagents so their combined maximum stays within that bound. Resolve uncertain counts by inspecting source or configuration, listing tests, or using a dry run. Apply supported trial caps and timeouts in the runner.

Reuse previously successful evidence when its inputs and guarantees remain applicable. Diagnose failed runs with focused checks, then choose any further bounded run from the remaining evidence need and diagnosis. Keep each additional run tied to a distinct outstanding guarantee or diagnosed failure.

## Escalate material resource use

Execute necessary bounded runs autonomously when they fit the requested verification scope, available approved resources, and proportionate execution cost. Obtain explicit user authorization for materially increased paid compute, prolonged occupation of scarce or shared resources, or a substantial expansion beyond an explicit user limit or the justified resource scope.

When requesting authorization, identify the outstanding guarantee, the evidence real trials add beyond lighter checks, and the proposed maximum attempts, concurrency, timeout, and estimated resource or time cost when available. Reuse existing user authorization when its scope and bound cover the run.

A requirement, design example, implementation plan, or generated test specifying many trials establishes a potential verification obligation. Use `test-evidence-planning` for reassessment when equivalent lighter evidence would suffice; keep any settled real-trial obligation pending until sufficient evidence is established.

When authorization or reassessment is pending, report completed lighter evidence and the outstanding verification separately. Treat a required real-trial verification as complete when sufficient executable evidence has been established.

## Responsibility boundary

This skill governs the necessity decision before trial execution and the budget for justified trials. `test-evidence-planning` owns required coverage, validation methods, and reassessment of settled test definitions; `test-evidence-implementation` owns executable test establishment; `ci-execution-efficiency` owns CI selection and configuration.

Skill guidance constrains agent decisions. For unattended or automatically triggered execution needing a mechanically enforced ceiling, implement the corresponding limit in the test runner, script, or CI configuration through its owning implementation workflow.
