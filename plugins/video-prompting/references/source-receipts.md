# Source Receipts and Provenance

Paper trail for why this skill recommends what it recommends. Grouped by camp.
Source: VideoPrompting_UserGuide_2603d.md, Appendix E.

---

## How to Use This File

This file answers one question: **Why does this skill keep recommending restraint,
structure, motion-first prompting, and model-specific styles?**

Because the official docs and model guides keep saying versions of exactly that.

---

## Camp 1 Receipts: Motion Minimalists

### Runway Gen-4 / Gen-4.5

Runway's guidance is unusually blunt about prompt simplicity and motion-first i2v.
Their Image to Video Prompting Guide frames the image as defining composition,
subject, lighting, and style — while the prompt should describe motion, camera, and
temporal progression. The Gen-4 guide highlights simplicity, motion focus, positive
phrasing, and referring to subjects in general terms.

**Supports:** prompt-the-delta, anti-bloat, positive-first.

### MiniMax Hailuo

MiniMax frames i2v as evolution from the supplied first frame, not reinvention.
Docs define i2v as generation based on initial image plus text describing dynamic
scene evolution. The platform exposes first-and-last-frame and subject-reference
modes, reinforcing the reference-driven orientation.

**Supports:** short motion-led prompts, let the board carry the visual burden.

---

## Camp 2 Receipts: Structured Shot Planners

### Google Veo 3.1

Google treats prompting as a decomposable craft. The Vertex AI guide says breaking
your idea into key components is the most effective way to guide the model. Includes
an explicit "Anatomy of a Veo prompt" section. Notes you don't need all elements in
every prompt (selective structure, not compulsory bloat). Supports negative prompts
with noun-style exclusions rather than instructive wording.

**Supports:** structured prompts for complexity, selective use, negative nouns.

### OpenAI Sora 2 / Sora 2 Pro

Sora's guidance supports structured anatomy, image references for control, and
separation of prose from API settings. The guide says separating information types
is effective, not every detail needs inclusion, and shorter clips follow instructions
more reliably. Image inputs can preserve brand assets, characters, or environments.
Duration/resolution should be set via API, not described in prose.

**Supports:** production memo approach, clip-splitting, API parameter discipline.

---

## Camp 3 Receipts: Reference-Loyal Puppeteers

### Kling 1.6 / Kling 3 Family

Kling's quickstart centers i2v around a compact Subject + Movement formula. Kling 3
materials emphasize strong subject stability and consistency during motion-heavy
generation. Across Kling's onboarding, the prompt behaves less like a screenplay and
more like a motion order attached to a reference frame.

**Supports:** motion hierarchy, start-frame respect, compact prompt style.

---

## Camp 4 Receipts: Cinema Goblins

### Seedance 1.0 / 1.5 Pro

ByteDance describes Seedance with cinematic ambition: strong storytelling, emotional
expression, autonomous cinematography (long takes, dolly zooms), cinematic scene
transitions, professional color grading. These are strengths that also explain why
subtle insert shots can drift into bigger gestures if under-constrained.

**Supports:** boxed prompt style for restraint, scope control on technical shots.

---

## Cross-Model Patterns

1. **Motion-first is not just preference.** Across Runway, MiniMax, and i2v in
   general, docs repeatedly frame the text prompt as "what happens next," not a
   re-litigation of the start frame.

2. **Structure helps when complexity rises.** Veo and Sora both support organized
   prompt anatomy when shots have many moving parts.

3. **Negative prompting is situational.** Runway leans positive-first. Veo supports
   negatives with noun-style exclusions. First-pass positive, then targeted negatives
   after real failures.

4. **Better boards beat fatter prompts.** Several official guides emphasize input
   image quality and visual anchors. If the board is wrong, no paragraph saves it.

---

## Source Attribution Key

Content in this skill uses these source tags:

- `[source: official docs]` — from model maker's published guidance
- `[source: UserGuide 2603d]` — from the March 2026 VideoPrompting UserGuide
- `[source: field experience]` — from production testing on real shots
- `[source: web research YYYY-MM]` — from web research at the given date
- `[source: enhancer tuning]` — from iterative enhancer instruction refinement
