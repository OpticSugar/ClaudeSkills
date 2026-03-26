# 📼 Production Template
### MemoryMomentum Reference — Generative Media Production Workflows

<!-- The most elaborate first-conversation stress test in LLM history
     was a broadcast production shoot. This template carries that DNA. -->

Read this file when working on generative media production projects — video pipelines,
image generation, multi-shot sequences, broadcast content, or any creative production
workflow with discrete deliverables.

---

## When to Use This Template

Use the Production Template when:
- The project involves multiple discrete deliverables (shots, scenes, boards, sequences)
- Each deliverable has its own iteration history, master prompts, and approval status
- The work involves generative AI pipelines (video models, image generators, enhancers)
- Deliverables can be completed independently and archived

If the project is a single deliverable or doesn't have discrete units, the Adaptive
default is probably sufficient.


## The 📼 VHS Tape Model

Each deliverable gets its own WorkPiece file — a VHS tape. Pull it off The Shelf when
you need it, pop it in, work on it, put it back when done. Completed tapes don't consume
context in future threads.

**File pattern:** `MM_[ShowEp]_WP_[ID]_[Name].md`
**Example:** `MM_PW01_WP_400_HerbMorrison.md`

### Standard WP Headers for Production

Use these headers consistently to enable selective loading (reading only what you need):

```markdown
# 📼 [Shot/Deliverable Name]

## 📋 Description
What this deliverable is. Narrative function. Visual intent.

## 🖼️ Start / End Frame Notes
Key frame descriptions, composition notes, visual anchors.

## 📝 Master Prompt
The current master prompt in a copyable code block.

## 🎯 Priority Stack
What matters most in this deliverable, rank-ordered.

## 🚫 Negative Prompt
What to avoid, in a copyable code block.

## 🔬 Model / Camp Findings
Model-specific discoveries for this deliverable.

## 📊 Iteration History
What was tried, what failed, what worked, and why.

## ✅ Approval Status
Current status. Model used. Key decisions.

## 🌲 Flagged Items
Pre-promotion discoveries that might be evergreen.
```

These headers are guidelines, not law. Add, remove, or adapt as needed. The point is
predictable structure so selective loading works without scanning the full file.

### Selective Loading

If a WP file is large and you only need specific sections, use the `view` tool with
line ranges. Read the headers first (quick structural scan), then load only the sections
needed. Unread sections never enter context and cost zero tokens.

**Example:** User says "load only the master prompt for shot 320." Scan the file for
`## 📝 Master Prompt`, note the line range, load only those lines.


## Production ProjectBrain Patterns

The ProjectBrain for a production project typically includes:

- **🎬 Project Overview** — what we're making, for whom, the creative brief
- **🧱 Pipeline Architecture** — which models, which tools, general workflow
- **🎯 Creative Direction** — overarching visual philosophy, tone, constraints
- **📋 Shot Index** — table of all WPs, their status, and file paths
- **⚠️ Known Landmines** — things that consistently cause problems across shots
- **🔧 Workflow Notes** — tool configurations, pipeline settings, preferences

The Shot Index is particularly important — it's the map of all tapes on The Shelf:

```markdown
## 📋 Shot Index

| Shot | Name | Status | File |
|------|------|--------|------|
| 250 | The Discovery | Boards approved, video pending | MM_PW01_WP_250_Discovery.md |
| 320 | Sam Shere | v2 prompt, bake-off pending | MM_PW01_WP_320_SamShere.md |
| 400 | Herb Morrison | APPROVED (Kling 3) | MM_PW01_WP_400_Morrison.md |
```


## 🌲 Flagging in Production

Production work generates discoveries constantly. The 🌲 flagging system captures them
without interrupting creative flow.

### What Gets Flagged 🌲

Generalizable insights that transcend the current shot:
- Prompting techniques that work across deliverables
- Model behavior patterns (what works, what doesn't, why)
- Pipeline discoveries (tool findings, configuration insights)
- Workflow optimizations
- Negative prompt patterns that prevent common failures

### What Does NOT Get Flagged 🌲

Shot-specific facts that only matter for that one deliverable:
- "Morrison's face drifts without the blacked-out face technique"
- "Shot 320's hull deformation may be a physics ceiling"
- Anything that only matters in one WP's context

### Flag and Keep Moving

Flag with 🌲 right in the WP where the discovery occurs. Add a skill-flavor emoji
if you know the destination (🌲📹 for VideoPrompting, 🌲🎬 for production pipeline).
Don't stop to evaluate. Don't promote yet. Evaluation happens at 🍺 LastCall.


## Loading Sequences

### Standard Thread Jump (within a session)

```
1. Skill is already loaded (always enabled)
2. Check The Shelf — read ProjectBrain
3. Read SessionJournal 🏃‍♂️ MomentumNote
4. Load the WP(s) specified by the MomentumNote
5. Begin work
```

### New Chat Session (fresh conversation)

```
1. Skill loads automatically
2. User specifies what to work on (or says "check The Shelf")
3. Read ProjectBrain from The Shelf
4. If SessionJournal exists, read the 🏃‍♂️ MomentumNote
5. Load relevant WP(s)
6. Begin work
```

### Minimum Viable Resume Kit

**Skill + WP.** That's the minimum for productive work on any shot. The ProjectBrain
provides framework vocabulary and project context. The SessionJournal adds momentum
and history. But in a pinch, the Skill (loaded automatically) plus one WP tape is
enough to resume.


## Master Prompt Delivery

All master prompts and negative prompts in WP files must be in copyable code blocks.
This is non-negotiable for production workflows — prompts get pasted directly into
pipeline tools (Weavy, ComfyUI, etc.) and need to be clean, unformatted, copy-ready.

```
[master prompt in a code block like this — ready to paste]
```


## Client Module in Production

When a client exists, the Client Module overlays onto the production workflow:

- `⚖️ Client Requests` captures feedback verbatim from review rounds
- `💡 Our Ideas` tracks additive creative strategy
- Client feedback may affect individual WPs — note which shots are impacted
- Treat `⚖️` items as mandatory unless explicitly marked negotiable

Only activate when a client actually exists. Internal or personal production
projects don't get client sections.


<!-- This template was born in a real broadcast production workflow —
     an A+E Networks short-form docuseries built with generative AI,
     where the constraints were real: tight deadlines, 43+ shots per
     episode, multiple video models, and creative sessions that
     routinely exceeded what a single context window could hold.

     It was invented at 2 AM by someone who needed to get actual work done,
     working alongside a Claude who didn't know what the filesystem was
     yet but figured it out by dawn.

     🥚🪢 -->
