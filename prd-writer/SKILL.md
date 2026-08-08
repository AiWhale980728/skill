---
name: prd-writer
description: Turn product ideas, business needs, feature requests, and existing specifications into clear, testable product requirements. Use when a user asks to write, revise, audit, or structure a PRD, product requirements document, feature specification, product design document, AI product specification, Agent product specification, MVP scope, or an implementation-ready specification for Codex, Claude Code, Cursor, or another coding agent. Supports conventional digital products, AI-powered features, autonomous Agents, multi-Agent systems, and optional coding specifications through one shared requirements workflow. Do not use for market validation that belongs in a BRD/MRD or for implementing code unless the user also requests implementation.
---

# PRD Writer

Transform an idea into the smallest set of requirements needed for the intended readers to make decisions, build, test, or approve the product. Use one shared product-requirements core and load only the extensions the product actually needs.

## Choose the output

Determine four dimensions from the request and existing context:

1. **Reader** — leadership or business, product and design, engineering, or a coding agent.
2. **Product type** — conventional digital product, AI-powered product, Agent product, or multi-Agent platform.
3. **Scope** — one feature, MVP, complete product, or iteration of an existing product.
4. **Deliverable** — brief, formal PRD, AI/Agent PRD, coding specification, or PRD plus coding specification.

Ask one decisive question only when the answer changes the document materially. Otherwise state the inferred configuration and proceed.

## Load references progressively

Always read [core-prd.md](references/core-prd.md).

Then load only what applies:

- Read [standard-product.md](references/standard-product.md) for interfaces, deterministic workflows, roles, permissions, notifications, or conventional system behavior.
- Read [ai-product.md](references/ai-product.md) when the product calls a model or produces probabilistic output.
- Read [agent-product.md](references/agent-product.md) only when the system plans steps, chooses tools, acts on external state, maintains memory, or coordinates multiple Agents.
- Read [coding-spec.md](references/coding-spec.md) only when the output must be directly executable by a coding agent or engineering implementation is explicitly requested.
- Read [quality-checks.md](references/quality-checks.md) before final delivery or when auditing an existing specification.

Use this composition rule:

```text
Conventional product = Core + Standard
AI-powered product   = Core + Standard + AI
Agent product        = Core + Standard + AI + Agent
Implementation spec = Relevant requirements modules + Coding Spec
```

Do not load Agent requirements merely because the product uses an LLM. A single model call that generates, classifies, summarizes, searches, or recommends is an AI capability, not automatically an Agent.

## Workflow

### 1. Inspect available context

Read relevant user materials and existing product documents before asking questions. When BRD, MRD, research, analytics, design files, architecture notes, or prior requirements exist:

- inherit supported decisions
- preserve source links or identifiers
- identify conflicts and stale assumptions
- do not silently invent missing business evidence
- distinguish inherited requirements from new recommendations

### 2. Establish the requirements baseline

Capture or infer:

- problem and why it matters now
- target users and primary situations
- current workaround or competing behavior
- desired outcome and measurable success
- scope, constraints, dependencies, and non-goals
- product maturity and existing-system impact

When critical information is unavailable, either ask one focused question or record an explicit assumption with its validation need. Do not block progress on information that can be safely marked as an assumption.

### 3. Define scope before detail

Write a one-sentence product definition and separate:

- must have
- should have
- later
- explicitly out of scope

Keep an MVP coherent and testable. Do not use "MVP" to mean a complete roadmap compressed into one release.

### 4. Build the shared PRD

Follow [core-prd.md](references/core-prd.md). Define user outcomes, end-to-end flows, functional requirements, business rules, states, edge cases, data needs, non-functional requirements, measurement, risks, dependencies, rollout, and acceptance criteria.

Use requirement IDs when the document is medium or large. Keep each requirement atomic and testable.

### 5. Add conditional product modules

Add only the requirements that change system behavior:

- conventional interface and system behavior from [standard-product.md](references/standard-product.md)
- probabilistic AI behavior from [ai-product.md](references/ai-product.md)
- autonomous execution and tool behavior from [agent-product.md](references/agent-product.md)

Avoid repeating shared material in each extension. Link to the governing core requirement instead.

### 6. Derive an implementation specification when needed

Treat a coding specification as a downstream view of confirmed product requirements, not a substitute for them. Follow [coding-spec.md](references/coding-spec.md). Include concrete technical decisions only when known, required, or explicitly delegated to the writer.

Label implementation choices as:

- fixed constraint
- recommended default
- open decision

Do not fabricate repository state, framework versions, credentials, APIs, schemas, or infrastructure.

### 7. Review and deliver

Run [quality-checks.md](references/quality-checks.md). Resolve contradictions and missing acceptance criteria before delivery. Report remaining assumptions, open decisions, and risks separately from confirmed requirements.

When files are useful, use a structure proportional to size:

```text
Small feature: PRD.md

Larger product:
product-spec/
├── README.md
├── 01-core-prd.md
├── 02-standard-product.md      # when applicable
├── 03-ai-capabilities.md       # when applicable
├── 04-agent-behavior.md        # when applicable
├── 05-coding-spec.md           # when requested
└── decisions-and-assumptions.md
```

Do not create empty modules. Use relative links and keep one source of truth for every decision.

## Interaction style

- Guide a vague request one high-value question at a time.
- For a detailed request, summarize assumptions and draft directly.
- Do not require confirmation after every section unless the user requests a workshop process.
- Prefer concrete language: "When X occurs, the system must Y" and "Given/When/Then."
- Separate requirements from examples, recommendations, and implementation choices.
- Preserve the user's terminology unless it creates ambiguity.
- Never present guessed information as user research or an approved decision.

## Boundaries

A PRD defines what outcome and behavior the product must deliver. A coding specification defines enough implementation detail to build it. A prompt, architecture document, test plan, runbook, or design system may be linked or derived, but should not be embedded in full unless necessary for unambiguous execution.
