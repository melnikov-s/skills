# Canonical plan model

Normalize the source plan into this model before choosing a presentation. Omit fields that do not apply. Preserve explicit unknowns.

```yaml
objective: Plain-language description of the intended change
current_state: Relevant starting condition
desired_state: Observable end condition

stages:
  - id: stable-short-id
    title: Short action or milestone label
    outcome: What becomes true when this stage succeeds
    depends_on: [other-stage-id]
    workstream: Optional parallel lane
    inputs: []
    outputs: []
    owner: Known owner or unknown
    duration: Known estimate or unknown
    success_check: Observable proof of completion
    risks: [risk-id]
    decisions: [decision-id]

decisions:
  - id: stable-decision-id
    question: Choice that must be resolved
    options: []
    needed_before: stage-id
    status: open | decided
    resolution: Omit while open

risks:
  - id: stable-risk-id
    description: Concrete failure mode
    affects: [stage-id]
    mitigation: Known mitigation or unknown

assumptions:
  - statement: Belief the plan relies on
    validation: Evidence needed, if any

success_checks:
  - Observable outcome-level test
```

## Normalization rules

- Give every stage a unique stable ID and concise title.
- Use `depends_on` only for real ordering constraints.
- Put independent stages in workstreams rather than forcing a sequence.
- Model a decision separately when different answers change the route.
- Attach risks to affected stages instead of collecting them in a detached appendix.
- Distinguish a task output from the overall outcome.
- Retain uncertainty as `unknown`; never infer dates, owners, metrics, or confidence from silence.
- Combine low-level tasks into 3-7 meaningful stages for the primary view. Keep the original detail available beneath those stages.
- Keep labels stable across all derived formats.

## Compression test

The normalized plan should support three questions without consulting the original prose:

1. What changes if this succeeds?
2. What is the route, including parallel work and dependencies?
3. Where can the route fail or require a decision?
