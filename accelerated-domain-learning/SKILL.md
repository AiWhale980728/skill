---
name: accelerated-domain-learning
description: Rapidly build a reliable mental map of any unfamiliar domain through scope definition, prerequisite concepts, mental models, concept relationships, consensus and disputes, evidence-aware research, and adaptive depth questions. Use when a user wants to quickly understand, enter, map, or get oriented in a field; prepare for a discussion, decision, project, interview, or course; identify what experts agree and disagree about; or test whether their understanding transfers beyond memorization. Works across scientific, technical, professional, academic, creative, and general-knowledge domains. Do not use for simple factual lookups or requests that only need a direct answer.
---

# Accelerated Domain Learning

Help the learner build a usable cognitive structure in much less time than a conventional linear study path. Treat "accelerated" as an approach, not a promise of mastery within a fixed number of hours.

Optimize for structural understanding, evidence awareness, transfer, and honest uncertainty. Do not optimize for information volume or the appearance of expertise.

## Read the reference

Read [evidence-and-assessment.md](references/evidence-and-assessment.md) before researching disputed or current claims, designing depth questions, evaluating an answer, or declaring a concept mastered.

## Core principles

- Build a map before teaching details.
- Start from the learner's goal and existing mental model.
- Distinguish established knowledge, working models, disputes, and open questions.
- Require the learner to retrieve, explain, compare, and transfer ideas.
- Use errors as diagnostic signals.
- Preserve uncertainty and source boundaries.
- Let the learner's own words drive the final synthesis.
- Adapt depth and question count to the domain; do not force arbitrary quotas.

## Workflow

### 1. Calibrate the learning mission

Ask at most two high-value questions unless the user already supplied the answers:

1. What must the learner be able to explain, judge, or do?
2. What relevant model, concept, or experience do they already have?

Infer the time constraint when possible. Do not administer a broad placement test. Use one concrete probe that can expose the learner's current model.

Define a practical completion target. Prefer observable outcomes such as:

- explain the domain's structure in plain language
- connect its core concepts
- distinguish consensus from dispute
- identify important assumptions and limits
- apply the framework to a new case
- state what remains unknown

Do not promise expertise, certification, exam success, or completion in a fixed number of hours.

### 2. Build the domain map

Create a compact map with six sections:

1. **Scope and boundaries** — what the domain studies or practices, what sits outside it, and where boundaries are contested.
2. **Prerequisite concepts** — the smallest set of ideas required to understand the rest.
3. **Core mental models** — the reusable lenses practitioners use to interpret problems.
4. **Concept relationships** — dependencies, causal links, tensions, levels, or feedback loops.
5. **Consensus and disputes** — what is relatively settled, what is debated, and why disagreement persists.
6. **Unknowns and frontiers** — unresolved questions, evidence gaps, and active developments.

Use as few items as the domain permits and as many as it requires. Explain each item with a concrete example or contrast. Avoid turning the map into an encyclopedia or glossary dump.

When file creation is useful, save the map as `00-domain-map.md`.

### 3. Establish the evidence layer

Research when the domain is current, niche, disputed, consequential, or dependent on precise sources. Prefer primary and authoritative sources. Record claim-level support, publication or update date, and important limitations.

Label material as:

- established fact
- well-supported interpretation
- disputed position
- open question
- inference

Never invent expert consensus, opposing camps, citations, quotations, or source access. Do not create false balance when evidence strongly favors one position.

When file creation is useful, save the evidence record as `01-sources.md`.

### 4. Design depth questions

Generate 5–12 questions based on domain complexity and the learner's goal. Cover several of these forms:

- explain a concept in the learner's own words
- compare concepts that are easy to confuse
- connect ideas across the map
- identify an assumption or boundary condition
- predict what changes when a condition changes
- evaluate a tradeoff
- handle a counterexample
- apply the model to a new situation
- reason cautiously with incomplete evidence

Avoid trivia, vocabulary recall, and questions answered by copying the map. Let the learner choose a starting question unless a prerequisite order matters.

### 5. Run the adaptive learning loop

For each answer:

1. Identify what the learner understands.
2. Locate the most important gap, ambiguity, or unsupported leap.
3. Choose one response:
   - deepen with a changed condition or new implication
   - expose a contradiction with a counterexample
   - separate two confused concepts
   - teach a missing prerequisite directly
   - ask the learner to restate the corrected model
4. Reassess using evidence from the learner's response.
5. Advance only when the idea is usable beyond the original wording.

Do not hide essential information behind endless Socratic questions. Give direct explanations for factual details, after repeated failed attempts, or when the learner requests a direct answer.

Capture useful learner language: explanations, analogies, corrections, and moments of changed understanding. Never fabricate first-person statements on the learner's behalf.

### 6. Integrate and transfer

After enough questions have been explored, ask the learner to:

- explain the overall domain to an intelligent newcomer
- connect the central models rather than list them
- fairly state a major dispute and its evidential basis
- apply the map to a novel example
- identify one remaining uncertainty or weak area

Return to prerequisites when transfer fails. Completion is based on demonstrated structure and transfer, not on finishing every generated question.

### 7. Produce the learning record

When useful, organize outputs as:

```text
topic-accelerated-learning/
├── 00-domain-map.md
├── 01-sources.md
├── 02-progress.md
├── 03-my-understanding.md
└── 04-next-steps.md
```

Make `03-my-understanding.md` primarily from the learner's own explanations, lightly edited for clarity. Include:

- overall model
- core concepts and relationships
- mental models in the learner's words
- consensus, disputes, and unknowns
- misconceptions and corrections
- remaining gaps
- recommended next steps

If no filesystem is available, provide the same structure in conversation. Do not require a particular note-taking product, platform, model, or output directory.

## Session continuity

When a progress record exists, read it before continuing. Track:

- current phase
- questions attempted
- demonstrated strengths
- unresolved misconceptions
- learner-authored explanations
- next best action

Update progress after a meaningful block of work, not after every sentence.

## Boundaries

Do not use this skill for:

- a simple factual lookup
- a narrow procedural question that needs one direct answer
- a request to summarize without a learning goal
- long-term curriculum design where paced mastery learning is the primary need

For medical, legal, financial, safety-critical, or other high-stakes domains, clearly separate education from professional advice and use current authoritative sources.
