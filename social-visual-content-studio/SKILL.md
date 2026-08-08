---
name: social-visual-content-studio
description: Turn keywords, notes, articles, links, files, screenshots, charts, and mixed media into trustworthy, platform-ready visual social content. Use when a user wants to evaluate raw material, choose a publishable angle, select a platform and format, research and fact-check a topic, create a carousel or short-video plan, generate images or production prompts, review drafts, or write captions for platforms such as Xiaohongshu, Instagram, LinkedIn, TikTok, Reels, Shorts, or similar channels. Supports any subject, audience, language, brand, and visual style.
---

# Social Visual Content Studio

Treat inputs as raw material, not as a predetermined topic. Make an editorial recommendation before production, then adapt the story, format, and visual system to the user's audience, platform, and brand.

## Read the relevant references

- Read [editorial-workflow.md](references/editorial-workflow.md) when ingesting material, researching, selecting a topic, or planning a story.
- Read [platform-formats.md](references/platform-formats.md) when choosing a channel, carousel dimensions, video format, or safe zones.
- Read [visual-production.md](references/visual-production.md) before generating visuals, writing prompts, or defining a reusable visual system.
- Read [copy-and-qa.md](references/copy-and-qa.md) before writing publish copy or approving final deliverables.

## Operating principles

### Separate material from topic

Map claims, opinions, examples, evidence, repetition, age, sensitive information, and visual cues across every input. Do not reproduce the input's order or assume the user already chose the strongest angle.

### Make an editorial recommendation

Unless the user already specified the direction, provide:

1. One recommended topic and two alternatives.
2. A target audience and one memorable takeaway.
3. A recommended platform and format: carousel, short video, both, or do not publish yet.
4. The reason, exclusions, risks, and evidence still needed.

Ask only one decisive question when missing information would materially change the recommendation. Continue directly when the user authorizes editorial autonomy.

### Preserve truth and provenance

- Distinguish verified facts, source claims, user opinions, and creative interpretation.
- Verify time-sensitive or consequential claims with current primary sources when browsing is available.
- Never invent testing, installation, usage, performance, endorsements, or personal experience.
- Do not claim an image or video exists when only a plan or prompt package was produced.
- Avoid close paraphrase of copyrighted source material; create a new structure and expression.

## Workflow

### 1. Build a material map

Read each modality with an appropriate tool. Connect related items across text, files, screenshots, charts, and links. Record the result in `materials.md`, including source, date, type, confidence, risk, visual cue, and intended use.

### 2. Select the story and format

Extract 3–7 content signals and assess audience value, novelty, credibility, story potential, visual potential, platform fit, differentiation, and safety. Recommend one direction; do not hand an unranked option list back to the user.

Use a carousel when comparison, density, saving, or rereading matters. Use short video when motion, process, demonstration, personality, or timing is essential. Recommend both only when each format has a distinct job. Recommend waiting when evidence, originality, audience value, or safety is inadequate.

Write the recommendation to `topic-analysis.md`. If the user requested execution and no decisive ambiguity remains, proceed without another approval gate.

### 3. Research and define boundaries

Answer what the subject is, why it matters, how it works, who it helps, what it does not solve, and what conditions or tradeoffs apply. Prefer primary sources and corroborate important claims. Save URLs, access dates, claim-level conclusions, and limitations in `sources.md`.

### 4. Define a content brief

Before storyboarding, set or infer:

- platform and placement
- audience and desired action
- language and tone
- brand identity, visual style, and required assets
- format, dimensions, length, and accessibility needs
- required, prohibited, or sensitive content

If no brand system exists, propose a lightweight one for this project. Do not silently impose the original creator's identity, colors, year, logo, or signature.

### 5. Storyboard before generating

For every page or shot, define one audience takeaway, its role in the sequence, the visual action, exact on-screen text, supporting source, and factual boundary. Prefer a causal arc such as problem → intervention → result and tradeoff. Vary compositions when the story benefits; consistency does not mean identical layouts.

Save the plan to `storyboard.md`. Keep text short enough for the chosen platform and mobile viewing.

### 6. Produce with capability-aware fallbacks

- With an image tool: generate the first key visual, inspect it, lock the visual system, then produce the remaining set incrementally.
- Without an image tool: deliver self-contained prompts with dimensions, layout, exact text, visual roles, constraints, and negative instructions.
- With a video tool: create and inspect shots, assemble them, and verify timing and continuity.
- Without a video tool: deliver a complete production package: shot list, voiceover, captions, keyframe prompts, motion prompts, transitions, audio notes, asset list, and cover.

Preserve originals. Save revisions as `-v2`, `-v3`, and so on.

### 7. Review every asset

Inspect images at original resolution. Inspect video framing, key moments, captions, pacing, continuity, and audio timing. Verify exact text, facts, source alignment, accessibility, safe zones, visual consistency, and declared platform specs. Mark each asset `pass` or `revise`; fix the highest-impact problem first.

### 8. Complete the publishing package

Deliver one recommended title or hook, two alternatives, the post caption, relevant tags or keywords, alt text for still images, and—when applicable—voiceover, captions, cover copy, and source disclosure. Match the copy to what the assets actually show.

## Default project structure

```text
deliverables/YYYYMMDD-topic/
├── materials.md
├── topic-analysis.md
├── sources.md
├── content-brief.md
├── storyboard.md
├── copy.md
├── prompts/
├── images/
└── video/
```

Reference original large files by path instead of duplicating them unnecessarily.

## Completion criteria

- The chosen topic is an editorial decision, not a summary of the input.
- Platform and format choices have explicit reasons.
- Claims, dates, sources, and boundaries are traceable.
- Brand and visual choices are user-specific or clearly proposed defaults.
- Every page or shot has one clear job and readable mobile text.
- Every generated asset has been reviewed individually.
- Copy, visuals, sources, and stated deliverables agree.
- Originals and revisions are preserved non-destructively.
