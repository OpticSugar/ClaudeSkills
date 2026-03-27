# Prompt Starter Templates

Copyable templates for common shot types. Use as starting points, not rigid forms.
Source: VideoPrompting_UserGuide_2603d.md, Appendix C.

---

## Template 1: Delta Prompt

Best for: i2v, subtle motion, reference-driven work (Camps 1 & 3).

```
Locked shot. [primary motion]. [secondary motion]. [camera behavior].
[timing / evolution].
```

---

## Template 2: Structured Planner

Best for: complex shots, multi-beat, dialogue/audio (Camp 2).

```
Shot:
Subject:
Setting:
Lighting:
Actions:
Audio:
```

---

## Template 3: Boxed Subtle Shot

Best for: restrained moments on cinematic models (Camp 4 contained).

```
Single restrained moment. [primary motion]. [secondary motion]. The camera
remains [static / mounted / nearly still]. Motion stays subtle and realistic
throughout.
```

---

## Template 4: Escalation Prompt

Best for: shots that build over the clip duration.

```
Begins still. [event] appears rarely at first. Activity gradually increases.
Near the end it becomes slightly more frequent, but remains localized and
restrained.
```

---

## Template 5: Master Prompt (Bake-Off Pipeline)

Best for: camp-agnostic input to the multi-camp enhancer pipeline.

```
[Stability/anchor statement].
[Primary motion — the most important thing that happens].
[Secondary motion — environmental, atmospheric, supporting].
[Camera behavior — static, push, drift, texture].
[Timing/progression — how motion evolves across the clip].
[Constraints — what must NOT change, if at risk].
```

Use 🔒 on any line that must survive enhancer rewriting intact.
