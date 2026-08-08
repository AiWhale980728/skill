# AI Product Extension

Use this module whenever model output is probabilistic, generated, classified, ranked, retrieved, transformed, or recommended. Do not load the Agent extension unless the system also chooses actions or tools autonomously.

## AI capability inventory

For each model-assisted capability define:

| Field | Requirement |
|---|---|
| User outcome | Why AI is used |
| Input | User data, context, and limits |
| Output | Format, content, and confidence behavior |
| Trigger | User or system event |
| Model responsibility | What the model may decide |
| Deterministic responsibility | What code or rules must enforce |
| Human control | Review, edit, approve, retry, or reject |
| Fallback | Behavior when AI is unavailable or unsuitable |
| Measurement | Quality, latency, cost, and safety metrics |

Do not prescribe a provider or model unless it is a fixed constraint or a justified recommendation.

## Input and context

Specify:

- accepted modalities and formats
- required and optional context
- context source and freshness
- truncation or prioritization
- sensitive data handling
- prompt-injection boundaries
- user control over included data

## Output contract

Define:

- human-readable or structured format
- required fields and allowed values
- citations or provenance where applicable
- uncertainty and abstention behavior
- editable and regenerable portions
- length, language, tone, and policy boundaries
- validation performed outside the model

Never rely on prompt wording alone for authorization, security, schema enforcement, financial calculation, or irreversible behavior.

## Experience states

Cover:

- generating and streaming
- partial result
- cancellation
- timeout
- refusal
- insufficient information
- unsafe or unsupported request
- low-confidence result
- model or provider failure
- retry and alternate path

Tell the user what happened and what they can do next without exposing hidden reasoning.

## Quality evaluation

Define a representative evaluation set and metrics appropriate to the capability:

- task success or usefulness
- factuality and grounding
- relevance
- instruction and format adherence
- safety and policy compliance
- consistency
- latency
- cost
- human correction or rejection rate

Include slices for important user groups, languages, input lengths, risk levels, and edge cases. Set launch thresholds and regression guardrails when known.

## Safety and governance

Define:

- prohibited uses
- harmful or sensitive-content behavior
- privacy and retention
- user disclosure
- human review thresholds
- red-team scenarios
- logging and audit boundaries
- model or prompt change management

## Prompt requirements

A PRD should normally describe prompt responsibilities, variables, constraints, and output contracts. Put full production prompts in a separate versioned prompt specification when they are long, frequently changed, security-sensitive, or independently evaluated.
