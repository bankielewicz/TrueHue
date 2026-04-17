# True Hue v3 — Build Plan

**Status:** Proposed
**Scope:** Bug fixes from v2 + unfinished v1 commitments + fundamental gaps + QA infrastructure
**Target installation path:** `c:\projects\truehue\`
**Companion document:** `truehue-v3-spec.md` (AI-executable specification)

---

## Executive Summary

v3 addresses 22 concrete tasks across four tiers:

- **Tier 1 (6 tasks)** — Ship-blocker bugs introduced in v2 that actively degrade the skill's behavior or self-documentation
- **Tier 2 (8 tasks)** — Major content gaps in the deliverable, intake, and workflow phases
- **Tier 3 (5 tasks)** — Quality, accessibility, and robustness improvements
- **Tier 4 (3 tasks)** — Test infrastructure enabling regression testing and self-evaluation

After v3, the skill will: (a) produce output consistent with its own documentation, (b) cover the content areas a $300-$400 professional consultation covers, (c) handle solo photographers, color-blind users, and privacy-sensitive users, and (d) have bundled evals enabling future iteration without regression.

---

## Scope

### In scope for v3

All 22 tasks listed in the Task Inventory below. Each is concrete, executable without external data dependencies beyond what exists in v2, and contained within the skill's existing file structure or explicit additions to it.

### Out of scope — explicitly excluded

The following were considered and deliberately excluded:

1. **Specific brand or retailer recommendations** — Brand names and retailer quality go stale within months. Including them would introduce a maintenance burden and accuracy drift. v3 retains the few brand references that already exist (deep-skin foundation brands in the existing deliverable template) because those reference functional shade-range capability rather than trend-sensitive style. No new brand names added.

2. **Virtual try-on or image generation integrations** — Would require building a second skill or modifying the Visualizer. Not a palette quality improvement.

3. **Shopping API or e-commerce integrations** — Requires external data sources outside the skill's scope.

4. **Real-time cross-session memory** — Claude cannot persist context between sessions independently. Post-delivery validation (Task T2.8) works within a single session or relies on user-provided continuity.

5. **Professional referral system for in-person analysis** — Would require a maintained directory of certified analysts. Out of scope. Users are already directed to consider in-person analysis in the Known Limitations reference.

6. **Full internationalization / translation** — v3 remains English-only. Cultural inclusivity work in Tier 3 addresses description bias, not translation.

7. **Automatic PDF generation** — User already confirmed opt-in behavior. v3 adds invocation detail but keeps opt-in.

8. **Mode 4 full buildout if it turns out to be unnecessary** — Task T1.3 gives the option to either build Mode 4 properly or remove it from SKILL.md. Decision point documented within the task.

---

## Task Inventory

### Tier 1: Critical Bug Fixes

These tasks fix behaviors introduced in v2 that are actively broken or ship v2 in a state inconsistent with its own documentation. All Tier 1 tasks must be completed for v3 to be usable.

#### T1.1 — Rewrite `worked_example.md` to match v2 structure

**Problem:** The v1 worked example was carried forward unchanged into v2. It illustrates a deliverable that omits the Phase 3.5 check-in exchange, the Starter Capsule section, the conditional grooming sections, and the PDF offer. SKILL.md instructs Claude to "read the worked example before producing your first deliverable to calibrate tone and structure" — following this instruction currently causes Claude to produce v1-structured output instead of v2-structured output.

**Rationale:** Self-documentation integrity. The skill's calibration reference must match what the skill claims to produce.

**Acceptance criteria:**
- Example includes a full Phase 3.5 check-in exchange with sample user response and Claude's response to that response
- Example deliverable includes all mandatory sections (1, 2, 3, 4, 5, 6, 10, 11, 12)
- Example deliverable shows at least two conditional grooming sections (e.g., Eyewear + Watches) to demonstrate branching
- Example ends with the PDF offer and a sample user response (either yes or no, documented)
- Existing "Soft Autumn" narrative persona is preserved to maintain continuity

**Dependencies:** None. Can execute first.

---

#### T1.2 — Remove development marker in `self_check_worksheet.md`

**Problem:** The string `**NEW:** Grooming categories relevant to you` appears in the worksheet. "NEW:" is a development artifact that would ship looking unfinished.

**Rationale:** Professional polish. The user will see this worksheet directly.

**Acceptance criteria:**
- String `**NEW:** Grooming categories` does not appear anywhere in the file
- Checkbox item reads naturally without implying a version history
- No other "NEW:" or development markers exist anywhere in the skill

**Dependencies:** None.

---

#### T1.3 — Resolve Mode 4 (either build it or remove it)

**Problem:** SKILL.md declares four workflow modes. Modes 1 and 2 have templates. Mode 3 is described but treated as a subset of Mode 2. Mode 4 ("Palette Refinement") is described as "consultation-style conversation" with no template or detailed workflow. This leaves Claude without guidance for a declared mode.

**Rationale:** Either commit to all four modes with consistent depth, or don't declare them.

**Decision point:** Build `assets/palette_refinement_template.md` OR remove Mode 4 from SKILL.md.

**Recommendation:** Build it. Palette refinement is a genuinely useful mode for users already typed who want to understand their edge conditions. Removing it loses real capability.

**Acceptance criteria (if building):**
- New file `assets/palette_refinement_template.md` exists
- File contains: trigger phrases for Mode 4, input requirements (confirmed season + question to refine around), output structure covering adjacent-season borrowing, edge-case conditions, and at least one worked snippet
- SKILL.md Mode 4 description updated to reference this template

**Acceptance criteria (if removing):**
- Mode 4 removed from SKILL.md Workflow Modes section
- Remaining modes renumbered if needed for clarity

**Dependencies:** None.

---

#### T1.4 — Build `references/checkpoint_questions.md` for Phase 3.5

**Problem:** SKILL.md describes the Phase 3.5 check-in format but tells Claude to generate targeted questions ad hoc: "A question that tests the undertone reading." This produces inconsistent question quality across sessions and gives Claude no library to draw from.

**Rationale:** Consistency. Claude should have a vetted question library to pull from rather than improvising each time.

**Acceptance criteria:**
- New file `references/checkpoint_questions.md` exists
- Contains at least 5 vetted questions per dimension (Undertone, Value, Chroma, Contrast)
- Questions are specifically designed to surface disagreements, not confirmations — e.g., "do you feel more energized in bold saturated colors or softer muted ones" rather than "do you agree you're muted?"
- Includes guidance for when to pick which questions (e.g., undertone questions for deep-skin users focus on foundation behavior; for fair skin focus on jewelry and compliment patterns)
- SKILL.md Phase 3.5 section updated to reference this file

**Dependencies:** None.

---

#### T1.5 — Add season-naming convention disclaimer to `twelve_seasons.md`

**Problem:** The skill uses "Deep Autumn" and "Deep Winter" while other published systems use "Dark Autumn" and "Dark Winter" for the same sub-seasons. Users arriving with prior knowledge from a different system will see a naming mismatch without explanation.

**Rationale:** User trust. Acknowledging naming variation preempts confusion and signals the skill understands the ecosystem.

**Acceptance criteria:**
- `references/twelve_seasons.md` includes a clearly marked disclaimer section near the top
- Disclaimer lists known naming variants: Deep = Dark, True = Warm (for Spring/Autumn), True = Cool (for Summer/Winter), the "soft summer dumping ground" phenomenon from industry commentary
- Disclaimer notes the skill standardizes on Deep/True naming but recognizes Dark/Warm/Cool variants as equivalent
- `palette_library.md` updated to reference the same naming convention consistently

**Dependencies:** None.

---

#### T1.6 — Detail PDF skill invocation in `SKILL.md` and `swatch_card_layout.md`

**Problem:** SKILL.md says "invoke the pdf skill" without telling Claude to read the PDF skill's SKILL.md first, without showing invocation syntax, and without handling the case where the PDF skill is not available in the user's environment.

**Rationale:** Instruction completeness. Claude should not have to guess at sibling-skill interfaces.

**Acceptance criteria:**
- SKILL.md Phase 6 explicitly instructs Claude to read `/mnt/skills/public/pdf/SKILL.md` (and equivalent path translations) before first invocation
- `assets/swatch_card_layout.md` shows an example invocation pattern consistent with how Anthropic skills are typically chained
- Fallback documented: if PDF skill unavailable, Claude produces a hex-code-list deliverable the user can convert externally, and states this limitation
- PNG wallpaper fallback routing to frontend-design skill is similarly specified

**Dependencies:** None.

---

### Tier 2: Major Content Gaps

These tasks address content areas that a professional color analysis covers but this skill currently doesn't, or covers inadequately.

#### T2.1 — Add Pattern and Print guidance to deliverable template

**Problem:** Deliverable covers solid colors comprehensively, says nothing about patterns. Professional analysts distinguish: low-contrast users should favor smaller/subtler patterns; high-contrast users can carry bold patterns; muted users need subdued palettes within patterns; bright users can wear clear palettes within patterns.

**Rationale:** Real professional content gap.

**Acceptance criteria:**
- New conditional section in `assets/deliverable_template.md` covering pattern scale appropriate to user's contrast level
- Covers at minimum: scale (small/medium/large), density (sparse/dense), color-count recommendations, which prints to avoid entirely
- Links the guidance to the user's specific Contrast and Chroma readings from Phase 3

**Dependencies:** None.

---

#### T2.2 — Add Color Pairing Rules section to deliverable template

**Problem:** Deliverable gives 36 hex codes but no guidance on which pairings harmonize vs. clash within the palette. "Which of my palette colors go together" is a core wardrobe-building question.

**Rationale:** The palette is raw material; pairing rules are how the user converts material into outfits.

**Acceptance criteria:**
- New section in `assets/deliverable_template.md` covering within-palette pairing
- Addresses: neutrals + mids (safe foundations), neutrals + statement (high-impact outfits), mids + accents (balanced energy), which pairings to avoid (value clashes, chroma clashes within the same palette)
- Provides at least 5 specific example pairings using hex codes from whatever palette the user has
- Addresses the specific case of mixing across face-framing and non-face-framing zones

**Dependencies:** T2.1 is helpful context but not required.

---

#### T2.3 — Add Fabric Texture/Sheen guidance to deliverable template

**Problem:** Muted-chroma seasons often look better in matte and textured fabrics; bright-chroma seasons can handle shine and satin; certain undertones are flattered by specific fiber types. Not mentioned anywhere.

**Rationale:** Content gap. Fabric choice is part of how color reads in real life.

**Acceptance criteria:**
- New section in `assets/deliverable_template.md` covering fabric texture, sheen, and fiber guidance
- Addresses: matte vs. shiny recommendation tied to Chroma reading, fabric weight tied to Value reading, fiber-type harmony (e.g., silk and wool often work universally; polyester shine can clash with muted seasons)
- Includes guidance for both warm and cool climate wardrobes

**Dependencies:** None.

---

#### T2.4 — Add Body Coloring Beyond Face to intake and analysis

**Problem:** The analysis reads face only. Décolletage, inner arm, and the contrast between sun-exposed and non-exposed skin give additional undertone signal and catch cases where the face has been altered by sun damage, rosacea, or makeup residue.

**Rationale:** Professional analysts read multiple body areas. Face-only analysis misses signal.

**Acceptance criteria:**
- `assets/intake_template.md` adds an optional sixth photo: inner forearm (less sun-exposed area) on white paper
- Questionnaire adds a question about skin-color variation between exposed and unexposed areas
- SKILL.md Phase 3 Dimension 1 (Undertone) references the inner arm photo as a cross-check when submitted
- `references/undertone_cross_checks.md` extended with guidance on reading inner arm vs. face discrepancy

**Dependencies:** None.

---

#### T2.5 — Add Lifestyle/Profession/Climate questions to intake

**Problem:** Intake asks "what's driving the analysis" but doesn't capture the context that affects palette emphasis: profession (corporate vs. creative), climate (which temperature range of the palette to emphasize), formality mix (80% casual vs. 80% formal).

**Rationale:** Same season, different lifestyle contexts lead to meaningfully different palette emphasis in the deliverable.

**Acceptance criteria:**
- `assets/intake_template.md` adds three questions to the questionnaire: profession/work environment, climate/geography, formal-to-casual ratio
- `assets/deliverable_template.md` Starter Capsule section updated to incorporate these answers (e.g., climate affects fiber recommendations; profession affects which palette roles are most emphasized)

**Dependencies:** None.

---

#### T2.6 — Add Consultation Prep phase (Phase 0) to SKILL.md

**Problem:** User jumps straight into the heavy intake protocol. No brief exchange to establish context first. A 2-3 turn exchange before intake would catch cases where the user already has a season and wants Mode 2/3/4 rather than Mode 1, and would establish the relationship before asking for significant effort.

**Rationale:** Saves wasted effort when Mode 1 isn't what the user actually wants.

**Acceptance criteria:**
- SKILL.md new "Phase 0: Consultation Prep" section inserted before Phase 1
- Specifies at least 3 questions Claude asks first: have you been typed before, what's driving the analysis, which mode fits
- Specifies how Phase 0 outcomes route to Modes 1-4
- Subsequent phases renumbered where it improves clarity; or kept at their current numbers if the addition is designated as Phase 0 (zero)

**Dependencies:** None. Impacts SKILL.md structure.

---

#### T2.7 — Add Delivery Walkthrough phase (Phase 7) to SKILL.md

**Problem:** Deliverable is produced as a wall of text. Professional consultations end with structured Q&A: "let's walk through this section by section." Claude currently drops the deliverable and stops.

**Rationale:** Users retain and apply information better when it's walked through. Also catches clarification needs.

**Acceptance criteria:**
- SKILL.md new "Phase 7: Delivery Walkthrough" section after Phase 6
- Specifies Claude's closing move: offer to walk through any section, compare two sections, or do deeper dives into specific categories
- Distinguishes walkthrough from Mode 2/3/4 follow-ups — walkthrough is about explaining what was delivered; Modes are about new tasks
- Includes sample closing message template

**Dependencies:** None.

---

#### T2.8 — Build Post-Delivery Validation workflow

**Problem:** If user returns to a follow-up session with "I tried the palette and X happened," there's no structured workflow. Falls to ad-hoc conversation.

**Rationale:** Real professional consultations include a feedback loop. This is what "validation" means beyond the initial analysis.

**Acceptance criteria:**
- New file `assets/validation_followup_template.md` exists
- Covers trigger phrases ("the palette isn't working," "I got compliments on X but not Y")
- Structures the feedback collection: which colors worked, which didn't, in what context
- Specifies decision tree: (a) adjust palette emphasis within current season, (b) reconsider season assignment, (c) recommend in-person consultation if patterns suggest misdiagnosis
- SKILL.md Phase 7 section references this template as a follow-up option

**Dependencies:** T2.7 is required (walkthrough phase must exist before follow-up branches off it).

---

### Tier 3: Quality and Robustness

Accessibility, practical obstacles, and cultural bias corrections.

#### T3.1 — Add Two-Handed Photo Solutions to intake template

**Problem:** Holding a sheet of white paper at the cheek while taking a selfie requires two hands plus a camera. Solo users literally cannot execute the protocol as written.

**Rationale:** Practical obstacle affecting a large share of solo users.

**Acceptance criteria:**
- `assets/intake_template.md` adds a "Solo photographer solutions" subsection
- Specifies at least 4 concrete solutions: tape paper to mirror and use rear camera, prop paper against lamp or book, use camera timer + tripod/phone stand, ask family member or friend to help
- Addresses phone mounting options explicitly (common household objects that work)

**Dependencies:** None.

---

#### T3.2 — Build Second-Opinion / Between-Seasons protocol

**Problem:** Some cases are legitimately ambiguous between two seasons. v2 mentions this generally but has no structured output for "this could defensibly be either Soft Summer or Soft Autumn — here are both palettes and a testing protocol."

**Rationale:** Forcing a false binary when the answer is "both are defensible" produces worse guidance than acknowledging ambiguity.

**Acceptance criteria:**
- New file `references/between_seasons_protocol.md` exists
- Covers: criteria for triggering the protocol (when dimensions genuinely straddle two seasons), structured output format showing both candidate seasons side-by-side, testing protocol (specific outfits or colors to try to disambiguate), decision rule for when to tell the user to pursue in-person analysis
- SKILL.md Phase 4 section updated to reference this protocol as an alternative to forcing a single season

**Dependencies:** None.

---

#### T3.3 — Add Color-Blind Accessibility provisions

**Problem:** A color-blind user cannot necessarily read hex swatches in the deliverable. No provision for alternative description formats.

**Rationale:** Accessibility. Color analysis is particularly valuable to color-blind users (who often rely on others to help with clothing selection) but the deliverable format excludes them.

**Acceptance criteria:**
- `assets/intake_template.md` adds an optional question about color vision (standard type of colorblindness, if any)
- `assets/deliverable_template.md` adds instructions for color-blind-mode output: describes colors using standardized names plus undertone + value + saturation descriptors alongside hex codes, groups palette by brightness tier rather than hue, flags hex pairs that appear similar to color-blind viewers
- Color-blind mode is opt-in based on the intake question answer

**Dependencies:** None.

---

#### T3.4 — Add Privacy Guidance to intake

**Problem:** Users submit face photos. No mention of image retention, deletion, or hygiene practices.

**Rationale:** User trust and informed consent.

**Acceptance criteria:**
- `assets/intake_template.md` adds a "Privacy notes" section before photo submission
- Covers: Claude session photos are ephemeral within the chat and not used for training (factually accurate for the platform), recommendation to delete chat after analysis if desired, option to crop or edit photos to minimize identifying features beyond what's needed for analysis
- Factual accuracy: only claim what's accurate about Anthropic's products; does not make claims about developer-built applications using the Claude API

**Dependencies:** None.

---

#### T3.5 — Rewrite cultural descriptions in `twelve_seasons.md`

**Problem:** "Typical coloring" descriptions lean heavily on Northern European features ("golden blonde hair," "blue eyes," "porcelain skin"). This excludes the reality that Deep Winter or Soft Autumn users present differently across ethnic backgrounds.

**Rationale:** Accuracy and inclusivity. The season classifications apply across all heritages; the descriptions shouldn't suggest otherwise.

**Acceptance criteria:**
- Every season's "typical coloring" description in `references/twelve_seasons.md` includes at least two phenotypic examples from different heritage clusters
- Descriptions emphasize what makes someone fit the season (the four dimensions) rather than specific racial features
- No season's description implies a particular ethnic/racial default

**Dependencies:** None.

---

### Tier 4: QA and Testing Infrastructure

Enables regression testing, self-evaluation, and future iteration without breakage.

#### T4.1 — Build `evals/evals.json` with test cases

**Problem:** No test cases bundled. Future modifications have no regression safety net.

**Rationale:** The skill-creator framework supports evals. Not using it leaves v3 as fragile as v1 and v2 were.

**Acceptance criteria:**
- New directory `evals/` exists containing `evals.json`
- At least 5 test cases covering: full Mode 1 analysis with clean inputs, Mode 1 with degraded inputs requiring re-shoot, Mode 2 closet audit, Mode 4 palette refinement (if Mode 4 retained), edge case (between-seasons)
- Each test case has: trigger prompt, expected output structure checks, expected behavior (e.g., "should ask for re-shoot," "should run Phase 3.5 check-in")
- Schema conforms to skill-creator's evals.json format

**Dependencies:** T1.3 (Mode 4 decision must be made first).

---

#### T4.2 — Build self-evaluation rubric

**Problem:** SKILL.md has a self-check list but no scoring rubric. Claude can check "was this section included" but not "was it included at appropriate quality."

**Rationale:** Quality at scale. Self-evaluation improves consistency.

**Acceptance criteria:**
- New file `references/self_evaluation_rubric.md` exists
- Covers: per-section quality criteria (e.g., evidence cited for undertone reading, hex codes rather than color names, at least 8-12 avoid colors with reasoning), composite quality indicators, explicit "red flags" that indicate deliverable should be reworked
- SKILL.md final self-check section updated to reference this rubric

**Dependencies:** None.

---

#### T4.3 — Build sample intake submissions

**Problem:** Claude has no reference for what a "textbook clean" intake looks like vs. a "barely passable" one.

**Rationale:** Calibration. Having reference points makes quality-gate decisions more consistent.

**Acceptance criteria:**
- New file `references/sample_intakes.md` exists
- Contains at least 3 described intakes: one textbook clean, one with one fixable flaw, one with multiple flaws requiring rejection
- Each described intake covers: photo descriptions (textual only, not actual images), questionnaire answers, expected Claude quality-gate decision
- Includes one example of a deep-skin intake where vein test is appropriately skipped

**Dependencies:** None.

---

## Recommended Execution Order

Tier order is the recommended execution sequence. Within each tier, tasks can run in parallel except where Dependencies are noted. Suggested sequence:

1. **Phase A (Tier 1, parallel-safe):** T1.1, T1.2, T1.4, T1.5, T1.6 run in parallel or any order. T1.3 runs last in Tier 1 since its outcome (build vs. remove Mode 4) affects T4.1.

2. **Phase B (Tier 2, mostly parallel):** T2.1, T2.2, T2.3, T2.4, T2.5 run in parallel (all are additions to existing templates). T2.6 and T2.7 touch SKILL.md structure — run sequentially or in close coordination. T2.8 depends on T2.7.

3. **Phase C (Tier 3, all parallel):** T3.1, T3.2, T3.3, T3.4, T3.5 are independent. No dependencies among them.

4. **Phase D (Tier 4, sequential-ish):** T4.1 depends on T1.3 being complete. T4.2 depends on all content tasks being complete (since rubric evaluates against final content). T4.3 can run independently.

5. **Phase E (Integration):** Cross-reference audit, description-length check, repackage, install at `c:\projects\truehue\`.

---

## Dependencies Map

```
T1.3 (Mode 4 decision) ──> T4.1 (evals)
T2.7 (Walkthrough phase) ──> T2.8 (Validation followup)
All content tasks ──> T4.2 (Self-eval rubric)
All tasks ──> Phase E (Integration)
```

No circular dependencies. No task depends on external data sources.

---

## Acceptance Criteria Summary

v3 is complete when:

1. All 22 tasks meet their individual acceptance criteria
2. SKILL.md `description:` field stays under 1024 characters
3. `quick_validate.py` passes without errors
4. Every cross-reference in SKILL.md and asset/reference files resolves to an existing file
5. No development markers (NEW:, TODO:, FIXME:, etc.) appear in shipped content
6. Season naming is consistent across all files (Deep + True standardized, with Dark/Warm/Cool acknowledged as variants)
7. Packaged `.skill` file builds without errors
8. The bundled `evals/evals.json` runs through skill-creator's evaluation framework without schema errors

---

## Completion Definition

v3 is "done" when a fresh installation of the skill at `c:\projects\truehue\`:

- Honors user's grooming category selections (no padding, no omitting)
- Runs Phase 0 consultation prep before any heavy intake
- Runs Phase 3.5 check-in with varied, evidence-seeking questions drawn from the library
- Produces deliverables consistent with the updated worked example
- Offers Phase 7 walkthrough after delivery
- Handles color-blind users in opt-in alternative format
- Honors privacy-related user requests documented in intake
- Has test cases that pass against the current implementation
- Has a self-evaluation rubric Claude applies before sending deliverables

---

## Notes for Execution

- The companion `truehue-v3-spec.md` is the AI-executable specification. Hand that to Claude (not this plan) when asking for implementation.
- This plan is the approval document — it's what humans review and authorize. The spec is what executes.
- Any deviation from the plan during execution (e.g., discovering a task is larger or smaller than estimated) should be surfaced back to the human before committing.
- If the execution environment differs from Windows (`c:\projects\truehue\`), all file paths translate unchanged — the skill files use forward slashes natively.

---

*End of Plan*
