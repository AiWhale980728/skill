# Product-engineering templates

Use these templates when the user requests formal planning documents, the project is complex enough to need a durable handoff, or the current phase needs a written acceptance contract. Trim irrelevant fields; do not create paperwork that adds no decision value.

## Technical adaptation

```markdown
# Technical adaptation

## Product and phase
- Primary user and task:
- New/existing project:
- Current phase goal:
- Explicit non-goals:

## Chosen path
- Backend-first / vertical slice:
- Reason:
- Existing stack retained:

## Rules applied
- Invariants:
- Defaults adopted:
- Need-triggered modules:
- Deviations and reasons:

## Core contracts
- Data and assets:
- Agent/task states:
- API/streaming approach:
- Target client and responsive scope:

## Validation
- Offline/mock:
- Real provider:
- Browser/API:
- Deployment/remote:
- Owner acceptance:

## Material decisions
- Only questions that change scope, UX, cost, security, migration, or launch:
```

If the final section is empty, continue with safe defaults.

## Stage implementation document

```markdown
# Stage N | Name

## Goal and boundary
- User-visible outcome:
- Included:
- Explicitly excluded:
- Main loop fragment:

## Technical adaptation summary
- Adopted defaults:
- Triggered modules:
- Deviations:
- Development path:

## Environment and configuration
- Runtime/dependencies:
- Non-secret configuration keys:
- User-provided prerequisites:
- Ports/services:

## Data, assets, and state
- Persistence and schema/migration:
- Asset ownership/storage/lifecycle:
- States, transitions, confirmation points, and recovery:

## Interfaces and Agent behavior
- Endpoint/tool contracts and safe errors:
- Streaming/polling and terminal events:
- Prompt/output schema and validation:
- Tool allowlist, permissions, budget, steps, timeout:

## Frontend slice, if applicable
- Routes/pages/components:
- State matrix:
- Responsive/accessibility targets:

## Verification contract
- Offline/mock cases:
- Real-provider smoke:
- Browser/API loop:
- Target devices/sizes:
- Owner acceptance steps:

## Risk and handoff
- Cost/security/migration/rollback risks:
- Known issues and pending gates:
- Files/artifacts produced:
- What the next stage can safely reuse:
```

## Frontend state matrix

```markdown
| Page/module | Initial | Loading | Empty | Queued/running | Waiting user | Partial/success | Failed | Cancelled/disconnected | Recovery |
|---|---|---|---|---|---|---|---|---|---|
| | | | | | | | | | |
```

## Stage acceptance checklist

Write nontechnical, reproducible steps:

```markdown
- [ ] Open the supplied review URL.
- [ ] Complete the stated user task from input to a real result.
- [ ] Confirm what happens during waiting/running and what action is available.
- [ ] Exercise the applicable failure, retry, cancel, and refresh/recovery paths.
- [ ] Verify a second user cannot access the first user's private data, when multi-user behavior is in scope.
- [ ] Inspect the target desktop/mobile/device experience.
- [ ] Record any mismatch with the PRD/design and whether it is accepted for this stage.
```

Add task-specific expected results. Do not turn internal test commands into a product-owner checklist.

## Delivery report

```markdown
Conclusion: one sentence.

Completed
- Change and evidence.

Not completed / known issues
- Gate, impact, and reason.

Next step
- Exact owner or agent action.
```

Use precise gate language such as “implemented locally,” “automated tests passed,” “real-model smoke pending,” “deployed and remotely verified,” or “awaiting owner acceptance.”
