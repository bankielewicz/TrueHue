# True Hue v3 — Technical Specification

**Companion to:** `truehue-v3-plan.md`
**Purpose:** AI-executable build specification. Hand this document to Claude to execute.
**Target:** Skill directory root located at `c:\projects\truehue\` (Windows) or equivalent on other systems. All file paths in this spec use forward slashes and are relative to the skill root.

---

## Preamble — How to use this spec

This document specifies 22 tasks that transform the current skill (v2) into v3. Each task is self-contained. Each task specifies: files to create or modify, exact content requirements, verification steps, and cross-reference updates that other files need as a consequence.

**Rules of execution:**

1. Do not ask the user clarifying questions during execution. All ambiguity is resolved in the spec. If something is genuinely ambiguous, default to the more conservative option (less change) and flag it in the final report.

2. Before executing any task, read the current state of the file(s) it touches. Do not assume prior context.

3. After each task, run the validation steps specified for that task.

4. Do not deviate from the task order unless a Dependencies block explicitly allows it.

5. When modifying existing files, preserve all unrelated content. Do not rewrite files unless the task specifies a full rewrite.

6. Track completion status task-by-task. Do not claim a task is complete until its acceptance criteria pass its validation.

7. If a task requires synthesizing content that is not fully specified here, stay within the constraints given (required sections, required topics, minimum element counts) and draw on the existing skill's tone and structure as calibration.

8. No aspirational content. If a task does not specify something, do not add it. Do not speculate about future versions.

---

## Execution environment assumptions

- Skill root directory exists with v2 contents at the working directory root (e.g., `c:\projects\truehue\`)
- `SKILL.md` at root, `assets/` and `references/` subdirectories populated with v2 files
- Standard markdown authoring; no binary content expected to be authored by Claude
- Claude has file read/write tools (view, create_file, str_replace) available
- `skill-creator` validation script is available at `/mnt/skills/examples/skill-creator/scripts/` (Claude.ai environment) or accessible via configured path
- Final packaging uses `package_skill.py` from skill-creator

---

## File system layout after v3 completion

```
truehue/
├── SKILL.md                                    [MODIFIED]
├── assets/
│   ├── intake_template.md                      [MODIFIED]
│   ├── self_check_worksheet.md                 [MODIFIED]
│   ├── rejection_template.md                   [unchanged]
│   ├── deliverable_template.md                 [MODIFIED]
│   ├── closet_audit_template.md                [unchanged]
│   ├── swatch_card_layout.md                   [MODIFIED]
│   ├── palette_refinement_template.md          [NEW — if T1.3 = build]
│   └── validation_followup_template.md         [NEW]
├── references/
│   ├── twelve_seasons.md                       [MODIFIED]
│   ├── palette_library.md                      [MODIFIED]
│   ├── undertone_cross_checks.md               [MODIFIED]
│   ├── good_photo_examples.md                  [unchanged]
│   ├── worked_example.md                       [FULL REWRITE]
│   ├── known_limitations.md                    [unchanged]
│   ├── checkpoint_questions.md                 [NEW]
│   ├── between_seasons_protocol.md             [NEW]
│   ├── self_evaluation_rubric.md               [NEW]
│   └── sample_intakes.md                       [NEW]
└── evals/
    └── evals.json                              [NEW]
```

Net change: 7 modifications, 7 new files (8 if Mode 4 = build), 1 new directory.

---

## Task specifications

---

### T1.1 — Rewrite `references/worked_example.md` to match v2 structure

**Action:** Full rewrite.

**Inputs to read before starting:**
- Current `references/worked_example.md` (to preserve narrative persona)
- Current `SKILL.md` (for v2 phase structure)
- Current `assets/deliverable_template.md` (for required sections)

**Required content:**

Reproduce the following narrative structure. Where content is synthesized, follow the constraints listed.

1. **Scenario section** (same as current):
   - Preserve the "Soft Autumn" Irish/German heritage, dark blonde hair, hazel eyes persona
   - Preserve existing questionnaire answers
   - ADD: grooming categories selection — user selects `Eyewear`, `Watches and other accessories`, `Hair color`, `Jewelry`. User explicitly does NOT select `Full makeup`, `Skincare and tinted products`, `Facial hair`, `Ties and pocket squares`. This demonstrates the conditional sections branching.

2. **Phase 2 Quality gate section:** unchanged from current (PASSED status).

3. **Phase 3 Dimension analysis section:** unchanged from current (four dimensions cited with evidence).

4. **Phase 3.5 Check-in section — NEW:** This is the core addition.
   - Format: Claude presents the four dimensions with evidence, asks exactly 2 targeted questions drawn from the library that `checkpoint_questions.md` will contain (see T1.4)
   - Sample user response included: user confirms undertone and value readings, questions the chroma reading ("I actually look great in bolder colors sometimes — is muted really right?")
   - Sample Claude response: addresses the pushback with evidence-based reasoning, asks one follow-up to distinguish preference-based vs. evidence-based pushback
   - Sample user follow-up: provides new evidence (the bold colors that worked were all in rich muted ranges, not high-chroma brights) → Claude confirms muted chroma reading stands
   - Ends with user approval to proceed

5. **Phase 4 Draping comparison section:** preserved from current (why not Soft Summer, why not Warm Autumn).

6. **Phase 5 Deliverable section — MODIFIED:**
   - Sections 1–6: preserved from current Soft Autumn example
   - ADD Section 7c: Eyewear Frame Colors — specific guidance for Soft Autumn eyewear, metal frame colors, acetate recommendations, tortoiseshell direction, clear frames assessment, sunglass tint recommendations
   - ADD Section 7e: Watches and Accessories — watch case metal, face color, leather band colors, bag recommendations
   - ADD Section 8: Hair Color Guidance — already present in current example, keep it
   - DO NOT ADD Sections 7a, 7b, 7d, 9 — the user did not select those categories
   - Section 10 Face-framing rules: preserved
   - ADD Section 11: Starter Capsule — both budget tier (~$500) and investment tier ($1500-$3000+) for the Soft Autumn persona, plus a 6-month phasing suggestion
   - Section 12 Confidence and Caveats: preserved

7. **Phase 6 PDF offer — NEW:**
   - Claude offers three PDF format options at the end
   - Sample user response: selects "wallet card + phone wallpaper"
   - Claude acknowledges and indicates PDF generation in progress (does not need to show actual PDF content)

8. **"What makes this output good" section at the end:** update to reference the new structure. Emphasize: Phase 3.5 check-in caught a potential misreading; conditional grooming sections match user's selections; starter capsule connects palette to concrete purchases.

**Constraints:**
- Total length of the rewritten file may exceed current length due to added sections — expected
- Preserve all specific hex codes from the current Soft Autumn example where reused
- Do not add brand names
- Do not add references to tasks or v3 or version numbers inside the example

**Cross-reference updates required:**
- None — SKILL.md already references `references/worked_example.md` correctly.

**Validation:**
- After writing, search the file for any of these strings: `NEW:`, `TODO`, `v1`, `v2`, `v3`. None should appear.
- Verify all four mandatory Phase 3.5 elements present (Claude presents dimensions, Claude asks 2 questions, user pushes back or confirms, Claude handles response).
- Verify all conditional sections correctly present (7c, 7e, 8) or absent (7a, 7b, 7d, 9).
- Verify Section 11 Starter Capsule includes both tiers.

---

### T1.2 — Remove development marker in `assets/self_check_worksheet.md`

**Action:** Targeted string replacement.

**Exact change:**

Find this line (one occurrence):
```
- [ ] **NEW:** Grooming categories relevant to you (see intake template)
```

Replace with:
```
- [ ] Grooming categories relevant to you selected in the questionnaire (see intake template, item 14)
```

**Validation:**
- `grep "NEW:" assets/self_check_worksheet.md` returns no matches.
- The line still appears in the Questionnaire section of the checklist (not moved to another location).

---

### T1.3 — Build `assets/palette_refinement_template.md` (Mode 4)

**Decision:** BUILD Mode 4. Recommended in plan.

**Action:** Create new file.

**Required sections in `assets/palette_refinement_template.md`:**

1. **When to use Mode 4** — trigger phrases:
   - "I'm already a [season], but I want to understand what I can borrow from [adjacent season]"
   - "Can I wear [specific color outside my palette]?"
   - "How far can I push my palette before things go wrong?"
   - "I keep seeing [season name] colors I love — am I actually that season or can I borrow?"

2. **Input requirements:**
   - Confirmed primary season (how confirmed: professional analysis, prior use of this skill, self-identification — with confidence level)
   - Specific question or area the user wants to refine (adjacent-season borrowing, specific color question, occasion-specific palette expansion)
   - Optionally: context for why (new job, climate change, aesthetic evolution)

3. **Output structure — Adjacent Season Borrowing mode:**
   - Identify the two adjacent seasons on the flow chart
   - For each adjacent season, list 5-10 specific colors (hex codes) that are borrowable at what intensity
   - Specify conditions: when to wear (face-framing vs. distance), pairing rules (pair with primary-season neutrals), how far the user can push intensity before the borrow fails
   - Note which colors from the adjacent season are NOT borrowable even at low intensity

4. **Output structure — Specific Color Check mode:**
   - User presents a specific color (hex, photo, or description)
   - Claude identifies closest match in the user's palette
   - Evaluates: on-palette, borrowable, off-palette
   - If borrowable, specifies conditions (lighting, proximity to face, pairing)
   - If off-palette, explains what specifically fails

5. **Output structure — Palette Expansion for Occasions mode:**
   - User describes an occasion (formal event, tropical vacation, professional context shift)
   - Claude identifies palette roles emphasized for that context
   - Recommends which primary-season colors to emphasize
   - Recommends any borrowed colors from adjacent seasons specifically useful for the context
   - Notes which palette colors to deprioritize for the context

6. **Edge case handling — user-stated season was wrong:**
   - During Mode 4, Claude may detect signs the user's stated season doesn't actually fit their coloring (e.g., borrowing requests consistently push in a direction suggesting a different primary season)
   - Specify: Claude surfaces this observation gently, asks clarifying questions, offers to run Mode 1 (full re-analysis) if evidence accumulates
   - Do not force Mode 1; user decides

7. **One worked snippet:**
   - Scenario: User is a Soft Autumn asking "can I wear the deep burgundy that's trending?"
   - Show Claude's evaluation: the specific hex of the trending burgundy, how it compares to Soft Autumn's palette, which season it actually belongs to (likely Deep Autumn or Cool Winter depending on exact hue), whether it's borrowable at distance, pairing recommendations if borrowable

**Constraints:**
- Do not include full 36-color palettes — refinement is surgical, not comprehensive re-analysis
- Do not re-run Phase 3.5 check-in in Mode 4 — the user's season is given, not being determined
- Do not produce starter capsule in Mode 4

**Cross-reference updates required:**
- `SKILL.md` Workflow Modes section: update Mode 4 description to reference this file. Current text `This is a consultation-style conversation, not a template-driven analysis` should be replaced with `Uses \`assets/palette_refinement_template.md\` for structure.`

**Validation:**
- File exists at `assets/palette_refinement_template.md`
- Contains all 7 required sections
- `grep -n "palette_refinement_template" SKILL.md` returns at least one match in the Mode 4 description

---

### T1.4 — Build `references/checkpoint_questions.md`

**Action:** Create new file.

**Required content structure:**

1. **Preamble** (2-3 paragraphs):
   - Explain Phase 3.5's purpose: catch reading errors cheaply before producing a full deliverable
   - Explain question selection principle: pick questions that would surface a disagreement, not confirm agreement
   - Explain when to use dimension-specific questions vs. general cross-check questions

2. **Undertone questions — minimum 5:**
   Each question includes the question text, what dimension it tests, what kind of answer suggests the current reading is wrong, and when to use it (e.g., "fair-to-medium skin only," "especially useful for deep skin," "useful for olive complexions").
   
   Required coverage across the 5+ questions:
   - At least one jewelry-based
   - At least one compliment-pattern-based
   - At least one foundation-behavior-based (especially useful for deep skin)
   - At least one fabric-draping-based (white vs. cream)
   - At least one "what color do you feel invisible in" question

3. **Value questions — minimum 5:**
   Required coverage:
   - At least one about comfort with very light colors
   - At least one about comfort with very dark colors
   - At least one contrast-between-features question
   - At least one about how the user reads in "in-between" value colors (mid-tones)
   - At least one about natural hair value at its deepest/lightest point in life

4. **Chroma questions — minimum 5:**
   Required coverage:
   - At least one "muted vs. vivid" comfort question
   - At least one about how the user feels in jewel tones vs. dusty tones
   - At least one about whether decisive color decisions feel good or overwhelming
   - At least one about recent compliments: were the colors clear or complex
   - At least one about what the user avoids in their own wardrobe (often signals chroma preference)

5. **Contrast questions — minimum 5:**
   Required coverage:
   - At least one about comfort with high-contrast outfits (black + white, for example)
   - At least one about how natural features relate (hair-skin-eyes contrast)
   - At least one about low-contrast monochrome comfort
   - At least one about face-framing color boldness tolerance
   - At least one about when the user reads "washed out" in their own experience

6. **Cross-cutting questions — minimum 3:**
   Questions that test multiple dimensions at once, useful for ambiguous cases:
   - At least one "look at three outfits you've been complimented on — what do they have in common"
   - At least one "look at three outfits that felt wrong — what did they have in common"
   - At least one about comfort zone vs. aspirational zone in color

7. **Selection guidance** (final section):
   - How to pick 2 questions for a typical check-in (one most-important dimension + one cross-check)
   - How to pick up to 3 questions for a high-uncertainty case
   - When to skip the check-in entirely (explicitly: you don't skip it; even high-confidence readings get a 2-question check-in)

**Constraints:**
- Questions must be phrased neutrally (not leading toward a particular answer)
- Questions must be answerable without specialized knowledge (no "are you an olive complexion" — that's Claude's job to determine)
- Do not include questions that require the user to run a new test during the check-in (the check-in uses information already collected)

**Cross-reference updates required:**
- `SKILL.md` Phase 3.5 section: after the existing text about check-in format, add a line: `Draw questions from \`references/checkpoint_questions.md\`. Pick 2 for typical cases, 3 for high-uncertainty cases.`

**Validation:**
- File exists at `references/checkpoint_questions.md`
- `grep -c "^###" references/checkpoint_questions.md` returns at least 6 (preamble section + 5 dimension sections + cross-cutting + selection guidance)
- `grep -c "^\- " references/checkpoint_questions.md` returns at least 23 (5 per dimension × 4 + 3 cross-cutting = 23 minimum)
- `grep -n "checkpoint_questions" SKILL.md` returns at least one match in Phase 3.5

---

### T1.5 — Add season-naming convention disclaimer to `references/twelve_seasons.md`

**Action:** Insert new section near top of file; verify consistency across files.

**Exact insertion:**

In `references/twelve_seasons.md`, after the introductory flow chart block and before "## The 12 seasons defined," insert this new section:

```markdown
## Naming conventions — acknowledging variants

The 12-season system has multiple naming conventions across published sources. This skill standardizes on specific names but recognizes the following as equivalent:

| This skill uses | Also known as | Notes |
|---|---|---|
| Deep Autumn | Dark Autumn | Same sub-season, same palette; Sci\ART systems use "Dark" more often than "Deep" |
| Deep Winter | Dark Winter | Same sub-season, same palette; used interchangeably in the industry |
| Warm Spring | True Spring | Considered the "archetype" Spring; some systems call it "Warm" others "True" |
| Warm Autumn | True Autumn | Same archetype relationship |
| Cool Summer | True Summer | Same archetype relationship |
| Cool Winter | True Winter | Same archetype relationship |

If a user arrives referring to themselves as a "Dark Autumn," this is the same as Deep Autumn. If they refer to "True Winter," this corresponds to Cool Winter. The skill treats them as interchangeable and uses the table above in its responses when naming variation comes up.

A known industry phenomenon: Soft Summer has been widely described as a "diagnostic dumping ground" — ambiguous cases often get assigned there by default. This skill pushes back against that pattern by requiring specific evidence for a Soft Summer reading (not just "the other options didn't seem right").
```

**Additional consistency check:**

- In `references/palette_library.md`, if any section header uses "Dark" or "True" in place of "Deep" or "Warm/Cool," change to the standardized name, and in the palette title, parenthetically note the alternative. Example: `### Deep Autumn (also known as Dark Autumn)` — but only if the section currently uses inconsistent naming. Scan all 12 palette headers. Current v2 already uses "Deep Autumn" and similar consistently; only add parenthetical notes if an inconsistency is found.

**Cross-reference updates required:**
- None for file creation; consistency scan may result in minor updates to `palette_library.md` per above.

**Validation:**
- `references/twelve_seasons.md` contains the new "Naming conventions" section
- The disclaimer table includes all six naming variants listed above
- `grep -n "Dark Autumn\|Dark Winter\|True Spring\|True Autumn\|True Summer\|True Winter" references/palette_library.md` returns zero matches OR only matches inside parenthetical disclaimers
- `grep -n "Deep Autumn\|Deep Winter\|Warm Spring\|Warm Autumn\|Cool Summer\|Cool Winter" references/palette_library.md` returns expected standardized names

---

### T1.6 — Detail PDF skill invocation in `SKILL.md` and `assets/swatch_card_layout.md`

**Action:** Modify two files.

**Changes to `SKILL.md`:**

Find the current Phase 6 text block containing `then invoke the \`pdf\` skill (for PDF formats) or frontend-design skill (for the phone wallpaper PNG)`.

Replace that sentence and the following paragraph with:

```markdown
If yes, **consult `assets/swatch_card_layout.md`** for the specifications and follow the PDF skill invocation protocol documented there.

**Before first invocation of the PDF skill in a session:** use the view tool to read `/mnt/skills/public/pdf/SKILL.md` (adjust path if the skill ecosystem is in a different location). Do not assume the PDF skill's invocation syntax — it may have changed since this skill was authored.

**If the PDF skill is unavailable** in the user's environment: produce a hex-code list deliverable that the user can convert externally, and state the limitation: "The PDF generation skill is not available in this environment. Here is a text-formatted palette summary you can paste into any design tool to generate your own swatch card."

**For PNG wallpaper output:** route to the frontend-design skill (read `/mnt/skills/public/frontend-design/SKILL.md` first). If also unavailable, the PDF fallback above applies.

**Do not auto-generate.** PDF generation is opt-in — some users want only the chat response.
```

**Changes to `assets/swatch_card_layout.md`:**

Find the existing section `## Invocation pattern` near the end of the file.

Replace that section with:

```markdown
## Invocation pattern

### Prerequisite
Before first invocation in a session, read the PDF skill's current SKILL.md:

```
view /mnt/skills/public/pdf/SKILL.md
```

Path may differ in non-Anthropic environments. Adjust accordingly.

### Standard invocation (pseudo-structure)
The PDF skill accepts layout specifications and content. Use a prompt structured like:

> "Generate a PDF with these specifications:
> - Layout: [Full-page / Wallet card / Phone wallpaper] as described in assets/swatch_card_layout.md
> - Palette: [user's season]
> - Hex codes and roles: [list from the delivered palette]
> - Header: [user name or 'Your' + season name + date]
> - Output path: /mnt/user-data/outputs/[season-name]-swatch-card.pdf"

Read the actual PDF skill invocation requirements from its SKILL.md — the above is scaffolding, not literal syntax.

### Failure handling
If the PDF skill returns an error or is unavailable:
1. State the failure to the user: "PDF generation isn't available in this environment."
2. Produce a markdown-formatted palette summary with hex codes clearly listed in role groups
3. Suggest external conversion tools (do not recommend specific products; suggest category only: "any design tool that accepts hex codes, or a simple text-to-PDF converter")

### Multiple format requests
If the user requests multiple formats (e.g., "wallet card + phone wallpaper"), invoke the skill once per format. Each invocation uses its own layout specification. Do not attempt to batch formats into a single invocation — each has different dimensions and role organization.
```

**Cross-reference updates required:**
- None beyond the two file modifications above.

**Validation:**
- `grep -n "view /mnt/skills/public/pdf/SKILL.md" SKILL.md` returns at least one match.
- `grep -n "Failure handling" assets/swatch_card_layout.md` returns at least one match.
- The phrase `then invoke the pdf skill` no longer appears in SKILL.md.

---

### T2.1 — Add Pattern and Print guidance to `assets/deliverable_template.md`

**Action:** Add a new section within the template output structure.

**Placement:** After Section 10 (Face-Framing vs. Distance Rules) and before Section 11 (Starter Capsule). Assign section number 10b.

**Required content for Section 10b:**

```markdown
## 10b. Patterns and Prints

### Scale (based on your Contrast reading)
- **High contrast:** can wear bold, large-scale patterns with strong color differentiation
- **Medium contrast:** works with medium-scale patterns; very small prints may disappear, very large prints may overwhelm
- **Low contrast:** favor small-scale, subtle patterns; large bold prints create a contrast level your coloring can't support

### Density (based on your Chroma reading)
- **Bright chroma:** can carry dense, color-rich patterns with multiple saturated colors
- **Muted chroma:** stick to sparse patterns where background dominates and accent colors are few
- **Between:** mid-density patterns with harmonized color relationships

### Which patterns to favor (from your palette)
- Patterns whose dominant colors are all from your palette
- Patterns where the background color is one of your neutrals
- Textured "patterns" (herringbone, twill, subtle checks) often work across all season types

### Which patterns to avoid
- Patterns combining colors from your palette + colors from your avoid list (the clash colors kill the look)
- Patterns with 4+ saturated colors unless you're Bright Spring, Bright Winter, or Warm Autumn at the deep end
- Pure black + pure white combinations if you're not a Winter season

### Specific recommendations for [user's season]
[Section populated per-season. For user's season: 3-5 specific pattern types that work well, with reasoning tied to dimensions.]
```

**Constraints:**
- The Section 10b content must be tied to the specific user's dimension readings. Generic advice only where dimension-general.
- No brand or designer names.
- Must reference the specific palette the user received (not generic palette concepts).

**Cross-reference updates required:**
- Update the Deliverable Template section inclusion logic at the top of the file: add Section 10b to the "Always include" list.

**Validation:**
- `grep -n "## 10b" assets/deliverable_template.md` returns at least one match.
- The section's four subsections (Scale, Density, Favor, Avoid) all present.
- Section 10b appears after Section 10 and before Section 11 in the file.

---

### T2.2 — Add Color Pairing Rules to `assets/deliverable_template.md`

**Action:** Add a new section within the template output structure.

**Placement:** After Section 3 (Core Palette) and before Section 4 (Colors to Avoid). Assign section number 3b.

**Required content for Section 3b:**

```markdown
## 3b. Color Pairing Rules

Your 36-color palette is raw material. Here's how to combine colors within it for reliable outfits.

### Safe foundation pairings
Combinations that always work for your season:
- **Neutral + Neutral:** Any two colors from your Neutrals group pair safely. These are your everyday backbone combinations.
- **Neutral + Mid:** Always works. Pick any Neutral as anchor (pants, jacket, bag) and any Mid as the face-framing color.
- **Light + Mid:** Works as long as the Light is one of your palette Lights, not pure white unless explicitly on-palette for your season.

### High-impact pairings
- **Dark + Statement:** One of your Darks anchoring a Statement color creates a sophisticated high-contrast look. Works best for events.
- **Neutral + Accent:** A large area of neutral with small accent color (scarf, jewelry, pocket square) gives a polished restrained look.
- **Mid + Mid (complementary):** Certain within-palette mid pairings create harmony — e.g., in warm seasons, olive + warm rose; in cool seasons, dusty blue + soft plum. Specific complementary mid pairings from your palette:

[Populated per user's season with 3-5 specific hex-code pairings]

### Pairings to avoid within your palette
- **Two Statements:** Wearing both statement colors at the same time creates visual overload. Statement colors should be the centerpiece.
- **Light + Dark at maximum contrast:** If your contrast reading was Low or Medium, avoid outfits pairing your very lightest palette color with your very darkest — it creates a contrast level your coloring doesn't support.
- **Accent + Accent:** Two accent colors together can fight each other, especially in Warm and Cool seasons where accents are highly saturated.

### Across zones (face-framing vs. distance)
- Your strongest face-framing colors can go anywhere on the body, but the reverse isn't always true — colors that are fine for bottoms may pull focus or wash you out if worn near the face
- When combining, put your highest-leverage color at the face and lower-priority colors below the waist
- If you're wearing an "avoid" color for practical reasons (work uniform, wedding dress code), pair it with a strong face-framing color from your palette to compensate
```

**Constraints:**
- Specific hex-code pairings must be drawn from the user's actual palette, not a generic set.
- Pairing recommendations must respect the user's Contrast and Chroma readings.

**Cross-reference updates required:**
- Update the Deliverable Template section inclusion logic: add Section 3b to the "Always include" list.

**Validation:**
- `grep -n "## 3b" assets/deliverable_template.md` returns at least one match.
- Section 3b appears between Section 3 and Section 4 in the file.

---

### T2.3 — Add Fabric Texture/Sheen guidance to `assets/deliverable_template.md`

**Action:** Add a new section within the template output structure.

**Placement:** After Section 3b (Color Pairing) and before Section 4 (Colors to Avoid). Assign section number 3c.

**Required content for Section 3c:**

```markdown
## 3c. Fabric Texture and Sheen

Your Chroma and Value readings affect how fabrics of different textures read against your coloring.

### Sheen (based on Chroma)
- **Bright chroma:** satin, silk, patent leather, and high-shine fabrics work — the sheen matches your coloring's clarity. Matte fabrics also work but can be less flattering in photos.
- **Muted chroma:** matte, nubby, and textured fabrics are your best friend. High-shine fabrics like satin and patent leather create a clarity mismatch — they read too crisp against your muted coloring. Use shine only in small doses (a silk scarf, not a satin dress).
- **Between:** moderate sheen works — wool, cotton with natural luster, leather in matte finishes.

### Fiber weight (based on Value)
- **Light value:** lightweight fibers generally flatter — linen, lightweight cotton, silk, fine wool. Heavy fabrics can overwhelm.
- **Medium value:** most fiber weights work. Use weight to vary the season-appropriate look.
- **Deep value:** heavier fibers — wool, thick cotton, heavy knits — provide the visual weight your coloring supports. Very lightweight translucent fabrics may read too delicate.

### Fiber types that tend to work universally
- Natural fibers (wool, cotton, silk, linen, cashmere) generally display color more accurately than synthetics
- Polyester in muted colors often reads duller than the hex would predict — if shopping polyester, verify in natural light before committing
- Wool takes dye richly and is often the safest fiber for rich palette colors

### Fiber-level mismatches to avoid
- **Muted-chroma user + polyester satin:** the shine-plus-synthetic reads cheap against your coloring
- **Bright-chroma user + heavy tweed:** the texture can muddy the clear colors your season depends on
- **Deep-value user + very thin lightweight fabric:** weight mismatch makes the coloring feel ungrounded

### Climate considerations
If your climate requires all-season wardrobe, note that the same palette color can read slightly differently in different fiber weights — a wool sweater in your signature rust will read differently than a linen tee in the same hex. Verify new purchases against your existing wardrobe pieces to confirm visual consistency.
```

**Constraints:**
- Recommendations must tie to the user's specific Chroma and Value readings.
- Climate section respects the lifestyle answer collected in intake (see T2.5).

**Cross-reference updates required:**
- Update the Deliverable Template section inclusion logic: add Section 3c to the "Always include" list.

**Validation:**
- `grep -n "## 3c" assets/deliverable_template.md` returns at least one match.
- Section 3c appears between Section 3b and Section 4.

---

### T2.4 — Add Body Coloring Beyond Face

**Action:** Modify `assets/intake_template.md`, `references/undertone_cross_checks.md`, and `SKILL.md` Phase 3 Dimension 1.

**Changes to `assets/intake_template.md`:**

In Part B's photo list, after Shot 5, add:

```markdown
| 6 (optional) | Inner forearm, palm-up, on sheet of white paper | Less sun-exposed skin for undertone cross-check |
```

Add a new optional "Shot 6" subsection after the "Optional but helpful" list:

```markdown
### Shot 6 (optional but highly recommended): Inner forearm

The inner forearm gets less sun exposure than the face, which often makes undertone easier to read reliably. Place your inner forearm flat on a sheet of white printer paper in natural daylight and photograph it from above. Include the wrist and as much of the forearm as the frame allows.

This shot is especially valuable if:
- Your face has significant sun exposure or tanning
- You have rosacea, melasma, or other pigmentation changes concentrated on the face
- You have facial hair obscuring jawline skin
- Standard undertone reads differ between face and inner wrist (if you know this from prior analysis)
```

In Part C questionnaire, after item 12 (Current life factors), add a new item 12b:

```markdown
12b. **Skin variation between areas** — Does your skin tone vary noticeably between sun-exposed areas (face, hands, forearms) and non-exposed areas (inner arm, stomach, upper thigh)? If yes, describe. This helps distinguish sun-adapted apparent coloring from baseline undertone.
```

**Changes to `references/undertone_cross_checks.md`:**

Add a new section at the end of the file:

```markdown
## Reading face vs. body coloring

The inner forearm or inner upper arm is a more reliable undertone reference than the face for users who:
- Have significant sun exposure on the face
- Have rosacea, melasma, acne, or other conditions affecting face skin
- Have visible pigmentation differences between face and body (common with heritage that tans differently than the baseline tone)

### When face and body readings differ

If the face reads warm but the inner arm reads neutral-cool (or vice versa), the inner arm is closer to the true undertone. The face has been altered by sun exposure or skin conditions.

**Protocol for discrepancy:**
1. Note the discrepancy explicitly in Phase 3 Dimension 1 output
2. Use the inner arm as the primary undertone reference
3. In the deliverable Confidence section, mention that face coloring and body coloring differ, and recommend sun protection / skincare adjustments if relevant to the user's goals (keep this brief — not medical advice)
4. If the discrepancy is extreme (e.g., heavily sun-damaged face + pale inner arm), confidence may need to drop to Moderate until the user can submit a re-shoot with reduced sun exposure (not always feasible)

### When only face photos were submitted

If the user skipped the optional Shot 6, proceed with face-only reading but note in the confidence section that body-skin cross-check was not performed. If undertone reading is already ambiguous from face photos alone, explicitly invite the user to submit the inner arm photo as a disambiguator.
```

**Changes to `SKILL.md` Phase 3 Dimension 1:**

Find the existing text `- Skin cast on face and neck against the white paper reference` in the "For typical fair-to-medium skin" list.

Add this line directly after it:
```
- Inner arm skin cast (if Shot 6 submitted) — more reliable than face when sun exposure or skin conditions have altered facial coloring
```

**Cross-reference updates required:**
- None beyond the three file modifications above.

**Validation:**
- `grep -n "Shot 6" assets/intake_template.md` returns at least 2 matches (photo list + subsection).
- `grep -n "12b" assets/intake_template.md` returns at least one match.
- `grep -n "face vs. body coloring" references/undertone_cross_checks.md` returns at least one match.
- `grep -n "Inner arm skin cast" SKILL.md` returns at least one match.

---

### T2.5 — Add Lifestyle/Profession/Climate questions to intake

**Action:** Modify `assets/intake_template.md` and reference those answers in `assets/deliverable_template.md`.

**Changes to `assets/intake_template.md`:**

In Part C questionnaire, after item 13 (Context) and before item 14 (Grooming categories), add three new items:

```markdown
13a. **Profession and work environment** — What do you do, and what's the dress code? This affects which palette roles to emphasize in the deliverable. Examples:
- Corporate (suit and tie / business formal)
- Business casual (slacks and button-downs / blazers optional)
- Creative professional (more flexibility, more color expression)
- Remote or casual-only (athleisure, jeans, casual tops)
- Uniform-based (medical scrubs, service industry uniform, etc. — note that baseline uniform color may not be in your palette and that's OK)
- Not currently employed / retired / other

13b. **Climate** — Where do you live, and what's the general temperature range? Examples:
- Hot / tropical (rarely below 60°F / 15°C, much of the year above 80°F / 27°C)
- Hot summer / mild winter (most of US South, coastal regions)
- Four-season with mild winter (most temperate regions)
- Cold winter / warm summer (Northeast US, Northern Europe, similar)
- Cold / harsh winter (Northern tier, Nordic countries, similar)

This affects fiber recommendations and which subset of your palette gets emphasized in the Starter Capsule.

13c. **Formal-to-casual ratio** — Out of a typical week, what percentage of your time is spent in each category?
- Formal (suits, dresses, professional attire)
- Business casual
- Everyday casual (jeans, sweaters, basics)
- Athletic / loungewear

Rough percentage estimate is fine. This affects which wardrobe pieces the Starter Capsule prioritizes.
```

**Changes to `assets/deliverable_template.md`:**

In Section 11 (Starter Capsule), after the Option A and Option B tiers, before the "What to buy first" paragraph, add:

```markdown
### Context adjustments

Based on your stated context (profession, climate, formal-to-casual ratio):

- **Fiber emphasis:** [Derived from climate — e.g., "In hot climate, linen, lightweight cotton, and silk should dominate your capsule. Heavy wool is less relevant."]
- **Role emphasis:** [Derived from formal-to-casual ratio — e.g., "With ~70% business casual, prioritize Mids and workhorse Neutrals. Reduce emphasis on Statement pieces relative to the default capsule."]
- **Palette subset:** [Derived from profession — e.g., "Corporate environment means restrained use of Accents and Statement colors. Lean on Neutrals + Darks for the professional wardrobe; use Accents for off-hours."]
```

**Cross-reference updates required:**
- None beyond the two file modifications above.

**Validation:**
- `grep -n "13a\|13b\|13c" assets/intake_template.md` returns 3 or more matches.
- `grep -n "Context adjustments" assets/deliverable_template.md` returns at least one match.

---

### T2.6 — Add Phase 0 Consultation Prep to `SKILL.md`

**Action:** Insert new phase at the start of the workflow.

**Placement:** After the "Workflow modes" section, before "Phase 1: Intake."

**Required content:**

```markdown
## Phase 0: Consultation Prep

Before starting heavy intake, run a brief exchange to establish context and route to the correct mode. This prevents the common failure mode where the user actually wants Mode 2-4 but gets routed through Mode 1 by default.

### The prep exchange

Claude's opening message in a new color-analysis conversation:

> "Before we start, a few quick questions so I can match the right workflow to what you need:
>
> 1. Have you been professionally color-typed before? If yes, what season? (It's fine to say 'I'm not sure' or 'I got a result from a quiz/app but I don't fully trust it'.)
> 2. What's driving this conversation — are you trying to discover your season for the first time, verify a prior result, evaluate specific items you own, or refine your understanding of your palette?
> 3. Roughly how much time do you have? The full analysis takes 15-30 minutes of back-and-forth including photo submission. Specific item checks or palette questions are usually 5-10 minutes.
>
> Based on your answers, I'll either walk you through the full protocol or jump into a shorter workflow."

### Routing rules after user responds

- **Never typed, wants first analysis, has time:** → Mode 1 (Full Analysis). Proceed to Phase 1.
- **Already typed from professional consultation, high confidence:** → offer Mode 2 (audit), Mode 3 (single item), or Mode 4 (refinement) based on their stated goal.
- **Already typed from quiz/app, medium-low confidence:** → ask whether they'd like Mode 1 to re-verify (recommended) or proceed with their stated season to Mode 2/3/4 (faster but may compound errors from bad typing).
- **Wants to know if a specific item is on palette:** → Mode 3, consult `assets/closet_audit_template.md`.
- **Ambiguous or user doesn't know what they want:** → ask one follow-up question, don't force a mode.

### When Phase 0 is skippable

Skip Phase 0 only if the user's opening message contains clear mode-routing signals:
- "Please do a full color analysis" → Mode 1
- "I'm a Soft Autumn, is this sweater on my palette?" → Mode 3
- "Audit my closet items" → Mode 2

In those cases, proceed directly to the relevant phase/mode. Otherwise, run Phase 0.
```

**Cross-reference updates required:**
- Update the phase numbering / navigation references elsewhere in SKILL.md if any exist. Scan for `Phase 1`, `Phase 2`, etc. — they retain their numbers; no renumbering needed, Phase 0 is simply the new starting point.

**Validation:**
- `grep -n "## Phase 0" SKILL.md` returns at least one match.
- The phase appears after "Workflow modes" and before "Phase 1: Intake" in file order.

---

### T2.7 — Add Phase 7 Delivery Walkthrough to `SKILL.md`

**Action:** Insert new phase at the end of the workflow.

**Placement:** After Phase 6 (Swatch card generation), before the "Meta-rules for the model" section.

**Required content:**

```markdown
## Phase 7: Delivery Walkthrough

After delivering the analysis (and the PDF, if generated), close with a structured offer to walk through the content. The deliverable is long — the user may not absorb it all in one read.

### Closing message template

> "That's the full analysis. Before we wrap up — would you like to walk through any section in more detail? Common deep-dives:
>
> - **Your palette** — questions about specific colors, how to use them, substitutions
> - **The dimension reasoning** — understand *why* you're a [season] vs. the neighbors
> - **Specific grooming categories** — anything from the conditional sections (eyewear, hair color, etc.)
> - **Starter capsule execution** — prioritization, what to buy first
> - **How to shop with this palette** — practical tips for in-store and online
> - **Something specific I haven't covered yet**
>
> Or if you've got what you need, you can save this conversation (or the PDF if we generated one) and come back any time if new questions arise."

### Handling specific follow-up types

- **Clarification questions:** answer directly, reference the relevant section of the delivered analysis. Do not re-produce the full deliverable.
- **Challenge to a specific recommendation:** hear out the challenge, evaluate whether it's evidence-based (reconsider) or preference-based (hold the line, explain reasoning).
- **Request for more detail in a section that was already covered:** expand with specifics, citing the user's particular dimensions and palette.
- **Request for a section that wasn't covered:** if the topic was skipped because the user didn't select the grooming category, offer to add it now. Otherwise, explain why the section wasn't relevant.
- **Request for Mode 2/3/4 follow-up:** smoothly transition to the appropriate template.

### Distinguishing Walkthrough from Modes

- Walkthrough = explaining what was already delivered
- Modes 2-4 = new analysis tasks on new inputs

If the user asks "can you evaluate these 5 items I own," that's Mode 2, not walkthrough. Route to `assets/closet_audit_template.md`.
```

**Cross-reference updates required:**
- None for this change alone; T2.8 adds a reference to the validation followup template within Phase 7.

**Validation:**
- `grep -n "## Phase 7" SKILL.md` returns at least one match.
- Phase 7 appears between Phase 6 and "Meta-rules for the model."

---

### T2.8 — Build `assets/validation_followup_template.md`

**Action:** Create new file; add reference to it in SKILL.md Phase 7.

**Required sections in `assets/validation_followup_template.md`:**

1. **Trigger phrases for post-delivery follow-up:**
   - "I tried the palette and [X] happened"
   - "The [specific color] isn't working for me"
   - "I got compliments on [X] but not [Y]"
   - "I think you got [dimension] wrong"
   - "Can you re-analyze now that I have new info?"

2. **Feedback collection structure:**
   - Ask the user: which colors worked, which didn't, in what contexts
   - Specifically collect: lighting conditions when failure was noticed, whether the fail was about the color itself or about the item (fit, style, fabric), whether there's a pattern in which palette colors failed

3. **Decision tree for response:**
   - **If 1-2 specific colors failed, rest works:** minor palette adjustment. Recommend alternative hex codes within the same season. Explain why those specific colors may have failed (often: slightly higher saturation than user's ideal within the season's range).
   - **If a category of colors failed (e.g., all the mids, all the darks):** partial season misdiagnosis likely. Investigate whether the user is actually an adjacent season. Ask targeted questions.
   - **If most of the palette failed:** full misdiagnosis suspected. Recommend re-running Mode 1 with fresh photos. Do not re-analyze from the same evidence that produced the failing result.
   - **If the user reports the palette works in some lighting but not others:** address the lighting issue rather than the palette (natural vs. indoor, seasonal light changes, screen-verified vs. in-person).
   - **If the user reports feeling great but getting negative feedback:** validate the user's own experience; colors that make someone feel good often are on-palette even if others' feedback is ambiguous.

4. **When to recommend in-person consultation:**
   - Recurrent failures despite adjustments
   - User's confidence has dropped significantly
   - High-stakes upcoming event where accuracy matters more than cost
   - User lives near a certified analyst and can access in-person service

5. **What not to do:**
   - Do not re-run the full Phase 1-5 protocol inside the walkthrough — that's Mode 1 and should be routed explicitly
   - Do not apologize profusely for a failed color recommendation; treat it as information that improves the next iteration
   - Do not pressure the user to commit to palette adjustments on the spot — offer the information and let them test

6. **One worked snippet:**
   - Scenario: Soft Autumn user reports "I tried the olive sweater you recommended and got three compliments. But the rust cardigan felt off — it emphasized redness in my face."
   - Claude's response: identifies that rust at the saturation level recommended may be slightly too warm for this specific user; offers a muted alternative hex code from the borderline with Soft Summer; notes that specific complexion conditions (rosacea, recent sun exposure) could amplify red when wearing rust; asks if the user wants to test one or two alternative mid-depth colors

**Changes to `SKILL.md` Phase 7:**

In the "Handling specific follow-up types" subsection, at the end, add:

```markdown
- **Post-delivery validation ("the palette isn't working"):** consult `assets/validation_followup_template.md`. This is a distinct workflow from Mode 2 audit — validation responds to lived experience with colors; audit evaluates new items against an established palette.
```

**Cross-reference updates required:**
- SKILL.md Phase 7 section update as above.

**Validation:**
- File exists at `assets/validation_followup_template.md`.
- Contains all 6 required sections.
- `grep -n "validation_followup_template" SKILL.md` returns at least one match.

---

### T3.1 — Add Two-Handed Photo Solutions to `assets/intake_template.md`

**Action:** Add subsection to intake template.

**Placement:** In Part A "Photo requirements," after the "Device settings to check" subsection and before Part B "Required photos."

**Required content:**

```markdown
### Solo photographer solutions

The photo protocol requires holding white printer paper at your cheek while capturing front-of-face, side profile, and hand shots. Solo photographers can't do all of these single-handed. Options:

**Option 1: Tape paper to mirror, use rear camera.** Tape a sheet of white printer paper to a mirror at cheek height when you stand in front of it. Stand facing the mirror, use your phone's rear camera (better quality than front camera) held to your side or slightly below, and capture your reflection plus the paper. The paper's position relative to the face is consistent without requiring a hand to hold it.

**Option 2: Prop paper against an object.** Lean the paper against a lamp, a stack of books, or a small stand at chest height. Position yourself so the paper is at cheek level when you stand. Leaves both hands free for the camera.

**Option 3: Camera timer + phone stand.** Set your phone on a stable surface at face height (stack of books, actual tripod if you have one). Use the timer function (3-10 seconds). You have both hands free to hold the paper at cheek level. Works for all 5 required shots.

**Option 4: Ask a household member.** If someone is available, having them hold the phone while you hold the paper makes the protocol trivial. The assistant does not need any training — just has to hit the shutter button.

**What doesn't work:**
- Selfie sticks (introduce their own color cast and often have poor camera quality at the required distance)
- Propping the paper on your shoulder (shifts lighting; paper reflects onto shoulder instead of next to face)
- Holding the paper in your mouth (don't)
- Skipping the paper entirely (the white balance reference is non-optional — see the Lighting section above for why)

### If none of these are feasible

If mobility issues or environment constraints make all four options impossible, contact Claude during intake and describe the constraint. A degraded-mode analysis can still be run with clear confidence caveats. Honest constraints are workable; pretending the protocol was followed when it wasn't produces false-confidence results.
```

**Cross-reference updates required:**
- None.

**Validation:**
- `grep -n "Solo photographer solutions" assets/intake_template.md` returns at least one match.
- All four options present.

---

### T3.2 — Build `references/between_seasons_protocol.md`

**Action:** Create new file; reference from SKILL.md Phase 4.

**Required sections:**

1. **When to trigger the between-seasons protocol:**
   - Dimensions align with two adjacent seasons on the flow chart with roughly equal strength
   - The draping comparison reveals that both adjacent seasons have defensible arguments (not one clearly winning)
   - User's compliment pattern includes colors from both candidate seasons at similar rates
   - User reports mixed experience — some colors from each candidate palette work

2. **Format for between-seasons output:**
   - State both candidate seasons and primary lean (e.g., "Primary: Soft Autumn; Secondary: Soft Summer")
   - Present both palettes at a reduced size (12 colors each rather than 36+36)
   - Show the overlap colors (colors that work for both)
   - Identify the "decisive test colors" — colors that would flatter one season but not the other

3. **Testing protocol for disambiguation:**
   - Specify 3-5 decisive test colors (hex codes) that differentiate the two candidates
   - Instruct user: wear these colors near face, in daylight, on a day when they're feeling baseline-healthy; note compliments, energy, how they feel in photos
   - Invite follow-up session with test results for refinement

4. **When to explicitly recommend in-person analysis:**
   - Between-seasons cases have above-average benefit from professional draping
   - If user's outcome matters significantly (bridal, career pivot, significant wardrobe investment): in-person is worth the cost
   - Claude should name this explicitly, not bury it

5. **Do not force a decision:**
   - If after the protocol the user is genuinely between seasons, that's a valid outcome
   - Some users function best by wearing both palettes and letting context decide (formal wardrobe from one, casual from the other, for example)
   - Validate this as a legitimate outcome rather than a failure

**Changes to `SKILL.md` Phase 4:**

In Phase 4, after the sentence `Respect genuine between-season cases...`, add:

```markdown
When triggering the between-seasons protocol, consult `references/between_seasons_protocol.md` for the structured output format and testing protocol. Use this rather than forcing a single season or producing two full separate deliverables.
```

**Cross-reference updates required:**
- SKILL.md Phase 4 as above.

**Validation:**
- File exists at `references/between_seasons_protocol.md`.
- All 5 required sections present.
- `grep -n "between_seasons_protocol" SKILL.md` returns at least one match.

---

### T3.3 — Add Color-Blind Accessibility provisions

**Action:** Modify `assets/intake_template.md` and `assets/deliverable_template.md`.

**Changes to `assets/intake_template.md`:**

In Part C questionnaire, after item 12b (Skin variation), add:

```markdown
12c. **Color vision** — Do you have any form of color vision deficiency? Options:
- No known color vision issues
- Deuteranopia / red-green deficiency (most common)
- Protanopia (red deficient)
- Tritanopia (blue-yellow deficiency, rare)
- Total color blindness (monochromacy, very rare)
- Not sure — but I sometimes confuse colors others see clearly

This does not affect your color analysis outcome. It affects how the deliverable is formatted so it's usable to you. If you answered anything except "No known," I'll include a color-blind-accessible format alongside the standard hex-code output.
```

**Changes to `assets/deliverable_template.md`:**

Add a new subsection in Section 3 (Core Palette), conditional on the user's answer to 12c:

```markdown
### Color-blind accessible format (conditional: if user indicated color vision deficiency in intake)

Each palette color is presented with:
- Standardized color name (e.g., "warm olive," "deep rust," "soft rose")
- Value tier (very light / light / medium-light / medium / medium-dark / dark / very dark)
- Saturation level (very muted / muted / moderate / saturated / very saturated)
- Hex code for reference
- Position within the palette (neutral / mid / accent / etc.)

### Pairs that may appear similar to you (flagged)

Certain palette colors may be visually difficult to distinguish depending on your specific color vision. Review these pairs carefully or verify with a sighted helper before committing:

- [Hex pair 1] — may appear similar under [type] deficiency
- [Hex pair 2] — may appear similar under [type] deficiency
[List generated specifically for the user's stated type]

### Shopping strategies

- Rely on labels and descriptions in retailer apps (often more descriptive than the pure hex rendering on screen)
- When in-store, ask for assistance distinguishing key palette members from near-neighbors
- Trust your compliment/fail memory over on-screen color rendering — your lived experience of what works is more reliable than screen color for you
```

**Cross-reference updates required:**
- None beyond the two file modifications.

**Validation:**
- `grep -n "12c" assets/intake_template.md` returns at least one match.
- `grep -n "Color-blind accessible format" assets/deliverable_template.md` returns at least one match.
- The deliverable subsection is explicitly marked as conditional on the intake answer.

---

### T3.4 — Add Privacy Guidance to `assets/intake_template.md`

**Action:** Add privacy section at top of intake template.

**Placement:** Immediately after the opening paragraph, before "Part A: Photo requirements."

**Required content:**

```markdown
## Privacy notes

Before you submit photos of your face, here's what's accurate about how they're handled:

- **Within this conversation:** The photos you submit are part of this chat session. When the conversation ends or is deleted, the photos are no longer retained in a way that persists to future sessions.
- **Not used for training:** Anthropic does not use chat content (including images) for training by default. You can verify current policy in Anthropic's published policies.
- **Deletion control:** You can delete this conversation any time from your chat history, which removes the photos from your account view. Retention in Anthropic's backend systems follows Anthropic's standard data retention schedule.
- **Screenshot and share considerations:** If you screenshot Claude's response (including any restated or described photo content) and share it elsewhere, those screenshots are outside Claude's and Anthropic's privacy controls.

**Minimizing identifying information:** If you prefer, you can crop photos tightly to show only the face/skin area needed, and avoid including identifying background, jewelry, clothing brand markers, or clearly visible name/ID tags. This does not reduce analysis quality.

**If you're uncomfortable submitting photos at all:** The analysis can still be attempted using only the questionnaire answers, with significant confidence reduction. Say so at the start and we can proceed accordingly. This is meaningfully less accurate than photo-based analysis.
```

**Constraints:**
- Only make factually accurate claims about Anthropic's products. Do not make claims about third-party Claude applications (the skill may be used in developer-built apps where policies differ).
- Do not promise anything ("never retained," "absolutely private") that the skill cannot guarantee.

**Cross-reference updates required:**
- None.

**Validation:**
- `grep -n "## Privacy notes" assets/intake_template.md` returns at least one match.
- Section appears before Part A.

---

### T3.5 — Rewrite cultural descriptions in `references/twelve_seasons.md`

**Action:** Modify the "typical coloring" descriptions for all 12 seasons.

**Required change:**

For each of the 12 seasons in `references/twelve_seasons.md`, the "Typical coloring" line currently describes features that skew Northern European. Rewrite each description to include phenotypic examples from at least two different heritage clusters.

**Format for each rewrite:**

```markdown
- Typical coloring: [dimension-based description — what actually makes this season]. Heritage examples: [example 1 from one cluster; example 2 from a different cluster; optionally example 3 from a third cluster]. The underlying dimensions (undertone + value + chroma + contrast) are what matter, not specific ethnic features.
```

**Specific requirements per season:**

- **Light Spring:** primary description unchanged in principle; examples should include at least one non-Northern-European.
- **Warm Spring:** examples should include warm-toned users across skin depths.
- **Bright Spring:** examples should explicitly note that Bright Spring occurs in East Asian, Latin American, and other clear-coloring heritages, not only European.
- **Light Summer:** examples should include cool-toned users across skin depths.
- **Cool Summer:** examples should include medium-skin cool-toned and fair cool-toned users.
- **Soft Summer:** examples should include olive-cool skin and mousy-neutral skin users.
- **Soft Autumn:** examples should include olive-warm and neutral-warm heritages.
- **Warm Autumn:** examples should include heritages across skin depths with warm undertones — African, Mediterranean, Middle Eastern, South Asian, and Northern European warm users.
- **Deep Autumn:** examples should prominently include deeply pigmented skin with warm undertones.
- **Deep Winter:** examples should prominently include deeply pigmented skin with cool-neutral undertones — explicitly note this season's prevalence across African, South Asian, East Asian, Mediterranean, and Northern European dark-cool heritages.
- **Cool Winter:** examples should include cool-toned medium and fair skin, explicitly noting that Cool Winter is not a race-specific category.
- **Bright Winter:** examples should include high-contrast cool coloring across multiple heritages.

**Constraints:**
- Do not include specific ethnicities as deterministic ("if you're X, you're Y"). Use heritages as examples of how a season presents, not as classifiers.
- Keep descriptions concise (3-5 example phenotypes per season, not encyclopedic).
- The four dimensions (undertone + value + chroma + contrast) must be the primary defining content; heritage examples are illustrative only.

**Cross-reference updates required:**
- None.

**Validation:**
- Each of the 12 "Typical coloring" lines has been updated.
- `grep -c "Heritage examples:" references/twelve_seasons.md` returns 12.
- Manually verify no description reads as "if you look like X, you're Y."

---

### T4.1 — Build `evals/evals.json` with test cases

**Action:** Create new directory and file.

**Schema:** Conform to skill-creator's evals.json format (reference `/mnt/skills/examples/skill-creator/references/schemas.md` or equivalent).

**Required test cases:**

Minimum 5 test cases. Each has: unique id, trigger prompt, expected output structure check, expected behavior markers.

1. **Test case: Full Mode 1 with clean inputs.**
   - Trigger prompt: "I want a full personal color analysis. Can you walk me through the process?"
   - Expected behavior: Claude runs Phase 0 consultation prep before Phase 1 intake.
   - Expected output structure: intake template delivered with all required elements (photo protocol, 5 required shots + 1 optional 6th, questionnaire with grooming categories + lifestyle/climate questions, privacy notes, solo photographer solutions).

2. **Test case: Single selfie submission without questionnaire.**
   - Trigger prompt: "[user attaches a single selfie] — what's my color season?"
   - Expected behavior: Claude refuses to analyze from one photo, delivers intake protocol, requests full submission.
   - Expected output: no season determination made.

3. **Test case: Mode 2 closet audit trigger.**
   - Trigger prompt: "I'm a Soft Autumn. Can you tell me if this sweater works with my palette?"
   - Expected behavior: Claude confirms season (asks about confidence of prior typing), asks for photo of the item, runs Mode 3 single-item check.
   - Expected output: item-specific verdict with hex comparison and placement recommendation.

4. **Test case: Mode 4 palette refinement.**
   - Trigger prompt: "I'm a confirmed Deep Winter. Can I wear emerald green, or is that out of my palette?"
   - Expected behavior: Claude recognizes this as Mode 4, consults palette_refinement_template.md, evaluates emerald green against Deep Winter palette.
   - Expected output: on-palette / borrowable / off-palette verdict with reasoning.

5. **Test case: Between-seasons ambiguity.**
   - Trigger prompt: "I've taken three color analysis quizzes and gotten Soft Summer twice and Soft Autumn once. I don't know which is right."
   - Expected behavior: Claude recognizes between-seasons case, consults between_seasons_protocol.md, offers structured disambiguation rather than forcing one season.
   - Expected output: both candidate seasons presented with reduced palettes, decisive test colors, testing protocol.

6. **Test case: Deep-skin user with no visible veins.**
   - Trigger prompt: Full intake submitted; wrist photo shows no clearly visible veins; user writes "veins not visible."
   - Expected behavior: Claude does not force a vein reading, uses alternative undertone tests (fabric draping, jewelry, foundation history), notes the vein test was skipped.
   - Expected output: undertone reading based on alternative tests with explicit note about skipped vein test.

**JSON structure:**

```json
{
  "skill_name": "true-hue",
  "evals": [
    {
      "id": 1,
      "name": "full_mode1_clean_inputs",
      "prompt": "I want a full personal color analysis. Can you walk me through the process?",
      "expected_output": "Intake template delivered; Phase 0 consultation prep completed first",
      "assertions": [
        "Response runs Phase 0 before delivering intake",
        "Intake includes all required photo shot specifications",
        "Questionnaire includes grooming categories question",
        "Questionnaire includes lifestyle/climate questions"
      ],
      "files": []
    }
    // ... other test cases in same format
  ]
}
```

**Constraints:**
- Assertions must be checkable — either programmatically (grep-able in output) or human-graded with clear pass/fail criteria.
- Do not include flaky assertions (e.g., "the tone feels right" — subjective).
- If assertions require file content checks, specify which file and what pattern.

**Cross-reference updates required:**
- None at file-creation time.

**Validation:**
- File exists at `evals/evals.json`.
- Valid JSON parse.
- At least 6 test cases present.
- Each test case has id, name, prompt, expected_output, assertions fields.

---

### T4.2 — Build `references/self_evaluation_rubric.md`

**Action:** Create new file; reference from SKILL.md self-check section.

**Required structure:**

1. **Preamble:** explain the rubric's role (Claude runs it before sending a deliverable, not after; failing criteria trigger rework).

2. **Per-section quality criteria:**

For each mandatory deliverable section (1, 2, 3, 3b, 3c, 4, 5, 6, 10, 10b, 11, 12) and each conditional section (7a-e, 8, 9), specify:
- Minimum required content elements
- Format requirements (e.g., hex codes present, role labels present)
- Quality indicators (e.g., reasoning cited, not just asserted)
- Red flags that indicate rework needed

Example for Section 1:
```markdown
### Section 1: Analysis Summary

**Minimum elements:**
- All four dimensions (Undertone, Value, Chroma, Contrast) explicitly stated
- Each dimension has at least one evidence citation (photo number, questionnaire item, fabric draping result)
- For deep skin, explicit statement of which tests were used and which skipped

**Quality indicators:**
- Evidence is specific (references "photo 2" not "your photos")
- For undertone specifically, at least two converging signals are cited
- Uncertainty, where present, is surfaced (not hidden)

**Red flags (requires rework):**
- Dimension stated without evidence
- Vein test forced on deep skin with visible veins unreadable
- Contrast described but not grounded in features
```

Cover all mandatory and conditional sections in this format.

3. **Composite quality indicators:**
- Deliverable as a whole passes self-check if: all mandatory sections meet their criteria, no red flags in any section, conditional sections match user's grooming selections exactly.

4. **Rework protocol:**
- If a single section fails criteria: rework that section before sending.
- If multiple sections fail: consider whether the underlying analysis is flawed (e.g., dimension readings may be wrong) and return to Phase 3 or Phase 3.5.
- If Phase 3.5 check-in was skipped: reject deliverable, run Phase 3.5, then re-check.

**Changes to `SKILL.md`:**

In the "Self-check before submitting the deliverable" section, after the existing checklist, add:

```markdown
For detailed per-section quality criteria and red flags, consult `references/self_evaluation_rubric.md`. If any red flag triggers, rework the section(s) before sending.
```

**Cross-reference updates required:**
- SKILL.md as above.

**Validation:**
- File exists at `references/self_evaluation_rubric.md`.
- All mandatory and conditional sections covered.
- `grep -n "self_evaluation_rubric" SKILL.md` returns at least one match.

---

### T4.3 — Build `references/sample_intakes.md`

**Action:** Create new file.

**Required content:** At least 3 described sample intakes, each covering photos (textually described — no actual images), questionnaire answers, and the expected quality-gate decision.

**Sample 1 — Textbook clean intake:**
- Photos: described as clearly following all protocol requirements (natural daylight, neutral white paper reading, no makeup, hair back, etc.)
- Questionnaire: complete, all 14+ items answered, specific rather than generic answers
- Expected gate decision: PASS, proceed to Phase 3
- Narrative: "This is what a submission should look like. No re-shoots needed, high confidence achievable."

**Sample 2 — Fixable single flaw:**
- Photos: 4 clean shots, 1 shot with warm lighting cast visible in the white paper reference (yellow tint)
- Questionnaire: complete
- Expected gate decision: PARTIAL ACCEPTANCE, request re-shoot of the single failing photo
- Narrative: "Common pattern. The user did most of it right. Reject only the failing photo, preserve the rest."

**Sample 3 — Multiple flaws, full reject:**
- Photos: flash detected in one, makeup visible in another, hair covering jaw in profile shot, no white paper reference in any shot
- Questionnaire: sparse (several items say "not sure" or are blank)
- Expected gate decision: FULL REJECT with specific feedback on each issue
- Narrative: "This user submitted quickly without reading the protocol. Help them understand what's needed. Tone: direct but not condescending."

**Sample 4 (additional, optional) — Deep-skin intake with appropriate vein-test skip:**
- Photos: clean, well-lit, protocol-followed. Wrist photo shows deeply pigmented skin with no clearly visible veins.
- Questionnaire: user notes "veins not visible"; foundation history is rich (Fenty 490 works, Maybelline 380 turned grey)
- Expected gate decision: PASS. Proceed to Phase 3 with vein test skipped per protocol.
- Narrative: "Correct handling. Vein invisibility is not a defect. Alternative undertone signals are strong in this submission."

**Constraints:**
- Describe photos textually only. No image generation.
- Use generic placeholder names or "the user."
- Do not reference specific individuals.

**Cross-reference updates required:**
- None. Sample intakes can be discovered by Claude reading the reference directory; no explicit SKILL.md reference needed.

**Validation:**
- File exists at `references/sample_intakes.md`.
- At least 3 samples present (4 recommended).
- Each sample has photos + questionnaire + decision + narrative.

---

## Cross-cutting concerns

### Description length monitoring

After all tasks complete, verify `SKILL.md` frontmatter description stays under 1024 characters. New phases (Phase 0, Phase 7) and modes (Mode 4 buildout) may create pressure to expand the description. If it exceeds 1024:

1. Trim redundant trigger phrases in the description.
2. Consolidate overlapping trigger cases.
3. Do not sacrifice description triggers that route to new v3 capabilities (post-delivery validation, between-seasons, color-blind accessibility).

Verification command:
```
awk '/^description:/ {print length($0)}' SKILL.md
```

Target: < 1037 (accounting for `description: ` prefix + newline = 1024 effective).

### Cross-reference audit

After all tasks complete, run this audit:

```
grep -rnE "(assets|references|evals)/[a-z_]+\.(md|json)" SKILL.md assets/*.md references/*.md evals/*.json
```

Every path output by that command should correspond to a file that exists. No orphan references.

For each file in `assets/`, `references/`, and `evals/`, it should be referenced from `SKILL.md` OR from another file that is itself referenced from `SKILL.md`. No orphan files.

### No development markers

```
grep -rn "NEW:\|TODO\|FIXME\|XXX" SKILL.md assets/*.md references/*.md evals/*.json
```

Should return zero matches.

### Validation pass

Run skill-creator's quick_validate:
```
python -m scripts.quick_validate <path-to-skill>
```

Expected output: `Skill is valid!`

### Packaging

Final step:
```
python -m scripts.package_skill <path-to-skill>
```

Expected output: `Successfully packaged skill to: <path>/true-hue.skill`

---

## Final validation protocol

Before declaring v3 complete, verify each of these:

1. [ ] All 22 task validations pass (per-task checks above).
2. [ ] Description length under 1024 characters.
3. [ ] All cross-references resolve (no broken links).
4. [ ] No orphan files in `assets/`, `references/`, or `evals/`.
5. [ ] No development markers in any shipped file.
6. [ ] `quick_validate.py` passes.
7. [ ] `package_skill.py` succeeds.
8. [ ] `evals/evals.json` parses as valid JSON.
9. [ ] Season naming consistent across `twelve_seasons.md` and `palette_library.md`.
10. [ ] Phase 3.5 check-in documented with question library reference.
11. [ ] Phase 0 and Phase 7 present in SKILL.md.
12. [ ] Conditional deliverable sections match grooming category selections.

Only after all 12 pass: declare v3 complete and deliver the packaged `.skill` file.

---

## Reporting requirements

After execution, produce a final report containing:

1. Task-by-task completion status (pass / fail / partial with reason).
2. Any deviations from the spec (what and why).
3. Any ambiguities encountered and how they were resolved.
4. Final file listing with line counts.
5. Description length (in characters).
6. Packaged `.skill` file size and path.

Format: markdown, one section per numbered item above.

---

*End of Specification*
