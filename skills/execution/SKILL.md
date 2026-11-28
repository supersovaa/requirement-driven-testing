---
name: test-execution-budget
description: Use when selecting or running verification for games, simulators, or episode-based systems, and for other workflows that may run costly end-to-end trials.
---

# Test Execution Budget

Before choosing a command, check what its tests and indirect runners can launch. If a complete game, simulation, episode, or other costly trial is possible, assess necessity even for a single trial and bound the runs that are justified.

Before command selection, apply the [prohibition on high-volume repetition](../planning/SKILL.md#prohibit-high-volume-repetition). Return definitions prescribing it to `test-evidence-planning` for replacement, keeping the governing guarantee pending. Apply the necessity and budgeting rules below only to permitted verification methods.

## Establish whether real trials are necessary

Identify the specific settled guarantee or diagnostic question, the failure to detect, and relevant existing evidence. Compare complete trials with source or contract inspection, compilation, deterministic unit or component tests, focused state-transition tests, controlled fixtures, injected results, and reusable verified evidence.

**Choose zero complete trials** when a lighter method establishes the same guarantee. For example, verify large trial-count inputs, dispatch counts, progress reporting, aggregation, and stop handling using controlled results or a counting substitute when these establish the contract.

Select a small bounded set of complete real trials when the outstanding guarantee specifically depends on the complete game or episode lifecycle or an actual end-to-end integration path. Verify individual game-state transitions through focused tests when those establish the guarantee. For every selected complete trial, identify the evidence that a zero-trial method leaves uncovered. Existing loops, a broad test command, or a large number in an example prompt require examining the assertions and their owning guarantee.

For permitted real-trial methods, return a settled definition to `test-evidence-planning` when an equivalent lighter method appears sufficient. Keep its guarantee pending until sufficient evidence is established or its obligation is revised by the owning workflow. Keep requirement or design changes with their owning workflow.

## Bound the necessary execution

Inspect candidate commands, test definitions, runners, and configuration to determine the maximum number of complete trial attempts they could start. Include loops inside tests, multiple targets, parameterized cases, parallel workers, automatic retries, and attempts already started when assessing remaining evidence, including attempts by other workers or agents.

For each outstanding guarantee, choose a bounded run sized to the evidence still needed and its expected resource cost. Set an explicit maximum of started attempts, concurrency, and supported timeouts before execution; estimate runtime and compute cost from available evidence when possible. Start with the smallest number sufficient for the guarantee, often one targeted trial. A distinct remaining integration guarantee may warrant its own bounded run even after previous trials for the same task or PR.

Count each started attempt, including failed, interrupted, and timed-out runs, against the selected run's bound. Allocate attempt quotas across workers or subagents so their combined maximum stays within that bound. Resolve uncertain counts by inspecting source or configuration, listing tests, or using a dry run. Apply supported trial caps and timeouts in the runner.

Reuse previously successful evidence when its inputs and guarantees remain applicable. Diagnose failed runs with focused checks, then choose any further bounded run from the remaining evidence need and diagnosis. Account for attempts, elapsed time, and compute cost already spent on the task or PR when judging whether further work remains proportionate. Keep each additional run tied to a distinct outstanding guarantee or diagnosed failure.

## Escalate material resource use

For verification methods permitted by the planning rules, execute necessary bounded runs autonomously when they fit the requested verification scope, available approved resources, and proportionate execution cost. Obtain explicit user authorization for materially increased paid compute, prolonged occupation of scarce or shared resources, or a substantial expansion beyond an explicit user limit or the justified resource scope.

When requesting authorization, identify the outstanding guarantee, the evidence real trials add beyond lighter checks, and the proposed maximum attempts, concurrency, timeout, and estimated resource or time cost when available. Reuse existing user authorization when its scope and bound cover the run.

When authorization or reassessment is pending, report completed lighter evidence and the outstanding verification separately. Treat a required real-trial verification as complete when sufficient executable evidence has been established.

## Responsibility boundary

This skill governs the necessity decision before trial execution and the budget for justified trials. `test-evidence-planning` owns required coverage, validation methods, and reassessment of settled test definitions; `test-evidence-implementation` owns executable test establishment; `ci-execution-efficiency` owns CI selection and configuration.

Skill guidance constrains agent decisions. For unattended or automatically triggered execution needing a mechanically enforced ceiling, implement the corresponding limit in the test runner, script, or CI configuration through its owning implementation workflow.
