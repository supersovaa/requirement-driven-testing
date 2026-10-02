# requirement-driven-testing

A lightweight skill for deriving executable test evidence from settled requirements and design.

## Core idea

Treat tests as executable evidence of already-settled requirements and design.

- Keep requirement tests and design tests distinct by their authoritative source.
- Establish missing executable tests before the target implementation when the guarantee can be meaningfully tested.
- Reuse existing tests when they already provide sufficient evidence.
- Do not manufacture a failing test when existing behavior already satisfies the requirement.
- Distinguish missing test support from missing production dependencies.
- Let settled requirements take precedence over design, tests, and implementation; return conflicting design to its owning workflow for alignment.
- Prioritize test gaps discovered during implementation review before ordinary cleanup or refactoring.

The skill does not define requirements or design. It derives and restores executable evidence from them while leaving those decisions with their owning workflows.

## Files

- `SKILL.md` — installable skill definition.
- `README.md` — overview.
- `LICENSE` — MIT License.
