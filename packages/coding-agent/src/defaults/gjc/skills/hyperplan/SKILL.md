---
name: hyperplan
description: Adversarial multi-agent planning — multiple critics cross-examine a plan before execution.
source: "ported from oh-my-openagent hyperplan and rebranded for GJC"
---

# Hyperplan

`hyperplan` produces a battle-tested plan through adversarial planning: a draft is attacked from multiple angles by independent critics, then synthesized into a hardened plan.

## Use when

- A high-stakes or architecturally risky change needs a rigorously stress-tested plan.
- The user asks for `hyperplan`.

## Workflow

1. Pre-analysis: `metis` classifies intent and surfaces hidden requirements; fire `explore` and `librarian` for context.
2. Draft: build an initial plan (delegate to `metis` and `oracle`).
3. Adversarial review: run `momus` (plan executability) and `oracle` (architecture and correctness) as independent critics; optionally fan out multiple critic passes in parallel via the task tool.
4. Synthesize: fold the critiques into a single hardened plan and stop at pending approval.

## Delegation

`metis` for pre-planning, `oracle` as the architecture critic, `momus` as the plan critic, and `explore` / `librarian` for evidence.

## Output

A reviewed plan with scope, sequencing, risks, and verification. Do not execute until the user approves.
