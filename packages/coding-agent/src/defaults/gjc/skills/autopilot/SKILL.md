---
name: autopilot
description: Full autonomous pipeline from idea to working, verified code — clarify, plan, execute, verify.
source: "ported from oh-my-openagent autopilot and rebranded for GJC"
---

# Autopilot

`autopilot` runs the full lifecycle autonomously: clarify the request, plan it, execute it, and verify it — layering the planning and execution loops on top of `ralph` and `ultrawork`.

## Use when

- The user wants a whole feature or fix taken from idea to working code with minimal intervention.
- The user asks for `autopilot`.

## Pipeline

1. Clarify: if requirements are ambiguous, run `/skill:deep-interview` (or delegate intent analysis to `metis`) until scope is clear.
2. Plan: build a reviewed plan with `/skill:ralplan` (planning plus `oracle` and `momus` review). Stop at pending approval if execution approval has not been given.
3. Execute: drive the work to completion via `ralph` / `ultrawork`, delegating to `sisyphus-junior` and `hephaestus` and coordinating with `atlas`.
4. Verify: build, tests, and real-surface checks, with a reviewer gate via `oracle`.

## Delegation

The full OmO roster via the task / sub-agent tool. Use `atlas` to orchestrate the todo list end to end.

## Stop conditions

- Goal complete and verified — stop and report evidence.
- Blocked by a missing decision or external dependency — ask the user.
