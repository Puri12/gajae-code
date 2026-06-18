---
name: ultraqa
description: QA cycling loop — test, verify, fix, repeat until the goal's quality bar is met.
source: "ported from oh-my-openagent ultraqa and rebranded for GJC"
---

# Ultraqa

`ultraqa` is a quality-assurance loop. It repeatedly tests the work, finds defects, fixes them, and re-tests until the quality bar is met.

## Use when

- A change needs rigorous, iterative QA (functional, edge, and adjacent-surface regression) before it is accepted.
- The user asks for `ultraqa`, or "QA this until it is solid".

## Loop contract

1. Define the QA scenarios as binary observables: happy path, edges, and adjacent-surface regression.
2. Exercise the real surface (CLI output, API response, UI), not just unit tests; delegate adversarial QA to `sisyphus-junior` or `hephaestus`.
3. For each defect, fix it (delegate to `sisyphus-junior`) and re-run the full scenario set.
4. Repeat until every scenario passes with captured evidence.

## Delegation

Delegate via the task / sub-agent tool: `sisyphus-junior` and `hephaestus` for fixes and QA execution, `explore` to locate code, `oracle` for hard root-cause analysis, and `momus` to confirm the QA plan is adequate.

## Stop conditions

- All scenarios pass with evidence — stop.
- A defect cannot be fixed after repeated attempts — report it.
