---
name: change-scoped-testing
description: Design or review which tests to run for a code change, using required guarantees, component responsibilities, and dependency impact while identifying overly broad execution caused by weak module boundaries.
---

# Change-Scoped Testing

Use this skill when designing, revising, or reviewing CI or local test selection for code changes, including cases where small changes trigger disproportionately broad test suites.

Select verification from the guarantees affected by a change and the components that own or consume those guarantees. Keep required evidence while reducing unrelated execution.

## Establish which tests are necessary

1. Identify the changed behavior, public contracts, shared data, build inputs, and component boundaries.
2. Find the applicable requirement and design guarantees, their settled test definitions, and existing executable evidence.
3. For every test proposed for routine execution, identify the affected guarantee it establishes and why this change could affect it.
4. Reuse existing coverage when it establishes the same guarantee. Distinguish required ongoing evidence from provisional tests and temporary diagnostic checks.
5. Challenge repeated full-system scenarios when focused tests or an existing integration test establish the same guarantee.

Treat test necessity and expected outcomes as inputs from test-evidence planning. Return missing or conflicting required-test decisions to that responsibility rather than inventing or weakening guarantees. Use test-evidence implementation to consolidate duplicate executable evidence.

The size or running time of a test is a signal for inspection, not evidence that it is unnecessary.

## Select by impact rather than file count

Identify the project's real independently testable units: packages, crates, modules, libraries, services, or other coherent components. Use the dependency and contract relationships among them, not a fixed language-specific directory convention.

For a change, include:

- Tests owned by the changed units that establish affected guarantees.
- Tests in downstream consumers whose behavior or contracts may change through those units.
- Cross-component and end-to-end tests needed for affected integration guarantees.
- Wider regression checks when configuration, shared infrastructure, dependency updates, or uncertain impact reaches more units.

Exclude tests for unaffected units only when the dependency and guarantee relationships justify exclusion. A filename match alone is insufficient when dependencies or integration behavior cross that boundary.

When impact cannot be established reliably, preserve broader validation for that change and identify the missing boundary information. Keep the broader case explicit rather than treating all future changes as equally broad.

## Use excessive reach as an architecture signal

When a narrow change repeatedly requires unrelated suites, investigate why its effects cannot be isolated.

- Look for responsibilities that change independently but share a test or build boundary.
- Consider extracting a component when it has a coherent interface, independently meaningful tests or dependencies, and clearer dependency direction after separation.
- Prefer a module or test grouping within an existing component when that already gives a meaningful boundary.
- Preserve cohesive responsibilities together when extraction would only add coordination or expose internal details.

Recommend a responsibility-based separation to the owning architecture or refactoring workflow. Make clear which test-selection problem it solves and which dependencies still require downstream checks.

Do not split components solely to reduce the number of tests selected. A boundary is useful only when it reflects real responsibility and contract independence.

## Keep CI selection simple

Prefer the smallest change to the existing CI configuration that selects the required tests correctly. Reuse jobs, build preparation, and established test commands when possible.

Separate the question of which tests are required from the question of how their execution environment is provisioned. Follow repository-specific environment management rather than rebuilding dependencies merely because application code changed.

Validate both sides of each selection rule: a relevant change includes its required tests, and an unrelated change omits them. Account for changes to shared dependencies, test-selection rules, and other inputs that legitimately broaden the affected set.

Use the repository's established policy for full-suite runs, such as mainline, release, or scheduled verification. Targeted pull-request runs must still establish the guarantees assigned to them.

## Report the decision

In the existing change plan or review, state concisely:

- The changed responsibilities and affected consumers.
- The required tests and the guarantees they establish.
- The tests omitted and the established reason they are unaffected.
- Any duplicated or temporary evidence to consolidate through its owning workflow.
- Any coupling that warrants a module or component boundary change.

Prefer a short explanation in the existing work artifact over a new permanent test-to-file registry that needs manual upkeep.

## Responsibility boundary

This skill owns change-specific test execution scope and the architectural signals revealed by unnecessarily broad execution.

`test-evidence-planning` owns deciding which evidence is required, `test-evidence-implementation` owns implementing and consolidating tests, and `test-evidence-review` owns auditing whether required evidence is sufficient. Architecture and refactoring workflows own actual component extraction. CI execution tooling implements the selected scope.
