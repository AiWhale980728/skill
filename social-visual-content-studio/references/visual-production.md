# Visual production

## Build a project-specific visual system

Define these before generation:

- audience impression: e.g. credible, warm, playful, premium, technical
- medium: photography, editorial illustration, collage, diagram, 3D, UI capture, or mixed
- palette and contrast
- typography roles
- composition and spacing
- recurring character, object, motif, or none
- logo, signature, date, and attribution rules
- prohibited motifs and brand conflicts

Use user-provided brand assets when available. If none exist, propose a temporary system and label it as a proposal. Never inherit a previous creator's portrait, signature, year, corner labels, or personal palette.

## Reference-image roles

Assign one explicit responsibility to each reference image: identity, medium, typography, palette, layout, product accuracy, or series continuity. State that old text, subjects, logos, and props must not be copied unless requested.

## Prompt structure

Every production prompt should include:

```text
Purpose and platform:
Canvas and safe area:
Audience takeaway:
Reference-image responsibilities:
Subject, scene, action, and emotion:
Composition and hierarchy:
Visual medium, palette, texture, and lighting:
Exact allowed on-image text:
Factual boundaries and required details:
Accessibility requirements:
Prohibited elements:
Output filename:
```

List on-image wording exactly and prohibit extra text. Prefer adding critical copy in a layout tool when the image model cannot reliably render it.

## Incremental generation

Generate a key visual first. Inspect identity, composition, readability, style, and factual depiction. Lock only the choices that passed, then create the next representative inner asset. Produce the remaining set after both are stable.

Change one major variable per revision. Preserve rejected or superseded files with version suffixes so decisions remain traceable.

## Video production package

When no end-to-end video tool is available, include:

- overall duration, aspect ratio, frame rate, and safe zones
- hook and shot table
- complete conversational voiceover
- timed caption text or SRT
- keyframe prompt per shot
- motion and camera prompt per shot
- required screenshots, recordings, footage, music, and effects
- cover prompt and copy
- continuity notes for people, props, space, lighting, and motion

Do not substitute animated stills when the story requires a real interface or physical process to be visible.
