# 🏆 ModelScout — Video Model Evaluation & Ranking

**Source:** Weavy workflow audit (2026-03-24) + web research (2026-03-24) + field experience.
**Scoring:** 1-10 scale. Tags: `[web]` = research, `[field]` = our testing, `[mixed]` = both.
**Model tiers:** Some models have multiple quality tiers (e.g., Kling 3 Standard vs Pro).
Scores assume the best available tier unless noted. Tier variants may need separate
assessment as we gain field experience.

## Attribute Key
OBE=Prompt Obedience | PHO=Photorealism | ACT=Acting | CAM=Camera Control |
LIT=Lighting | LIK=Character Likeness | MOT=Motion Quality | TMP=Temporal Coherence |
ART=Artifact Avoidance | SNS=Common Sense

---

## Camp 1: 🎯 Motion Minimalists

### Runway Gen-4.5 `rw_4_5_video_original`
**Config:** 8s, 1280×720, concat | **Tier:** S [web]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 9   | 8.5 | 7   | 9   | 8   | 8   | 9   | 9   | 7   | 8   |

**Best for:** Controlled i2v, hero shots, physical plausibility, clean motion
**Avoid for:** Ultra-realistic talking heads (Veo/Kling edge), budget-constrained bulk work
**Notes:** #1 on Artificial Analysis Elo (1,247). Best-in-class motion physics and camera control. Occasional causal reasoning errors (effect before cause). Character consistency improved but Kling 3 may edge it for realism. Under 1,000 char prompt limit (shared with Gen-4).

### Runway Gen-4 `rw_4_video_original`
**Config:** 8s, 1280×720, concat | **Tier:** A [web]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 8   | 8   | 6   | 8   | 7   | 7   | 8   | 8   | 7   | 7   |

**Best for:** Fast proof-of-concept, existing Gen-4 pipelines, cost efficiency
**Avoid for:** Work requiring Gen-4.5's improved physics and consistency
**Notes:** Solid workhorse superseded by Gen-4.5. Same speed. Under 1,000 char limit.

### Runway Gen-4 Turbo `rw_4_video`
**Config:** 10s, 1280×720, concat | **Tier:** A- [web]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 7   | 7   | 6   | 7   | 7   | 7   | 7   | 7   | 7   | 7   |

**Best for:** Longer clips (10s), rapid iteration when speed > quality
**Avoid for:** Final hero shots (Gen-4.5 is better quality)
**Notes:** Speed-optimized variant. 10s max is unique among Runway models.

### Veo 3.1 i2v `google-veo3-i2v`
**Config:** Std, v3.1, 8s, 1080p, audio ON, enhance OFF, native neg | **Tier:** S [web]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 8   | 9.5 | 8   | 8   | 9   | 8   | 8   | 8   | 8   | 8   |

**Best for:** Photorealism, natural lip-sync, audio-visual generation, camera vocabulary
**Avoid for:** Cramming too many events into one clip
**Notes:** Elo ~1,226. Industry-leading photorealism (9.5/10 in reviews). Native audio with strong lip-sync. Supports negative prompts (noun-style). Gets raw prompt (not concat).

### Minimax Hailuo-02 `minimaxV2`
**Config:** Pro, fixed 6s, concat | **Tier:** B+ [web]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 7   | 7   | 6   | 6   | 7   | 7   | 7   | 7   | 6   | 6   |

**Best for:** Efficient short scene evolution from strong first frame
**Avoid for:** Anything needing > 6s, complex prompts, fine camera control
**Notes:** Fixed 6s — no duration choice. Responds well to short, motion-led prompts. Don't overcomplicate.

---

## Camp 2: 📋 Structured Shot Planners

### Google Veo 2 `google-veo2`
**Config:** 8s, 16:9, concat | **Tier:** B+ [web]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 7   | 8   | 7   | 7   | 7   | 7   | 7   | 7   | 7   | 7   |

**Best for:** Reliable mid-tier production, structured prompts
**Avoid for:** Anything Veo 3.1 does (it's the upgrade)
**Notes:** Older generation. Superseded by Veo 3.1 but still competent. No native neg prompt.

### LTX 2 Video `ltx2_video`
**Config:** ltx-2-pro, 25fps, 8s, 1920×1080, enhance OFF, concat | **Tier:** B+ [web]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 7   | 7   | 5   | 6   | 7   | 6   | 7   | 7   | 6   | 6   |

**Best for:** High-resolution output (supports up to 4K), open-source ecosystem
**Avoid for:** Complex character performance, cinematic nuance
**Notes:** Released Jan 2026. Strong on textures and resolution. Pro model selected. Consumer-friendly (runs on RTX 4070 Ti). Less refined on acting/performance.

### Sora 2 `sora`
**Config:** sora-2 (standard), 8s, 1280×720, concat | **Tier:** A [web]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 8   | 9   | 7   | 8   | 8   | 7   | 8   | 8   | 7   | 8   |

**Best for:** Structured shot briefs, precise scene planning, physics accuracy, audio
**Avoid for:** No character reference system — poor for identity persistence across shots
**Notes:** Elo ~1,206 (Pro). Excels at detailed dynamics and complex prompts. Two 4s > one 8s. Pro available with higher res. Currently using standard.

### Wan 2.5 `fal-ai/wan-25-preview`
**Config:** 10s, 1080p, enhance OFF, native neg | **Tier:** B+ [web]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 7   | 7   | 6   | 6   | 7   | 7   | 7   | 7   | 6   | 6   |

**Best for:** Longer clips (10s), cinematic narrative, multi-shot with reference
**Avoid for:** Quick single-shot iteration (slower)
**Notes:** Open-source lineage. Strong text rendering. Gets raw prompt. 10s duration.

### Wan 2.2 `wan22`
**Config:** 720p, 121 frames, film interp, ~5.04s effective, native neg | **Tier:** B [web]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 6   | 7   | 5   | 6   | 6   | 6   | 6   | 7   | 6   | 6   |

**Best for:** Stylized content, custom scoring workflows, heavy config tuning
**Avoid for:** Quick production work (complex settings, short effective duration)
**Notes:** Most configurable model. Effective ~5s despite 121 frames. Film interpolation doubles count. Older generation — Wan 2.5/2.6 supersede for most uses.

---

## Camp 3: 🎭 Reference-Loyal Puppeteers

### Kling 3 `kling` (3.0 — score assumes best tier)
**Config:** 3.0 Std (Pro available), 8s, 16:9, CFG 0.5, audio ON, native neg | **Tier:** S [mixed]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 8   | 9   | 8   | 8   | 8   | 9   | 9   | 8   | 6   | 7   |

**Best for:** Photorealistic i2v, character consistency, multi-shot, natural motion
**Avoid for:** Text rendering (known weakness), budget-constrained bulk work (expensive)
**Notes:** 8.1-8.26/10 in reviews. "Likely best general-purpose video model" (Chase Jarvis). Won our Hindenburg Ep250 "discovery" shot on Standard tier [field]. Strongest character likeness and motion realism. Text/artifact avoidance is weakest attribute. Currently on Standard — bump to Pro for max quality when budget allows.

### Kling 1.6 `kling_16` (1.6 Pro)
**Config:** 1.6 Pro, 10s, 16:9, CFG 0.5, native neg | **Tier:** A- [web]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 7   | 7   | 6   | 7   | 7   | 7   | 7   | 7   | 6   | 6   |

**Best for:** Longer 10s clips, basic i2v with good start-frame respect
**Avoid for:** Anything Kling 3 does better (which is most things)
**Notes:** Previous generation. Pro selected. 10s duration. Superseded by Kling 3 for quality.

### Kling F&L Frame `kling` (O1 Pro)
**Config:** O1 Pro, 10s, guidance 0.5, native neg | **Tier:** A- [web]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 7   | 7   | 6   | 7   | 7   | 7   | 7   | 7   | 6   | 6   |

**Best for:** Dedicated first-and-last-frame workflows, controlled transitions
**Avoid for:** Text-to-video (not its strength)
**Notes:** O1 Pro model. Specialized for F&L frame interpolation. 2.1 Pro and 2.5 Turbo Pro also available.

### Kling Video `kling` (2.6 Pro)
**Config:** 2.6 Pro, 10s, 16:9, concat (no native neg) | **Tier:** A [web]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 7   | 8   | 7   | 7   | 7   | 8   | 8   | 7   | 6   | 7   |

**Best for:** General i2v production, 10s clips, cinematic realism
**Avoid for:** Precision negative prompting (concat only, no native neg)
**Notes:** Only Kling model on concat path. Described as having "cinematic aesthetic and lighting control." 2.6 was previous state-of-art before 3.0.

### Grok Imagine Video `xai/grok-imagine-video`
**Config:** 8s, 720p, 16:9, concat | **Tier:** B+ [mixed]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 4   | 7   | 6   | 8   | 7   | 7   | 8   | 7   | 5   | 3   |

**Best for:** Speed king (always finishes first), cheap iteration ($0.05/sec), camera direction
**Avoid for:** ANYTHING requiring prompt obedience or common sense. Consistently adds unwanted elements, invents surprises, ignores explicit exclusions. Never produced a usable final take in our pipeline [field].
**Notes:** The dark horse you keep rooting for but can't trust. #1 in i2v benchmarks (Elo 1,329) but benchmarks don't capture the "random explosions and silly characters" problem. Photorealism is genuinely good. Camera following is strong. But OBE and SNS scores are dramatically lower in production than web reviews suggest. 720p max. Always finishes first. Always gets something wrong. 🐎💔

---

## Camp 4: 🎪 Cinema Goblins

### Seedance V1.5 Pro `fal-ai/.../seedance/v1.5`
**Config:** 8s, 1080p, 16:9, audio ON, cam fixed OFF, concat | **Tier:** A+ [web]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 8   | 8   | 8   | 8   | 8   | 7   | 8   | 8   | 6   | 7   |

**Best for:** Cinematic storytelling, camera control (dolly zooms!), multi-language dialogue, emotional performance
**Avoid for:** Subtle restrained insert shots (will over-cinematic without boxing)
**Notes:** Strong narrative continuity. Director-level camera control. 8+ language lip-sync. Physics-accurate motion. Camera Fixed toggle is your restraint lever. Auto-fills narrative intent — feature AND hazard.

### Moonvalley `moonvalley`
**Config:** 1920×1080, 5s, native neg | **Tier:** B [web]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 5   | 6   | 5   | 5   | 6   | 5   | 6   | 6   | 6   | 4   |

**Best for:** Fully licensed data (IP-safe), basic motion clips
**Avoid for:** Complex prompts, precision work, anything requiring strong prompt following
**Notes:** "Marey" model. Trained on licensed data only. Consistently underperforms on complex prompts in reviews. 5s or 10s only. Wooden spoon recipient in multiple multi-model tests.

### Seedance V1.0 `fal-seedance`
**Config:** Pro, 10s, cam fixed OFF, concat | **Tier:** B+ [web]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 7   | 7   | 7   | 7   | 7   | 6   | 7   | 7   | 6   | 6   |

**Best for:** Cinematic expressiveness with 10s duration, narrative filling
**Avoid for:** Restrained technical shots (same over-cinematic risk as V1.5)
**Notes:** Older Seedance. V1.5 Pro is the upgrade. Still capable for expressive shots. No audio. 10s gives more room than V1.5's 8s.

### Pixverse V4.5 `pixverse/pixverse-v4.5`
**Config:** 1080p, 16:9, 8s, normal motion, SFX ON, native neg | **Tier:** B+ [web]

| OBE | PHO | ACT | CAM | LIT | LIK | MOT | TMP | ART | SNS |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 7   | 7   | 6   | 6   | 6   | 6   | 7   | 7   | 6   | 6   |

**Best for:** High-volume social/branded content, fast iteration, multi-subject handling
**Avoid for:** Complex cinematic work, ultra-realism
**Notes:** ⚠️ 1080p + 8s combo may conflict. Strong on prompt coherence and complex actions per reviews. Style/effect presets available (all OFF currently). V5 exists as upgrade. SFX enabled.

---

## ⚠️ Configuration Flags

1. ~~**Kling 3 → Standard, not Pro.**~~ Resolved: cost choice. Kling 3 Std won Hindenburg 250 discovery shot. Bump to Pro when budget allows. Scores assume best tier.
2. **Pixverse 1080p + 8s** — potential conflict per model docs. Verify in field.
3. **Wan 2.2 ~5.04s effective** — shortest actual clip via frame interpolation.
4. **Moonvalley 5s** — consistently weakest in multi-model tests. Consider priority.
5. **Hailuo-02 fixed 6s** — no duration control.
6. **Sora 2 Standard, not Pro** — Pro gives higher res options.
7. **Model tier variability** — Stu bounces between model tiers for cost/results. Scores assume best tier. Separate tier assessment is a future enhancement.

## 🏕️ Camp Orphans (disconnected, available on request)

Four legacy models sit disconnected in the Weavy workflow. Not scored, but available:
- **Runway Gen-3 Alpha Turbo** (Camp 1) — last-gen Runway, 1280×768 aspect ratio
- **Minimax Video Director** (Camp 1) — bracket-based camera syntax `[Pan left, Zoom in]`
- **Minimax Video 01 / Hailuo** (Camp 1) — ⭐ has **Subject Reference / S2V-01** input for character-driven video (LOST in Hailuo-02 upgrade). Reconnect if character consistency matters.
- **Wan Video 2.1 1.3B** (Camp 2) — text-to-video only, 480p, exposed inference params

## Prompt Routing

**Concat** (11): Runway ×3, Hailuo-02, Veo 2, LTX 2, Sora 2, Kling 2.6, Grok, Seedance ×2
**Native neg** (8): Veo 3.1, Wan ×2, Kling 3/1.6/F&L, Moonvalley, Pixverse

---

## 🎰 PredictionGame Log

| Date | Shot | Predicted Winner | Actual Winner | Notes |
|------|------|-----------------|---------------|-------|
| — | — | — | — | No bake-offs yet |

**Accuracy:** 0/0 (0%)
