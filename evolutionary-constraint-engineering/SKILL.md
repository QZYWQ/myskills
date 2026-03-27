---
name: evolutionary-constraint-engineering
description: Use when a request is ambiguous, high-stakes, cross-module, or likely to contain hidden assumptions, conflicting requirements, feasibility uncertainty, or a need to choose between solo, paired, and orchestrated delivery before implementation.
---

# Evolutionary Constraint Engineering

## Overview

Turn vague intent into executable constraints before writing code, then choose the cheapest execution mode that can preserve rigor.

Core rule:

1. User input is a hypothesis, not a specification.
2. Code is a constraint-solving result, not a literal rewrite of user prose.
3. Do not implement until the constraint set is converged enough to solve.

## When To Use

Use this skill when:

- the request is underspecified, contradictory, or high-stakes
- the work crosses modules, services, or technical layers
- feasibility is uncertain and needs probing
- requirement translation matters more than code syntax
- the task may need explicit choice between `solo`, `paired`, and `orchestrated` execution

Do not use this skill for trivial, already-concrete, low-risk edits.

## Hard Gates

Do not implement before all of these are true:

- assumption audit completed
- candidate requirements normalized
- orthogonal challenge recorded
- dependency chain completed
- high-risk paths probed
- red-blue pressure findings recorded
- review gate approved implementation readiness
- EVCL draft exists

If any gate fails, return to the earliest invalid stage.

## Mode Selection

Score the task first:

- cross-module: `+1`
- high-risk or high-cost mistake: `+1`
- conflicting requirements: `+1`
- needs probe: `+1`
- parallelizable subdomains >= 2: `+1`
- isolatable write scope: `+1`

Default thresholds:

- `0-1` => `solo`
- `2-3` => `paired`
- `4+` => `orchestrated`

Use `solo` for local tightly coupled work.

Use `paired` when implementation is still mostly single-threaded but needs one independent role:

- `paired-challenge`
- `paired-probe`
- `paired-review`

Use `orchestrated` when the task is cross-module, high-risk, probe-heavy, or naturally parallel.

For the full decision template, read:

- `references/mode-selection.md`

## Role Model

Use these roles explicitly, even in single-model mode:

- `auditor`
- `expander`
- `normalizer`
- `challenger`
- `dependency-mapper`
- `probe-engineer`
- `red-team`
- `blue-team`
- `review-gate`
- `implementer`
- `verifier`
- `integrator`

If only one model is available, simulate the roles in sequence. Never let one pass propose, defend, and approve the same idea.

## Workflow

1. Record `mode decision`.
2. Run `Constraint Discovery`:
   - assumption audit
   - possibility expansion
   - requirement normalization
3. Run `Constraint Convergence`:
   - orthogonal challenge
   - dependency completion
   - feasibility probing
4. Run `Constraint Hardening`:
   - red-blue pressure
   - review gate
5. Draft EVCL.
6. Only then implement from EVCL.
7. Feed every failure back into the system as new hypothesis input.

## Required Artifacts

Always produce these artifacts, even briefly:

- `mode decision`
- `assumption register`
- `constraint pool`
- `converged requirement set`
- `dependency map`
- `probe log`
- `red-blue findings`
- `EVCL draft`

For structure and templates, read:

- `references/evcl.md`
- `references/evcl-v2-template.md`
- `references/artifact-templates.md`

## Orchestration Adapter

When in `orchestrated` mode, define:

- roles to dispatch
- read/write scope per role
- return contract per role

The `integrator` must merge all returned artifacts back into EVCL before implementation approval.

Keep orchestration separate from constraint logic: this skill decides what must be solved; the orchestrator decides who should work on each part.

## Never

- Never implement before recording `mode decision`.
- Never dispatch implementation work before drafting EVCL.
- Never let `implementer` redefine requirements.
- Never start `orchestrated` mode without a write-scope plan.
- Never let the same pass propose and approve the same idea.
- Never keep `paired` or `orchestrated` mode if they do not improve rigor or speed.

## References

- `references/mode-selection.md`
- `references/evcl.md`
- `references/evcl-v2-template.md`
- `references/artifact-templates.md`
- `references/pressure-scenarios.md`
