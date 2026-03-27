# Mode Selection

Use this checklist before implementation.

## Score

Add one point for each true condition:

1. Work crosses multiple modules or layers.
2. Wrong implementation would be expensive or dangerous.
3. Requirements conflict or contain strong ambiguity.
4. Hard parts need probing or validation code.
5. There are at least two independent subdomains that could run in parallel.
6. Write scope can be isolated between workers.

## Thresholds

- `0-1`: `solo`
- `2-3`: `paired`
- `4+`: `orchestrated`

## Guardrails

Choose `solo` even with a higher score when:

- a failing test already narrows the bug to a local implementation point
- multiple agents would edit the same small write set
- the work is tightly coupled and sequential

Choose `paired` when:

- one independent challenge, probe, or review pass is enough
- implementation still belongs to one main owner

Choose `orchestrated` when:

- there are multiple real task lanes
- stronger orthogonality is needed
- evidence gathering benefits from parallel roles

## Paired Submodes

- `paired-challenge`: independent challenger attacks the requirement set
- `paired-probe`: independent probe worker validates hard feasibility questions
- `paired-review`: independent reviewer judges implementation readiness or final compliance
