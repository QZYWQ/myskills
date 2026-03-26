---
name: evolutionary-constraint-engineering
description: Use when a request is ambiguous, high-stakes, cross-module, or likely to contain hidden assumptions, conflicting requirements, or feasibility risk. This skill converts user intent into validated constraints before implementation, especially for agentic coding, architecture design, and end-to-end delivery.
---

# Evolutionary Constraint Engineering

Turn vague intent into executable constraints before writing code.

The core rule is simple: user input is a hypothesis, not a specification. The job is to expose blind spots, remove invalid paths, and carry only verified constraints into implementation.

## When To Use

Use this skill when:

- the request is underspecified or self-contradictory
- the work crosses multiple modules, services, or teams
- the cost of building the wrong thing is high
- feasibility is uncertain and needs probing
- the user wants agentic or AI-native engineering workflow
- implementation quality depends more on requirement translation than code syntax

Do not use this skill for trivial edits where the task is already concrete, local, and low-risk.

## Operating Model

Treat delivery as a staged constraint compiler:

1. Intent enters as raw hypothesis.
2. Hypotheses expand into candidate possibilities.
3. Candidate possibilities are filtered into valid constraints.
4. Constraints are pressure-tested before coding.
5. Code is generated only after the constraint set is coherent enough to solve.

The skill is designed to make weaker models reliable by forcing workflow discipline.

If only one model is available, simulate role separation in sequence instead of skipping it. Write outputs in distinct passes:

- `builder pass` proposes
- `challenger pass` attacks
- `probe pass` validates
- `review pass` decides

Do not let one paragraph both propose and approve the same idea.

## Hard Gates

Do not implement before these gates are satisfied:

- assumption audit completed
- candidate requirement set normalized
- contradictions challenged from an orthogonal viewpoint
- missing dependencies completed
- feasibility probed with evidence
- red-blue pressure pass recorded

If any gate fails, go back to the earliest invalid stage instead of improvising downstream.

## Required Artifacts

Always produce these artifacts, even if briefly:

- `assumption register`
- `constraint pool`
- `converged requirement set`
- `dependency map`
- `probe log`
- `red-blue findings`
- `EVCL draft`

For structure and templates, read:

- `references/evcl.md`
- `references/artifact-templates.md`

## Workflow

### 1. Assumption Audit

Convert the request into explicit assumptions.

- Identify ambiguity, omissions, impossible claims, and hidden dependencies.
- Ask or infer what must be true for the request to make sense.
- Separate observed facts from user claims.

Output:

- what is known
- what is assumed
- what is disputed
- what must be verified

### 2. Possibility Expansion

Deliberately widen the solution space.

- Generate multiple plausible interpretations, solution routes, and edge scenarios.
- Use expansion to reveal blind spots, not to commit to options.
- Prefer breadth over polish.

Output:

- candidate paths
- boundary scenarios
- hidden stakeholder concerns
- likely failure modes

### 3. Requirement Normalization

Translate expanded material into atomic requirements.

- Split broad ideas into concrete requirement points.
- Rewrite vague requests as observable constraints.
- Map each requirement to the function, module, feature, or system level it affects.

Output:

- atomic requirement list
- requirement hierarchy
- traceability from demand to implementation layer

### 4. Orthogonal Challenge

Attack the candidate set from outside its own logic.

- Introduce objections, conflicts, missing context, and reality checks.
- Remove requirements that rely on fantasy, contradiction, or unjustified complexity.
- Keep only constraints that survive external challenge.

Output:

- invalidated items
- unresolved conflicts
- surviving constraint set

### 5. Dependency Completion

Repair broken end-to-end chains.

- Build the dependency graph across requirements, modules, states, and data flows.
- Detect missing preconditions and support links.
- Add only what is necessary to keep the chain executable.

Output:

- dependency map
- missing prerequisites
- completed end-to-end chain

### 6. Feasibility Probing

Replace speculation with evidence.

- Use small experiments, validation code, mocks, shell probes, or targeted searches.
- Probe the hard parts first.
- Kill paths that fail empirical checks.

Output:

- probe intent
- method
- evidence
- keep or discard decision

### 7. Red-Blue Pressure

Stress the converged design before coding.

- Red side attacks boundaries, malformed inputs, extreme states, abuse patterns, and operational failure.
- Blue side responds with fixes, mitigations, or explicit non-goals.
- Any unresolved critical attack sends the work back upstream.

Output:

- attack list
- blue responses
- accepted risks
- returned constraints

If running in single-model mode, use the `Single-Model Self-Challenge` template from `references/artifact-templates.md` and force the attack and defense passes to be written separately.

### 8. Review Gate

Pause and judge whether the constraint set is coherent enough to implement.

Approval standard:

- constraints are testable
- dependencies are complete
- major unknowns have been probed
- critical attacks have responses
- EVCL is sufficient for another model to continue implementation

### 9. Implementation

Only now convert constraints into code.

- treat code generation as solving for a valid point inside the constrained solution space
- preserve traceability between EVCL items and implementation artifacts
- when implementation fails, record the failure as a new constraint input instead of patching blindly

### 10. Verification Loop

Every issue discovered later re-enters the same system.

- convert bug or gap into a new hypothesis
- run it back through audit, challenge, completion, and probing as needed
- evolve the EVCL instead of treating failures as isolated accidents

## EVCL Rules

Evolutionary Constraint Language is the persistent handoff format.

An EVCL entry should express:

- intent
- validated constraint
- affected layer
- dependency links
- verification method
- open risk
- current status

Write EVCL so another model can continue the work without reconstructing the whole reasoning chain.

Minimum EVCL quality bar:

- every implementation-relevant constraint has an `id`
- every `validated` entry has at least one verification method
- every `discarded` or `deferred` entry records why
- every dependency refers to another explicit entry or named prerequisite
- no entry mixes hard constraints with taste, preference, or brainstorming residue

Before handoff, re-check EVCL against `references/evcl.md`.

## Heuristics

- Prefer deleting false requirements over satisfying all requests literally.
- A requirement that cannot be observed, tested, or challenged is not ready.
- If a path has not been probed, it is still speculation.
- If red can break it and blue has no answer, it is not converged.
- If another model cannot implement from the EVCL, the abstraction is still too vague.

## Common Failures

- treating user prose as truth
- using one voice to propose, defend, and approve in the same pass
- expanding possibilities and never converging
- converging by intuition instead of filtering
- skipping probes because a design sounds plausible
- using red-blue language performatively without concrete attacks
- writing code before dependency completion
- losing the evolving constraint state in long conversations

## Minimal Usage Pattern

1. Build the assumption register.
2. Expand possibilities.
3. Normalize into atomic constraints.
4. Challenge and filter.
5. Complete dependencies.
6. Probe feasibility.
7. Run red-blue pressure.
8. Draft EVCL.
9. Implement.
10. Recycle failures back into the loop.
