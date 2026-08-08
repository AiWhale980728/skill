# PRD Quality Checks

Run the relevant checks before delivery. Fix internal inconsistencies directly. Report decisions that require product authority.

## Scope and evidence

- The problem, user, situation, and consequence are clear.
- Claims based on research, analytics, or prior documents are traceable.
- Assumptions are labeled and paired with a validation need.
- Goals, MVP scope, later scope, and non-goals do not contradict each other.
- The document does not invent urgency, customer evidence, approval, ownership, or deadlines.

## Requirements

- Every requirement describes observable behavior or outcome.
- Medium and large documents use stable requirement IDs.
- Requirements are atomic, testable, and prioritized.
- Normal, empty, partial, failure, permission, and recovery states are covered where relevant.
- Business rules, object states, and permissions agree.
- Acceptance criteria test outcomes rather than implementation activity.
- Undefined adjectives such as "fast," "intuitive," "secure," or "high quality" have been replaced by thresholds or review methods.

## Product-type routing

- A conventional product does not contain unnecessary AI or Agent sections.
- An AI product defines input, output, human control, fallback, evaluation, and safety.
- An LLM call is not mislabeled as an autonomous Agent.
- An Agent product defines authority, tools, memory, approval, verification, recovery, and trajectory evaluation.
- Multi-Agent design is justified by a concrete benefit.

## AI and Agent safety

- Deterministic code enforces permissions, schema, security, and irreversible-action gates.
- Model uncertainty and abstention behavior are defined.
- Prompt injection and untrusted content are handled.
- Tool preconditions, side effects, verification, and failure recovery are specified.
- Consequential actions have bounded authority and human oversight.
- No hidden chain-of-thought requirement appears in the document.

## Coding specification

- Implementation details are generated only when requested.
- Fixed constraints, recommendations, and open decisions are distinguished.
- Existing repository facts were inspected rather than guessed.
- Technology choices are consistent across architecture, interfaces, data, and tests.
- Requirement IDs map to implementation slices and verification.
- Commands, versions, schemas, and paths are concrete only when supported.
- Secrets or personal data are not embedded.

## Document integrity

- Each decision has one source of truth.
- Split files use valid relative links.
- Optional modules are omitted rather than left empty.
- Terms and entities are named consistently.
- Confirmed requirements, recommendations, assumptions, risks, dependencies, and open decisions are visibly distinct.
- The final summary states what is ready, what remains unresolved, and what should happen next.

## Delivery summary

End with:

1. deliverable and intended readers
2. product type and modules included
3. confirmed scope
4. major assumptions
5. blocking open decisions
6. top risks
7. recommended next action
