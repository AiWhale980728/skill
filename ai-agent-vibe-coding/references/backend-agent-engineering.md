# Backend and Agent engineering

Use for core Agent development, backend APIs, prompts, model calls, persistence, and backend validation.

## Baseline for a new project

When no existing platform constraint applies, prefer:

- A currently maintained Python runtime compatible with the target environment.
- FastAPI for HTTP/API delivery, Pydantic for contracts and model-output validation, and pytest for deterministic tests.
- Git plus one reproducible dependency definition and lock strategy.
- Official or verified-compatible model SDKs.

Keep an existing reasonable stack. Record actual versions; do not force the handbook's historical versions onto a current project.

Add SQLAlchemy and Alembic when relationships, transactions, concurrent updates, or durable schema migration require a relational database. Add queues, vector databases, OCR, or dynamic Agent planners only when the product requires them.

## Layering

Keep these concerns separate even if folder names differ:

```text
API or automated entry point
  -> application/domain service
  -> Agent/model/tool adapters
  -> repositories and asset storage
```

- Reusable business rules stay out of routes and frontend components.
- Prompts live in versioned, reviewable resources rather than long strings embedded in endpoints.
- Model/provider names, endpoints, timeouts, budgets, and parameters come from configuration.
- Client initialization failures, request failures, timeouts, rate limits, parsing failures, and exhausted retries converge on a controlled error contract.

## API contracts and long tasks

Every interface defines request, success response, errors, authentication, authorization, idempotency, timeout, and retry behavior.

Long tasks must have a persistent task ID and recoverable state. Choose one of:

- SSE or fetch streaming for server-to-client incremental output.
- Submit task, poll status, and fetch result for durable asynchronous work.
- WebSocket only for genuine bidirectional, high-frequency interaction.

For SSE, terminate every stream with either a final `done` event or an `error` event. Use the same safe error shape as ordinary API responses. Do not silently disconnect or expose a stack trace.

## State and persistence

- Persist important business data, human-confirmation checkpoints, task state, and produced artifacts when they must survive restart or client changes.
- Use explicit, controlled state values and documented transitions. Add unknown-state fallbacks for older/newer clients.
- A structured-file store needs schema versioning, atomic writes, corruption handling, concurrency boundaries, and a migration path.
- Store large images, audio, video, and documents in a file/object store; store their metadata, ownership, and lifecycle in structured storage.
- Important deletes require confirmation; production systems usually need soft-delete or audit evidence.

## Model output and prompts

Treat model output as untrusted:

1. Specify a machine-checkable output contract.
2. Include positive examples and clarify common forbidden variants when format matters.
3. Parse common equivalent forms where safe; do not waste repeated calls on harmless formatting variation.
4. Validate deterministically with a schema.
5. Retry only a bounded number of times for retryable failures.
6. Separate structural failure from subjective content quality. Product-quality tolerance belongs to owner acceptance, not an infinite parser retry loop.

Record model identity/version, latency, token/cost data when available, and error type without logging secrets or sensitive source content.

## Agent autonomy boundary

- Use deterministic state machines for fixed, high-risk, or compliance-sensitive workflows.
- Allow dynamic tool selection only when it is product-essential and bounded by a tool allowlist, validated parameters, budget, maximum steps, timeout, permission checks, and persistent human-confirmation points.
- External sending, publication, paid calls beyond an accepted budget, deletion, overwrite, and other irreversible actions require deterministic controls and the appropriate user authorization.

## Configuration, files, and safety

- Secrets are server-side only. Local secrets may use an ignored `.env`; commit only a redacted `.env.example`. Production secrets use the platform's controlled secret mechanism.
- If users enter provider keys through a UI, transmit them only to a protected backend, store them according to the product's security level, redact responses, and exclude them from logs.
- Validate upload size, extension, actual content type, and safe filename. Prevent path traversal; add malware/content isolation where risk requires it.
- Do not log full private documents, prompts, credentials, or raw provider errors containing sensitive content.

## Two-layer model validation

### Offline/mock layer

Run on every relevant stage. Cover business rules, state transitions, input validation, parsers, error mapping, idempotency, recovery, and permission boundaries. Model calls are mocked so this layer is reproducible offline.

### Real-provider smoke layer

Before claiming a critical Agent contract is verified, exercise at least one real path for each materially different model contract:

```text
real input -> real provider -> deterministic validation -> persistence/return -> user-viewable result
```

Record provider/model, time, cost where observable, result, and coverage mapping. Also test realistic authentication, timeout/rate-limit behavior proportionally. For a stream, confirm first output timing and a valid `done` or `error` terminator.

If a usable credential is absent, continue safe implementation with mocks but mark the real-provider gate pending. Never promote mock evidence to real validation.

## Completion check

- Relevant services start using documented commands.
- Deterministic tests pass.
- Real-provider smoke passes or is explicitly pending.
- Critical API/Agent loop is observable independently of a polished frontend.
- README or equivalent runbook records startup, configuration keys without values, and verification steps.
- Temporary services are stopped unless the user asked to retain a preview.
