# EVCL Reference

EVCL means Evolutionary Constraint Language.

It is not a programming language. It is a structured handoff format for preserving validated intent across long AI-driven delivery cycles.

## Purpose

Use EVCL to keep these things stable across iterations:

- what the system is trying to achieve
- what constraints have already survived filtering
- what dependencies must stay intact
- what has been probed and verified
- what remains risky or unresolved

## EVCL Layers

Think of EVCL as three stacked layers:

1. `Intent layer`
   Stores the job the system is trying to do.
2. `Constraint layer`
   Stores the rules that survived challenge and now bind implementation.
3. `Delivery layer`
   Stores verification, risk, and handoff state.

If an entry does not help one of these layers, it probably does not belong in EVCL.

## EVCL Entry Shape

Use one block per atomic constraint group.

```text
[EVCL]
id: C-001
title: Ops SLA output must remain observational until incident ledger exists
kind: constraint
intent: expose SLA contract now without fabricating incident truth
constraint:
  - API may return SLA metrics
  - output status must be observation
  - no fabricated incident ticket records
scope:
  feature: ops-monitoring
  module: monitor
affected_layers:
  - api
  - service
  - verification
depends_on:
  - D-001 monitor overview contract
verification:
  - contract test for authorized and unauthorized access
  - response field assertions
open_risks:
  - no incident ledger yet
status: validated
handoff_note: implement with contract-first tests and no fabricated persistence
```

## Required Fields

- `id`
- `title`
- `kind`
- `intent`
- `constraint`
- `scope`
- `affected_layers`
- `depends_on`
- `verification`
- `open_risks`
- `status`

## Optional Fields

- `source`
- `disposition_reason`
- `owner`
- `handoff_note`
- `non_goals`

## Field Semantics

- `id`
  Use stable identifiers such as `C-001`, `D-014`, `R-007`.
- `kind`
  Use one of: `intent`, `constraint`, `dependency`, `risk`, `decision`.
- `constraint`
  Write only observable or enforceable statements.
- `scope`
  Name the affected feature, module, service, or workflow boundary.
- `depends_on`
  Point to another EVCL id or a named prerequisite.
- `verification`
  State how the entry can be checked. If the entry is `validated`, this cannot be empty.
- `open_risks`
  Capture only unresolved delivery risk, not generic worry.
- `handoff_note`
  Tell the next model what must not be lost during implementation.

## Status Vocabulary

Use one of:

- `hypothesis`
- `expanded`
- `challenged`
- `probed`
- `validated`
- `discarded`
- `deferred`

Recommended flow:

`hypothesis -> expanded -> challenged -> probed -> validated`

Branch outcomes:

- invalid path: `challenged -> discarded`
- blocked path: `probed -> deferred`

Do not skip directly from `hypothesis` to `validated` unless the item is already backed by external hard evidence.

## Handoff Rules

Before another model implements from EVCL, the package should include:

- the EVCL entries needed for the change
- any probe evidence that killed competing paths
- unresolved risks that still constrain implementation
- the exact verification surface expected after coding

The handoff consumer should not need the full prior conversation if EVCL is complete enough.

## Quality Checklist

Use this checklist before calling EVCL ready:

- every entry is atomic enough to test
- every hard dependency is explicit
- every validated entry names a verification path
- every discarded or deferred entry explains why
- every handoff-critical entry includes a `handoff_note`
- no entry contains brainstorming-only material
- no field depends on unstated context like "the previous option" or "as discussed"

## Writing Rules

- Keep each entry atomic enough to test.
- Write constraints as observable statements.
- Record discards explicitly when they matter to future work.
- Link entries instead of restating the same dependency many times.
- Prefer plain language over pseudo-formal syntax.

## Anti-Patterns

- mixing multiple unrelated constraints into one entry
- storing conclusions without evidence
- writing goals without verification methods
- leaving dependencies implicit in prose
- marking speculative items as validated
- recording design taste as if it were a hard constraint
- losing dependency edges between entries
