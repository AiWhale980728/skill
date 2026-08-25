# Frontend for AI Agent products

Use for Web frontend creation or changes where task states, streaming, artifacts, recovery, or real browser acceptance matter.

## Baseline and boundaries

For a new Web MVP without conflicting constraints, prefer a maintained Next.js App Router release, React, TypeScript strict mode, Tailwind CSS with semantic design variables, a single consistent icon set, Vitest/React Testing Library, Playwright for the core loop, and reproducible locked dependencies.

Preserve an existing reasonable framework and package manager. Do not upgrade major versions or reorganize a working repository merely to match this baseline.

Introduce optional libraries only for demonstrated complexity:

- TanStack Query for shared server data, caching, invalidation, retries, or pagination.
- Zustand for genuinely shared client-only state that does not belong in URL or server state.
- React Hook Form plus Zod for complex/dynamic forms.
- Radix or shadcn/ui for numerous complex accessible controls.
- OpenAPI generation only when the backend contract is stable and maintained.

## Source of truth and state placement

Separate four state categories:

| State | Examples | Default owner |
|---|---|---|
| URL | task ID, tab, filter | Route/query string |
| Server | progress, artifacts, permissions, balance | Backend via API |
| Local UI | draft input, dialog, local selection | Component/local context |
| Preference | theme, sidebar, noncritical hints | User settings or local storage |

Backend state and artifacts are the final facts. Local storage, animations, elapsed time, or a closed stream cannot prove a task succeeded. Refresh by task ID and reconcile with the backend.

## Unified Agent task states

Map backend states into explicit user meanings as applicable:

`idle`, `submitting`, `queued`, `running`, `streaming`, `waiting_user`, `succeeded`, `partially_succeeded`, `failed`, `cancelled`, `disconnected`, and `stale`.

Unknown values get a safe visible fallback and diagnostic evidence; never coerce them silently to success. Each visible state should answer:

1. What is happening?
2. What, if anything, must the user do?
3. What happens next?

Keep loading, empty, failed, denied, and not-found distinct.

## Streaming, polling, cancellation, and recovery

- Prefer SSE/fetch streaming for one-way incremental output, polling when the backend exposes durable status queries, and WebSocket only for true two-way real-time needs.
- Close streams on task switch or page exit. After disconnect, query the task by ID before reconnecting; never create a replacement task blindly.
- Poll with a clear interval/backoff, reduce or pause while hidden, and stop on terminal states.
- Batch streamed UI updates, preserve a user's scroll position, deduplicate reconnection output, and keep internal reasoning/logs separate from user-visible results.
- Browser request cancellation and backend task cancellation are different. Label the control honestly when the backend cannot cancel work.
- Prevent duplicate expensive actions with immediate UI state, server-side idempotency, and lookup-before-retry after uncertain network failure.
- Persist user-confirmation checkpoints. Show completed work, why input is needed, meaningful options and effects, the recommended option, reversibility, and a way back.

## API and error boundary

Centralize base URL, authentication, timeout, retry, streaming, and error normalization. UI components call a feature API, not scattered raw `fetch` calls.

Normalize failures to a safe application error containing at least a code, user-facing message, retryability, and request/task ID when available. Never show raw provider errors, stack traces, secrets, or private payloads.

Public browser configuration may use the framework's public environment mechanism. Model keys, database credentials, private prompts, authorization rules, and admin tokens never enter a public environment variable or client bundle. Hiding a button is not authorization; the backend enforces access.

## Forms, models, uploads, and artifacts

- Show required fields and limits before submit; keep user input after failure.
- Ensure the selected/default model actually exists. Never silently substitute a different model.
- Validate uploads on the backend as well as the client; show progress, failure, retry, replace, and delete-before-submit behavior.
- Give artifacts a common model: ID, kind, name, processing/ready/failed state, preview/download location, type/size/time, and metadata.
- Do not present a processing artifact as final. Handle expired URLs, authorization, cross-origin failures, media loading, and download errors.
- Put final results and next actions first. Raw JSON, request IDs, and diagnostics belong in a secondary details/developer view.

## Visual system and responsive behavior

Respect confirmed design artifacts first, then product/brand requirements, then confirmed references, then a neutral baseline. Do not copy protected assets.

Establish one representative page before broad rollout when the visual direction is not frozen. Use semantic color, typography, spacing, radius, shadow, control, focus, disabled, loading, and error tokens. Avoid premature universal components with excessive parameters.

Unless the PRD says otherwise, inspect the core flow near 390, 768, 1280, and 1440 CSS pixels. On mobile, transform navigation and tables appropriately, keep dialogs scrollable and actions reachable, avoid accidental horizontal scrolling, and target roughly 44 by 44 pixels for touch controls.

Use semantic HTML, labels, keyboard access, visible focus, dialog focus management, non-color-only status, suitable alternative text, adequate contrast, reduced-motion support, and restrained live regions.

For voice or media interaction, verify HTTPS permission behavior, runtime media-format support including iOS/Safari, authenticated media fetching, audio queue cleanup, and a real-device loop. Prefer turn-based voice for an MVP unless full duplex and interruption are explicit requirements.

## Verification and acceptance

Run the project's equivalent of:

```text
lint -> typecheck -> unit/component/integration tests -> production build -> browser E2E/manual inspection
```

Exercise at least one real loop:

```text
enter -> input -> submit -> observe running -> handle confirmation if any
-> view real artifact -> refresh/recover
```

Inspect console, network, duplicate requests, every relevant state, scrolling, menus/dialogs, media, return/navigation, disconnect/recovery, desktop, and mobile. A build or mock page is not acceptance.

For every page/visual change, provide a verified clickable review URL and keep the preview available for owner inspection when feasible. Automated browser QA supports delivery but does not replace manual owner acceptance.

Do not announce completion while unexplained lint/type/build failures remain, the core interface is mocked, target sizes are unusable, duplicate submission is possible, recovery is missing, or the implementation materially conflicts with accepted product/design intent. If the owner accepts a staged exception, record the issue, impact, workaround, and follow-up.
