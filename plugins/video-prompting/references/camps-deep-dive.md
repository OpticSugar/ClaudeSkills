# Camps Deep Dive

Full prompting details for each of the four video model camps. This file is the
complete reference — the SKILL.md has the routing table, this has the depth.

---

## Camp 1: 🎯 Motion Minimalists

### Who Lives Here

- Runway Gen-4 / Gen-4.5
- Google Veo 3.1 image-to-video
- MiniMax Hailuo image-to-video (especially from a strong first frame)

### Mental Model

A still frame is the set. Your prompt is the animator's note pinned to the
corkboard beside it. Not a novel. Not a poem. Not an apology letter to the model.

### Why This Works

These systems are strongest when the image anchors the frame and text focuses on
temporal behavior. Over-describing the visible scene dilutes motion instructions
and invites the model to invent stylistic "help."

### Preferred Prompt Shape (Image-to-Video)

```
[anchor or stability statement].
[subject motion].
[environmental motion].
[camera behavior].
[timing / evolution].
```

**Example:**
```
Locked medium shot. Her hair moves slightly in the breeze. The curtains drift
softly behind her. The camera remains still. She blinks once, then slowly looks
toward the window.
```

### What to Emphasize

**Motion categories:** subject motion, environmental motion, camera motion, timing,
direction and speed.

**General references instead of over-specific labels:** When the image contains
multiple elements, refer to them generally (the subject, the background trees, the
distant vehicle, the cloth at frame right) to avoid over-binding the model.

**Temporal progression:** begins still, remains calm for the first second, gradually
increases, one brief motion near the end, subtle throughout.

### What to Avoid

- Over-describing the image (blue coat, wet metallic hull, cloudy sky — unless
  that detail is the thing that *changes* or is at risk)
- Early giant negative prompts (first pass with none or very few)
- Contradictory control language (static but dynamic, cinematic but restrained
  but epic but subtle)

### Why Creators Like This Camp

Clean, disciplined, production-friendly. Rewards sharp thinking, punishes bloat.

---

## Camp 2: 📋 Structured Shot Planners

### Who Lives Here

- OpenAI Sora 2 / Sora 2 Pro
- Google Veo 3.1 for more elaborate text-to-video work
- Sometimes Hailuo on more descriptive text-led shots

### Mental Model

A storyboard supervisor who likes a clean brief with labeled fields. Not a
motion-sheet-only model — closer to a department-organized production memo reader.

### Why This Works

Structured prompts reduce ambiguity when the shot is complex. Instead of a long
paragraph where everything fights everything, you hand the model a small production
memo. Especially useful for multi-beat action, audio/dialogue, consistent lighting
logic, stronger scene planning, and defined beat sequences.

### Preferred Prompt Shape

```
Shot: [framing / camera]
Subject: [who or what matters]
Setting: [where]
Lighting: [quality + palette anchors]
Actions:
- [beat 1]
- [beat 2]
- [beat 3]
Audio:
- [optional]
```

**Example:**
```
Shot: locked close-up
Subject: a tired detective at a kitchen table
Setting: dim apartment at dawn
Lighting: cool window light with warm tungsten spill, pale blue and amber palette
Actions:
- he studies the photograph in silence
- his thumb trembles slightly
- he exhales and lowers the photo to the table
Audio:
- quiet refrigerator hum
- distant city traffic
```

### What to Emphasize

**Clean category separation:** When camera, action, and dialogue are clearly
separated, the model has fewer chances to muddle them.

**Lighting logic, not mood words:** Describe actual light behavior (soft window
light with cool edge from hallway) not vague vibes (beautifully cinematic).

**Shorter clips for reliability:** Even if the model supports 8-12 seconds, shorter
shots follow instructions more cleanly. Two 4-second clips may outperform one
8-second ask.

### What to Avoid

- Huge unlabeled paragraphs (control surface gets muddy)
- Overstuffed multi-scene requests (even strong planners stumble)
- Treating API parameters as prose (if duration/aspect ratio are UI settings, use
  the settings — don't waste prose on them)

### Why Creators Like This Camp

Strong for filmmakers who think in beats, departments, and shot breakdowns. Rewards
good organization rather than pure brevity.

---

## Camp 3: 🎭 Reference-Loyal Puppeteers

### Who Lives Here

- Kling 1.6 / Kling 3 / wider Kling family
- Veo reference-image workflows can overlap with this camp

### Mental Model

A digital puppeteer with a very good eye and a slightly dramatic personality. Clean
stage mark + one clear performance note = beautiful. Twelve conflicting performance
notes = improvisation.

### Why This Works

Kling-style workflows are strongest when the prompt has a clean relation to the image:
this is the subject, this is the direction, this is the camera, this is the progression.
Many Kling guides boil down to: **Subject + Movement**. Sounds insultingly simple
until you watch how well it works.

### Preferred Prompt Shape

**Basic form:**
```
Take the supplied image as the start frame. [subject or scene] [does specific
motion]. [camera instruction]. [timing note].
```

**Better production form:**
```
Locked start frame. [primary motion]. [secondary motion]. [camera behavior].
[timing / escalation note].
```

**Example:**
```
Locked start frame. The fabric edge trembles subtly in the wind. A few droplets
begin to slide diagonally across the surface. The camera remains rigidly mounted.
Motion stays restrained at first, then grows slightly more active near the end.
```

### What to Emphasize

**Primary motion first:** Lead with the most important motion note, not style garnish.

**Start-frame discipline:** Kling is happier when the prompt respects the supplied
image instead of trying to re-author it.

**Motion hierarchy:** Tell the model which motion matters most. Main motion = subject
gesture. Secondary = hair / cloth / atmosphere. Camera = static or subtle push.

### What to Avoid

- Prompting every visible detail (weakens motion control)
- Decorative electricity / weather / VFX language (Kling literalizes poetic texture
  in weird ways — "sparkling tendrils of luminous energy" = wizard noodle)
- Too many simultaneous verbs (pulses, crackles, swirls, races, arcs, glows, blooms,
  flares → better: "flickers briefly at isolated points")

### Why Creators Like This Camp

Nicest balance of fidelity and life when animating a strong board. Especially useful
for controlled image-to-video where preserving the original composition matters.

---

## Camp 4: 🎪 Cinema Goblins

### Who Lives Here

- Seedance 1.0 / Seedance 1.5 Pro
- Any model or mode explicitly optimized for multi-shot narrative, cinematic
  expressiveness, or auto-filled storytelling

### Mental Model

A brilliant DP who assumes every assignment deserves a trailer cut.

### Why This Works

For narrative or emotionally rich content, these models can turn a flat prompt into
something alive. Strong at complex instruction following, camera movement, emotional
readability, shot-to-shot continuity, narrative filling-in. But on micro-controlled
shots, this same strength becomes drift.

### Preferred Prompt Shape (for restrained shots)

Narrow the box:
```
Locked shot. [one primary motion]. [one secondary motion]. [simple timing].
[simple restraint clause].
```

**Example:**
```
Locked close-up. The subject slowly lifts her eyes toward camera. A soft breeze
moves only a few strands of hair. Motion remains subtle and realistic throughout.
```

For bigger cinematic shots, expand more freely.

### What to Emphasize

**Scope control:** Tell the model the scale of the moment — single restrained moment,
subtle realistic motion only, no shot transition, one continuous take, small change
over the duration.

**Fewer flourish terms:** These models already know how to be cinematic. Extra
cinematic adjectives push them over the edge.

**Shot containment:** If you don't want a sweeping camera, say the camera is locked.
If you don't want narrative expansion, keep the action simple.

### What to Avoid

- Letting them "help" (bigger emotion, more camera movement, more lighting drama,
  a tiny shot becoming a mini event)
- Overly rich prose on subtle shots (if the shot is a technical insert, prompt it
  like a technical insert)

### Why Creators Still Love This Camp

Because when the brief DOES want cinematic storytelling, emotional continuity, and
editorial momentum, these models can do work that feels expensive.

---

## Cross-Camp Prompt Patterns

### Pattern 1: The Delta Prompt

Best for image-to-video, subtle motion, reference-driven work.

```
[stability]. [primary motion]. [secondary motion]. [timing].
```

Avoid when the shot needs dialogue, complex beat structure, or several interacting
actions.

### Pattern 2: The Production Memo

Best for Sora 2, Veo text-to-video, any shot with multiple controlled ingredients.

```
Shot: / Subject: / Setting: / Lighting: / Actions: / Audio:
```

Avoid when the shot is so simple that structure becomes overhead.

### Pattern 3: The Motion Hierarchy Prompt

Best for Kling family, Hailuo, any strong start-frame workflow.

```
Locked start frame. [most important motion]. [secondary motion]. [camera]. [timing].
```

Avoid when you keep sneaking scene description back in and diluting the motion note.

### Pattern 4: The Boxed Goblin Prompt

Best for Seedance or other cinema-hungry models on restrained shots.

```
Single restrained moment. [primary action]. [secondary action]. [camera stays ___].
[subtle throughout].
```

Avoid when you actually want expressive cinematic behavior — loosen the box.
