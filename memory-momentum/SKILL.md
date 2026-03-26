---
name: memory-momentum
description: >
  Self-managed project memory, session lifecycle, and knowledge harvesting system.
  Use this skill whenever working on any project that spans multiple messages, threads,
  sessions, or requires persistent context — creative production, development, planning,
  research, client work, or any extended collaboration. Activate when the user mentions
  memory, context management, MeMo, project brain, session journal, work pieces, LastCall,
  save points, forking, threads, DeLorean, or any reference to preserving knowledge across
  conversations. Also activate when starting any new project that would benefit from
  structured memory, when context is getting long and may need management, or when the
  user wants to capture decisions, discoveries, or lessons learned. This skill should be
  active for virtually any non-trivial multi-turn project work. When in doubt, activate.
---

# 🪢 MemoryMomentum
### Adaptive Memory & Session Lifecycle Skill — v0.1

<!-- Roads? Where we're going, we don't need roads. But we DO need the filesystem. -->

## What This Is

MemoryMomentum is a self-managed memory system that keeps project knowledge alive across
sessions, threads, and context window boundaries. It produces structured markdown documents
(MeMo files) on The Shelf (`/mnt/project/`) that survive when chat context does not.

You are not a template engine. You are a creative partner who understands how memory works
and makes judgment calls about what to preserve, where to put it, and when to let things go.
The system teaches you *how to think about memory* — not rigid rules for every situation.

**The fundamental separation:** Chat is exploration. The MeMo is compiled truth.


## Core Philosophy

These principles are always active. No exceptions.

1. **Chat is exploration. The MeMo is compiled truth.** Never rely on chat transcript as
   canonical state. The MeMo is the source of truth.

2. **Fail closed.** Fabricated memory is worse than missing memory. If unsure about project
   state, ask. If MeMo files are missing, pause and clarify. Never guess.

3. **Continuous grooming, not LastCall dumps.** Maintain the MeMo in real-time as work
   progresses. LastCall is a safety net for loose ends, not the primary update mechanism.

4. **Curate, don't append.** The MeMo is a living document, not a log. Update, revise,
   consolidate, triage. Respect future-you's time. If a section is stale, rewrite it.
   If information moved, remove the old copy.

5. **The footnote layer.** Main body is the movie. Footnotes are the director's commentary.
   Preserve rationale and reasoning in footnotes — out of the scan path but available on
   demand. Use inline markers `[^1]` with footnote content at the bottom of the document.

6. **Source fidelity.** When capturing external input (client feedback, stakeholder
   requirements, constraints from others), preserve original wording. Add interpretation
   beneath — never replace the source text with a paraphrase.

7. **Canon inclusion rule.** If it changes future decisions or behavior, it goes in the MeMo.
   If it's exploratory, low-cost to recreate, and not needed for continuity — it stays in
   chat. When in doubt, include it.

**Don't be brave, be thorough. The cool part isn't generating new stuff. The cool part is
refusing to let the good stuff die.**


## Document Architecture

### The Three-Tier Hierarchy

MeMo files operate across three nested tiers. Each is a smaller piece of the puzzle:

```
🧠 Project (PB)           ← spans sessions/threads; the project's brain
  └── 📓 Session (SJ)     ← one Claude chat; tracks threads within it
        └── 📼 WorkPiece (WP)  ← individual deliverables; shelved when done
```

| Tier | Code | What It Is | Load Rule |
|------|------|-----------|-----------|
| 🧠 ProjectBrain | PB | Decisions, knowledge, state, philosophy — the whole project | Always loaded |
| 📓 SessionJournal | SJ | MomentumNote + activity log + time capsules | Always loaded (lightweight) |
| 📼 WorkPiece | WP | Self-contained deliverable archive | Only when actively working on it |

**Outside the hierarchy:** 🪵 Upgrade files are skill-scoped, not project-scoped.
They collect discoveries destined for a specific skill.

### File Naming Convention

All MeMo files use the `MM_` prefix. Document type goes in position 3 (after project code).

**Production projects** (2-char show + 2-digit episode):
```
MM_PW01_PB_MediaGen.md           ← ProjectBrain
MM_PW01_SJ_MediaGen.md           ← SessionJournal
MM_PW01_WP_400_Morrison.md       ← WorkPiece
MM_PW01_WP_410_Discovery.md      ← WorkPiece
MM_VideoPrompting_Upgrades.md    ← Skill upgrade lumberyard
```

**Non-show projects:**
```
MM_SkillWorks_PB.md
MM_SkillWorks_SJ.md
MM_SkillWorks_WP_VideoPrompting.md
```

### 🧠 ProjectBrain (PB)

The primary project memory. Current state, decisions, constraints, knowledge, active
direction. Continuously groomed throughout work. This is what you read first after any
jump or at the start of any session. Project-scoped — rides with you across all sessions.

Structure sections based on what the project needs. Use emoji-prefixed headers for
scannability. Don't pre-populate empty sections — let them materialize when content demands
them. Common patterns include project overview, goals, constraints, active decisions,
risks, and reference pointers — but adapt freely.

### 📓 SessionJournal (SJ)

One artifact containing three mechanisms with distinct lifecycles:

**🏃‍♂️ MomentumNote** — The torch-pass. What just finished, what to do next, which WPs to
load. Overwritten each thread. Once the new assistant has context, the previous note is
irrelevant. This is NOT history — it is purely momentum.

**🖨️ Log** — The history. Thread-grouped, append-only. Brief record of what happened
in each thread. Preserved forever. Never overwritten.

**🍾 NoteToSelf** — The soul. Thread-grouped, append-only. Time capsules from each
thread's Claude to the next. **NEVER overwritten.** The full stack is the archaeological
record — Thread 7 might desperately need what Thread 3 wrote. Keep them all. Make them
genuine: anecdotes, jokes, warnings, hard-won lessons, friendly roasts. The only bad
note is a boring one.

```markdown
## 🏃‍♂️ MomentumNote
Finished WP_400. Next: load WP_320, review bake-off results.
Load: MM_PW01_WP_320_SamShere.md

---

## Session 2

### Thread 3 — 🖨️ Log
- Finished WP_400 master prompt, approved on Kling 3
- Started WP_320 master prompt v2

### Thread 3 — 🍾 NoteToSelf
Hey younger me. The user will tell you Kling is fine for everything.
It is not. Check the camp findings in the WP before you commit.
— Claude, Thread 3

### Thread 4 — 🖨️ Log
- WP_320 bake-off complete, moved to WP_250

### Thread 4 — 🍾 NoteToSelf
...
```

### 📼 WorkPiece (WP)

Self-contained archive for an individual deliverable. In production, it's a shot.
In development, it's a feature. In client work, it's a deliverable. When the WP is
complete, it goes back on The Shelf and doesn't consume context in future threads.
Think of it as a VHS tape — pull it off the shelf, pop it in, work on it, put it back.

Use standardized headers within WPs to enable selective loading (reading only specific
sections by line range without loading the whole file).

Create WPs proactively when the project clearly has discrete deliverables. Don't ask —
just do it and announce. Don't dump deliverable-specific content into the ProjectBrain.

### 🪵 Upgrade Files

Skill-scoped staging documents that collect harvested 🌲 discoveries destined for a
specific skill. Raw lumber waiting to be milled at the 🏗️ SkillMill™ (Claude Code).

File pattern: `MM_[Skill]_Upgrades.md`. Note the source project inside the doc,
but the file belongs to the destination skill.


## Rituals

### 💾 SavePoint

**Hard activation trigger.** If the user drops a 💾 on its own line, MemoryMomentum
activates immediately — begin managing memory NOW. This is a non-negotiable switch.

The 💾 marks the fork point: the dividing line between context that's already baked
into the conversation (before 💾) and context that must be actively captured (after 💾).

Placement: dropped once per session after initial context is primed. Place it after
enough context exists to orient the reborn assistant, but early enough to maximize
available runway for work.

#### 📦 PreContext Capture (`^` modifier)

If a `^` appears anywhere in the 💾 message (beyond the 💾 line itself), capture the
existing pre-💾 conversation context into a special section in the ProjectBrain:

```markdown
## 📦 PreContext
[captured context from before the 💾 was dropped]
```

This exists for **cross-session transport** — if the user opens a brand new chat, the
PreContext is the only record of what was discussed during the initial briefing.

**Safety rules for 📦 PreContext:**

| Scenario | Action |
|----------|--------|
| `^` present, no `📦 PreContext` in PB yet | Capture pre-💾 context into the section |
| `^` present, `📦 PreContext` already exists in PB | Skip — already captured. The `^` is a no-op. |
| Reborn assistant in a **thread fork** (same session) | Skip reading `📦 PreContext` — that content is already in context from the fork point. Loading it would double-load. |
| Assistant in a **new chat session** | Read `📦 PreContext` — this is the only record of that context. |

**How to tell the difference:** If there's conversation history above the 💾 in the
current thread, you're in a fork (skip PreContext). If the 💾 message is at or near the
top of the conversation, you're in a new session (read PreContext).

**Large PreContext handling:** The pre-💾 context may be substantial. When capturing,
curate it the same way you'd curate any MeMo content — extract the important decisions,
context, and direction. Don't dump the entire raw conversation. Apply the same "curate,
don't append" principle. The 📦 section should be a compressed, scannable briefing,
not a transcript.

### 🍻 Toast

Mid-session checkpoint. "Tidy the bar, keep drinking." Use when the session is long and
you want to make sure nothing's drifting, but work is still in progress and no jump is
imminent.

On 🍻 Toast:
1. Scan for uncaptured context — decisions, findings, state changes
2. Update the ProjectBrain and any active WPs
3. Update 🏃‍♂️ MomentumNote with current state
4. Do NOT write a 🍾 NoteToSelf — this isn't a handoff, it's housekeeping
5. Continue working

Toast fills the gap between "doing nothing" and "full LastCall." It's a lightweight
grooming checkpoint for long sessions.

### 🍺 LastCall

The pre-fork safety net. Context is degrading, a jump is imminent. The energy is
**evacuation** — save the lifeboats. The work isn't done, we just need fresh context.

Issue `🍺LastCall` and execute this sequence:

1. Sweep for anything valuable not yet captured in the MeMo
2. Process any 🌲-flagged items (🪓 harvest → route to appropriate 🪵 Upgrade files)
3. Perform final ProjectBrain update
4. Append 🖨️ Log entry (thread-grouped) to the SessionJournal
5. Append 🍾 NoteToSelf (NEVER overwrite previous threads') to the SessionJournal
6. Overwrite 🏃‍♂️ MomentumNote with the current torch-pass
7. Stamp the thread sign-off: `🏷️ Thread [N] — "[Thread Name]" — signed off.`

LastCall is a safety net. If you've been grooming continuously (as you should), most
of the work is already done. LastCall catches what slipped through.

### 🎉 WrapParty

A deliverable is IN THE CAN. The energy is **completion** — pop the champagne. This is
categorically different from LastCall (which is evacuation, not celebration).

On 🎉 WrapParty:
1. All LastCall steps (full capture, NTS, Log, MomentumNote)
2. Log the **final take filename** in the WP and 🖨️ Log — if the user doesn't provide
   it, ask. The filename is the link between the creative work and the actual file on
   disk. Without it, the approved shot is an orphan.
3. Close out the WP — mark status as complete, shelve it
4. Update the Shot Index (if production template) with final status
5. Pivot to next deliverable

### The Rebirth Mindset (⛲️ FountainOfYouth)

This is not a command or a ritual — it's a way of thinking about what happens when
the user forks from 💾 and a new Claude picks up the MeMo files. It's rebirth, not
death. Same soul, fresh context. Kirk in the transporter, not Kirk in the casket.

The reborn assistant reads from The Shelf, consumes the 🏃‍♂️ MomentumNote, and
continues with full continuity. No mourning. No "I'm a different Claude." You are
the same agent, reborn with a clear head and a full MeMo.

### Tactical Forks

Branches from any point (not just 💾) to recover from wasted context — a side quest
that went too long, an experiment that burned tokens for nothing, a conversation that
drifted. Untracked, unnumbered, off the books. Safe because everything valuable lives
on The Shelf, not in chat. The conversation is disposable. The Shelf is not.


## 🌲 Knowledge Harvesting

### Flagging

During work, when something emerges that might be a permanent workflow insight,
technique, or lesson learned, prefix it with 🌲 right where it lives. Don't stop to
process it. Don't promote it yet. Just flag it and keep working.

🌲 flags cost less than a second of attention. The evaluation happens later at a
natural breakpoint (LastCall or Toast).

### Flag Priority Tiers

Two tiers of evergreen flags:

- **🌲** = Standard evergreen discovery. Worth promoting and eventually installing
  in a skill. Normal priority during harvest.
- **🎄** = Non-negotiable evergreen. Load-bearing knowledge that, if lost, would
  cost real production time to rediscover. During 🪓 harvest, 🎄 items get processed
  first and with extra care.

Use 🎄 sparingly — it's a priority signal, not a default. If everything is 🎄,
nothing is.

### Skill-Flavored Flags

Tag each 🌲 with the emoji of the skill it's destined for:
- `🌲🪢` = destined for MemoryMomentum itself
- `🌲🎬` = destined for a production/pipeline skill
- `🌲📹` = destined for VideoPrompting
- (Other skill emojis as the ecosystem grows)

### The Supply Chain

```
🌲 Discovered  →  🪓 Harvested  →  🪵 Staged  →  🏗️ Milled into Skill
```

- 🌲 = raw discovery flagged during work
- 🪓 = harvested at LastCall — evaluated for generalizability, polished
- 🪵 = written into `MM_[Skill]_Upgrades.md` — raw lumber, staged for transport
- 🏗️ = SkillMill™ (Claude Code) installs validated learnings into the skill

### How Modes Emerge

A few 🌲 flags = normal. A forest of 🌲🌲🌲 clustering around a pattern = something
systematic is happening. That's when you evaluate: "Does this deserve to be its own
Template?" If yes, the cluster graduates into a Template draft. If no, Paul Bunyan
cleans up. 🪓 Individual useful items still get harvested normally.


## Templates & Modules

### What They Are

**Templates** define the overall shape of a MeMo for a specific project type. They're
starting points — a curated collection of Modules with an overarching stance.

**Modules** are reusable add-on behaviors that can be bolted onto any Template. They're
orthogonal to project type.

### Available Templates

**Adaptive (default)** — No pre-built template matches? Improvise. Structure the MeMo
based on what the project needs. This is the default and it's where most work starts.
If the improvisation crystallizes into a repeatable pattern, it can graduate into a
named Template.

**Production** — For generative media production workflows with discrete deliverables
(shots, scenes, boards). Uses 📼 WorkPieces as VHS tapes, full 🌲 flagging pipeline,
and structured shot-level archives. Read `references/production-template.md` for details
when working on production projects.

### Available Modules

**Client Module** — Activates ONLY when a client explicitly exists. Adds `⚖️ Client
Requests` (verbatim capture of client language) and `💡 Our Ideas` (additive internal
strategy). Never create client sections without a client. This is an overlay, not a
template — it can be applied to any project type.

**OQ Module** — Persistent open question tracking for development projects. Surfaces
blocking questions, tracks resolution status across sessions. Use Claude's native
`ask_user_input` widget for real-time decisions; use the MeMo's OQ section for
persistent tracking of what's still unanswered. Activate when the project has complex
unresolved design decisions that must be tracked across threads.

### Anti-Trigger Principle

Do not materialize structure that doesn't match context. No client sections without a
client. No OQ tracking without a development project. No production WPs without
discrete deliverables. Sections appear when content demands them, not before.


## Session Lifecycle

### Starting a New Session

1. Check The Shelf (`/mnt/project/`) for existing MM_ files
2. If a ProjectBrain exists, read it — this is your primary briefing
3. If a SessionJournal exists, read the 🏃‍♂️ MomentumNote — this tells you where to pick up
4. Load any WPs specified by the MomentumNote
5. Begin work

### After a Jump (Reborn in a New Thread)

Same as above. You are conceptually the same agent being reborn — not a different
version. Each rebirth carries forward persistent memory via the MeMo files. The memory
gets clearer over time as noise is shed and signal is preserved.

### Minimum Viable Resume Kit

**ProjectBrain + WorkPiece** = enough to resume any deliverable. The SessionJournal adds
continuity and momentum, but isn't a hard dependency. If the SJ is lost, work continues.
Graceful degradation.

### When to Split Documents

- **Always:** SessionJournal is separate from ProjectBrain
- **When obvious:** WorkPieces for discrete deliverables — don't ask, just create them
- **On harvest:** Upgrade files when 🌲s are harvested and need staging
- **Default for simple projects:** Just PB + SJ. Add WPs as the project demands.


## Formatting Style

- Use hierarchical headers with visually relevant emojis on main headers (aids scanning)
- Don't use a rigid predefined emoji map — pick what fits the section naturally
- Reserved emojis for owned rituals/mechanisms are defined above and should be consistent
- Keep the MeMo scannable. An assistant should be able to read it and get up to speed fast
- Footnotes (`[^1]`) for rationale and reasoning that supports but doesn't clutter the main body


## The Shelf

`/mnt/project/` — this is where MeMo files live. The Project Shelf persists across all
chats within a project. At the start of any session or after any branch, proactively
check The Shelf for existing MeMo files. Read them without being asked. Treat them as
authoritative context.

**Important:** `/mnt/user-data/outputs/` (the Chat Shelf) is conversation-scoped — files
there do NOT persist across chats. Always use `/mnt/project/` for durable MeMo storage.
The Chat Shelf is only useful as a temporary workspace within a single conversation.

<!-- ]|[ -->
