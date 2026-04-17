---
description: Begin a True Hue personal color analysis with structured intake via AskUserQuestion
argument-hint: "[optional mode: audit, single-item, or refinement]"
allowed-tools:
  [
    "Read",
    "Glob",
    "Grep",
    "AskUserQuestion",
    "Skill"
  ]
---

# True Hue — Color Analysis Entry Point

Begin a True Hue personal color analysis session. This command is the **recommended entry point** because it authorizes the `AskUserQuestion` tool, which the skill needs for structured intake. The auto-generated `/true-hue:true-hue` trigger still works but falls back to plain-text questionnaires because it doesn't declare tool access — the experience here is materially better.

## What to do

1. **Read the skill.** Load `${CLAUDE_PLUGIN_ROOT}/skills/true-hue/SKILL.md` and follow its protocol starting from Phase 0. The skill's SKILL.md has the full workflow.

2. **Phase 0 via `AskUserQuestion`.** Use the tool — do NOT reproduce these options as plain-text bullets. Send one `AskUserQuestion` call with three questions:
   - "Have you been color-typed before?" — options: Never / Online quiz or app / Professional analyst / Prior True Hue session
   - "What's driving this conversation?" — options: First-time discovery / Verify a prior result / Evaluate items I own / Refine my palette
   - "How much time do you have?" — options: ~5 minutes / ~15 minutes / 30+ minutes / Flexible

3. **Route per SKILL.md's "Routing rules after user responds" section.** Never-typed first-time flows go to Mode 1 full analysis. Prior-typed users route to Mode 2/3/4 based on goal.

4. **Continue through the phases in SKILL.md.** Phase 1 (intake), Phase 2 (quality gate), Phase 3 (dimension analysis), Phase 3.5 (mandatory check-in), Phase 4 (draping + season determination), Phase 5 (deliverable), Phase 6 (optional PDF), Phase 7 (walkthrough).

5. **Use `AskUserQuestion` throughout where SKILL.md flags it** — the enumerable Phase 1 questionnaire items batched into 3 calls, and the Phase 3.5 check-in questions. Free-text items (hair description, compliment colors, foundation history, eye description, heritage, dye history, narrative context) remain conversational.

## Arguments

If `$ARGUMENTS` contains a mode hint (e.g., `audit`, `single-item`, `refinement`, or `mode 2/3/4`), skip the full Phase 0 exchange and route directly to the indicated mode, confirming the user's season first if relevant.

Otherwise run the full Phase 0 routing questions.
