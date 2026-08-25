# Skill

A collection of reusable AI Agent Skills for personal use. This repository maintains instructions, workflows, and supporting resources for Codex, Claude Code, and other agents compatible with the Skills format.

## Repository Structure

Each Skill lives in its own top-level directory. The directory name must match the `name` in its `SKILL.md`:

```text
skill/
├── README.md
└── <skill-name>/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    ├── references/
    ├── scripts/
    └── assets/
```

Other than `SKILL.md`, add `agents/`, `references/`, `scripts/`, or `assets/` only when the Skill actually needs them.

### Cross-Platform Compatibility

- `SKILL.md` is the cross-platform core of a Skill. It defines triggering conditions and the primary workflow.
- `references/`, `scripts/`, and `assets/` contain supporting resources loaded only when needed.
- `agents/openai.yaml` is optional Codex/OpenAI product metadata for display names, short descriptions, default prompts, and other interface features.
- Claude Code does not depend on `agents/openai.yaml`; this file neither replaces nor changes the universal instructions in `SKILL.md`.
- A Skill may include optional adapters for multiple agent platforms, but its core workflow should not depend on any single platform.

## Skills

### accelerated-domain-learning

Accelerated Domain Learning helps learners build a reliable mental map of an unfamiliar field quickly, then tests genuine understanding through evidence checks, deep questions, and adaptive follow-ups.

Key capabilities:

- Calibrate the learning goal, existing knowledge, and observable completion criteria.
- Establish domain boundaries, prerequisites, mental models, and concept relationships.
- Distinguish consensus, major debates, open questions, and frontier directions.
- Select evidence sources by knowledge type and label facts, opinions, and inferences.
- Generate explanation, distinction, boundary, counterexample, transfer, and evidence-evaluation questions.
- Locate misconceptions, repair missing prerequisites, and adapt the depth based on the learner's answers.
- Produce a cognitive summary and continued learning path in the learner's own language.
- Support scientific, technical, humanities, professional-practice, and general-knowledge domains.

Directory: [accelerated-domain-learning](./accelerated-domain-learning/)

### prd-writer

Universal PRD Writer turns product ideas, business needs, feature requests, and existing specifications into product requirements that can be reviewed, accepted, and implemented.

Key capabilities:

- Use one requirements core for standard digital products, AI products, Agent products, and multi-Agent systems.
- Adjust output depth based on audience, product type, requirement size, and deliverable.
- Define the problem, users, goals, scope, flows, features, metrics, risks, and acceptance criteria consistently.
- Load standard interaction, AI capability, Agent behavior, and Coding Spec modules only when needed.
- Distinguish confirmed requirements, assumptions, recommendations, risks, dependencies, and pending decisions.
- Derive implementation specifications for Codex, Claude Code, Cursor, and other coding agents.
- Audit existing PRDs for completeness, consistency, testability, and AI/Agent safety boundaries.
- Avoid hard-coded platforms, frameworks, authors, directories, and unnecessary template expansion.

Directory: [prd-writer](./prd-writer/)

### ai-agent-vibe-coding

AI Agent Vibe Coding advances an approved PRD or an existing AI Agent codebase into a staged, testable, reviewable, and deployable product.

Key capabilities:

- Determine whether the product is in technical adaptation, core Agent loop, formal frontend, release preparation, or deployment.
- Choose between a backend-first path and a vertical slice based on the product's interaction model.
- Define Agent states, persistence, prompts, model-output validation, tool permissions, and human confirmation points.
- Design streaming, polling, failure, cancellation, disconnection, recovery, and multimedia artifact experiences.
- Keep mock testing, real-model smoke tests, browser verification, remote deployment, and product-owner acceptance separate.
- Provide templates for technical adaptation, staged implementation, state matrices, acceptance checklists, and delivery reports.
- Support Volcengine veFaaS as a default deployment reference while requiring current official verification on the day of deployment.
- Protect credentials, data isolation, backup and restore, cost authorization, and external-write boundaries.

Directory: [ai-agent-vibe-coding](./ai-agent-vibe-coding/)

### social-visual-content-studio

Social Visual Content Studio turns keywords, notes, articles, links, files, screenshots, charts, and mixed source material into trustworthy, clear, publishable social-media visuals.

Key capabilities:

- Extract valuable topics from raw source material instead of mechanically summarizing it.
- Recommend a target audience, platform, and carousel or short-video format.
- Research, verify, and record factual sources and content boundaries.
- Produce complete storyboards for carousels, visual notes, and short videos.
- Build a visual system and generation prompts aligned with the user's brand.
- Review every slide or shot for factual accuracy, wording, readability, and platform fit.
- Deliver titles, body copy, tags, alt text, voice-over, and captions.
- Support channels such as RedNote, Instagram, LinkedIn, TikTok, Reels, and Shorts.

Directory: [social-visual-content-studio](./social-visual-content-studio/)

## Installation

### Codex

Copy the complete directory of each Skill you want to use into the Codex Skills directory:

```bash
cp -R accelerated-domain-learning ~/.codex/skills/
cp -R prd-writer ~/.codex/skills/
cp -R ai-agent-vibe-coding ~/.codex/skills/
cp -R social-visual-content-studio ~/.codex/skills/
```

Restart or reload Codex. Invoke a Skill explicitly by name, or let it trigger automatically when the request matches its `description`.

### Claude Code

Copy the complete directory of each Skill into the Claude Skills directory, for example:

```bash
cp -R accelerated-domain-learning ~/.claude/skills/
cp -R prd-writer ~/.claude/skills/
cp -R ai-agent-vibe-coding ~/.claude/skills/
cp -R social-visual-content-studio ~/.claude/skills/
```

Paths and supported behavior may vary by client version. Follow the current documentation for the client you use.

## Composed Workflows

These Skills can run independently or in sequence. The output of one phase can become the input to the next, reducing repeated context gathering while keeping research, product definition, engineering, and content consistent.

### From an Unfamiliar Domain to Product Requirements

```text
accelerated-domain-learning
        ↓
     prd-writer
```

1. Use `accelerated-domain-learning` to build a domain map covering core concepts, evidence, debates, and unknowns.
2. Use `prd-writer` to inherit confirmed research findings and define target users, product scope, functional requirements, and acceptance criteria.
3. When implementation is next, let `prd-writer` derive a Coding Spec.

Example:

```text
I want to build an AI product that helps people understand their personal carbon footprint.

First, use $accelerated-domain-learning to map the carbon-accounting field
and distinguish industry consensus, major debates, and unresolved questions.

Then use $prd-writer to turn the confirmed research into an MVP PRD,
clearly separating inherited facts, product assumptions, and open questions.
```

### From Product Requirements to Published Content

```text
prd-writer
     ↓
social-visual-content-studio
```

1. Use `prd-writer` to define product positioning, target users, core features, value, and capability boundaries.
2. Use `social-visual-content-studio` to turn the approved product information into a carousel or short video for the target platform.
3. Keep every product claim, data point, and limitation consistent with the PRD.

Example:

```text
First, use $prd-writer to define the MVP PRD for this AI meeting assistant.

Then use $social-visual-content-studio to create a LinkedIn carousel
based on the approved users, core value, and capability boundaries.
Do not present unverified assumptions as implemented features.
```

### From Product Requirements to a Reviewable AI Agent Product

```text
prd-writer
     ↓
ai-agent-vibe-coding
```

1. Use `prd-writer` to define target users, product scope, Agent behavior, risk boundaries, and acceptance criteria.
2. Use `ai-agent-vibe-coding` to inspect the approved PRD and current code, produce a technical adaptation, and choose a backend-first or vertical-slice path.
3. Advance the core Agent, formal frontend, real-model verification, and release preparation through real user loops, preserving separate evidence for testing, deployment, and owner acceptance.

Example:

```text
First, use $prd-writer to turn this research Agent idea into a reviewable MVP PRD.

After the PRD is approved, use $ai-agent-vibe-coding to inspect the current code,
state a concise technical adaptation, and complete the first real, recoverable,
reviewable Agent loop. Do not use mock output or a successful build
as evidence of real-model behavior or product-owner acceptance.
```

### From Domain Research to Product Definition and Content Publication

```text
accelerated-domain-learning
        ↓
     prd-writer
        ↓
social-visual-content-studio
```

This end-to-end workflow supports entering a new field and turning it into a product direction:

1. Build a domain model and evidence base.
2. Turn the opportunity into reviewable, testable product requirements.
3. Turn confirmed product information into trustworthy publication content.

At every phase, distinguish confirmed facts, reasonable inferences, product assumptions, and open questions so downstream Skills do not treat unverified information as fact.

## Usage Examples

### Accelerated Domain Learning

```text
Use $accelerated-domain-learning to help me understand behavioral economics.
Build the domain map first, then test my understanding with deep questions.
```

```text
I have a quantum-computing discussion in two days and only know basic physics.
Build a reliable mental framework and identify the consensus, debates, and unknowns.
```

### Universal PRD Writer

```text
Use $prd-writer to turn this product idea into an MVP PRD
for product and engineering review.
```

```text
Write a PRD for this research Agent. Define tool permissions, context,
human confirmation, failure recovery, and evaluation metrics,
then derive a Coding Spec that Codex can implement.
```

### Social Visual Content Studio

```text
Use $social-visual-content-studio to analyze these articles and screenshots,
recommend the strongest topic, platform, and content format,
then produce the complete creation plan.
```

```text
Turn this industry report into a LinkedIn carousel.
Verify the key data first, then deliver the content brief and slide-by-slide storyboard.
```

```text
Turn this product demo into a 45-second vertical short video.
Deliver the shot list, voice-over, captions, and keyframe prompts.
```

### AI Agent Vibe Coding

```text
Use $ai-agent-vibe-coding with this approved PRD and existing code.
Identify the current phase and complete the next smallest real Agent loop.
Report mock tests, real-model smoke tests, browser verification,
and product-owner acceptance as separate states.
```

## License

This repository is licensed under the [PolyForm Noncommercial License 1.0.0](./LICENSE).

You may use, study, modify, and redistribute the material for permitted noncommercial purposes under the license terms. Commercial use requires separate permission from the repository owner.

This summary is provided for convenience and does not replace the full license text.
