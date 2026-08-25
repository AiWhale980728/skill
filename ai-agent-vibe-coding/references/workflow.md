# Workflow and phase gates

Use this reference when deciding where to start, how to slice work, or whether a product may advance to frontend or deployment.

## Inputs and responsibilities

Expected product inputs, when relevant:

- Confirmed PRD or an equivalent product definition.
- Existing code, data, interfaces, constraints, and prior acceptance evidence.
- Target users, core task, inputs/process/artifacts, Agent interaction shape, success criteria, delivery phase, model/cost limits, and data/non-functional constraints.
- Confirmed design direction or references for formal frontend work.
- Target deployment environment and release authority for public launch.

Derive technical entities, states, APIs, storage, testing, and implementation details from those inputs. Do not ask a product manager to choose low-level frameworks or database mechanics unless that choice materially affects product outcomes.

## Phase router

| Current evidence | Next phase | Required output |
|---|---|---|
| Product scope exists, implementation does not | Adaptation | Compact technical adaptation and first-stage boundary |
| Core Agent value unverified | Core loop | Smallest real input to model/tool to durable result loop |
| Core loop accepted, product UI incomplete | Formal frontend | Representative page, state matrix, then staged Web client |
| Local product accepted, release not prepared | Release preparation | Migration, security, persistence, monitoring, rollback plan |
| Release preparation verified | Deployment | Public endpoint plus remote behavior evidence |
| Deployed product has defects or drift | Post-launch repair | Scoped diagnosis/fix with remote re-verification |

Do not infer that passing one row automatically authorizes or proves the next.

## Adaptation decision

Record these briefly before substantial work:

- Product and primary user task.
- New or existing project and retained constraints.
- Current phase goal and explicit non-goals.
- Backend-first or vertical-slice path and why.
- Adopted defaults, need-triggered modules, and deliberate deviations.
- Core data, assets, task states, interfaces, and target client.
- Validation layers required for this phase.
- Decisions that materially affect scope, UX, cost, security, data migration, or launch.

If no material decision is missing, continue. For formal output use `templates.md`.

## Stage slicing

Each stage should create one observable, reversible increment:

1. Adaptation and contracts.
2. Runnable skeleton and one minimal entry point.
3. First real Agent loop with durable state and a viewable artifact.
4. Full interaction for required confirmation, streaming/polling, retry, cancel, and recovery.
5. Quality and release preparation.
6. Deployment and post-launch verification, only when requested and authorized.

Stages may be merged for a small project, but every delivery still needs a real loop and explicit evidence.

## Gate definitions

### Core loop gate

- Real input reaches the intended model/tool contract.
- Output is parsed and validated deterministically.
- Result and task state are recoverable after process restart when required.
- Offline tests cover logic and failures.
- At least one real-provider smoke test passes, or is explicitly pending due to missing credentials.
- Product owner has not been told the Agent quality is accepted unless they actually accepted it.

### Formal frontend gate

- Core backend contract is sufficiently stable for the stage.
- A representative page establishes the confirmed visual direction before broad rollout when visual work is material.
- Loading, empty, running, waiting, success, partial success, failure, cancellation, disconnect, and recovery states are designed as applicable.
- A real browser loop reaches a real result; mock-only flows are labeled.
- Target desktop and mobile widths are inspected.
- A clickable review URL is delivered for owner inspection when a page is changed.

### Release-preparation gate

- Authentication and server-side authorization are defined.
- User/tenant data isolation is tested.
- Business data and file assets have durable storage, backup, restore, and retention rules.
- Secrets use controlled storage and are excluded from repository, package, logs, and browser.
- Observability, error handling, rate/cost controls, migration, and rollback are documented and tested proportionally.

### Deployment gate

- User explicitly requested or authorized deployment/publication and any paid resources.
- Local acceptance is not represented as remote success.
- Provider state, application behavior, and public URL are read back after mutation.
- Owner acceptance remains pending until the owner manually reviews the delivered endpoint.

## Stage report

Report in this order:

1. One-sentence conclusion.
2. Completed and evidence.
3. Not completed, known issues, and evidence boundaries.
4. Next owner or agent action.

Avoid collapsing “implemented,” “tests passed,” “deployed,” and “accepted” into a single status.
