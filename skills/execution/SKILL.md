---
name: test-execution-budget
description: Bound repeated full-system simulations and other costly trial-based verification before running or rerunning tests, including local and automated runs.
---

# Test Execution Budget

Use this skill before executing or rerunning verification whose workload grows with repeated complete games, simulations, episodes, trials, or similar end-to-end runs. Apply it to direct commands and test runners that invoke such work indirectly.

## Establish the total workload

Inspect the selected commands, test definitions, runners, and configuration to determine the maximum number of complete trials. Include loops inside tests, test targets, parameterized cases, parallel workers, retries, and runs already performed for the current work unit.

Use **10 complete end-to-end trials per work unit** as the default cumulative autonomous execution ceiling. Select fewer when they establish the required result. Count each simulated game or equivalent end-to-end run as one trial, regardless of the number of test processes used.

Use only commands whose trial count is bounded within the remaining authorized budget. When the count is uncertain, establish it through source/configuration inspection or a listing or dry-run facility before execution. Apply a runner-level trial cap and appropriate timeout when the runner supports them.

## Choose proportionate evidence

Begin with the smallest focused deterministic check, typically one representative trial, then add distinct boundary or integration cases needed by the settled guarantee.

For an interface that accepts large counts, verify count parsing, limit acceptance, dispatch, aggregation, or stopping through a bounded fixture, counting substitute, or other controlled test when that evidence establishes the contract. Reserve large real simulation batches for guarantees that actually depend on their complete execution or statistical sample size.

Treat existing successful evidence as consumed coverage. Reuse it when the relevant inputs and guarantees remain unchanged. Count retries and diagnostic reruns against the same budget.

## Escalate necessary large runs

When required verification exceeds the remaining autonomous budget, identify the governing guarantee, explain why smaller or controlled evidence is insufficient, and provide the proposed total trial count and expected resource or time cost when estimable. Obtain the user's explicit authorization for that bounded run before executing it.

A requirement, design example, implementation plan, or previously generated test containing a large number establishes a verification obligation, while **explicit user authorization** establishes permission to spend beyond the autonomous execution ceiling. Reuse an existing user authorization when its scope and bound already cover the proposed run.

When authorization is pending, preserve the required verification as pending, report the bounded checks completed, and hand the remaining work back to the responsible workflow. Mark completion only when the required evidence is established.

## Responsibility boundary

This skill governs the execution budget for repeated trial-based verification. `test-evidence-planning` owns required coverage and validation methods; `test-evidence-implementation` owns executable tests; `ci-execution-efficiency` owns CI selection and configuration.

Skill guidance constrains agent decisions. For unattended or automatically triggered execution requiring a mechanically enforced ceiling, implement the corresponding limit in the test runner, script, or CI configuration through its owning implementation workflow.
