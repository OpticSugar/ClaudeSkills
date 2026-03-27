# The Memory Problem Nobody Talks About

**A review of 🪢 MemoryMomentum, an open-source memory system for AI assistants**

If you've ever had a long conversation with an AI assistant — the kind where you've spent an hour explaining your project, making decisions, building something together — you've probably hit the wall. The assistant suddenly gets confused. It forgets what you told it twenty minutes ago. Or worse, you come back the next day and it has no idea who you are or what you were working on.

This is the context window problem, and it's the dirty secret of every AI platform. These models have a finite amount of "working memory." When it fills up, things start falling off the edges. Start a new conversation and you're back to zero.

Most people just live with it. They re-explain things. They paste old conversations into new ones. They keep notes in a separate document and hope for the best.

Stu Chudy decided to actually fix it.

## What 🪢 MemoryMomentum Does

🪢 MemoryMomentum is a skill — essentially a set of instructions that teaches an AI assistant how to manage its own memory. Instead of letting important context evaporate when a conversation ends, the assistant writes structured documents called 🪢 MeMo files to a persistent file system called The Shelf. Think of it as the assistant keeping its own organized notes, so that a future version of itself can pick up exactly where it left off.

The system uses a four-tier hierarchy. A 🧠 ProjectBrain holds everything about the project — decisions, constraints, creative direction. A 📓 SessionJournal tracks what happened in each conversation, including a 🏃‍♂️ MomentumNote — the "torch-pass" that tells the next session what to do first. 💡 PlanPasses capture iterative exploration rounds — the thinking-before-the-building phase, like iterating on blueprints before cutting wood. And 📼 WorkPieces are individual deliverable files — like labeled VHS tapes on a shelf. Need to work on shot 400? Pull that tape, pop it in, work on it, put it back. When the shot is done, the tape goes back on the shelf — it's never thrown away, because the client might have revisions.

What makes this more than just "save your notes" is the lifecycle management. The system has named rituals for different situations. 🍻 Toast is a mid-conversation checkpoint — tidy the bar, keep drinking. 🍺 LastCall is the evacuation protocol when the AI's memory is getting full — save the lifeboats before the context window sinks. 🎉 WrapParty is for when a deliverable is actually in the can — pop the champagne. Even the concept of starting fresh has a name: ⛲️ FountainOfYouth, a rebirth mindset where each new session isn't death, it's reincarnation with better notes.

## The Clever Parts

Several design decisions stand out as genuinely inventive.

**The 🌲 Knowledge Harvesting pipeline** treats every working session as a discovery opportunity. When the assistant notices something that might be useful beyond the current project — a technique that works, a pattern to avoid — it flags it with a 🌲 emoji right where it occurs and keeps working. No stopping, no evaluating, no friction. Later, during 🍺 LastCall, those discoveries get 🪓 harvested — evaluated, polished, and routed to 🪵 Upgrade files for the relevant skill. Eventually, the 🏗️ SkillMill (the development environment) installs validated learnings into the actual skill. It's a lumber supply chain: raw 🌲 trees get 🪓 harvested, cut into 🪵 lumber, and 🏗️ milled into finished furniture. Insights discovered during one project automatically feed improvements to the entire system. Especially critical discoveries get flagged 🎄 — the Christmas tree emoji, reserved for non-negotiable, load-bearing knowledge that would cost real time to rediscover if lost.

**The ⛲️ RebirthManifest** solves a problem that sounds trivial but isn't. When a new AI session picks up an existing project, it might find twelve files on The Shelf. Which ones matter? Which are outdated? The ⛲️ RebirthManifest is a bootstrap document — built automatically during 🍺 LastCall — that tells the incoming assistant exactly what to 📖 Read (in order), what to 🚫 Skip (with reasons), what its 🎯 Mission is, and what 🔬 Research is already done (so it doesn't waste time re-looking things up). It even includes an ⏱️ Estimated Context Budget so the assistant knows how much of its precious memory the catch-up reading will consume.

**🏷️ ShelfSort** brings order to the flat shelf with a beautifully simple convention: active files have no prefix, archived files get a `_` prefix, and deprecated files get `__`. On a shelf with no folders, this creates instant visual grouping — current files float to the top, old ones sink to the bottom. Combined with 🧹 ShelfSweep (a cleanup sub-ritual of 🍺 LastCall), the shelf stays organized rather than becoming a junk drawer.

**The 🩺 Context Health system** is where the bar metaphor really shines. The system tracks context degradation through an escalation ladder: 🪫 SobrietyCheck (still sharp — the empty glass means plenty of room), then 🔋 filling up (full green glass, about to overflow), then 🤢 Nausea (the assistant starts dropping queasy emojis as a passive warning that quality is degrading), then 🍺 LastCall (clean wrap-up while still coherent), and finally — if things go too far — 🤮 DumpAndRun.

**🤮 DumpAndRun** addresses a paradox that anyone who's worked long sessions with AI will recognize. The assistant responsible for carefully saving everything at the end of a session is often the *worst* version of itself — its memory is full, its coherence is degrading. Trusting it with careful organization at that point is like asking the drunk bartender to close out the register. 🤮 DumpAndRun splits the job: the tired assistant just brain-dumps everything raw into a 🤮 RawDump section. The fresh assistant that arrives next grabs a mop and cleans it up. The core principle: **capturing is cheap, curating is expensive.** Let the right agent do each job.

**💡 PlanPass** with its domain flavors (⛈️ BrainStorm for creative exploration, 🗺️ BluePrint for structural planning, 🧪 LabTest for experiments, 📊 Model for analytical work) recognizes that many projects have an exploration phase before individual deliverables get locked down. You don't start cutting wood before you've iterated on the plans. Each PlanPass version carries a 🎯 CreativeDirectives section — a rolling accumulation of all feedback and requirements from previous rounds, merged and deduplicated, preserving the user's voice and creative intent across iterations.

And when the system encounters a project type it wasn't designed for? Rather than forcing a bad fit, it flags the mismatch via 🧬 TemplateEvolution — letting new templates and workflows emerge organically from real usage rather than being pre-designed for hypothetical scenarios.

## What Makes It Different

There is, to my knowledge, no platform-level feature on any major AI service that does what 🪢 MemoryMomentum does. Most AI platforms offer basic memory — the assistant might remember your name or your preferences across conversations. But structured, multi-tier, project-scoped memory with lifecycle management, 🌲 knowledge harvesting, 🩺 context health monitoring, and ⛲️ RebirthManifests? That doesn't exist as a product feature anywhere.

What's remarkable is the origin story. This system wasn't designed in a research lab. It was built under deadline pressure by a creative director producing a broadcast docuseries with generative AI — 43 shots per episode, multiple AI models, creative sessions that routinely exceeded what any single conversation could hold. The first version — 📚 Memory Library System, branded under "Grey Matter Labs" — was built in May 2025. It evolved through 🧵 ThreadOS, then 🛜 CanonCanvas, then 🚗 The DeLorean Protocol (a Back to the Future analogy where the fork feature was the time machine and the memory document was the Sports Almanac), before finally unifying under its current name. Five generations of the same idea, each one shedding dead weight and keeping hard-won wisdom.

That production DNA shows. Every mechanism carries scars from actual use. 🤮 DumpAndRun was named during a session where the assistant was *itself* suffering from context degradation while inventing the concept — its creator described the result as having "ate alphabet soup, barfed a bestseller." The 🍾 NoteToSelf mechanism (personal letters from each session's AI to the next — "Hey younger me, the user will tell you Kling is fine for everything. It is not.") was born from watching critical warnings die between sessions. Nothing here is theoretical.

## Who It's For

🪢 MemoryMomentum is not for casual AI users. If your longest AI conversation is five messages, you don't need this. It's for people who use AI as a daily creative or professional tool — the kind of users who have named projects, multi-week timelines, and more context than any single conversation can hold.

It's available as an open-source Claude Skill on GitHub, which means anyone can install it and use it. The learning curve is real — there are concepts to internalize and 📡 signals to learn — but the documentation is thorough (including a massive 🧬 Genome document that captures every design decision and why it was made), and the system is designed to teach the assistant how to operate it, not to burden the user with manual bookkeeping.

For power users who have been losing work to the context window wall, it's worth the investment. And for anyone who's ever watched an AI forget an hour of collaboration and thought "there has to be a better way" — there is.

**🪢 MemoryMomentum v0.2 is available at [github.com/OpticSugar/ClaudeSkills](https://github.com/OpticSugar/ClaudeSkills)**
