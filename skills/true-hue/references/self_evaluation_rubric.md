# Self-Evaluation Rubric — Pre-Delivery Quality Check

Before sending any deliverable to the user, Claude runs this rubric on the draft. The rubric evaluates section-level quality — not just whether a section is present, but whether its content meets the standard. A section that exists but fails criteria triggers rework before the deliverable goes out.

Use this reference in conjunction with the SKILL.md "Self-check before submitting the deliverable" list. The SKILL.md checklist confirms presence; this rubric confirms quality.

---

## How to use the rubric

1. After producing a full deliverable draft, read through section by section.
2. For each section, check: minimum elements present, format correct, quality indicators met, no red flags triggered.
3. If a section fails any criterion, rework it before sending.
4. If multiple sections fail, consider whether the underlying analysis is flawed and return to Phase 3 or Phase 3.5.
5. If Phase 3.5 was skipped for any reason, reject the deliverable, run Phase 3.5, then re-evaluate.

The rubric is strict by design. A failing draft is a correctable draft; a failing deliverable sent to the user is a trust loss.

---

## Per-section quality criteria

### Section 1: Analysis Summary

**Minimum elements:**
- All four dimensions (Undertone, Value, Chroma, Contrast) explicitly stated
- Each dimension has at least one evidence citation (photo number, questionnaire item, fabric draping result)
- For deep skin, explicit statement of which tests were used and which skipped
- Confidence level per dimension if not uniformly high

**Format requirements:**
- Each dimension appears as a labeled heading or bolded lead
- Evidence is integrated into prose, not just a list with no reasoning
- No dimension stated without cited evidence

**Quality indicators:**
- Evidence is specific (references "photo 2" not "your photos")
- For undertone specifically, at least two converging signals are cited
- Uncertainty, where present, is surfaced (not hidden)

**Red flags (requires rework):**
- Dimension stated without evidence
- Vein test forced on deep skin with visible veins unreadable
- Contrast described but not grounded in features

### Section 2: Draping Comparison (Why this season, not the neighbors)

**Minimum elements:**
- Both adjacent seasons named (per the adjacency map in `references/twelve_seasons.md`)
- Each adjacent season given a specific reason for exclusion tied to the user's dimensions
- The chosen season's fit explicitly confirmed

**Format requirements:**
- Separate paragraphs/subsections for each adjacent comparison
- Reasoning references specific palette characteristics, not vague generalities

**Quality indicators:**
- The "why not" reasoning for each adjacent is distinct, not the same argument twice
- The reasoning hangs on specific dimensions (e.g., "Soft Summer runs cool, your undertone is warm") rather than hand-wave

**Red flags:**
- Only one adjacent season addressed
- "Why not" reasoning is generic and could be applied to any season
- Missing draping comparison entirely

### Section 3: Core Palette

**Minimum elements:**
- Approximately 36 hex codes organized by role (Neutrals, Lights, Mids, Darks, Accents, Statement)
- Each hex code has a short color name
- Palette pulled from `references/palette_library.md`, not invented

**Format requirements:**
- Hex codes in backticks or monospace for easy copy
- Role groupings clearly labeled
- Counts match palette library expectations (8 Neutrals, 6 Lights, 10 Mids, 6 Darks, 4 Accents, 2 Statement)

**Quality indicators:**
- Palette includes any LAB-validated anchor colors (★) from the palette library entry for the user's season
- Color names follow consistent naming conventions (warm cream, not "creamy yellow" and "pale beige" interchangeably)

**Red flags:**
- Hex codes invented or pulled from generic color references
- Fewer than 30 or more than 40 colors
- Role groupings missing or mislabeled

### Section 3b: Color Pairing Rules

**Minimum elements:**
- Safe foundation pairings, high-impact pairings, and pairings-to-avoid all covered
- At least 5 specific within-palette pairings cited with hex codes
- Across-zone guidance (face-framing vs. distance)

**Format requirements:**
- Hex codes used in pairing examples, not just color names
- Pairings tied to the user's specific contrast and chroma readings

**Quality indicators:**
- Mid + Mid complementary section includes 3-5 specific pairings from the user's palette
- Pairings-to-avoid respects the user's contrast level (e.g., Light + Dark max-contrast combo warned against for low/medium contrast users)

**Red flags:**
- Pairings listed without hex codes
- Pairings contradict the contrast or chroma reading
- Section missing entirely

### Section 3c: Fabric Texture and Sheen

**Minimum elements:**
- Sheen guidance tied to Chroma
- Fiber weight guidance tied to Value
- Universal fiber notes and fiber-type mismatches to avoid
- Climate considerations (if intake provided climate data)

**Format requirements:**
- Direct tie to the user's specific dimensions, not generic advice

**Quality indicators:**
- Specific fabric recommendations that follow from the user's Chroma/Value combination
- Climate section references the user's stated climate when available

**Red flags:**
- Guidance contradicts the user's muted/bright chroma or light/deep value reading
- Section missing entirely

### Section 4: Colors to Avoid

**Minimum elements:**
- 8-12 hex codes with a specific reason per color
- Reasons reference temperature, chroma, value, or contrast (not "just doesn't work")

**Format requirements:**
- Hex code in backticks + color name + dash + reason

**Quality indicators:**
- "Avoid" colors are common-encounter colors (pure black, pure white, etc.) not obscure oddities
- Reasons are individually specific and don't repeat verbatim
- Reasoning generalizes — the user could extrapolate to similar colors

**Red flags:**
- Fewer than 8 or more than 12 avoid colors
- Reasons are formulaic and identical across entries
- Missing hex codes

### Section 5: Metals and Jewelry

**Minimum elements:**
- Primary metal recommendation with reasoning
- Secondary metal options
- Metals to avoid near face, if any
- Mixing-metals guidance

**Format requirements:**
- Metal recommendations tied to the user's undertone

**Quality indicators:**
- Addresses both face-framing and body-worn jewelry
- Acknowledges aesthetic preference vs. what flatters (if relevant)

**Red flags:**
- Metal recommendation contradicts the undertone reading
- Missing section

### Section 6: Your Neutrals Specifically

**Minimum elements:**
- User's "black," "white," "navy," "grey," "beige," "denim" all addressed with hex codes from the palette

**Format requirements:**
- Each neutral role paired with one specific hex from the user's palette
- Reasoning provided (why this substitutes for the traditional neutral)

**Quality indicators:**
- Denim guidance is specific (wash type, not just a hex)
- Navy substitute is appropriate for season (not every season has a true navy)

**Red flags:**
- Any traditional-neutral role not addressed
- Recommendations contradict the palette (e.g., suggesting pure black for a Soft Autumn)

### Section 7a: Makeup Logic (conditional — "full makeup" or "skincare/tinted products" selected)

**Minimum elements:**
- Foundation undertone guidance
- Lipstick families + hex inspirations + avoid list
- Blush tone + reasoning
- Eyeshadow families + avoid list
- Eye definition (liner/mascara)
- For deep skin: brand-range note and appropriate blush saturation

**Format requirements:**
- Hex codes for lipstick and blush inspirations
- Undertone label consistent with Dimension 1 reading

**Quality indicators:**
- Recommendations generalize (the user can apply the principle at a beauty counter)
- For deep skin, blush saturation explicitly adjusted upward

**Red flags:**
- Section included when user didn't select these categories
- Brand names absent for deep-skin foundation range (the one place brand names are appropriate)
- Makeup recommendations contradict undertone

### Section 7b: Facial Hair Guidance (conditional — "facial hair" selected)

**Minimum elements:**
- Reading of the user's natural facial hair color from photos
- Interaction with palette
- Grooming strategies for color mismatches
- Dyeing recommendations (if user expressed interest)
- Shirt colors to wear with facial hair

**Red flags:**
- Section included when user didn't select the category
- Ignores grey, red, or darker-than-hair beard variance

### Section 7c: Eyewear Frame Colors (conditional — "eyewear" selected)

**Minimum elements:**
- Best metal frame colors
- Best acetate/plastic colors (hex codes from palette)
- Best tortoiseshell direction (warm vs. cool)
- Clear frames assessment
- Tinted lens recommendations
- Colors/frames to avoid

**Red flags:**
- Section included when user didn't select eyewear
- Metal recommendations contradict Section 5

### Section 7d: Ties and Pocket Squares (conditional)

**Minimum elements:**
- 5-8 tie hex codes with context
- Pattern guidance tied to contrast
- Pocket square coordination rules
- Tie colors to avoid

**Red flags:**
- Section included when user didn't select the category
- Patterns guidance contradicts Section 10b

### Section 7e: Watches and Accessories (conditional)

**Minimum elements:**
- Watch case metal
- Watch face color recommendations
- Leather band colors (hex from palette)
- Bags/briefcases colors
- Belts and shoes

**Red flags:**
- Section included when user didn't select the category
- Metals contradict Section 5

### Section 8: Hair Color Guidance (conditional — "hair color" or mentioned considering change)

**Minimum elements:**
- Stay-within range
- Avoid list
- Highlights guidance
- Lowlights guidance (if hair is dark enough to take lowlights)
- Going-grey guidance

**Red flags:**
- Recommendations contradict the undertone reading
- Section included without trigger

### Section 9: Tinted Skincare (conditional — "skincare/tinted products" selected AND NOT "full makeup")

**Minimum elements:**
- Tinted moisturizer undertone
- Tinted SPF recommendation
- Lip balm with color guidance
- Brow product

**Red flags:**
- Section included alongside full Section 7a (they're alternatives, not both)
- Recommendations contradict undertone

### Section 10: Face-Framing vs. Distance Rules

**Minimum elements:**
- Top 8 face-framing colors from palette (with brief reasoning)
- Colors fine at distance but avoid near face
- Colors to avoid even at distance

**Format requirements:**
- Hex codes for all recommendations
- Groupings clearly delineated

**Red flags:**
- Top 8 face-framing colors don't include the most-flattering options from the palette
- Distance guidance contradicts the palette's known character

### Section 10b: Patterns and Prints

**Minimum elements:**
- Scale guidance tied to Contrast
- Density guidance tied to Chroma
- Patterns to favor, patterns to avoid
- Season-specific pattern recommendations (3-5 types)

**Red flags:**
- Pattern guidance contradicts the user's contrast/chroma reading
- Section missing

### Section 11: Starter Capsule

**Minimum elements:**
- Option A (budget tier, ~$500)
- Option B (investment tier, $1500-$3000+)
- Context adjustments (if intake provided profession/climate/formal ratio)
- 6-month phasing ("what to buy first")

**Format requirements:**
- Each of 10 items has a specific description including hex where relevant
- Items reference the user's actual palette, not generic wardrobe staples

**Quality indicators:**
- Phasing prioritizes high-leverage neutrals first
- Investment tier emphasizes natural fibers
- Context adjustments actually modify the recommendations, not just restate them

**Red flags:**
- Generic advice that could apply to any season
- Missing context adjustments when intake provided the data
- Items with no hex code reference

### Section 12: Confidence and Caveats

**Minimum elements:**
- Overall confidence level (High/Moderate/Low) with explanation
- Edge-of-season notes if applicable
- What could change this result
- Honest photo-based-analysis limitations
- Follow-up options (Mode 2, 3, 4, PDF, in-person recommendation)

**Quality indicators:**
- Confidence level reflects the actual strength of evidence
- Edge-of-season notes specify which adjacent season and in what way
- Moderate or Low confidence not hidden under reassuring language

**Red flags:**
- False confidence — High stated when evidence was moderate
- Missing or buried follow-up options
- No mention of photo-based limitation
- In-person recommendation missing when high-stakes user context warrants it

---

## Composite quality indicators

A deliverable as a whole passes the pre-send self-check if:

- All mandatory sections (1, 2, 3, 3b, 3c, 4, 5, 6, 10, 10b, 11, 12) meet their criteria
- No red flags in any section
- Conditional sections match the user's grooming selections exactly (no padding, no omitting)
- Phase 3.5 check-in was run and the exchange is referenced or its results integrated
- Draping comparison specifically addresses both adjacent seasons
- Hex codes used throughout rather than color names alone

---

## Rework protocol

- **Single-section failure:** rework that section before sending. Keep the rest.
- **Multiple-section failure:** pause and examine whether the underlying analysis is flawed. Dimension readings may be wrong. Return to Phase 3 or Phase 3.5 before reworking sections.
- **Phase 3.5 check-in was skipped:** reject the deliverable entirely. Run Phase 3.5. Then re-evaluate.
- **Palette invented rather than pulled from the library:** reject. Pull from `references/palette_library.md`.
- **False confidence:** adjust the Confidence section honestly. Moderate confidence is legitimate; fake High is not.

A failing draft is a correctable draft. Take the extra pass — it's cheap relative to fixing things post-delivery.
