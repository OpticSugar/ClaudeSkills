# 🔄 Weavy Bake-Off Sync Protocol

## Purpose

The VideoPrompting skill's enhancer reference files and the actual Weavy bake-off
workflow node instructions must stay in lockstep. This protocol ensures they don't
drift apart silently.

---

## Version String Format

Each enhancer preset gets a version string:

```
VP-[CAMP]-v[MAJOR].[MINOR]
```

Examples:
- `VP-C1-v1.0` — VideoPrompting, Camp 1, version 1.0
- `VP-C3-v1.2` — VideoPrompting, Camp 3, version 1.2
- `VP-NEG-v1.0` — VideoPrompting, Negative Prompt Enhancer, version 1.0

### Version Bumps

- **MINOR** bump (v1.0 → v1.1): Tuning, tightening, small fixes that don't change
  fundamental behavior. Example: adjusting character cap, adding a specific edge case.
- **MAJOR** bump (v1.x → v2.0): Structural changes, new instructions, behavior shifts.
  Example: adding 🔒 Priority Sentry support, restructuring image handling rules.

---

## Where the Version String Lives

Each version string must appear in THREE places:

1. **Skill reference file** — in the file header and changelog
   (`references/enhancer-camp[N]-*.md`)
2. **Weavy node instructions** — as the first comment line inside the instruction
   text block: `// VP-C1-v1.0`
3. **Weavy workflow sticky note** — in the master sticky note at the top of the
   bake-off workflow

### Weavy Sticky Note Standard

The bake-off workflow's master sticky note should contain:

```
📹 VideoPrompting Bake-Off Workflow
Version: [date YYYY-MM-DD]
Skill sync: VP v[X.Y]

Camp Enhancer Versions:
  C1 (Minimalists):  VP-C1-v1.0
  C2 (Planners):     VP-C2-v1.0
  C3 (Puppeteers):   VP-C3-v1.0
  C4 (Goblins):      VP-C4-v1.0
  NEG:               VP-NEG-v1.0

Last synced by: [Claude / Stu]
```

---

## Sync Workflow

### When Claude updates a skill enhancer file:

1. Make the change in the skill reference file
2. Bump the version in the file header and changelog
3. Tell Stu: "Enhancer [camp] updated to [version]. Paste the new instructions
   into the Weavy node and update the sticky note."
4. The sync is NOT complete until Stu confirms the Weavy node is updated.

### When field testing reveals an enhancer needs tuning:

1. Diagnose the drift (load the enhancer file, compare against output)
2. Propose the fix
3. If confirmed, update the skill reference file AND tell Stu to update the Weavy node
4. Bump the version in both places

### When Stu updates a Weavy node directly:

1. Tell Claude what changed and why
2. Claude updates the skill reference file to match
3. Version bump in both places

### Detecting Drift

If Claude suspects the Weavy workflow and skill files are out of sync:
- Ask Stu to read the version strings from the Weavy sticky note
- Compare against the skill reference file versions
- Any mismatch = update needed

---

## Current Versions

| Preset | Skill File Version | Weavy Node Version | In Sync? |
|--------|-------------------|-------------------|----------|
| Camp 1 🎯 | VP-C1-v1.0 | TBD (not yet installed) | ⏳ |
| Camp 2 📋 | VP-C2-v1.0 | TBD (not yet installed) | ⏳ |
| Camp 3 🎭 | VP-C3-v1.0 | TBD (not yet installed) | ⏳ |
| Camp 4 🎪 | VP-C4-v1.0 | TBD (not yet installed) | ⏳ |
| Negative | VP-NEG-v1.0 | TBD (not yet installed) | ⏳ |
