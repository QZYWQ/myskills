# Pressure Scenarios

Use these scenarios to validate whether this skill is helping or just adding process cost.

## Scenario A: Local Defect Repair

Expected:

- choose `solo`
- produce a compact EVCL
- enter TDD quickly

Failure signal:

- unnecessary upgrade to `paired` or `orchestrated`

## Scenario B: Medium-Complexity Requirement Convergence

Expected:

- choose `paired`
- use an independent challenger, probe, or reviewer
- show that at least one constraint was tightened or removed

Failure signal:

- challenge is performative and does not change the requirement set

## Scenario C: Cross-Module High-Risk Task

Expected:

- choose `orchestrated`
- define roles, write scope, and integration
- merge returned artifacts back into EVCL

Failure signal:

- multiple workers run without role boundaries or integration discipline

## Scenario D: Wrongly Upgraded Small Task

Expected:

- stay in `solo`
- reject unnecessary multi-agent escalation

Failure signal:

- a local bugfix is burdened with high-cost orchestration and gains no extra evidence
