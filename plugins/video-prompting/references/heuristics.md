# Field-Tested Heuristics

Rules of thumb that have survived real production pressure. Not science — sanity rails.
Source: VideoPrompting_UserGuide_2603d.md, Appendix A + field experience.

---

## 🎯 The 70/20/10 Rule (Image-to-Video)

A useful working ratio for many image-to-video prompts:

- **70%** — motion and progression
- **20%** — camera behavior and stability
- **10%** — style or mood, only if genuinely needed

If your prompt spends more than 10% on style language, ask whether the start frame
already carries that information.

---

## 🔬 The One-New-Variable Rule

When iterating on a failing prompt, change ONE important thing at a time:

- density
- speed
- timing
- camera stability
- environmental motion
- negative list

This makes debugging dramatically easier. If you change three things and it improves,
you don't know which fix worked. If you change one thing, you do.

---

## 🖼️ The Board-First Rule

A better board beats a better prompt.

If the model keeps misunderstanding the frame, improving the source image may have
more value than adding another paragraph of text. Several official model guides
emphasize input image quality, image references, and visual anchors for exactly
this reason.

---

## 📏 The Clip-Split Heuristic

If a prompt needs more than one dramatic beat, split it into separate clips.

Even on models that support 8-12 seconds, two 4-second clips cut together may
outperform one 8-second ask. Shorter clips follow instructions more reliably.

---

## 🧹 The Negatives-Last Rule

Do not front-load negatives. The iteration order is:

1. Clear positive prompt (skeleton)
2. Add missing control (one variable)
3. Add negatives only after real failure modes appear
4. Structural rethink if still failing

Negatives are a surgical tool, not a lifestyle.

---

## 🎭 The Camera Texture vs. Camera Motion Distinction

A lot of "make it feel alive" requests really want camera TEXTURE (vibration,
handheld tremor, mount judder, rolling shutter energy), not actual camera MOTION
(pan, tilt, push, dolly).

If the user wants "liveliness" but the frame should stay essentially put, use
texture language, not motion language.

---

## 🔒 The Priority Sentry Sparingness Rule

Use 🔒 on master prompt lines only when drift would ruin the shot. If everything
is 🔒, nothing is. Reserve it for load-bearing creative decisions.
