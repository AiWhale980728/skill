# Core PRD

Use this module for every product. Scale the depth to the decision and scope; a single feature should not receive a full-platform template.

## 1. Document context

Record:

- product or feature name
- status and version
- owner when provided
- intended readers
- scope and deliverable type
- source materials
- confirmed decisions, assumptions, and open questions

Do not invent an author, approver, deadline, or research source.

## 2. Problem and opportunity

Explain:

- the user or business problem
- who experiences it and in what situation
- the current behavior or workaround
- why the problem matters now
- evidence and uncertainty
- the consequence of doing nothing

Keep evidence separate from interpretation. If the business case or market need is not established, identify the dependency on BRD, MRD, research, or validation rather than manufacturing justification.

## 3. Product definition

Provide:

- one-sentence product definition
- target users and excluded users
- primary jobs or outcomes
- value proposition
- product principles that constrain decisions
- non-goals

## 4. Goals and success

Define a small set of outcome metrics. For each metric include:

| Field | Meaning |
|---|---|
| Metric | What is measured |
| Baseline | Current state, if known |
| Target | Desired value or direction |
| Timeframe | When it should be observed |
| Instrumentation | How data will be collected |
| Guardrail | What must not deteriorate |

Do not substitute output counts for outcomes without explaining the relationship.

## 5. Scope and prioritization

Separate:

- P0 / must have
- P1 / should have
- later
- out of scope

For each item state the user outcome and rationale. Record dependencies and decisions that could change scope.

## 6. User journeys

Describe each primary journey as:

1. trigger
2. preconditions
3. user actions
4. system responses
5. completion state
6. interruption and recovery
7. follow-up state

Use a Mermaid diagram when branching, ownership, or state transitions are hard to understand linearly.

## 7. Functional requirements

Give each medium or large requirement a stable ID.

| ID | Requirement | Rationale | Priority | Dependencies | Acceptance criteria |
|---|---|---|---|---|---|

Write atomic behavior:

> When [trigger/condition], the system must [observable behavior], so that [user outcome].

Specify:

- inputs and validation
- processing and business rules
- outputs and states
- permissions
- empty, loading, partial, success, and failure behavior
- edge cases
- reversibility where relevant

Do not hide multiple behaviors inside one vague requirement.

## 8. Data and measurement

Define only what product decisions require:

- data inputs and provenance
- core entities and ownership
- retention, deletion, export, and audit needs
- analytics events and properties
- reporting requirements
- privacy classification and consent

A formal database schema belongs in the coding specification unless it is itself a product constraint.

## 9. Non-functional requirements

Set measurable requirements where relevant:

- latency and throughput
- availability and recovery
- accessibility
- compatibility
- localization
- security and privacy
- regulatory or policy constraints
- observability
- scalability
- supportability

Avoid phrases such as "fast," "secure," or "user friendly" without an observable threshold or review method.

## 10. Rollout and operations

Cover:

- release stages and eligibility
- migration or backward compatibility
- feature flags or rollback
- support and escalation
- documentation and training
- monitoring
- launch decision criteria

## 11. Risks, dependencies, and open decisions

Keep three distinct lists:

- **Risk** — uncertain event and its impact, mitigation, and owner when known.
- **Dependency** — external condition required for delivery.
- **Open decision** — unresolved choice, options, decision owner, and deadline when known.

## 12. Acceptance

Use Given/When/Then for behavior that must be tested. Cover happy paths, key boundaries, permission failures, unavailable dependencies, and recovery. Acceptance criteria must describe externally observable results rather than implementation activity.
