# Common Failure Patterns and Likely Causes

Diagnostic reference for when a clip isn't working. Check against these patterns
before adding more prompt complexity.
Source: VideoPrompting_UserGuide_2603d.md, Appendix B + field experience.

---

## The shot feels like a still image

**Likely causes:**
- Prompt contains no environmental motion
- No camera texture (vibration, handheld tremor, mount judder)
- No micro-motion in secondary elements
- All motion instructions are too subtle or absent

**Fix:** Add at least one secondary motion layer and consider camera texture.

---

## The model goes too cinematic

**Likely causes:**
- Vague cinematic adjectives (dramatic, epic, stunning)
- Too much style garnish
- Using a Cinema Goblin prompt style for a technical insert

**Fix:** Strip style language. Box the shot. Use Camp 1 or 3 posture.

---

## Timing is wrong (too fast, too slow, wrong distribution)

**Likely causes:**
- Motion type described, but not distribution across the clip
- No hold / ramp / escalation language
- No temporal anchors (begins still, gradually increases, near the end)

**Fix:** Add explicit timing language. See the timing/progression vocabulary in
the SKILL.md or camps-deep-dive.

---

## Model changes things that should stay fixed

**Likely causes:**
- No stability clause
- Too much scene description causing reinterpretation
- Model "helping" by animating elements you didn't mention

**Fix:** Add explicit stability statements: "framing remains locked," "exposure
remains constant," "background stays soft."

---

## Model invents unwanted elements

**Likely causes:**
- Prompt ambiguity leaving room for interpretation
- Insufficient reference image strength
- Need for a targeted negative after first-pass diagnosis

**Fix:** Tighten the prompt, improve the source image, or add a specific negative
for the observed phantom element.

---

## Camera drifts when it should be locked

**Likely causes:**
- No explicit camera instruction
- Vague "cinematic" language implying movement
- Model's default behavior includes subtle camera motion

**Fix:** State camera behavior explicitly: "camera remains rigidly mounted" or
"static frame, no camera motion."

---

## Enhancer is rewriting away from intent

**Likely causes:**
- Master prompt is ambiguous, giving the enhancer room to interpret
- Enhancer instructions are too loose for this shot type
- 🔒 Priority Sentry not used on critical lines
- Enhancer is adding negatives or style language not in the original

**Fix:** Review enhanced output against enhancer instructions. Tighten the
instructions or use 🔒 on load-bearing lines. See the enhancer tuning protocol
in the SKILL.md.
