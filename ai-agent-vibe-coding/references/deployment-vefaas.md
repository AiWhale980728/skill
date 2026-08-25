# Deployment and Volcengine veFaaS

Use only when public release, production preparation, deployment diagnosis, or post-launch verification is in scope.

The user-authored deployment handbook uses Volcengine veFaaS plus API Gateway and TOS as the default for a small AI Agent product without company infrastructure. Treat this as a baseline, not an irreversible platform mandate. Existing company infrastructure, compliance constraints, data residency, scale, and accepted deployment choices take precedence.

## Before any mutation

1. Confirm the MVP/core loop and formal frontend acceptance state separately.
2. Inspect the actual repository, deployment config, runtime compatibility, current provider resources, region, account/identity, IAM permissions, billing implications, and remote history.
3. Read the installed `vefaas` skill and current official provider guidance when available. Verify CLI syntax, supported runtimes, service eligibility, endpoints, and limits on the day of deployment.
4. Produce a product-language release summary: public entry point, authentication, durable data, file storage, observability, estimated cost class, migration/rollback, and owner actions.
5. Obtain authorization for paid-resource creation, cloud mutation, public release, or destructive cleanup when it is not already explicit.

Do not ask the user to paste AK/SK or another secret into chat. Prefer an approved local credential store, provider login flow, or platform secret injection. Never echo secret values.

## Responsibility boundary

The owner may need to register or authenticate the cloud account, complete identity verification, approve billing, grant scoped IAM permissions, and perform account-admin console actions. Give one short, screen-specific action at a time and continue inspecting safely while waiting.

Use least privilege. The historical handbook lists service-level FullAccess policies for quick bootstrap; do not apply them automatically. Request only resources needed by the selected design and document removal/downscoping after bootstrap.

## Release-preparation invariants

- Secrets are excluded from Git, build contexts, packages, browser bundles, command output, and logs.
- Packaging exclusions cover local environments, data, caches, test artifacts, `.env`, and deployment-local configuration as applicable. Verify the actual package contents or exclusion mechanism.
- The server listens on the platform-provided interface/port and uses a startup command compatible with the actual project layout.
- Production configuration is installed before first release when startup depends on it.
- Business data and task state are durable and restorable; large files use object storage.
- Authentication, server-side authorization, and user/tenant isolation are tested.
- Structured logs carry request/trace IDs without sensitive raw content; errors are observable and actionable.
- Database/storage migration and rollback are explicit.

## Historical veFaaS baseline to verify

The source handbook used these patterns. Check the current CLI help and official skill before executing them:

```text
vefaas inspect
vefaas gateway list --first
vefaas env set ...
vefaas deploy ...
vefaas domains
vefaas fn scale --id <function-id> --min 1
```

For a FastAPI layout whose entry is `app/main.py`, the historical reliable startup form was:

```text
python -m uvicorn app.main:app --host 0.0.0.0 --port 8000
```

Auto-detection is evidence, not authority. Resolve the real app entry and test the exact production command locally or in an equivalent environment.

The historical runtime allowed writes only under `/tmp`. Verify the current runtime filesystem. If `/tmp` remains ephemeral, it is not primary durable storage.

## Data durability decision

Choose and document an explicit recovery point objective (RPO), recovery time objective (RTO), retention, and restore test.

- Prefer a managed relational database or accepted company data platform for production user/business data when eligibility and budget permit.
- An always-warm function plus SQLite under ephemeral storage and periodic object-store backup is only an early-beta fallback. It does not turn ephemeral storage into a database guarantee. Use it only with owner acceptance of the loss window, tested restore, single-writer/concurrency limits, and a migration plan.
- Store audio, images, video, and large documents in TOS or another object store. Store metadata and ownership in structured durable storage. Verify current regional endpoints and SDK addressing/signature requirements from official docs.

## Frontend deployment

Deploy frontend and backend as separately verifiable applications when the platform design requires it. For Next.js standalone output, verify that static/public assets are included and that the runtime command matches the produced directory.

Treat variables used by rewrites or static generation as build-time inputs when the framework resolves them during build. Runtime secret configuration cannot retroactively alter a compiled public value. Prefer same-origin API proxying when it materially simplifies browser authentication and CORS, but verify normal and streaming routes through the full deployed path.

HTTPS is required for browser capabilities such as microphone and camera outside localhost.

## Deployment sequence

Adapt the exact commands to current evidence:

1. Validate local tests, build, production startup, migrations, and package exclusions.
2. Resolve or create the approved gateway/entry resource in the chosen region.
3. Install non-secret configuration and platform secrets before the first startup that needs them.
4. Deploy the backend without combining unrelated risky changes.
5. Read back provider state and exercise health plus a real API/Agent path.
6. Configure scaling only after an initial deployed version exists, if the current platform still requires that order.
7. Deploy the frontend with the verified backend target/build inputs.
8. Read back the public URLs and test browser/API behavior, authentication, streaming, files, and target device capabilities.
9. Exercise isolation, persistence, backup, restore, logging, alerting, and rollback.
10. Deliver the public entry point and a nontechnical owner acceptance checklist. Keep owner acceptance pending until performed.

Do not use “the URL opens” as the sole success criterion. It proves reachability, not login, isolation, durability, observability, or the core Agent loop.

## Diagnosis patterns

Verify rather than blindly copying these historical causes:

| Symptom | Check |
|---|---|
| Framework/entry not detected | Resolve real entry and set an explicit startup command |
| Executable not found | Prefer module invocation when supported; confirm it is packaged |
| Read-only filesystem | Locate writes; move transient files only to a supported writable path and durable data to durable storage |
| Huge or secret-containing package | Inspect ignore rules and built artifact contents |
| Access denied | Identify account type, action, resource, region, and missing least-privilege policy |
| Release already rolling | Read release state; avoid repeated deploys; use provider-supported abort only after inspecting impact |
| Public page opens but API fails | Verify frontend build-time backend target, proxy/stream routing, auth cookies/headers, and CORS |
| Data disappears after idle/restart | Prove actual storage class, scaling behavior, backup freshness, and restore path |

## Remote acceptance evidence

Verify separately:

- Provider reports the intended version/configuration.
- Public URL is reachable over HTTPS.
- Authentication rejects invalid/unauthenticated access appropriately.
- User A cannot access user B data.
- A real core Agent loop succeeds through the deployed path.
- Refresh/relogin/restart behavior matches the persistence claim.
- Files are durable and access-controlled.
- Logs and alerts contain a trace/request ID and omit sensitive content.
- Rollback or recovery procedure is executable.

Report remote verification, owner acceptance, and target-user beta as three different states.
