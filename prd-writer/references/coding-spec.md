# Coding Specification Extension

Use this module when a coding Agent or engineering team needs implementation-ready detail. Derive it from confirmed product requirements. Do not let technical convenience silently change user outcomes or scope.

## Decision status

Label every material technical choice:

- **Fixed constraint** — required by the user, organization, existing system, or external contract.
- **Recommended default** — proposed by the writer and open to revision.
- **Open decision** — unresolved and potentially blocking.

Inspect an existing repository before describing its architecture or dependencies. Never invent repository state.

## Implementation overview

Define:

- supported platforms and runtime
- architecture boundary
- fixed technology constraints
- external services
- environments
- authentication and authorization approach
- deployment and rollback expectations

When starting from scratch, prefer the simplest stack that satisfies the PRD. Explain recommendations rather than presenting preferences as requirements.

## Project structure

Provide a concise tree only for files and directories that matter. State the responsibility and ownership boundary of each major area. Reuse existing conventions when a repository exists.

## Interfaces and components

For user interfaces define:

- routes or entry points
- component responsibilities
- public props or inputs
- states and interactions
- accessibility behavior
- responsive behavior
- design-token source

Use concrete interface definitions only when the language and framework are known.

For APIs define:

- method or event
- path or topic
- auth and permission
- request and response schema
- validation
- errors
- idempotency
- pagination or streaming
- rate and timeout behavior

## Data model

Define:

- entities and relationships
- field types and validation
- ownership and tenancy
- indexes or lookup needs
- lifecycle, retention, and deletion
- migration and backward compatibility

Provide SQL, ORM, or typed schemas only when the technology is fixed or explicitly delegated.

## AI implementation

When the AI Product extension applies, link every AI call to its PRD capability and define:

- provider/model selection status
- prompt or instruction location
- context assembly
- structured-output schema
- validation
- streaming and cancellation
- timeout, retry, and fallback
- evaluation fixtures
- observability
- cost controls

When the Agent extension applies, also define tool adapters, approval enforcement, state persistence, trajectory logs, idempotency, rollback or compensation, and resumption.

## Security and configuration

List configuration keys without secret values. Define:

- data classification
- secret storage
- authorization enforcement
- input and output sanitization
- dependency trust boundaries
- audit events
- abuse and rate controls

## Delivery plan

Break implementation into vertical slices that produce testable user value. For each slice include:

| Slice | User-visible result | Dependencies | Files or systems | Tests | Done condition |
|---|---|---|---|---|---|

Avoid a plan that completes all backend layers before any end-to-end behavior can be tested.

## Verification

Map requirements to tests:

| Requirement ID | Unit | Integration | End-to-end | Evaluation | Manual review |
|---|---|---|---|---|---|

Include commands only when they are valid for the chosen project. Define expected outcomes, not merely "tests pass."

## Suggested structure

Use one file for a small project. For a larger project, split by implementation concern:

```text
coding-spec/
├── README.md
├── architecture.md
├── interfaces.md
├── data-model.md
├── ai-and-agent.md        # when applicable
├── delivery-plan.md
└── verification.md
```

Use relative links and reference requirement IDs instead of duplicating the PRD.
