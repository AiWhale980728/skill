# Standard Product Extension

Use this module for deterministic interfaces, workflows, roles, permissions, notifications, integrations, and system states. Do not repeat the Core PRD; add only details required to remove ambiguity.

## Information architecture

Define, when applicable:

- objects and their relationships from the user's perspective
- navigation and entry points
- page, screen, command, or API surface
- search, filtering, sorting, and pagination
- canonical ownership of settings and actions

Avoid prescribing visual styling unless design is within scope.

## Interaction requirements

For every meaningful interaction specify:

| Element or action | User intent | System response | States | Validation | Accessibility |
|---|---|---|---|---|---|

Cover:

- first use and onboarding
- empty, loading, partial, success, and error states
- destructive actions and confirmation
- undo, cancellation, and retry
- concurrent edits or stale data
- keyboard and assistive-technology behavior when relevant
- responsive behavior when relevant

## Roles and permissions

Use a matrix:

| Capability | Role A | Role B | Role C | Notes |
|---|---|---|---|---|

Define object ownership, visibility, delegation, approval, audit, and access-revocation behavior. Apply least privilege.

## State and lifecycle

For important objects define:

- states
- allowed transitions
- actor or event that triggers each transition
- validation and permission requirements
- side effects
- terminal and reversible states

Use a state diagram when more than four states or several actors are involved.

## Notifications

Specify:

- triggering event
- recipient
- channel
- timing and frequency
- content requirements
- preference and opt-out behavior
- deduplication
- failure handling

## Integrations

Describe product-level contracts:

- user value and workflow
- authorization model
- required data
- direction and frequency of synchronization
- conflict resolution
- unavailable or rate-limited behavior
- deletion and revocation

Put endpoint schemas and SDK details in the coding specification unless fixed externally.

## Standard-product acceptance

Verify:

- every action has a visible result
- object states and permissions agree
- destructive actions are recoverable or deliberately confirmed
- interrupted workflows can resume or fail safely
- notifications and integrations do not duplicate or leak information
