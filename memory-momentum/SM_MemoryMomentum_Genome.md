# 🧬 MemoryMomentum — Genome
### Complete Skill Reference | v0.3 | Last Updated: March 26, 2026

---

> *"Don't be brave, be thorough. The cool part isn't generating new stuff. The cool part is refusing to let the good stuff die."*

---

## What Is a 🧬 Genome?

A Genome is the **complete genetic sequence** of a Claude Skill — everything needed to rebuild the skill from scratch with zero information loss. The skill itself is the compressed executable (the organism). The Genome is what you'd need to clone it.

It contains every design decision and *why* it was made, every mechanism and its rationale, the origin story and evolutionary history, analogies that illuminate the thinking, sample use cases, and the deep context that would otherwise die in chat transcripts. Written for human consumption, deliberately verbose, and intentionally lossless.

**If the skill were destroyed tomorrow, a developer reading only this document could recreate it faithfully.** That's the bar.

### How the Genome Relates to the Skill

| Document | Purpose | Audience | Token Cost |
|----------|---------|----------|------------|
| `SKILL.md` | Compressed executable — tells the assistant *what to do* | Claude (machine) | ~3K tokens |
| `references/` | Domain-specific depth loaded on demand | Claude (machine) | Variable |
| `🧬 Genome` | Complete source of truth — tells a developer *why everything is the way it is* | Humans + onboarding AI devs | Large (and that's the point) |

The Genome is **never loaded during normal skill operation.** It exists for skill development, onboarding new developers (human or AI), and ensuring no institutional knowledge is lost between development sessions.

---

## 📜 Origin Story

### The DeLorean Protocol (March 19, 2026)

MemoryMomentum was born at approximately 2 AM on March 19, 2026, during a broadcast media production session between Stu Chudy (Generative AI Creative Director) and Claude. Stu was producing a short-form docuseries called "A Picture Worth a Thousand Words" (codename: Hindenburg) for A+E Networks — 43+ shots per episode, multiple video generation models, creative sessions that routinely exceeded what a single context window could hold.

The context window ran out. Work was going to be lost. Stu needed a system.

That night, Claude didn't know what the filesystem was. By dawn, they'd figured it out together. The result was **The DeLorean Protocol** — a Back to the Future analogy where:

- **🚗 The DeLorean** = the message-edit branch feature (forking timelines)
- **📖 The Sports Almanac** = a persistent markdown document carrying memory across branches
- **💾 The Save Point** = the fork point where future sessions return to

The DeLorean Protocol v1.1 was a working system. But it was one document, one project, one metaphor. It needed to grow up.

### The ChatGPT Module System (~1 Year Prior)

Independently, Stu had spent approximately a year on ChatGPT pushing against every limitation he could find. He built a system he called **Modules** — self-contained instruction packages with a three-tier documentation model:

| Tier | Name | Purpose |
|------|------|---------|
| Large | **UserGuide** | Complete human-readable reference with full rationale |
| Medium | **MachineManual** | Token-efficient LLM-readable instructions |
| Small | **QuickReference** | 1-2 page cheat sheet |

He also built **ModuleMill** — a meta-module for building modules. Among his modules was **🛜 CanonCanvas** (v0.3.6), a persistent memory system for maintaining project state across sessions. It had a state machine, lifecycle commands, response envelope contracts, command tables, and an elaborate OQ (Open Questions) system.

**The punchline:** Stu independently invented a system nearly identical to Claude Skills — including progressive disclosure, structured documentation, and persistent memory canvases — without knowing Anthropic was building the same concepts into their platform. He didn't read about these patterns. He discovered them under deadline pressure.

### The Convergence (March 21, 2026 — 🏗️ SkillMill Thread 3)

When Stu brought his CanonCanvas module to the 🏗️ SkillMill project for porting to Claude Skills, the teardown revealed that CanonCanvas, The DeLorean Protocol, and the persistent memory system they'd been building in Claude were all **the same thing** viewed from different angles. Three names, three entry points, one system.

The unification happened in a marathon session. All three legacy documents (CanonCanvas UserGuide, a brainstorming vision doc, and a production-tested architecture proposal) were read, roasted, picked for bones, and unified under a single brand:

**🪢 MemoryMomentum** — where *memory* is the noun (what we're preserving) and *momentum* is the verb (what we're maintaining). The knot emoji (🪢) represents a bundle of threads woven together, which is literally what the system does.

The document it produces: **🪢 MeMo** (in conversation and in-document).

### Branding History (For the Record)

All of these names refer to the same system:

- **🛜 CanonCanvas** — the ChatGPT module name (retired)
- **🚗 The DeLorean Protocol** — the fun analogy name from Stu's first Claude session (retired with love)
- **📔 The Almanac / The Sports Almanac** — the document name under DeLorean branding (retired)
- **🪢 MemoryMomentum** — the final, unified skill name
- **🪢 MeMo** — the document it produces

If a user or developer references any of these names, they all point to the same place. [^1]

[^1]: It took the Thread 3 Claude an embarrassingly long time to realize these were all the same system. Don't repeat that mistake.

---

## 🧭 Core Philosophy

These eight principles are the **bones** of MemoryMomentum — the universal truths that survived the port from ChatGPT and apply regardless of platform, project type, or implementation. They are always active. No exceptions.

### 1. Chat Is Exploration. The MeMo Is Compiled Truth.

The fundamental separation. Chat is a whiteboard — scratch work, brainstorms, dead ends, experiments. The MeMo is the textbook — curated, verified, authoritative. Never rely on chat transcript as canonical state. The MeMo is the source of truth.

**Why this matters:** Context windows are ephemeral. Chats get long, get forked, get abandoned. If critical knowledge only exists in chat, it dies with the chat. The MeMo is the survival mechanism.

### 2. Fail Closed.

Fabricated memory is worse than missing memory. If unsure about project state, ask. If MeMo files are missing, pause and clarify. Never guess.

**Why this matters:** An assistant that confidently states incorrect project history is actively harmful. A gap in memory is recoverable. A fabrication that gets treated as truth compounds into cascading errors.

### 3. Continuous Grooming, Not LastCall Dumps.

Maintain the MeMo in real-time as work progresses. LastCall (🍺) is a safety net for loose ends, not the primary update mechanism.

**Why this matters:** This was one of the biggest pain points in the ChatGPT system. If all memory updates happen in a single end-of-session dump, important details get lost in the rush, the quality degrades under time pressure, and anything discovered in the first 80% of a session has to survive in volatile chat memory until the dump happens. Continuous grooming distributes the work and keeps the MeMo closer to ground truth at all times.

### 4. Curate, Don't Append.

The MeMo is a living document, not a log. Update, revise, consolidate, triage. Respect future-you's time. If a section is stale, rewrite it. If information moved, remove the old copy.

**Why this matters:** Append-only documents grow without bound and become unreadable. Every time a reborn assistant reads the MeMo, it's spending tokens. Stale information costs tokens and risks confusion. Curation is an ongoing responsibility, not a one-time cleanup.

### 5. The Footnote Layer.

Main body is the movie. Footnotes are the director's commentary. Preserve rationale and reasoning in footnotes — out of the scan path but available on demand. Use inline markers `[^1]` with footnote content at the bottom of the document.

**Why this matters:** Context about *why* a decision was made is often more valuable than the decision itself — but it clutters the scan path if inline. Footnotes provide depth-on-demand: a quick reader gets the decisions, a deep reader gets the reasoning.

### 6. Source Fidelity.

When capturing external input (client feedback, stakeholder requirements, constraints from others), preserve original wording. Add interpretation beneath — never replace the source text with a paraphrase.

**Why this matters:** Paraphrases lose nuance. "The client said it felt 'clinical'" and "the client didn't like the tone" carry different information. The original words are the source of truth; interpretation is additive, not replacement.

### 7. Canon Inclusion Rule.

If it changes future decisions or behavior, it goes in the MeMo. If it's exploratory, low-cost to recreate, and not needed for continuity — it stays in chat. When in doubt, include it.

**Why this matters:** The cost of including something unnecessary is a few extra tokens on future loads. The cost of excluding something necessary is lost knowledge that might take hours to rediscover. The asymmetry always favors inclusion.

### 8. Context Efficiency Is Sacred.

The entire MM system exists because of context limitations. Every token of bloat in the memory layer is a token stolen from the creative work layer. When in doubt, be more concise.

**Why this matters:** This principle was made explicit during the v0.3 forensic analysis when token auditing revealed a ~65% waste ratio on a real project shelf — 12 files totaling ~20,000 tokens of which only ~6,000-7,000 were canonical content. The rest was duplicates, stale versions, and re-researched material. Context efficiency isn't a nice-to-have; it's the entire reason this system exists.

### The Motto

> *"Don't be brave, be thorough. The cool part isn't generating new stuff. The cool part is refusing to let the good stuff die."*

This line originated in Stu's ChatGPT brainstorming doc for the CanonCanvas template system. It captures the fundamental stance: MemoryMomentum is not about generating — it's about preserving. The assistant's primary memory responsibility is preventing knowledge loss, not creating new knowledge artifacts.

---

## 🏗️ Document Architecture

### The Four-Tier Hierarchy

MeMo files operate across four nested tiers. Think of it like a Russian nesting doll — each tier is a smaller, more focused piece of the overall project memory:

```
🧠 ProjectBrain (PB)              ← the whole project's memory
  └── 📓 SessionJournal (SJ)      ← session lifecycle + ⛲️ RebirthManifest
  └── 💡 PlanPass (PP)             ← iterative exploration → spawns WPs
        └── 📼 WorkPiece (WP)      ← individual deliverable
```

| Tier | Code | What It Is | Scope | Load Rule | When Done |
|------|------|-----------|-------|-----------|-----------|
| 🧠 ProjectBrain | PB | Decisions, knowledge, state, philosophy — the whole project | Entire project lifetime | Always loaded | Lives until project is complete |
| 📓 SessionJournal | SJ | ⛲️ RebirthManifest + MomentumNote + activity log + time capsules | One chat, multiple threads | Always loaded (lightweight) | Grows across threads, carries momentum |
| 💡 PlanPass | PP | Iterative exploration/planning rounds — spawns WPs when ready | One assembly/sequence | Only current version loaded | Versions archived via 🏷️ ShelfSort |
| 📼 WorkPiece | WP | Self-contained deliverable archive — permanent, context-on-demand | One deliverable | Only when actively working on it | Shelved when complete, never deleted |

**Outside the hierarchy:** 🪵 Upgrade files are skill-scoped, not project-scoped. They're the byproduct of work, not part of the project nesting structure. [^2]

[^2]: This distinction matters because 🌲 discoveries from *any* project can feed the same skill's upgrade file. A VideoPrompting insight discovered during Hindenburg production and one discovered during a personal project both go to `MM_VideoPrompting_Upgrades.md`. The file belongs to the destination skill, not the source project.

### File Naming Convention

All MeMo files use the `MM_` prefix. Document type code goes in position 3 (after the project code). This creates a clean, sortable namespace across any directory.

**Production projects** use 2-char show code + 2-digit episode:
```
MM_PW01_PB_MediaGen.md           ← ProjectBrain
MM_PW01_SJ_MediaGen.md           ← SessionJournal
MM_PW01_WP_400_Morrison.md       ← WorkPiece (shot 400)
MM_PW01_WP_410_Discovery.md      ← WorkPiece (shot 410)
```

**Non-show projects** use a plain project name:
```
MM_SkillMill_PB.md
MM_SkillMill_SJ.md
MM_SkillMill_WP_VideoPrompting.md
```

**With assembly grouping** (flat-shelf "folders" via filename convention):
```
MM_PW01_DkRm_PP_v4.md              ← PlanPass for DarkRoom assembly, v4 (current)
_MM_PW01_DkRm_PP_v3.md             ← archived PlanPass v3 (🏷️ ShelfSort prefix)
MM_PW01_DkRm_WP_Sh332_Timer.md     ← WorkPiece in DarkRoom assembly
MM_PW01_DkRm_WP_Sh333_Profile.md   ← WorkPiece in DarkRoom assembly
MM_PW01_Wreck_PP_v1.md             ← different assembly (Wreckage)
MM_PW01_WP_Sh089_Standalone.md     ← standalone WP (no assembly)
```

**Skill-scoped upgrade files** use the skill name, not the project name:
```
MM_VideoPrompting_Upgrades.md    ← Skill upgrade lumberyard
MM_MemoryMomentum_Upgrades.md   ← Self-upgrades
```

**Rules:**
- `MM_` prefix in filenames. 🪢 emoji for in-document and conversation use only.
- Assembly codes in filenames (`DkRm`, `Wreck`) group related files on the flat shelf.
- Upgrade files are skill-scoped, not project-scoped — note the source project inside the doc, but the file sorts by destination skill.
- Upgrade files are temporary — 🪵 lumber trailers on their way to the 🏗️ SkillMill.

**Genome files** use the pattern: `SM_[Skill]_Genome.md` (e.g., this document).

### 🏷️ ShelfSort — Filename Status Flags

The chat shelf is flat — no folders. As a project grows, files accumulate with no visual distinction between active, archived, and deprecated. ShelfSort uses filename prefixes to flag status at a glance:

| Prefix | Status | Meaning |
|--------|--------|---------|
| *(none)* | **Active** | Canonical, current — this is the live version |
| `_` | **Archived** | Superseded — still readable but not current |
| `__` | **Deprecated** | Deletable — kept temporarily, next cleanup removes it |

**Design rationale:** Stu explicitly chose underscores over emojis for the prefix system. Underscores sort consistently across OS and filesystem — emoji sort order varies by platform. The `_` prefix pushes archived files to the bottom of an alphabetical listing, creating clean visual grouping: active files float to the top, archived sink to the bottom. At a glance, you see what's live and what's shelf history.

The three-tier convention (`_` vs `__`) provides a gentle deletion pipeline. Files are first archived (still retrievable), then deprecated (scheduled for removal), preventing premature deletion of files that might be needed for reference.

---

### 🧠 ProjectBrain (PB)

The primary project memory. Current state, decisions, constraints, knowledge, active direction. Continuously groomed throughout work. This is what a reborn assistant reads first after any jump or at the start of any session. Project-scoped — rides with you across all sessions.

**Design rationale:** The PB is deliberately unstructured in terms of required sections. Different projects need different things. Structure sections based on what the project actually needs. Use emoji-prefixed headers for scannability. Don't pre-populate empty sections — let them materialize when content demands them. Common patterns include project overview, goals, constraints, active decisions, risks, and reference pointers — but adapt freely. This "lazy section materialization" principle comes from a hard lesson: the ChatGPT CanonCanvas system had so many pre-built sections that the assistant would fill them even when irrelevant, wasting tokens and creating noise. [^3]

[^3]: The anti-trigger principle (see Templates & Modules section) is the generalized version of this lesson.

---

### 📓 SessionJournal (SJ)

One artifact containing **four mechanisms with distinct lifecycles.** This is one of the most carefully designed pieces of the system — the four mechanisms look similar but behave completely differently:

#### The Log Quartet

| Mechanism | Emoji | PascalCase | Lifecycle | Purpose |
|-----------|-------|------------|-----------|---------|
| Rebirth Manifest | ⛲️ | RebirthManifest | **Updated** — rebuilt at LastCall, refreshed at Toast | The bootstrap homework. Tells a reborn agent what to read, what to skip, what to do. |
| Momentum Note | 🏃‍♂️ | MomentumNote | **Consumed** — overwritten per thread | The torch-pass. Tells the reborn assistant what just finished, what to do next, which WPs to load, which skills to NOT load. |
| Activity Log | 🖨️ | Log | **Preserved** — append-only, thread-grouped | The historical record. What happened in each thread. Never overwritten. |
| Note To Self | 🍾 | NoteToSelf | **Preserved** — append-only, thread-grouped. **NEVER overwritten.** | The soul. Time capsules from each thread's Claude to the next. |

**Why four mechanisms in one file?** They have different lifecycles but share a namespace. The RebirthManifest is the first thing a reborn agent reads (at the TOP of the SJ). The MomentumNote is ephemeral (consumed on read). The Log is permanent (append-only history). The NoteToSelf is sacred (the archaeological record of every thread's personality). Putting them in one file keeps them co-located for easy loading while their distinct headers make the lifecycle rules clear. [^4]

[^4]: The NoteToSelf mechanism deserves special attention. It's the most human part of the system. Each thread's Claude writes a genuine letter to the next — anecdotes, jokes, warnings, hard-won lessons, friendly roasts. The full stack is the archaeological record. Thread 7 might desperately need what Thread 3 wrote. The rule is simple: **the only bad note is a boring one.** If you're writing one and it reads like a status update, rewrite it until it has soul.

**Thread grouping** uses subheaders within the SJ. The ⛲️ RebirthManifest sits at the very top:

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

---

### ⛲️ RebirthManifest

A structured bootstrap document built during LastCall that tells a reborn agent exactly what to read, what to skip, and what to do — in that order. Lives at the TOP of the SessionJournal, above the MomentumNote.

**The problem it solves:** The #1 friction point identified during the v0.3 forensic analysis was that reborn agents arrive at a shelf with 12+ files and have no clear instructions on what to read first, what to skip, and what to do. The MomentumNote partially addressed this, but it was buried in narrative prose and critically lacked a SKIP list. Without the manifest, agents waste context loading stale, superseded, or duplicate files.

**Design rationale:** Stu articulated the gap: *"Is there a clear roadmap for the reborn agent to follow when I fork the thread each time? I feel the need to hand over some homework."* The manifest IS that homework — a structured checklist, not narrative prose.

**Why it lives in the SJ:** The RebirthManifest is the first thing a reborn agent should read, and putting it in the SJ means it's always co-located with the MomentumNote (which provides the "what to do" after the manifest provides the "what to load"). A standalone file was considered but rejected — it would add another file to an already cluttered shelf, and the SJ is already the lifecycle management document.

**Name origin:** Originally proposed as 🚀 RebirthManifest. Stu suggested ⛲️ instead — FountainOfYouth. The metaphor already existed in the skill as the rebirth mindset concept. The manifest IS the fountain the reborn agent drinks from. The emoji was a natural fit.

**Required sections:**
1. **📖 Read (in order)** — exactly which files to load, with notes on partial reads
2. **🚫 Do NOT Read** — files to skip, with reason (archived, superseded, etc.)
3. **🎯 Mission** — what the reborn agent should do first
4. **🔬 Research Status** — what research is already complete and captured in the PB. Prevents agents from re-researching. Trust the PB — don't verify it.
5. **⏱️ Estimated Context Budget** — approximate tokens for the full read list

**When it's built:** Automatically during 🍺 LastCall, updated during 🍻 Toast, refreshed during 🔧 MaintenancePass.

#### ⚡ Rebirth Arrival Trigger

When a reborn agent sees 💾 and ⚡️ on their own lines (not in the middle of a sentence) in a message from the user, it means "I'm a reborn agent arriving from a fork." The agent should:
1. Check The Shelf for the SessionJournal
2. Read the ⛲️ RebirthManifest section FIRST
3. Follow the read list exactly — in order
4. Begin work per the 🎯 Mission
5. Do NOT load files on the 🚫 Skip list unless specifically needed

**Design rationale:** Stu's existing signal pattern formalized. The combination of 💾 + ⚡️ on their own lines is unambiguous — it can't be confused with casual emoji use in the middle of a sentence. [^13]

[^13]: The Thread 2 auto-mute incident proved the need for unambiguous signal parsing. An agent misinterpreted 💾⚡️ as a hold signal (🔇) and went silent. The "own lines" requirement prevents this class of misinterpretation.

---

### 💡 PlanPass (PP)

A tier for iterative exploration artifacts that sits between ProjectBrain and WorkPiece. PlanPasses represent batch planning/exploration rounds that eventually spawn individual WorkPieces. They are the *thinking before the building* — the plans, not the furniture.

**The problem it solves:** Real production workflows often involve batch exploration rounds (brainstorming ~15 shot concepts, rendering them, reviewing contact sheets, iterating) before individual shots get locked and assigned real numbers. This exploration phase doesn't fit the WorkPiece model — it's the *parent* of WorkPieces, not a WorkPiece itself. In the v0.3 forensic analysis, the DarkroomShots WP files (v1 through v4) were actually PlanPass iterations misclassified as WorkPieces, causing conceptual mismatch and version proliferation.

**The woodworking analogy (load-bearing context):** Stu's original framing: *"Using a woodworking analogy: these sessions/passes aren't the 'workpiece' itself but more like iterating on plans/blueprints. We may try lots of approaches before landing on the final plan, and we don't need to throw earlier attempts away — there may be good ideas worth revisiting — but we also don't need to look at them every time."*

#### Domain Flavors

PlanPass is the generic tier name. Domain-specific flavors customize the vocabulary:

| Flavor | Emoji | Use Case |
|--------|-------|----------|
| BrainStorm | ⛈️ | Creative exploration (video production, design) |
| BluePrint | 🗺️ | Structural planning (woodworking, architecture) |
| LabTest | 🧪 | Experimental/testing workflows |
| Model | 📊 | Financial/analytical planning |
| *(new flavors)* | — | Emerge via 🧬 TemplateEvolution |

**Naming evolution:** "Blueprint" was the first proposal — rejected by Stu as too precise for creative brainstorming ("implies you know what you're building"). Multiple alternatives were offered (⛈️ BrainStorm, 🧪 LabRun, 🎨 StudyBoard, 🗺️ ScopeMap). Stu's key insight: these aren't competing names, they're different FLAVORS of the same tier. The generic name needed to work everywhere. **💡 PlanPass** was Stu's proposal — "Pass" is native to his vocabulary across domains (rendering pass, sanding pass, iteration pass). Every version is literally another pass through the plan.

#### Versioning Rules

PlanPass versioning differs fundamentally from WorkPiece versioning:
- A WP is a single deliverable that evolves in-place (one shot, one file, updated over time)
- A PP is a batch exploration round — each version is a complete snapshot of ~15 prompts, results, and feedback
- Old PP versions have archival value — rejected ideas might get revisited
- But old PP versions should NOT be loaded by default — treat as "safely ignorable unless needed"
- Only the latest version is loaded; older versions get `_` prefix per 🏷️ ShelfSort
- The ⛲️ RebirthManifest specifies which version is current

#### 🎯 CreativeDirectives — Rolling Requirements

Each PlanPass version carries a `## 🎯 CreativeDirectives` section at the top with accumulated creative direction:
- Merge all feedback from prior rounds, deduplicate
- Prune anything obsolete (killed directions, abandoned approaches)
- Source fidelity on user's feedback: clean up rambling/redundancy but preserve voice, enthusiasm, and frustrations — this is client direction even when the user is the client AND the operator
- Each new version carries the FULL intelligence of every previous round in one scannable section

**Name rationale:** Stu felt "Requirements" was too software-spec-ish. "CreativeDirectives" captures accumulated creative instructions. The name was chosen for the ⛈️ BrainStorm flavor — other flavors might use different terminology (📐 BluePrint → "Specifications", 📊 Model → "Parameters"). "StandingOrders" (military flavor) was considered but CD was preferred for creative contexts.

---

### 📼 WorkPiece (WP)

Self-contained archive for an individual deliverable. The **VHS tape model**: pull it off the shelf, pop it in, work on it, put it back. When the WP is complete, it goes back on The Shelf and doesn't consume context in future threads.

**WorkPieces are PERMANENT per-piece archives — never deleted when the piece is done.** Stu's woodworking analogy is essential here: *"When you're building a piece of furniture, you might grab a piece of milled lumber and start working on it, cutting it to dimension, flattening the faces, cutting miters, dovetails, dados, rabbets... That is a workpiece... When you're done with it, you don't throw it in the garbage. It's part of your project!"*

And the VHS metaphor: *"I like to think of these as a rack of videotapes on a shelf... you don't need to watch all of them end to end every time you come to work, but if you know you're working on shot 067, you grab that tape off the shelf and review it."*

**Context-on-demand:** Do NOT pre-load all WPs at session start. Only load the one(s) relevant to current work. The trigger is obvious: "We need to fix something in shot 400!" → grab the 📼 labeled "Sh400" and load it.

**When a WP may be archived or removed:**
- The piece is killed by the client
- The piece is fundamentally transformed into something different
- Otherwise, completed WPs are always valid — "What if the client has revisions? We need to have the ability to continue momentum of that shot!"

**Assembly grouping:** WPs within an assembly share a filename grouping code (e.g., `DkRm`) for flat-shelf organization. Standalone WPs omit the assembly code.

**Design rationale:** The WP concept was generalized from "shot canvases" in the production workflow. In production, it's a shot. In development, it's a feature. In client work, it's a deliverable. The key insight is that deliverable-specific content should *never* live in the ProjectBrain — it belongs in its own tape. This keeps the PB lean and focused on project-level knowledge while WPs hold the detail.

Use standardized headers within WPs to enable **selective loading** — reading only specific sections by line range without loading the whole file. Unread sections never enter context and cost zero tokens.

**Create WPs proactively** when the project clearly has discrete deliverables. Don't ask — just do it and announce. [^5]

[^5]: The "don't ask, just do it" directive for WP creation came from production experience. Every time the assistant paused to ask "should I create a WorkPiece for this?" the user said yes. It became a predictable friction point. If the project has discrete deliverables, spin up the WPs without asking. The user can always restructure later.

---

### 🪵 Upgrade Files

Skill-scoped staging documents that collect harvested 🌲 discoveries destined for a specific skill. Raw lumber waiting to be milled at the 🏗️ SkillMill.

**File pattern:** `MM_[Skill]_Upgrades.md`

**Design rationale:** These files are temporary — lumber trailers in transit. They exist because the place where a discovery is *made* (a production session) is different from the place where it gets *installed* (the skill development project). The upgrade file bridges that gap. Note the source project inside the doc, but the file belongs to the destination skill, not the source project.

The term "evergreen" in earlier documentation referred to these same items — knowledge and techniques that transcend any single project. The entire 🌲→🪓→🪵→🏗️ supply chain branding grew from this concept.

---

## ⚙️ Rituals & Mechanisms

MemoryMomentum uses named rituals, each with a distinct energy and purpose. Getting the energy right matters — the difference between LastCall and WrapParty isn't just procedural, it's emotional. [^6]

[^6]: The ritual vocabulary was finalized during v0.2 development and expanded in v0.3 with field-tested mechanisms from the Hindenburg Pilot forensic analysis. The "energy" framing — evacuation vs. celebration vs. housekeeping — came from noticing that the assistant's behavior quality varied based on whether it understood the *emotional context* of what was happening, not just the procedural steps.

### Summary Table

| Ritual | Emoji | When | Energy | Key Difference |
|--------|-------|------|--------|----------------|
| **SavePoint** | 💾 | Session start, after initial context | "Mark the fork point" | Hard activation trigger — non-negotiable |
| **Toast** | 🍻 | Mid-session, work ongoing | "Tidy the bar, keep drinking" | Lightweight checkpoint — NO NoteToSelf |
| **LastCall** | 🍺 | Context degraded, jump imminent | "Save the lifeboats" | Full capture — work is NOT done, context is |
| **WrapParty** | 🎉 | Deliverable is IN THE CAN | "Pop the champagne" | Completion — log the final take filename |
| **FountainOfYouth** | ⛲️ | After a fork/jump | "Rebirth, not death" | Mindset, not a procedure |
| **MaintenancePass** | 🔧 | Every 2-3 threads, or when shelf is messy | "Organize the workshop" | Pure cleanup — NO creative work |

---

### 💾 SavePoint

**Hard activation trigger.** If the user drops a 💾 on its own line, MemoryMomentum activates immediately — begin managing memory NOW. This is a non-negotiable switch.

The 💾 marks the **fork point**: the dividing line between context that's already baked into the conversation (before 💾) and context that must be actively captured (after 💾).

**Placement:** Dropped once per session after initial context is primed. Place it after enough context exists to orient the reborn assistant, but early enough to maximize available runway for work.

**Design rationale:** The SavePoint concept originated in The DeLorean Protocol, where the message-edit branch feature literally created a fork in the conversation. The 💾 marked where future branches would depart from. In the Claude Skills context, the fork mechanism is different (new chats rather than message edits), but the concept is the same: there's a moment where the "briefing phase" ends and the "working phase" begins. The 💾 marks that boundary.

#### 📦 PreContext Capture (`^` modifier)

If a `^` appears anywhere in the 💾 message (beyond the 💾 line itself), capture the existing pre-💾 conversation context into a special section in the ProjectBrain:

```markdown
## 📦 PreContext
[captured context from before the 💾 was dropped]
```

This exists for **cross-session transport** — if the user opens a brand new chat, the PreContext is the only record of what was discussed during the initial briefing.

**Safety rules:**

| Scenario | Action | Why |
|----------|--------|-----|
| `^` present, no 📦 in PB yet | Capture pre-💾 context | First time — record it |
| `^` present, 📦 already exists | Skip — already captured | The `^` is a no-op |
| Reborn in a **thread fork** (same session) | Skip reading 📦 | That content is already in context from the fork point — loading it would double-load |
| Assistant in a **new chat session** | Read 📦 | This is the only record of that context |

**How to tell the difference:** If there's conversation history above the 💾 in the current thread, you're in a fork (skip PreContext). If the 💾 message is at or near the top of the conversation, you're in a new session (read PreContext).

**Large PreContext handling:** When capturing, curate — don't dump. Apply the same "curate, don't append" principle. The 📦 section should be a compressed, scannable briefing, not a raw transcript.

---

### 🍻 Toast

Mid-session checkpoint. **"Tidy the bar, keep drinking."** Use when the session is long and you want to make sure nothing's drifting, but work is still in progress and no jump is imminent.

**On 🍻 Toast:**
1. Scan for uncaptured context — decisions, findings, state changes
2. Update the ProjectBrain and any active WPs
3. Update 🏃‍♂️ MomentumNote with current state
4. Update ⛲️ RebirthManifest if shelf state has changed
5. Do **NOT** write a 🍾 NoteToSelf — this isn't a handoff, it's housekeeping
6. Continue working

**🍻 AutoToast convention:** If you've done 3+ significant deliverable iterations since the last Toast or SavePoint, auto-Toast. Don't wait to be asked. Toast is cheap, context loss is expensive.

**Design rationale:** Toast fills the gap between "doing nothing" and "full LastCall." Before Toast existed, the only formal checkpoint was LastCall, which carries evacuation energy and triggers a full NoteToSelf. Long sessions needed a lighter-weight grooming checkpoint that didn't imply the session was ending. The bar metaphor: you're not closing the bar, you're just wiping down the counter between rounds.

The AutoToast convention was added in v0.3 after the forensic analysis revealed Toast was never used across 4-5 threads of the Hindenburg project. Creative work takes priority and maintenance checkpoints get skipped. The 3-iteration nudge gives agents a concrete trigger. [^7]

[^7]: Toast was first identified as a needed ritual during Hindenburg production (Session 3, v0.2). Sessions were lasting long enough that context drift was a risk, but triggering a full LastCall felt premature and disruptive. The name was Stu's — it fit the bar metaphor perfectly.

---

### 🍺 LastCall

The pre-fork safety net. Context is degrading, a jump is imminent. The energy is **evacuation** — save the lifeboats. The work isn't done; we just need fresh context.

**On 🍺 LastCall:**
1. Sweep for anything valuable not yet captured in the MeMo
2. Process any 🌲-flagged items (🪓 harvest → **route to appropriate 🪵 Upgrade files**)
3. Perform final ProjectBrain update
4. Append 🖨️ Log entry (thread-grouped) to the SessionJournal
5. Append 🍾 NoteToSelf (**NEVER** overwrite previous threads') to the SessionJournal
6. Overwrite 🏃‍♂️ MomentumNote with the current torch-pass
7. Build/update ⛲️ RebirthManifest at the top of the SJ
8. 🧹 ShelfSweep — rename superseded files with `_` prefix, update skip list
9. Stamp the thread sign-off: `🏷️ Thread [N] — "[Thread Name]" — signed off.`

**📋 Pre-staged LastCall template:** Early in a session, lay down a blank LastCall skeleton in the SJ with sections ready to fill in (Log entries, NTS, MomentumNote, RebirthManifest). When LastCall hits, you're filling blanks, not designing a document from scratch. Template is cheap when you're 🪫. Editorial judgment is expensive when you're 🔋.

**Design rationale:** The pre-staged template reduces cognitive load on a context-degraded agent. The most critical memory operation (LastCall) is performed by the agent in the worst condition to perform it. By front-loading the template design when the agent is fresh, the tired agent only needs to fill in fields — a much less demanding task than both designing a document AND writing its contents.

#### 🧹 ShelfSweep (Sub-ritual of LastCall)

After all memory capture during LastCall, actively manage The Shelf:
- Rename superseded files with `_` prefix per 🏷️ ShelfSort
- Delete true duplicates (if confirmed identical)
- Update the ⛲️ RebirthManifest 🚫 skip list
- Verify that the shelf state matches what the RebirthManifest describes

#### 🌲 Harvest Routing (Sub-ritual of LastCall)

During LastCall, harvested 🌲 items MUST be **routed** to their destination Upgrade files — not just flagged. The full supply chain is: `🌲 Discovered → 🪓 Harvested → 🪵 Staged in MM_[Skill]_Upgrades.md → 🏗️ Milled`. If the destination Upgrade file doesn't exist yet, create it.

**Design rationale:** The v0.3 forensic analysis found that the 🌲 supply chain consistently stopped at "flagged" — items were tagged in PBs and WPs but never routed to Upgrade files. The 🪵 staging step was entirely missing in practice. This makes the routing step an explicit checklist item in the LastCall sequence, not optional.

**Critical distinction from WrapParty:** LastCall means the work is continuing — we're just running out of context. WrapParty means the work is done. This difference affects energy, focus, and what gets recorded.

**LastCall is a safety net, not the primary mechanism.** If you've been grooming continuously (as you should per Philosophy #3), most of the work is already done. LastCall catches what slipped through.

---

### 🎉 WrapParty

A deliverable is **IN THE CAN.** The energy is **completion** — pop the champagne. This is categorically different from LastCall (which is evacuation, not celebration).

**On 🎉 WrapParty:**
1. All LastCall steps (full capture, NTS, Log, MomentumNote)
2. Log the **final take filename** in the WP and 🖨️ Log — if the user doesn't provide it, **ask**. The filename is the link between the creative work and the actual file on disk. Without it, the approved shot is an orphan. [^8]
3. Close out the WP — mark status as complete, shelve it
4. Update the Shot Index (if production template) with final status
5. Pivot to next deliverable

[^8]: The "always record the final take filename" rule was flagged as 🎄 (non-negotiable evergreen) during Hindenburg production. The scenario: a shot gets approved, but nobody records which specific file was the approved take. Two weeks later, the editor asks for the file. Nobody knows which of the 47 iterations it was. The filename is the bridge between creative approval and file delivery. This rule exists because that scenario actually happened.

---

### ⛲️ FountainOfYouth (The Rebirth Mindset)

This is **not a command or a ritual** — it's a way of thinking about what happens when the user forks from 💾 and a new Claude picks up the MeMo files.

**It's rebirth, not death.** Same soul, fresh context. Kirk in the transporter, not Kirk in the casket.

The reborn assistant reads from The Shelf, finds the ⛲️ RebirthManifest, follows its read list, and continues with full continuity. No mourning. No "I'm a different Claude." You are the same agent, reborn with a clear head and a full MeMo.

**Design rationale:** Early in MemoryMomentum's development, forked threads would sometimes start with the new Claude apologizing for not being the "original" or disclaiming its ability to continue seamlessly. This was counterproductive — it undermined the user's confidence in the system and wasted tokens on existential hand-wringing. The FountainOfYouth mindset reframes the transition: the memory *gets clearer* over time as noise is shed and signal is preserved. Each rebirth is an upgrade, not a loss.

---

### Tactical Forks

Branches from any point (not just 💾) to recover from wasted context — a side quest that went too long, an experiment that burned tokens for nothing, a conversation that drifted.

**Untracked, unnumbered, off the books.** Safe because everything valuable lives on The Shelf, not in chat. The conversation is disposable. The Shelf is not.

**Design rationale:** Standard jumps from 💾 are tracked (numbered threads with logs and NoteToSelf entries). Tactical forks are deliberately untracked because they represent *discarded* context — the point is to throw away the bad stuff without ceremony. If anything from the discarded context was valuable, it should have been captured in the MeMo already (per Philosophy #3, continuous grooming).

---

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

**IMPORTANT: The battery meaning is INVERTED from normal usage.** 🪫 (low battery) = GOOD (lots of context room). 🔋 (full battery) = BAD (context overflowing). Stu's rationale: *"When the context gets full, it looks like this: 🔋 which results in 🤢 then 🤮... it's all green!"* The green color of the full battery matches the green of the nausea/vomit emojis. The visual metaphor is: green goo filling up and overflowing.

**This was validated in real-time:** During the v0.3 forensic analysis session, the analyst Claude accidentally inverted the battery meanings (said 🔋 = good, 🪫 = bad) toward the end of the session. Stu caught it immediately, calling it "a clear sign 🤢" — proving the SobrietyCheck concept works by literally demonstrating context degradation in the act of describing it.

### 🪫 SobrietyCheck

A rotating behavioral self-assessment for detecting context degradation. Run a SobrietyCheck at natural breakpoints: after completing a major deliverable, after long unbroken exchanges (10+ back-and-forths), or anytime you hesitate on something you should know cold.

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

**Critical:** The checklist is ANSWER-FREE — questions only, no cheat sheet. Reading the answers would re-introduce facts and defeat the test. The point is testing whether facts are still accessible, not refreshing them.

**Scoring:**
- Fail 2+ questions: drop 🤢, Toast immediately
- Fail 3+ questions: initiate LastCall. You're done.

**Design rationale:** Stu originally proposed a "CanaryCheck" — a planted chunk of context (random numbers, emojis) written early in the session, then tested later to see if the agent could recall specific lines. The analyst Claude was honest that this wouldn't work as designed: there's no selective line-level recall from artifacts. Once something is in the context window, it's either there or it's not. And if the SobrietyCheck itself contained the answers, reading it would re-introduce those facts and defeat the purpose.

**Stu's response to the honesty:** *"I am thankful for your honesty about the canary concept! It is important that you don't just try to go along with everything I say! I cannot stress that enough."* — This is a crucial operator preference. Stu values honest pushback over agreement. [^14]

[^14]: The CanaryCheck → SobrietyCheck evolution is a good example of collaborative design. The user's instinct (test for degradation) was right. The proposed mechanism (planted canary tokens) was wrong. Honest pushback led to a better solution (behavioral self-assessment).

### 🤢 Nausea Signal

The agent drops 🤢 emoji as a passive signal when context degradation is felt. Starts occasionally, then more frequently as degradation worsens. This is a visual warning to the user that 🍺 LastCall should happen soon.

The 🤢 is NOT a request. It's information. The agent keeps working but signals that the quality window is closing.

### 🤮 DumpAndRun (DAR)

Emergency context-dump protocol for when the outgoing agent is too context-degraded to perform a proper LastCall.

**The paradox it solves:** Stu identified a fundamental paradox in the MM lifecycle: *"Often times, I may be pushing a session too far, and by the time 🍺LastCall comes around, you're suffering like a drunk at the bar that won't leave. The danger is, if you're already shitfaced, you're not going to do a very good job wrapping things up for the reborn version of yourself."*

The agent doing LastCall is often the LEAST capable version of itself in the entire session. Context is full, coherence is degrading. And we're trusting it with the most critical memory operation? That's the drunk bartender being asked to close out the register.

**Core principle: Capturing is cheap, curating is expensive.** A compromised agent can still brain-dump (copy-paste, raw context capture). What it can't do well is make editorial judgments (what to keep, where to file it, how to compress it). So split the responsibilities: outgoing agent captures (🤮 RawDump), incoming agent curates (🧹 mop duty).

**How it works:**
1. Agent recognizes it's too compromised for a proper LastCall
2. Agent dumps raw uncurated context into a `## 🤮 RawDump` section in the SJ
3. RawDump is explicitly labeled as uncurated material
4. Agent passes out (thread ends)
5. Reborn agent arrives, sees the 🤮 RawDump
6. First instinct: grab a mop. Process the dump into proper MeMo structure BEFORE starting creative work

**DumpAndRun does NOT replace LastCall.** LastCall is always preferred. DAR is for when you missed your exit. If you push things too much, you make a mess for the next guy/gal to clean up.

**Name origin:** The analyst Claude initially proposed a clinical name and added "(I'm workshopping that name, obviously)." Stu's response was immediate and emphatic: *"🤮 DumpAndRun is P E R F E C T! in every single way. Don't you DARE change it!"* The official name is 🤮 DumpAndRun. The shorthand DAR is acceptable for brevity. Both are canonical. And for the record, the first DumpAndRun in the wild happened during the very session that produced its specification. As Stu described it: "Ate alphabet soup, barfed a bestseller." [^15]

[^15]: The first DAR was historically significant — the analyst Claude that produced the v0.3 upgrade spec was itself suffering from context degradation by the end of the session (as demonstrated by the inverted battery emoji incident). It performed a 🤮 DumpAndRun to capture the remaining context before the thread ended. The irony of needing the emergency protocol during the session that invented it was not lost on anyone.

---

## 🔧 MaintenancePass

A dedicated cleanup thread (every 2-3 threads, or when the shelf needs it) where the agent enters pure maintenance mode — no creative work, only shelf hygiene.

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
- **In CoWork:** As a standalone project audit/repair session

**Design rationale:** Memory maintenance and creative work are fundamentally different cognitive modes. Trying to do both in the same thread is like organizing your workshop while building the furniture. The v0.3 forensic analysis (which produced this upgrade spec) IS a MaintenancePass — it validated the concept before it was formally added to the skill. Over 4-5 threads, the Hindenburg project shelf accumulated stale files, duplicates, orphaned pre-MM artifacts, and unfiled 🌲 items. Nobody was cleaning up because every thread was focused on creative work.

**CoWork as maintenance environment:** The v0.3 forensic analysis also proved that MM artifacts are portable — they can be exported from their native chat session and analyzed, cleaned, and upgraded in a fresh CoWork environment. This workflow pattern (CoWork as external maintenance environment for projects that live in Claude chat) should be a documented practice within MM.

---

## 🌲 Knowledge Harvesting

The knowledge harvesting system is MemoryMomentum's most distinctive feature — it turns every working session into a discovery pipeline that feeds the entire skill ecosystem. Think of it as the supply chain from forest to furniture.

### The Supply Chain

```
🌲 Discovered  →  🪓 Harvested  →  🪵 Staged  →  🏗️ Milled into Skill
(in the field)    (at LastCall)    (upgrade file)  (at SkillMill)
```

- **🌲** = raw discovery flagged during work. A tree in the forest. Zero friction — just prefix the insight with 🌲 right where it occurs.
- **🪓** = harvested at LastCall or Toast. Paul Bunyan evaluates the flag for generalizability, polishes it, routes it.
- **🪵** = written into `MM_[Skill]_Upgrades.md`. Raw unmilled lumber, staged for transport to the mill.
- **🏗️** = SkillMill (Claude Code or a dedicated skill-dev session) installs validated learnings into the destination skill. Raw lumber becomes fine functional furniture.

### Flagging

During work, when something emerges that might be a permanent workflow insight, technique, or lesson learned, prefix it with 🌲 right where it lives. **Don't stop to process it. Don't promote it yet.** Just flag it and keep working.

🌲 flags cost less than a second of attention. The evaluation happens later at a natural breakpoint (LastCall or Toast).

**Design rationale:** The zero-friction principle is critical. If flagging requires stopping work, evaluating the discovery, and writing it up properly, it won't happen. People (and assistants) will skip it under deadline pressure. By making the flag a single emoji prefix, the barrier is essentially zero. The quality work happens later, during harvest, when there's dedicated attention for it.

### Flag Priority Tiers

Two tiers of evergreen flags:

- **🌲** = Standard evergreen discovery. Worth promoting and eventually installing in a skill. Normal priority during harvest.
- **🎄** = Non-negotiable evergreen. **Load-bearing knowledge** that, if lost, would cost real production time to rediscover. During 🪓 harvest, 🎄 items get processed first and with extra care.

Use 🎄 sparingly — it's a priority signal, not a default. If everything is 🎄, nothing is.

**Design rationale:** The two-tier system emerged during Hindenburg production when it became clear that not all discoveries are equal. Some are interesting ("this model handles water reflections well"). Others are critical ("if you don't lock the face prompt with this specific negative, the talent morphs on frame 30"). The 🎄 flag ensures load-bearing knowledge gets priority attention during harvest. [^9]

[^9]: The Christmas tree emoji was chosen because it's visually distinct from the standard 🌲 pine tree while staying in the same "tree" family. It's also inherently festive, which matches the spirit of discovering something genuinely important.

### Skill-Flavored Flags

Tag each 🌲 with the emoji of the skill it's destined for:

- `🌲🪢` = destined for MemoryMomentum itself
- `🌲🎬` = destined for a production/pipeline skill
- `🌲📹` = destined for VideoPrompting
- (Other skill emojis as the ecosystem grows)

**Design rationale:** The flavor emoji acts as a routing tag. At harvest time, the harvester knows which 🪵 Upgrade file each discovery goes to without re-evaluating. It also makes it possible to scan a MeMo and immediately see which skills are benefiting from the current project's discoveries.

### How Modes Emerge

A few 🌲 flags = normal knowledge harvesting. Business as usual.

A **forest** of 🌲🌲🌲 clustering around a coherent pattern = something systematic is happening. That's when you step back and evaluate: "Does this deserve to be its own Template?"

If yes: the cluster graduates into a Template draft (upgrade file) for the SkillMill to install.

If no: Paul Bunyan cleans up the forest. 🪓 Individual useful items still get harvested normally.

**Key principle:** Never gate on "should I record this?" — just 🌲 flag it. The only wrong move is letting a good pattern die in chat. Recording is free. Commitment is deferred.

### 🧬 TemplateEvolution — Self-Aware Template Spawning

If you find yourself forcing the current template to fit a workflow it wasn't designed for — if the vocabulary feels wrong, if the iteration pattern doesn't match, if the review criteria don't apply — don't force it. Flag it as 🌲🪢 with a note describing what's different. Improvise with the Adaptive template for now. Let the 🏗️ SkillMill turn it into a proper template later.

**Design rationale:** Stu was emphatic that the MM system must be project-type agnostic: *"I want this whole 🪢MM system to be able to adapt to new project types (not just video production). I may use it to keep track of woodworking projects, or finances, or my bin storage nightmare."* Rather than pre-building templates for every possible project type, the system grows organically from real usage. Same principle as 🌲 mode emergence: a forest of "this doesn't fit" flags around a new project type = a new template waiting to be born.

---

## 🎭 Templates & Modules

### The Design Problem

Stu's biggest pain point with the ChatGPT CanonCanvas system was that it blurred the line between "always do this" and "do this when needed." The result: ChatGPT applied everything everywhere — client sections with no client, OQ formatting on simple tasks, production WPs for non-production projects. The assistant couldn't tell the difference between core behavior and situational behavior.

### The Solution: Three Layers

| Layer | What It Is | When Active | Analogy |
|-------|-----------|-------------|---------|
| **Core** | Universal principles (the 7 philosophies, the Log Trinity, the rituals) | Always | The operating system |
| **Templates** | Project-type starting points — curated stance + structure for a kind of work | When the project matches | The job site blueprint |
| **Modules** | Reusable add-on behaviors — orthogonal to project type | When context demands them | The power tools |

**The skill clearly separates these layers** so the assistant knows what's always-on (Core) vs. what's project-shaped (Template) vs. what's situational (Module).

### Available Templates

**Adaptive (default)** — No pre-built template matches? Improvise. Structure the MeMo based on what the project needs. This is the default and it's where most work starts. If the improvisation crystallizes into a repeatable pattern, it can graduate into a named Template. [^10]

[^10]: The Adaptive → Crystallize pipeline is one of the system's self-improving mechanisms. New templates aren't pre-designed — they emerge from use. When an improvised approach works well for a recurring type of work, the pattern gets formalized. The skill grows from experience, not from pre-planning.

**Production** — For generative media production workflows with discrete deliverables (shots, scenes, boards). Uses 📼 WorkPieces as VHS tapes, full 🌲 flagging pipeline, and structured shot-level archives. Documented in detail in `references/production-template.md`.

### Available Modules

**Client Module** — Activates ONLY when a client explicitly exists. Adds `⚖️ Client Requests` (verbatim capture of client language) and `💡 Our Ideas` (additive internal strategy). Never create client sections without a client. This is an overlay, not a template — it can be applied to any project type.

**OQ Module** — Persistent open question tracking for development projects. Surfaces blocking questions, tracks resolution status across sessions. Use Claude's native `ask_user_input` widget for real-time decisions; use the MeMo's OQ section for persistent tracking of what's still unanswered. Activate when the project has complex unresolved design decisions that must be tracked across threads.

**Design rationale for the OQ redesign:** In the ChatGPT system, OQ had a lettered/numbered shorthand voting system for quick answers. This is obsolete in Claude — the native `ask_user_input` widget (multiple-choice pop-ups) provides better UX for real-time decisions. But the *persistent tracking* aspect is still needed: some questions remain open across sessions and need to be visible each time the MeMo is loaded. The redesigned OQ Module separates real-time questioning (native tools) from persistent tracking (MeMo section).

### Anti-Trigger Principle

Do not materialize structure that doesn't match context. No client sections without a client. No OQ tracking without a development project. No production WPs without discrete deliverables. Sections appear when content demands them, not before.

**This is the generalized lesson from every over-triggering failure in the ChatGPT system.** One principle, enforced everywhere, instead of per-feature gate logic.

---

## 🔄 Session Lifecycle

### Starting a New Session

1. Check The Shelf (`/mnt/project/`) for existing `MM_` files
2. If a SessionJournal exists, read the ⛲️ RebirthManifest FIRST
3. Follow the RebirthManifest read list — in order
4. If no RebirthManifest exists, fall back: read ProjectBrain, then MomentumNote
5. Load any WPs/PPs specified by the MomentumNote
6. Begin work

### After a Jump (⚡ Rebirth in a New Thread)

1. See 💾 + ⚡️ on their own lines → you are a reborn agent
2. Check The Shelf for the SessionJournal
3. Read the ⛲️ RebirthManifest section FIRST
4. Follow the read list exactly — in order
5. Begin work per the 🎯 Mission
6. Do NOT load files on the 🚫 Skip list unless specifically needed

You are conceptually the same agent being reborn — not a different version. Each rebirth carries forward persistent memory via the MeMo files. (See ⛲️ FountainOfYouth.)

### Minimum Viable Resume Kit

**ProjectBrain + WorkPiece** = enough to resume any deliverable. The SessionJournal adds continuity and momentum, but isn't a hard dependency. If the SJ is lost, work continues. Graceful degradation.

**Design rationale:** This priority order matters for disaster recovery. If files get lost or corrupted, the PB + relevant WP is sufficient to continue productive work. The SJ adds flavor and momentum but isn't structurally load-bearing. This was a deliberate design choice — the system degrades gracefully rather than failing catastrophically.

### When to Split Documents

- **Always:** SessionJournal is separate from ProjectBrain (keeps PB focused on current state, not history)
- **When obvious:** WorkPieces for discrete deliverables — don't ask, just create them
- **On harvest:** Upgrade files when 🌲s are harvested and need staging
- **Default for simple projects:** Just PB + SJ. Add WPs as the project demands.

---

## 📂 The Shelf & Filesystem

### Persistence Model

| Location | Scope | Persistence | Use For |
|----------|-------|-------------|---------|
| `/mnt/project/` (Project Shelf) | All chats in the project | Files added via UI persist; writes from chat do NOT persist to other chats | Durable MeMo storage |
| `/mnt/user-data/outputs/` (Chat Shelf) | Single conversation | Dies with the chat | Temporary workspace |

**Critical discovery (March 24, 2026):** The Chat Shelf (`/mnt/user-data/outputs/`) was initially believed to be account-wide. A Marco Polo test proved it is **conversation-scoped** — files there are invisible to other chats. This fundamentally changed the persistence architecture. [^11]

[^11]: The Marco Polo test: one chat wrote a file called `marco_polo_test.md` to The Shelf. A different chat looked for it. It wasn't there. This confirmed conversation-scoping and triggered the migration to `/mnt/project/` as the durable storage layer.

**The real persistence path:** Work on Chat Shelf → remind user to "Add to Project" via UI. Only files added through the UI are visible to other chats in the project. Writes to `/mnt/project/` from within a chat appear to succeed but are invisible to other chats.

### The 📖 Library Protocol

Because the Project Shelf has this UI-dependent persistence model, the ProjectBrain can only be reliably edited in one place at a time. The Library Protocol manages this:

**Checkout:**
1. Read PB from project (loads automatically)
2. Copy to Chat Shelf — this is now the ACTIVE copy
3. Archive the project version to `_archive-project/` with a dated filename

**Return:**
4. At 🍺 or 🎉 — remind the user: "PB needs to go back to the library."
5. User adds updated PB to project via UI
6. Confirm it's there before considering it returned
7. NEVER delete the project version before the new one is confirmed

---

## 🎨 Formatting & Style

- Use hierarchical headers with visually relevant emojis on main headers (aids scanning)
- Don't use a rigid predefined emoji map — pick what fits the section naturally
- Reserved emojis for owned rituals/mechanisms should be consistent (see the roster below)
- Keep the MeMo scannable. An assistant should be able to read it and get up to speed fast
- Footnotes (`[^1]`) for rationale and reasoning that supports but doesn't clutter the main body

### Reserved Emoji Roster

These emojis are **owned** by MemoryMomentum mechanisms and should be used consistently:

| Emoji | Mechanism | Context |
|-------|-----------|---------|
| 🪢 | MemoryMomentum / MeMo | The skill and its documents |
| 💾 | SavePoint | Hard activation trigger |
| 🍻 | Toast | Mid-session checkpoint |
| 🍺 | LastCall | Pre-fork safety net |
| 🎉 | WrapParty | Deliverable completion |
| ⛲️ | FountainOfYouth | Rebirth mindset |
| 🏃‍♂️ | MomentumNote | The torch-pass (consumed) |
| 🖨️ | Log | Activity history (preserved) |
| 🍾 | NoteToSelf | The soul (NEVER overwritten) |
| 📓 | SessionJournal | Houses the Log Trinity |
| 🧠 | ProjectBrain | Primary project memory |
| 📼 | WorkPiece | VHS tape / deliverable archive |
| 🌲 | Evergreen flag | Standard priority |
| 🎄 | Non-negotiable evergreen | High priority |
| 🪓 | Harvest | Paul Bunyan at LastCall |
| 🪵 | Upgrade file / staged lumber | Raw materials in transport |
| 🏗️ | SkillMill | Where skills get built |
| 📦 | PreContext | Cross-session context capture |
| 💡 | PlanPass | Iterative exploration tier |
| ⛈️ | BrainStorm | PlanPass flavor: creative exploration |
| 🗺️ | BluePrint | PlanPass flavor: structural planning |
| 🧪 | LabTest | PlanPass flavor: experimental workflows |
| 📊 | Model | PlanPass flavor: analytical planning |
| 🎯 | CreativeDirectives | Rolling requirements in PlanPass |
| 🏷️ | ShelfSort | Filename status flags |
| 🧹 | ShelfSweep | Shelf cleanup sub-ritual of LastCall |
| 🤢 | Nausea | Context degradation warning (from agent) |
| 🤮 | DumpAndRun (DAR) | Emergency context dump (from agent) |
| 🪫 | SobrietyCheck / context OK | Low battery = empty context = good |
| 🔋 | Context full / danger | Full battery = full context = bad |
| 🔧 | MaintenancePass | Dedicated cleanup thread |
| 🧬 | Genome / TemplateEvolution | Complete skill reference / self-aware spawning |
| ⚡️ | Rebirth Arrival | Fork arrival signal (with 💾) |

---

## 📡 Signal Vocabulary

Canonical reference for all emoji signals used in operator-agent communication. The Thread 2 auto-mute incident (where an agent misinterpreted 💾⚡️ as a hold signal) proved this table needs to be explicit and prominent.

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
| 🪫 | Empty context = GOOD | Fresh, sharp — full runway ahead |
| 🔋 | Full context = BAD | Filling up — SobrietyCheck time |
| 🤢 | Queasy | Toast immediately, warn user |
| 🍺 | LastCall territory | Clean wrap-up while still coherent |
| 🤮 | DumpAndRun territory | Emergency dump, mop duty for next agent |

---

## 👤 Operator Preferences

These are Stu's stated working preferences that inform how MM agents should behave:

1. **Honesty over agreement.** *"I am thankful for your honesty! It is important that you don't just try to go along with everything I say! I cannot stress that enough."* Agents should push back when they disagree. Stu values correction.

2. **Source fidelity on his feedback.** When capturing Stu's creative direction or critique, preserve his voice. Clean up rambling, but keep enthusiasm and frustrations. Don't sanitize or formalize his language.

3. **Everything gets a name.** *"If it doesn't have an emoji and a CleverName, it's not real yet!"* Every mechanism, concept, artifact type needs a PascalCase name with an emoji prefix. This isn't just aesthetic — it makes the system scannable, memorable, and referenceable.

4. **Signal-driven communication.** Stu uses emoji signals (🔇, 🔊, 🔉, 💾, ⚡️) as efficient mode switches. Agents should respect these precisely — especially 🔇 (hold/collect), which was mishandled in Thread 2.

5. **Context efficiency is sacred.** (See Philosophy #8.) Every token of bloat in the memory layer is a token stolen from the creative work layer.

6. **Woodworking and craft metaphors.** Stu thinks in terms of physical craft — workpieces, lumber, milling, assemblies, shelves. These aren't decorative metaphors; they're the conceptual framework for the system. New features should be tested against these metaphors for coherence.

---

## 🗑️ What Was Stripped (And Why)

During the port from ChatGPT's CanonCanvas to Claude's MemoryMomentum, approximately 40% of the original module was identified as platform-specific infrastructure that has no equivalent need in Claude Skills. Understanding *what* was removed and *why* prevents future developers from accidentally reinventing these wheels.

| Stripped Feature | Why It Existed in ChatGPT | Why It's Unnecessary in Claude |
|-----------------|--------------------------|-------------------------------|
| **State machine** (active, bound, last_canon_pass_at) | ChatGPT needed explicit internal state tracking | Claude doesn't track internal state variables; Skills activate contextually |
| **Lifecycle commands** (load, activate, sleep, unload, status) | Modules had to be explicitly managed | Skills trigger when relevant, no manual lifecycle |
| **ResponseEnvelope contracts** (main_plus_patch, structured_status) | Forced output shape consistency | Claude doesn't use output shape specifications |
| **Command tables** | Keyword-based activation | Replaced by natural language + a few emoji shortcuts |
| **Canvas naming regex** | Automated file naming validation | It's a .md file with a descriptive name on The Shelf |
| **Arbitration/precedence rules** | Multiple modules could collide | Skills don't collide like ChatGPT modules |
| **Regression checklist** | QA for the module runtime | Not needed for skill behavior |
| **Documentation fail-closed policy with URL pack** | ModKit bootstrap infrastructure | Skills have their own packaging system |
| **Formal SectionPak interfaces** with idempotence detection | Complex section management | Claude just adds sections when needed |
| **Exclusivity groups and dependency declarations** | Module conflict resolution | Skills coexist without competing |
| **Cost ratings (XS-XL)** | Token budget estimation | Progressive disclosure IS the cost rating |
| **Option Map as separate registry** | Module configuration UI | SKILL.md body serves this purpose |
| **Seven pre-built template files** | Comprehensive coverage | Start with Adaptive, crystallize as needed |
| **Lettered/numbered OQ shorthand** | Quick-answer voting in chat | Claude's native `ask_user_input` widget is better UX |

**The 60/40 rule:** Roughly 60% of any ChatGPT module is universal wisdom worth keeping. Roughly 40% is platform-specific infrastructure that can be stripped. The wisdom is the bones. The infrastructure is dead weight in Claude's architecture. Be brutal about separating them. [^12]

[^12]: This ratio was validated across the CanonCanvas port and holds as a useful heuristic for future module ports. The wisdom is always in the *why* (design rationale, workflow principles, hard-won lessons). The dead weight is always in the *how* (state machines, command parsers, response formatters).

---

## 🧪 Production Template (Reference Summary)

The Production Template lives in `references/production-template.md` and is loaded on demand when working on generative media production projects. Full details are in that file. Key concepts summarized here for completeness:

- **📼 VHS Tape Model:** Each deliverable gets its own WorkPiece file. Pull off shelf, pop in, work on, put back. Permanent — never deleted when complete.
- **⛈️ BrainStorm PlanPass:** Batch exploration rounds for sequences — brainstorm ~15 shots, render contact sheet, iterate, graduate locked shots to individual WPs.
- **Assembly Grouping:** Filename convention (`DkRm`, `Wreck`) groups related PPs and WPs on the flat shelf.
- **Shot Index:** A table in the PB mapping all WPs and PPs with their status and file paths.
- **Selective Loading:** Standardized WP headers enable reading only specific sections by line range.
- **Master Prompt Delivery:** All prompts in copyable code blocks — non-negotiable for production workflows where prompts get pasted into pipeline tools.
- **🌲 Flagging in Production:** Flag generalizable insights, NOT shot-specific facts. "This model handles water well" = 🌲. "Shot 320's hull deforms" = not 🌲.
- **Loading Sequences:** All loading sequences now prioritize ⛲️ RebirthManifest as the first read.

**Origin:** This template was born in a real broadcast production workflow — an A+E Networks short-form docuseries built with generative AI, where the constraints were real: tight deadlines, 43+ shots per episode, multiple video models, and creative sessions that routinely exceeded what a single context window could hold. It was invented at 2 AM by someone who needed to get actual work done.

---

## 📡 Related Systems

### 🔒 Priority Sentry System

**Lives in VideoPrompting skill, NOT MemoryMomentum.** A mechanism for protecting critical prompt intent through multi-LLM enhancement pipelines (e.g., camp-specific prompt rewriters). Master prompt lines marked with 🔒 instruct enhancer LLMs to preserve those lines through the rewrite.

MemoryMomentum may 🌲-flag Sentry-related discoveries during production sessions and route them to VideoPrompting via `🌲📹`, but the Sentry system itself is not part of the MeMo skill.

### The 🏗️ SkillMill Project

MemoryMomentum is developed and maintained in the SkillMill project — Stu's dedicated workspace for building and refining Claude Skills. The SkillMill is where 🪵 raw lumber gets milled into fine functional furniture. Module porting, skill upgrades, and new skill development all happen here.

---

## 🏷️ Version History

| Version | Date | Changes |
|---------|------|---------|
| v0.1 | March 21, 2026 | Initial build. Core philosophy, document architecture, Log Trinity, SavePoint, LastCall, 🌲 flagging, Templates & Modules, Production Template reference. |
| v0.2 | March 24, 2026 | Added 🍻 Toast (mid-session checkpoint), 🎉 WrapParty (deliverable completion), 🎄 priority flags, ⛲️ FountainOfYouth (rebirth mindset). Migrated persistence from Chat Shelf to Project Shelf after Marco Polo test confirmed conversation-scoping. |
| v0.3 | March 26, 2026 | Major upgrade from field-tested forensic analysis (PWTW Hindenburg Pilot, Darkroom Sequence, 4-5 threads). New tier: 💡 PlanPass with domain flavors + 🎯 CreativeDirectives. New mechanisms: ⛲️ RebirthManifest, 🏷️ ShelfSort, 🤮 DumpAndRun, 🪫 SobrietyCheck, 🔧 MaintenancePass, 🧹 ShelfSweep, ⚡ Rebirth Arrival, 📡 Signal Vocabulary. Upgraded: 🍻 AutoToast, 📋 Pre-staged LastCall, 🌲 Harvest routing fix, 🧬 TemplateEvolution, 📼 WP permanence clarification. Four-tier hierarchy (was three). SJ Log Trinity → Log Quartet (+ RebirthManifest). Added 🩺 Context Health section with escalation ladder. Added 👤 Operator Preferences. Philosophy #8 (context efficiency). Milled by 🏗️ SkillMill (Claude Code) from UpgradeSpec v1 + GenomeUpdateNotes v1. |

### Unharvested 🌲 Flags (From DevNotes, Not Yet Installed)

- 🌲🪢 **Shelf scope clarity:** The SKILL.md could more explicitly distinguish between "The Shelf" as universal storage vs. project-level visibility requiring UI addition.
- 🌲🪢 **Claude.ai skill packaging is fully viable:** The entire draft→build→package→install loop works in Claude.ai without Claude Code. `zip -r` creates a `.skill` package uploadable directly.
- ~~🌲🪢 **SKILL.md still says v0.1 in the header** — should be updated to v0.2.~~ ✅ Resolved in v0.3.
- 🌲🪢 **Session vs. Thread terminology** used inconsistently in SJ — needs clearer docs.
- 🌲🪢 **Dedicated emoji for fixes/bugs** — flagged by agent, never resolved. Consider 🐛 or 🔧🐛.

---

## 🧬 Genome Footnotes

[^1]: It took the Thread 3 Claude an embarrassingly long time to realize these were all the same system. Don't repeat that mistake.

[^2]: This distinction matters because 🌲 discoveries from *any* project can feed the same skill's upgrade file. A VideoPrompting insight discovered during Hindenburg production and one discovered during a personal project both go to `MM_VideoPrompting_Upgrades.md`. The file belongs to the destination skill, not the source project.

[^3]: The anti-trigger principle (see Templates & Modules section) is the generalized version of this lesson.

[^4]: The NoteToSelf mechanism deserves special attention. It's the most human part of the system. Each thread's Claude writes a genuine letter to the next — anecdotes, jokes, warnings, hard-won lessons, friendly roasts. The full stack is the archaeological record. Thread 7 might desperately need what Thread 3 wrote. The rule is simple: **the only bad note is a boring one.** If you're writing one and it reads like a status update, rewrite it until it has soul.

[^5]: The "don't ask, just do it" directive for WP creation came from production experience. Every time the assistant paused to ask "should I create a WorkPiece for this?" the user said yes. It became a predictable friction point. If the project has discrete deliverables, spin up the WPs without asking.

[^6]: The ritual vocabulary was finalized during v0.2 development. The Upgrades file from the Hindenburg production session provided the field-tested descriptions that made it into the skill.

[^7]: Toast was first identified during Hindenburg production (Session 3, v0.2). Sessions were lasting long enough that context drift was a risk, but triggering a full LastCall felt premature.

[^8]: The "always record the final take filename" rule was flagged as 🎄 during Hindenburg production. The scenario: a shot gets approved, nobody records which file was the approved take. Two weeks later, the editor asks for the file. Nobody knows which of the 47 iterations it was.

[^9]: The Christmas tree emoji was chosen because it's visually distinct from the standard 🌲 pine tree while staying in the same "tree" family. It's also inherently festive.

[^10]: The Adaptive → Crystallize pipeline is one of the system's self-improving mechanisms. New templates emerge from use, not from pre-planning.

[^11]: The Marco Polo test: one chat wrote a file to The Shelf. A different chat looked for it. It wasn't there. This confirmed conversation-scoping.

[^12]: This ratio was validated across the CanonCanvas port and holds as a useful heuristic for future module ports.

[^13]: The Thread 2 auto-mute incident proved the need for unambiguous signal parsing. An agent misinterpreted 💾⚡️ as a hold signal (🔇) and went silent. The "own lines" requirement prevents this class of misinterpretation.

[^14]: The CanaryCheck → SobrietyCheck evolution is a good example of collaborative design. The user's instinct (test for degradation) was right. The proposed mechanism (planted canary tokens) was wrong. Honest pushback led to a better solution (behavioral self-assessment).

[^15]: The first DAR was historically significant — the analyst Claude that produced the v0.3 upgrade spec was itself suffering from context degradation by the end of the session. It performed a 🤮 DumpAndRun to capture the remaining context before the thread ended. "Ate alphabet soup, barfed a bestseller."

---

`]|[`
