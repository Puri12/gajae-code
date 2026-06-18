---
name: ulw-loop
description: Ultrawork loop — run ultrawork iteratively until the task is fully complete and verified.
source: "ported from oh-my-openagent ulw-loop and rebranded for GJC"
---

# Ulw-Loop

`ulw-loop` wraps `ultrawork` in a completion loop. It keeps fanning out parallel work and verifying until the task is fully done, instead of stopping after a single pass.

## Use when

- A multi-part task needs repeated parallel passes until everything is complete and verified.
- The user asks to "loop" or "keep going until done" on parallel work.

## Loop contract

1. Run an `ultrawork` pass: plan, fan out independent work to the OmO agents, then verify.
2. Re-check remaining work against the goal and the definition of done.
3. If anything is incomplete or failing, run another pass.
4. Stop only when every item is complete and verification passes (build and tests green, real user-facing surface exercised).

## Delegation

Same surface as `ultrawork`. Delegate via the task / sub-agent tool to `sisyphus-junior` and `hephaestus` for execution, `explore` and `librarian` for research, `oracle` for hard problems, `metis` and `momus` for planning and review, and `atlas` to orchestrate a whole todo list.

## Stop conditions

- All todos complete and verified — stop.
- A task fails repeatedly across passes — report the blocker instead of looping forever.
