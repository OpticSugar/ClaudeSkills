# Model-by-Model Shorthand

Quick reference for individual model personalities, strengths, and pitfalls.
Source: VideoPrompting_UserGuide_2603d.md + field experience.

---

## Runway Gen-4 / Gen-4.5

**Camp:** 1 (🎯 Motion Minimalists)
**Best identity:** Motion-first pragmatist.

**Use when:** You have a good source frame, want controllable i2v motion, want to
iterate cleanly.

**Likes:** Prompt simplicity, positive phrasing, motion-focused i2v prompts, general
references to subjects.

**Watch out for:** Prompt overload, negative prompt dependence.

**Character limit:** Under 1,000 characters.

---

## Google Veo 3.1

**Camp:** 1 (i2v) or 2 (t2v)
**Best identity:** Structured planner with strong camera vocabulary.

**Use when:** You want robust prompt anatomy, explicit camera/cinematic language,
or reference-image workflows.

**Likes:** Clear specific prompts, one focused moment for short clips, motion-only
prompting in i2v, explicit negative prompts when needed.

**Watch out for:** Cramming too many distinct events into one short clip.

**Negative prompts:** Supported. Describe unwanted elements as nouns — avoid
instructive "no" / "don't" wording.

---

## OpenAI Sora 2 / Sora 2 Pro

**Camp:** 2 (📋 Structured Shot Planners)
**Best identity:** Clean production memo interpreter.

**Use when:** You want organized shot briefs, deliberate scene planning, audio-aware
prompting.

**Likes:** Structured prompt fields, image input for control, explicit lighting logic,
concise shot lengths for higher reliability.

**Watch out for:** Prose that tries to set API parameters with words instead of
actual settings. Two 4-second clips may outperform one 8-second clip.

---

## Kling 1.6 / Kling 3 Family

**Camp:** 3 (🎭 Reference-Loyal Puppeteers)
**Best identity:** Start-frame puppeteer.

**Use when:** The input image is already strong, preserving composition matters, you
need a precise motion note more than full scene invention.

**Likes:** Subject + movement logic, clear motion hierarchy, start-frame respect.

**Watch out for:** Overly decorative action language, too many verbs competing. Kling
literalizes poetic texture — keep language physical and plain.

---

## MiniMax Hailuo / Hailuo 2.3 Family

**Camp:** 1 (🎯 Motion Minimalists)
**Best identity:** Efficient scene evolver.

**Use when:** You want first-frame animation with clean scene evolution, straightforward
prompt tied to the starting image.

**Likes:** Direct descriptions of scene evolution, simple camera tags where supported,
image-to-video with clear motion notes.

**Watch out for:** Overcomplicating the evolution prompt. Keep it short.

---

## ByteDance Seedance 1.0 / 1.5 Pro

**Camp:** 4 (🎪 Cinema Goblins)
**Best identity:** Narrative stylist with a camera addiction.

**Use when:** You want cinematic energy, stronger storytelling/expressive behavior,
multi-shot or emotional continuity.

**Likes:** Complex instruction following, camera movement, cinematic atmosphere,
narrative cohesion.

**Watch out for:** Drift on restrained technical shots. Gratuitous spectacle if
under-constrained. Autonomous cinematography is a feature AND a hazard.

---

## Model Update Protocol

When a new model enters the landscape or an existing model gets a significant update:
1. Test it with a known master prompt across the bake-off pipeline
2. Identify which camp it most naturally belongs to
3. Note any unique behaviors, quirks, or limits
4. Add an entry here and update the camp routing table in the SKILL.md
5. Flag with 🌲📹 for skill-level integration
