# EVCL v2 Template

Use this as the minimum persistent handoff format.

```yaml
evcl_version: 2
task_id: ""
mode: solo|paired|orchestrated

intent:
  summary: ""
  source: user|doc|code|test|probe|review

assumptions:
  known: []
  assumed: []
  disputed: []
  verify: []

constraints:
  - id: C1
    text: ""
    type: functional|nonfunctional|interface|risk|process
    layer: requirement|feature|module|function|test
    source_type: user|doc|code|test|probe|review
    confidence: low|medium|high
    status: candidate|validated|discarded|deferred|implemented|verified
    derived_from: []
    affects: []
    dependencies: []
    verification:
      - type: unit|integration|smoke|probe|review
        method: ""
        evidence: ""
    risks: []

rejected_paths: []

dependency_map:
  - from: C1
    to: C2

probe_log:
  - id: P1
    intent: ""
    method: ""
    evidence: ""
    decision: keep|discard

red_blue:
  attacks: []
  responses: []
  accepted_risks: []

implementation_targets:
  - constraint_id: C1
    files: []
    tests: []

feedback_inputs: []
reentry_from: discovery|convergence|hardening|implementation|verification|review_gate

open_questions: []
next_action: ""
```

## Quality Bar

Every implementation-relevant constraint must:

1. Have an `id`.
2. Name an affected layer.
3. Record `source_type` and `confidence`.
4. Record status.
5. Include at least one verification method once validated.

Every discarded or deferred item must record why.

If another model cannot implement from this EVCL without rebuilding the whole reasoning chain, the EVCL is too vague.
