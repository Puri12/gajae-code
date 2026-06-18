---
name: ralph
description: Self-referential execution loop that runs until the goal is complete, with a verification reviewer gate.
source: "ported from oh-my-openagent ralph and rebranded for GJC"
---

# Ralph

`ralph` is a persistent execution loop. It drives a task to guaranteed completion across iterations, adding durable progress and a reviewer gate on top of `ultrawork`'s parallelism.

## Use when

- The task must be driven to guaranteed completion, not just one parallel pass.
- The user asks for `ralph`, or "keep working until it is done and verified".

## Loop contract

1. Establish the goal and a clear, binary definition of done.
2. Each iteration: plan the next slice, delegate execution to the OmO agents, then verify (build, tests, and the real surface).
3. After significant work, gate completion with a reviewer — `oracle` for architecture and correctness, `momus` for plan adherence.
4. Persist progress under `.gjc/` between iterations and continue until the reviewer confirms the goal is met.

## Delegation

Delegate via the task / sub-agent tool: `sisyphus-junior` and `hephaestus` for execution, `explore` and `librarian` for research, `oracle` for review and hard problems, `metis` and `momus` for planning and review, and `atlas` for orchestration.

## Stop conditions

- The reviewer confirms the goal is complete and verified — stop.
- Repeated failure on the same blocker — report it rather than looping indefinitely.
