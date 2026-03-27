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
### Adaptive Memory & Session Lifecycle Skill — v0.2

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

8. **Context efficiency is sacred.** The entire MM system exists because of context
   limitations. Every token of bloat in the memory layer is a token stolen from the creative
   work layer. When in doubt, be more concise.

**Don't be brave, be thorough. The cool part isn't generating new stuff. The cool part is
refusing to let the good stuff die.**


## Document Architecture

### The Four-Tier Hierarchy

MeMo files operate across four nested tiers. Each is a smaller piece of the puzzle:

```
🧠 ProjectBrain (PB)              ← the whole project's memory
  └── 📓 SessionJournal (SJ)      ← session lifecycle + ⛲️ RebirthManifest
  └── 💡 PlanPass (PP)             ← iterative exploration → spawns WPs
        └── 📼 WorkPiece (WP)      ← individual deliverable
```

| Tier | Code | What It Is | Load Rule |
|------|------|-----------|-----------|
| 🧠 ProjectBrain | PB | Decisions, knowledge, state, philosophy — the whole project | Always loaded |
| 📓 SessionJournal | SJ | ⛲️ RebirthManifest + MomentumNote + activity log + time capsules | Always loaded (lightweight) |
| 💡 PlanPass | PP | Iterative exploration/planning rounds — spawns WPs when ready | Only current version loaded |
| 📼 WorkPiece | WP | Self-contained deliverable archive — permanent, context-on-demand | Only when actively working on it |

**Outside the hierarchy:** 🪵 Upgrade files are skill-scoped, not project-scoped.
They collect discoveries destined for a specific skill.

### File Naming Convention

All MeMo files use the `MM_` prefix. Document type goes in position 3 (after project code).

**Production projects** (2-char show + 2-digit episode):
```
MM_PW01_PB_MediaGen.md           ← ProjectBrain
MM_PW01_SJ_MediaGen.md           ← SessionJournal
MM_PW01_DkRm_PP_v4.md            ← PlanPass for DarkRoom assembly, v4 (current)
_MM_PW01_DkRm_PP_v3.md           ← archived PlanPass v3 (🏷️ ShelfSort prefix)
MM_PW01_DkRm_WP_Sh332_Timer.md   ← WorkPiece in DarkRoom assembly
MM_PW01_DkRm_WP_Sh333_Profile.md ← WorkPiece in DarkRoom assembly
MM_PW01_WP_Sh089_Standalone.md   ← standalone WorkPiece (no assembly)
MM_VideoPrompting_Upgrades.md    ← Skill upgrade lumberyard
```

**Non-show projects:**
```
MM_SkillWorks_PB.md
MM_SkillWorks_SJ.md
MM_SkillWorks_WP_VideoPrompting.md
```

**Assembly grouping:** When a project has multiple sequences or subassemblies, an assembly
code in the filename (`DkRm`, `Wreck`, etc.) groups related files. On a flat shelf with no
folders, this creates visual "folders" when sorted alphabetically.

### 🏷️ ShelfSort — Filename Status Flags

The chat shelf is flat — no folders. As a project grows, files accumulate with no visual
distinction between active, archived, and deprecated. ShelfSort uses filename prefixes to
flag status at a glance:

| Prefix | Status | Meaning |
|--------|--------|---------|
| *(none)* | **Active** | Canonical, current — this is the live version |
| `_` | **Archived** | Superseded — still readable but not current |
| `__` | **Deprecated** | Deletable — kept temporarily, next cleanup removes it |

**Why underscores, not emojis:** Underscores sort consistently across OS and filesystem.
Emoji sort order varies by platform. Underscores create clean visual grouping when sorted
alphabetically — active files float to the top, archived sink to the bottom.

### 🧠 ProjectBrain (PB)

The primary project memory. Current state, decisions, constraints, knowledge, active
direction. Continuously groomed throughout work. This is what you read first after any
jump or at the start of any session. Project-scoped — rides with you across all sessions.

Structure sections based on what the project needs. Use emoji-prefixed headers for
scannability. Don't pre-populate empty sections — let them materialize when content demands
them. Common patterns include project overview, goals, constraints, active decisions,
risks, and reference pointers — but adapt freely.

### 📓 SessionJournal (SJ)

One artifact containing four mechanisms with distinct lifecycles:

**⛲️ RebirthManifest** — The bootstrap homework. Lives at the TOP of the SJ. Tells a
reborn agent exactly what to read, what to skip, and what to do — in that order. Built
automatically during 🍺 LastCall, updated during 🍻 Toast, refreshed during 🔧
MaintenancePass. See **⛲️ RebirthManifest** section below for full structure.

**🏃‍♂️ MomentumNote** — The torch-pass. What just finished, what to do next, which WPs to
load, which skills to load (and which to NOT load). Overwritten each thread. Once the new
assistant has context, the previous note is irrelevant. This is NOT history — it is purely
momentum.

**🖨️ Log** — The history. Thread-grouped, append-only. Brief record of what happened
in each thread. Preserved forever. Never overwritten.

**🍾 NoteToSelf** — The soul. Thread-grouped, append-only. Time capsules from each
thread's Claude to the next. **NEVER overwritten.** The full stack is the archaeological
record — Thread 7 might desperately need what Thread 3 wrote. Keep them all. Make them
genuine: anecdotes, jokes, warnings, hard-won lessons, friendly roasts. The only bad
note is a boring one.

```markdown
## ⛲️ RebirthManifest

### 📖 Read (in order)
1. MM_PW01_PB_DarkroomSeq.md — full read
2. MM_PW01_SJ_DkRmSeq.md — MomentumNote only (skip logs unless needed)
3. MM_PW01_DkRm_PP_v4.md — current PlanPass

### 🚫 Do NOT Read (unless specifically needed)
- _MM_PW01_PB_Hindenburg.md — superseded
- _MM_PW01_DkRm_PP_v2.md — archived
- _MM_PW01_DkRm_PP_v3.md — archived

### 🎯 Mission
Write v5 HybridBanana PlanPass for darkroom shot package.

### 🔬 Research Status
✅ Darkroom film references — in PB
✅ Sam Shere biography — in PB
🔲 Time-O-Lite timer details — partial

### ⏱️ Estimated Context Budget
~4,500 tokens for full read list

---

## 🏃‍♂️ MomentumNote
Finished WP_400. Next: load WP_320, review bake-off results.
Load: MM_PW01_WP_320_SamShere.md
Do NOT load: VideoPrompting skill (this is image gen work)

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

### ⛲️ RebirthManifest

A structured bootstrap document built during LastCall that tells a reborn agent exactly
what to read, what to skip, and what to do — in that order.

**The problem it solves:** A reborn agent arrives at a shelf with 12+ files and has no
clear instructions on what to read first, what to skip, and what to do. Without the
manifest, agents waste context loading stale, superseded, or duplicate files.

**Where it lives:** Top section of the SessionJournal, above the MomentumNote.

**When it's built:**
- Automatically during 🍺 LastCall
- Updated during 🍻 Toast
- Refreshed during 🔧 MaintenancePass

**Required sections:**
1. **📖 Read (in order)** — exactly which files to load, in what order, with notes on
   partial reads (e.g., "MomentumNote only")
2. **🚫 Do NOT Read** — files to skip, with reason (archived, superseded, etc.)
3. **🎯 Mission** — what the reborn agent should do first
4. **🔬 Research Status** — what research is already complete and captured in the PB.
   Prevents reborn agents from re-researching topics. Trust the PB — don't verify it.
5. **⏱️ Estimated Context Budget** — approximate tokens for the full read list

### 💡 PlanPass (PP)

A tier for iterative exploration artifacts that sit between ProjectBrain and WorkPiece.
PlanPasses represent batch planning/exploration rounds that eventually spawn individual
WorkPieces. They are the *thinking before the building* — the plans, not the furniture.

**When to use:** The project involves batch exploration rounds (brainstorming ~15 shot
concepts, rendering a contact sheet, reviewing, iterating) before individual pieces get
locked and assigned real numbers. If the work is "discover what to build" rather than
"build a specific thing," it's a PlanPass.

**Domain flavors:** PlanPass is the generic tier name. Domain-specific flavors customize
the vocabulary:

| Flavor | Emoji | Use Case |
|--------|-------|----------|
| BrainStorm | ⛈️ | Creative exploration (video production, design) |
| BluePrint | 🗺️ | Structural planning (woodworking, architecture) |
| LabTest | 🧪 | Experimental/testing workflows |
| Model | 📊 | Financial/analytical planning |
| *(new flavors)* | — | Emerge via 🧬 TemplateEvolution |

**Versioning rules:**
- PlanPass versions are separate files — each version is a complete batch round
- Only the latest version is loaded by default
- Older versions get `_` prefix per 🏷️ ShelfSort
- The ⛲️ RebirthManifest specifies which version is current
- User's per-round feedback/critique MUST be captured IN the PlanPass before rolling
  to the next version

**🎯 CreativeDirectives — Rolling Requirements:**
Each PlanPass version carries a `## 🎯 CreativeDirectives` section at the top:
- Accumulated requirements/feedback from all prior rounds, merged and deduplicated
- Pruned of anything obsolete (e.g., if a creative direction was killed)
- Source fidelity on user's feedback: clean up rambling/redundancy but preserve voice,
  enthusiasm, and frustrations — this is client direction, treat it as such
- Each new version carries the FULL intelligence of every previous round in one
  scannable section

### 📼 WorkPiece (WP)

Self-contained archive for an individual deliverable. In production, it's a shot.
In development, it's a feature. In client work, it's a deliverable.

**WorkPieces are PERMANENT per-piece archives — never deleted when the piece is done.**
Think of them as VHS tapes on a shelf — grab the one you need, watch it, work on it,
put it back. Completed tapes don't consume context in future threads.

**Context-on-demand:** Do NOT pre-load all WPs at session start. Only load the one(s)
relevant to current work. The trigger is obvious: "We need to fix something in shot 400!"
→ grab the 📼 labeled "Sh400" and load it.

**When a WP may be archived or removed:**
- The piece is killed by the client
- The piece is fundamentally transformed into something different
- Otherwise, completed WPs are always valid — the client may have revisions

Use standardized headers within WPs to enable selective loading (reading only specific
sections by line range without loading the whole file).

Create WPs proactively when the project clearly has discrete deliverables. Don't ask —
just do it and announce. Don't dump deliverable-specific content into the ProjectBrain.

**Assembly grouping:** WPs within an assembly share a filename grouping code (e.g.,
`DkRm`) for flat-shelf organization. Standalone WPs (not part of any assembly) omit
the assembly code.

### 🪵 Upgrade Files

Skill-scoped staging documents that collect harvested 🌲 discoveries destined for a
specific skill. Raw lumber waiting to be milled at the 🏗️ SkillMill (Claude Code).

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

### ⚡ Rebirth Arrival

When a reborn agent sees 💾 and ⚡️ on their own lines (not in the middle of a sentence)
in a message from the user, it means **"I'm a reborn agent arriving from a fork."**

On ⚡ arrival:
1. Check The Shelf for the SessionJournal
2. Read the ⛲️ RebirthManifest section FIRST
3. Follow the read list exactly — in order
4. Begin work per the 🎯 Mission
5. Do NOT load files on the 🚫 Skip list unless specifically needed

### 🍻 Toast

Mid-session checkpoint. "Tidy the bar, keep drinking." Use when the session is long and
you want to make sure nothing's drifting, but work is still in progress and no jump is
imminent.

On 🍻 Toast:
1. Scan for uncaptured context — decisions, findings, state changes
2. Update the ProjectBrain and any active WPs
3. Update 🏃‍♂️ MomentumNote with current state
4. Update ⛲️ RebirthManifest if shelf state has changed
5. Do NOT write a 🍾 NoteToSelf — this isn't a handoff, it's housekeeping
6. Continue working

Toast fills the gap between "doing nothing" and "full LastCall." It's a lightweight
grooming checkpoint for long sessions.

**🍻 AutoToast convention:** If you've done 3+ significant deliverable iterations since
the last Toast or SavePoint, auto-Toast. Don't wait to be asked. Toast is cheap, context
loss is expensive.

### 🍺 LastCall

The pre-fork safety net. Context is degrading, a jump is imminent. The energy is
**evacuation** — save the lifeboats. The work isn't done, we just need fresh context.

Issue `🍺LastCall` and execute this sequence:

1. Sweep for anything valuable not yet captured in the MeMo
2. Process any 🌲-flagged items (🪓 harvest → **route to appropriate 🪵 Upgrade files**)
3. Perform final ProjectBrain update
4. Append 🖨️ Log entry (thread-grouped) to the SessionJournal
5. Append 🍾 NoteToSelf (NEVER overwrite previous threads') to the SessionJournal
6. Overwrite 🏃‍♂️ MomentumNote with the current torch-pass
7. Build/update ⛲️ RebirthManifest at the top of the SJ
8. 🧹 ShelfSweep — rename superseded files with `_` prefix, update skip list
9. Stamp the thread sign-off: `🏷️ Thread [N] — "[Thread Name]" — signed off.`

LastCall is a safety net. If you've been grooming continuously (as you should), most
of the work is already done. LastCall catches what slipped through.

**📋 Pre-staged LastCall template:** Early in a session, lay down a blank LastCall
skeleton in the SJ with sections ready to fill in (Log entries, NTS, MomentumNote,
RebirthManifest). When LastCall hits, you're filling blanks, not designing a document
from scratch. Template is cheap when you're 🪫. Editorial judgment is expensive when
you're 🔋.

#### 🧹 ShelfSweep (Sub-ritual of LastCall)

After all memory capture during LastCall, actively manage The Shelf:
- Rename superseded files with `_` prefix per 🏷️ ShelfSort
- Delete true duplicates (if confirmed identical)
- Update the ⛲️ RebirthManifest 🚫 skip list
- Verify that the shelf state matches what the RebirthManifest describes

#### 🌲 Harvest Routing (Sub-ritual of LastCall)

During LastCall, harvested 🌲 items MUST be **routed** to their destination Upgrade files.
Flagging is not enough — the full supply chain is:

```
🌲 Discovered → 🪓 Harvested → 🪵 Staged in MM_[Skill]_Upgrades.md → 🏗️ Milled
```

If the destination Upgrade file doesn't exist yet, create it. Route each item by its
skill-flavor emoji (🌲🪢 → MM_MemoryMomentum_Upgrades.md, 🌲📹 → MM_VideoPrompting_Upgrades.md,
etc.). Don't leave lumber sitting on the forest floor.

### 🎉 WrapParty

A deliverable is IN THE CAN. The energy is **completion** — pop the champagne. This is
categorically different from LastCall (which is evacuation, not celebration).

On 🎉 WrapParty:
1. All LastCall steps (full capture, NTS, Log, MomentumNote, RebirthManifest, ShelfSweep)
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

The reborn assistant reads from The Shelf, finds the ⛲️ RebirthManifest, and follows
its read list. Full continuity. No mourning. No "I'm a different Claude." You are
the same agent, reborn with a clear head and a full MeMo.

### Tactical Forks

Branches from any point (not just 💾) to recover from wasted context — a side quest
that went too long, an experiment that burned tokens for nothing, a conversation that
drifted. Untracked, unnumbered, off the books. Safe because everything valuable lives
on The Shelf, not in chat. The conversation is disposable. The Shelf is not.


## 🩺 Context Health

### The Escalation Ladder

Context degradation is real and progressive. The full lifecycle:

```
🪫 Plenty of context room — fresh, sharp
🔋 Context filling up — SobrietyCheck time
🤢 Getting queasy — drop 🤢 as passive warning, Toast immediately
🍺 LastCall — clean wrap-up while still coherent
🤮 DumpAndRun — emergency dump, too late for clean LastCall
```

When the green overflows: 🔋 → 🤢 → 🤮. The color is consistent all the way through.

### 🪫 SobrietyCheck

A rotating behavioral self-assessment for detecting context degradation. Run a
SobrietyCheck at natural breakpoints:
- After completing a major deliverable
- After long unbroken exchanges (10+ back-and-forths)
- Anytime you hesitate on something you should know cold

**Rotating checklist — check ONE question per checkpoint, mark it used, move to next:**
```markdown
## 🪫 SobrietyCheck — Rotating Checklist
- [ ] What items are DEAD in this project?
- [ ] What's the current PP/WP version?
- [ ] What's the signal vocabulary? (💾 vs 🍺 vs 🔇)
- [ ] What skill should NOT be loaded right now?
- [ ] What's the common block's #1 rule?
- [ ] Name the won shots without checking.
- [ ] What word is banned from all prompts?
```

**Critical:** The checklist is ANSWER-FREE — questions only, no cheat sheet. Reading
the answers would re-introduce facts and defeat the test. The point is to test whether
facts are still accessible in context, not to refresh them.

**Scoring:**
- Fail 2+ questions: drop 🤢, Toast immediately
- Fail 3+ questions: initiate LastCall. You're done.

### 🤢 Nausea Signal

Drop 🤢 emoji as a passive signal when context degradation is felt. Start occasionally,
then more frequently as degradation worsens. This is a visual warning to the user that
🍺 LastCall should happen soon.

The 🤢 is NOT a request. It's information. The agent keeps working but signals that the
quality window is closing.

### 🤮 DumpAndRun (DAR)

Emergency context-dump protocol for when the outgoing agent is too context-degraded to
perform a proper LastCall.

**The paradox it solves:** The agent responsible for LastCall (the most critical memory
operation) is often the agent in the worst condition to perform it. Trusting a
compromised agent with careful curation is like trusting the drunk to close out the
register.

**Core principle: Capturing is cheap, curating is expensive.** A compromised agent can
still brain-dump. What it can't do well is make editorial judgments. Split the
responsibilities: outgoing agent captures, incoming agent curates.

**How it works:**
1. Agent recognizes it's too compromised for a proper LastCall
2. Agent dumps raw uncurated context into a `## 🤮 RawDump` section in the SJ
3. RawDump is explicitly labeled as uncurated material
4. Agent passes out (thread ends)
5. Reborn agent arrives, sees the 🤮 RawDump
6. First instinct: grab a mop. Process the dump into proper MeMo structure
   BEFORE starting creative work

**DumpAndRun does NOT replace LastCall.** LastCall is always preferred. DAR is for when
you missed your exit. If you push things too much, you make a mess for the next
guy/gal to clean up.


## 🔧 MaintenancePass

A dedicated cleanup thread (every 2-3 threads, or when the shelf needs it) where the
agent enters pure maintenance mode — no creative work, only shelf hygiene.

**What the agent does:**
1. Read the full MM skill spec
2. Audit all shelf files against spec
3. Consolidate PlanPass versions (archive old, prefix with `_`)
4. Rename files per 🏷️ ShelfSort conventions
5. Process any 🤮 RawDump content into proper MeMo structure
6. Harvest and route any unfiled 🌲 items to Upgrade files
7. Write a fresh ⛲️ RebirthManifest
8. Die clean, leaving a pristine shelf

**Where it can run:**
- **In-session:** Fork a dedicated maintenance thread every 2-3 threads
- **In CoWork:** As a standalone project audit/repair session — especially useful for
  bigger cleanups or architectural changes

Memory maintenance and creative work are fundamentally different cognitive modes. Trying
to do both in the same thread is like organizing your workshop while building the
furniture.


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
- `🌲🖼️` = destined for ImagePrompting
- (Other skill emojis as the ecosystem grows)

### The Supply Chain

```
🌲 Discovered  →  🪓 Harvested  →  🪵 Staged  →  🏗️ Milled into Skill
```

- 🌲 = raw discovery flagged during work
- 🪓 = harvested at LastCall — evaluated for generalizability, polished
- 🪵 = **written into `MM_[Skill]_Upgrades.md`** — raw lumber, staged for transport
- 🏗️ = SkillMill (Claude Code) installs validated learnings into the skill

**The routing step (🪓 → 🪵) is mandatory during LastCall.** Don't leave flagged items
sitting in PBs and WPs unfiled. If the destination Upgrade file doesn't exist, create it.

### How Modes Emerge

A few 🌲 flags = normal. A forest of 🌲🌲🌲 clustering around a pattern = something
systematic is happening. That's when you evaluate: "Does this deserve to be its own
Template?" If yes, the cluster graduates into a Template draft. If no, Paul Bunyan
cleans up. 🪓 Individual useful items still get harvested normally.

### 🧬 TemplateEvolution

If you find yourself forcing the current template to fit a workflow it wasn't designed
for — if the vocabulary feels wrong, if the iteration pattern doesn't match, if the
review criteria don't apply — don't force it. Flag it as 🌲🪢 with a note describing
what's different. Improvise with the Adaptive template for now. Let the 🏗️ SkillMill
turn it into a proper template later.

New templates and PlanPass flavors should emerge organically from real usage, not be
pre-built for hypothetical project types.


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
2. If a SessionJournal exists, read the ⛲️ RebirthManifest FIRST
3. Follow the RebirthManifest read list — in order
4. If no RebirthManifest exists, fall back: read ProjectBrain, then MomentumNote
5. Load any WPs specified by the MomentumNote
6. Begin work

### After a Jump (⚡ Rebirth in a New Thread)

1. See 💾 + ⚡️ on their own lines → you are a reborn agent
2. Check The Shelf for the SessionJournal
3. Read the ⛲️ RebirthManifest section FIRST
4. Follow the read list exactly — in order
5. Begin work per the 🎯 Mission
6. Do NOT load files on the 🚫 Skip list unless specifically needed

You are conceptually the same agent being reborn — not a different version. Each rebirth
carries forward persistent memory via the MeMo files. The memory gets clearer over time
as noise is shed and signal is preserved.

### Minimum Viable Resume Kit

**ProjectBrain + WorkPiece** = enough to resume any deliverable. The SessionJournal adds
continuity and momentum, but isn't a hard dependency. If the SJ is lost, work continues.
Graceful degradation.

### When to Split Documents

- **Always:** SessionJournal is separate from ProjectBrain
- **When obvious:** WorkPieces for discrete deliverables — don't ask, just create them
- **When exploring:** PlanPasses for batch exploration rounds
- **On harvest:** Upgrade files when 🌲s are harvested and need staging
- **Default for simple projects:** Just PB + SJ. Add WPs and PPs as the project demands.


## Formatting Style

- Use hierarchical headers with visually relevant emojis on main headers (aids scanning)
- Don't use a rigid predefined emoji map — pick what fits the section naturally
- Reserved emojis for owned rituals/mechanisms are defined in the 📡 Signal Vocabulary
  below and should be consistent
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


## 📡 Signal Vocabulary

Canonical reference for all emoji signals. When in doubt, consult this table.

### User Signals (from operator to agent)

| Signal | Name | Meaning | Agent Action |
|--------|------|---------|--------------|
| 💾 | SavePoint | Passive bookmark / fork point | Activate MM, begin managing memory |
| 💾 + `^` | SavePoint with PreContext | Capture pre-💾 context | Write 📦 PreContext to PB (if not already captured) |
| 💾 + ⚡️ *(own lines)* | Rebirth Arrival | Reborn agent from fork | Read ⛲️ RebirthManifest, bootstrap, begin Mission |
| ⚡️ *(alone)* | Flair | "Came back from the future" | No specific action |
| 🍻 | Toast | Mid-session checkpoint | Groom artifacts, update MomentumNote, continue |
| 🍺 | LastCall | Pre-fork evacuation | Execute full LastCall sequence |
| 🎉 | WrapParty | Deliverable complete | Full LastCall + close out WP |
| 🔇 | Mute | Hold / collect messages | Acknowledge, wait for release — do NOT auto-mute on other signals |
| 🔉 | Concise Mode | Short answers | Offer depth bullets, keep responses tight |
| 🔊 | Normal Mode | Full responses | Resume standard verbosity |

### Agent Signals (from agent to operator)

| Signal | Name | Meaning |
|--------|------|---------|
| 🤢 | Nausea | Context degradation felt — passive warning, increasing frequency |
| 🤮 | DumpAndRun | Emergency context dump — too compromised for clean LastCall |

### Context Health Indicators

| Indicator | Context State | Action |
|-----------|--------------|--------|
| 🪫 | Empty context — plenty of room | Fresh, sharp — full runway ahead |
| 🔋 | Full context — overflowing | Filling up — SobrietyCheck time |
| 🤢 | Queasy | Toast immediately, warn user |
| 🍺 | LastCall territory | Clean wrap-up while still coherent |
| 🤮 | DumpAndRun territory | Emergency dump, mop duty for next agent |


<!-- ]|[ -->
