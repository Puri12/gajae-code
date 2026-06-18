---
name: ultrawork
description: Parallel execution engine — fan out independent work across GJC agents at once, with planning and verification.
source: "ported from oh-my-openagent ultrawork mode and rebranded for GJC"
---

# Ultrawork

`ultrawork` is GJC's parallel execution mode. It runs multiple agents simultaneously for independent work, routes each subtask to the right specialist, and verifies before declaring done. It provides parallelism and smart routing — not durable persistence (use `ralph`) and not a full autonomous pipeline (use `autopilot`).

## Use when

- Multiple independent subtasks can run at once.
- The user asks for `ultrawork` or high-throughput parallel execution.
- Work benefits from concurrent delegation across specialists.

## Do not use when

- A single sequential task with no parallelism — delegate once to `sisyphus-junior` or `hephaestus`.
- Guaranteed completion with verification loops — use `ralph`.
- A full idea-to-working-code pipeline — use `autopilot`.

## Certainty first

Do not start implementation until you are certain. Explore the codebase, resolve ambiguity, and form a precise plan. When unsure, fire `explore` / `librarian` in parallel to gather context, and consult `oracle` for hard architecture or debugging. Ask the user only if ambiguity remains after investigation.

## Delegation surface

Use the `task` / sub-agent tool with a specific agent:

- `explore` / `librarian` — read-only research; fire in parallel with `run_in_background=true`.
- `sisyphus-junior` — bounded implementation, refactor, and fix slices.
- `hephaestus` — deep, multi-step implementation that explores before acting and completes end-to-end.
- `oracle` — hard debugging after repeated failures, and multi-system architecture trade-offs.
- `metis` — pre-planning and intent analysis; `momus` — work-plan review.
- `multimodal-looker` — analyze attached media (PDFs, images, diagrams).
- `atlas` — orchestrate an entire todo list to completion by delegating to the other agents.

Fire ALL independent agent calls in ONE response — parallel by default. Never serialize independent work. Use `run_in_background=true` for research and long operations (installs, builds, test suites); use the foreground for quick checks.

## Workflow

1. Analyze the request; separate independent subtasks from dependent ones.
2. Fire independent exploration (`explore` / `librarian`) in parallel.
3. Plan the work breakdown; delegate planning to `metis` when scope is ambiguous and `momus` to review the plan.
4. Execute: fan out independent implementation slices to `sisyphus-junior` / `hephaestus` simultaneously; run dependent slices in order.
5. Verify before declaring done.

## Verification (non-negotiable)

- Write the failing test first, watch it fail, then make it pass.
- Run the affected tests and the build; require a clean typecheck on changed files.
- Manually exercise the real user-facing surface the change touches (CLI output, API response, UI) — not just "tests pass".
- Nothing is done without proof it works.

## Todo discipline

For any work with 2+ steps, track todos: keep exactly one in progress, mark each completed immediately, and never batch completions.
