# Agent Product Extension

Load this module only when the product interprets a goal and autonomously plans steps, selects tools, changes external state, uses memory, or coordinates other Agents.

## Autonomy contract

Define the Agent's authority:

| Decision class | Act automatically | Ask first | Prohibited |
|---|---|---|---|

Classify operations by reversibility, cost, data sensitivity, external impact, and affected people. Require confirmation for consequential actions unless the user has explicitly granted bounded authority.

## Task contract

For each Agent define:

- objective
- supported and unsupported tasks
- completion and stop conditions
- required context
- assumptions it may make
- when it must ask a question
- when it must abstain or escalate
- observable output or external effect

Avoid role descriptions that do not change behavior.

## Action loop

Specify the observable policy:

1. interpret the goal
2. inspect relevant context
3. identify missing information
4. plan at an appropriate granularity
5. choose an allowed tool or response
6. execute
7. verify the result
8. recover, replan, escalate, or finish

Do not require hidden chain-of-thought. Require concise plans, decisions, evidence, tool results, and user-visible status only when useful.

## Tool contract

For every tool define:

| Field | Requirement |
|---|---|
| Purpose | User outcome enabled |
| Preconditions | Context, auth, and approval |
| Input | Required parameters and source |
| Side effect | Read, create, update, send, purchase, or delete |
| Verification | How success is confirmed |
| Failure | Retry, alternate tool, rollback, or escalation |
| Limits | Rate, cost, scope, and forbidden uses |

Apply least privilege. Never infer permission for materially different actions.

## Context and memory

Separate:

- immutable task facts
- current working state
- conversation history
- retrieved external context
- user preferences
- durable memory
- shared multi-Agent state

Define provenance, freshness, conflict resolution, write criteria, retention, deletion, and user visibility. Do not treat generated text as fact without validation.

## Human oversight

Specify:

- approval gates
- preview and edit
- pause and cancel
- audit trail
- undo or compensation
- escalation owner
- recovery after interruption

The user must be able to understand what changed and what remains.

## Multi-Agent coordination

Only add multiple Agents when specialization, isolation, permissions, or parallel work creates measurable value. Define:

- orchestrator and ownership
- delegation criteria
- input and output contract
- shared-state schema
- conflict resolution
- retry and timeout
- duplicate-work prevention
- final authority

Do not create separate Agents merely to imitate an organization chart.

## Agent evaluation

Evaluate complete trajectories, not only final text:

- task completion
- correct tool and parameter selection
- unnecessary actions
- permission compliance
- factual grounding
- recovery quality
- reversibility
- latency and cost
- human intervention rate
- side effects and safety incidents

Include simulations for tool failure, stale context, conflicting instructions, malicious content, partial completion, and interruption.
