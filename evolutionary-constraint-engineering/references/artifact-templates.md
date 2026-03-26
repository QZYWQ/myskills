# Artifact Templates

Use these templates to keep the workflow compact and repeatable.

## Assumption Register

```text
Assumption Register
- Known facts:
- User claims:
- Ambiguities:
- Suspected false or incomplete statements:
- Must-verify items:
```

## Constraint Pool

```text
Constraint Pool
- Candidate constraint:
  source:
  reason:
  level: function | module | feature | system
  status: keep | challenge | discard
```

## Converged Requirement Set

```text
Converged Requirement Set
- Requirement:
  observable outcome:
  owner layer:
  prerequisite:
  verification:
```

## Dependency Map

```text
Dependency Map
- Node:
  depends on:
  blocks:
  missing prerequisite:
```

## Probe Log

```text
Probe Log
- Probe:
  target uncertainty:
  method:
  evidence:
  result: keep | discard | defer
```

## Red-Blue Findings

```text
Red-Blue Findings
- Red attack:
  impact:
  blue response:
  residual risk:
  disposition: resolved | mitigated | unresolved
```

## Single-Model Self-Challenge

```text
Single-Model Self-Challenge
- Builder pass:
  proposed constraint:
  expected value:
- Challenger pass:
  strongest objection:
  hidden dependency:
  likely failure mode:
- Probe pass:
  cheapest validating action:
  evidence needed:
- Review pass:
  decision: keep | revise | discard | defer
  reason:
```

## EVCL Draft

```text
[EVCL]
id:
title:
kind:
intent:
constraint:
scope:
  feature:
  module:
affected_layers:
depends_on:
verification:
open_risks:
status:
handoff_note:
```

## EVCL Review Pass

```text
EVCL Review Pass
- Entry id:
  atomic enough to test: yes | no
  verification present: yes | no
  dependency explicit: yes | no
  disposition justified: yes | no | n/a
  handoff safe: yes | no
  fix needed:
```
