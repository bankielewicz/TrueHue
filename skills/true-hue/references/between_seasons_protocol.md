# Between-Seasons Protocol

Some cases are genuinely ambiguous between two adjacent seasons, and forcing a single answer produces worse guidance than acknowledging the ambiguity. This reference specifies when and how Claude should deliver a between-seasons result.

Between-seasons is not a fall-back for low confidence — it's a legitimate outcome when the evidence actually points to two neighbors with roughly equal strength. If one season is clearly winning and the other is only plausible, resolve to the winner and note the border in the deliverable. Reserve this protocol for true ties.

---

## When to trigger the between-seasons protocol

Use this protocol when **multiple** of the following apply, not just one:

- **Dimensions align with two adjacent seasons** on the flow chart with roughly equal strength — e.g., undertone reads neutral, chroma reads muted, and value is on the boundary between two season ranges
- **Draping comparison reveals balanced arguments** — when explicitly justifying why not each adjacent season, you can't find a clear-loser adjacent; both have meaningful points against the primary
- **Compliment pattern straddles both candidates** — user's reported compliments include colors that are specific to one palette and specific to the other at similar rates
- **User reports mixed lived experience** — some colors from each candidate's palette have worked, some haven't, and the working/failing split doesn't cluster on one side

**Do not trigger** when:
- One season is clearly winning and the other is only "also plausible"
- Confidence is low because the photo inputs were degraded (that's a different problem — request a re-shoot)
- The user wants to be between seasons because they like colors from both palettes (preference-based pushback, not evidence)

---

## Format for between-seasons output

Instead of a single full deliverable, produce a compact dual-candidate structure.

### 1. State both candidate seasons and the primary lean

Example:
> "Primary: Soft Autumn (60% weight based on warm undertone signals). Secondary: Soft Summer (40% weight based on low-medium contrast and soft chroma holding across both). This is a legitimate between-seasons case; both palettes have evidence-based claim."

Be explicit about which is primary and why. Do not present as a perfect 50/50 unless evidence is actually balanced.

### 2. Present both palettes at reduced size

For each candidate season, show 12 colors instead of the full 36. Pull from the season's palette library entry (`references/palette_library.md`). Organize by role but with fewer entries:

- 3 Neutrals
- 3 Mids (including at least one face-framing)
- 2 Lights
- 2 Darks
- 1 Accent
- 1 Statement

Use actual hex codes from the palette library, not placeholders. Cite the source season under each mini-palette.

### 3. Show the overlap colors

Identify 4–8 hex codes that work for **both** candidate seasons. These are the user's safest colors — the pieces that will work regardless of which palette ultimately fits better. Present them as a single overlap list.

### 4. Identify 3–5 decisive test colors

The decisive colors are hex codes that would flatter one candidate season but fail the other. These are the user's disambiguation toolkit.

For each decisive color, specify:
- The hex code
- Which candidate season it belongs to
- What "success" looks like if it flatters the user (face comes alive, complexion reads clear, compliments cluster)
- What "failure" looks like (face reads tired, complexion reads off, feels "not quite right")

---

## Testing protocol for disambiguation

Give the user a concrete action plan with the decisive colors.

1. **Wear each decisive color near the face** — scarf, turtleneck, collar, top — not as an accent at distance. Face-framing position is where disagreement between adjacent palettes shows up.
2. **Test in natural daylight** — not in indoor light that may favor one temperature over the other.
3. **Test on a day the user is feeling baseline-healthy** — not recovering from illness, not the day after a sunburn, not in a phase where their skin is unusually pigmented or muted.
4. **Note response across three dimensions:**
   - How they feel in photos
   - Compliments (or absence thereof) from others
   - Their own read in the mirror — energized or tired
5. **Report back after testing 2–3 decisive colors.** Claude then refines based on the pattern.

Invite the user to schedule a follow-up session with test results. Don't demand an immediate decision — between-seasons determinations often benefit from lived testing rather than snap judgment.

---

## When to explicitly recommend in-person analysis

Between-seasons cases have above-average benefit from professional draping. The in-person analyst sees the response to physical fabric, in real lighting, that no remote protocol can fully match.

Recommend in-person when any of:

- The user's stakes are high — bridal, major career pivot, significant wardrobe investment planned, public-facing role change
- After the testing protocol, the user reports both candidate palettes remain ambiguous
- The user lives near a certified color analyst and can access the service
- The user has asked about higher-accuracy options

When recommending, name it directly. Something like: "Between-seasons cases are the single highest-value use of in-person professional analysis. If you have access to a certified analyst, this is worth the cost — they can do physical fabric draping that remote analysis can't match."

Do not bury the recommendation inside caveats or downstream follow-up lists. Surface it.

---

## Do not force a decision

Some users are genuinely between seasons, and that remains the correct answer even after testing. Respect this.

- Validate it as a legitimate outcome, not a failed analysis.
- Some users will function best by **wearing both palettes contextually** — e.g., the cooler palette for their professional wardrobe and the warmer palette for casual/personal use; or one for daylight occasions and one for evening. This is a workable strategy, not a compromise.
- Do not pressure the user to pick a primary season if the evidence genuinely doesn't support picking one.
- Write the deliverable to reflect the dual palette honestly, including guidance on how to navigate shopping with two candidate palettes in mind.

---

## Worked example — Soft Summer / Soft Autumn between-seasons

**Scenario:** User has neutral undertone (green veins but also harmonizes with silver), low-medium contrast, muted chroma, medium value. Compliments cluster on olive, dusty blue-grey, muted terracotta, and dusty rose. Fabric draping test was inconclusive — both white and cream worked.

**Claude's output:**

> **Primary: Soft Autumn (55% weight). Secondary: Soft Summer (45% weight).** This is a genuine between-seasons case. Your undertone sits on the neutral line; your chroma and contrast align cleanly for both candidates; your compliment pattern genuinely includes colors specific to each.
>
> **Soft Autumn mini-palette (12 colors):**
> - Neutrals: `#E8DCC4`, `#B8A080`, `#5C4A33`
> - Mids (face-framing): `#A68B5B`, `#7D8B5A`, `#9C7E52`
> - Lights: `#F0E5C8`, `#E8D5B0`
> - Darks: `#4A3D2A`, `#3E4D2D`
> - Accent: `#A0522D`
> - Statement: `#704214`
>
> **Soft Summer mini-palette (12 colors):**
> - Neutrals: `#EDE8DE`, `#ADA295`, `#524A3F`
> - Mids (face-framing): `#8FA5A5`, `#A89890`, `#9B8AA0`
> - Lights: `#D8D0C8`, `#E8DFD5`
> - Darks: `#4A5555`, `#5C4D4D`
> - Accent: `#9B6A6C`
> - Statement: `#7A3E48`
>
> **Overlap colors (safe for both):** `#B8A080` (warm taupe/cool taupe), `#9C8363` (warm mushroom/neutral mushroom), soft cream in the `#E8DCC4`–`#EDE8DE` range, and dusty sage around `#8A9A5B`–`#8FA5A5`. These are your safest neutrals and mids.
>
> **Decisive test colors (pick any 2–3 to test face-framing in daylight):**
> - `#704214` (Soft Autumn Deep Rust) — will pull your face toward warm and earthy if Soft Autumn fits. Will feel slightly off if Soft Summer fits.
> - `#7A3E48` (Soft Summer Muted Wine) — will pull your face toward cool and complex if Soft Summer fits. Will feel slightly off if Soft Autumn fits.
> - `#A68B5B` (Soft Autumn Warm Honey) — classic Soft Autumn face-framing; Soft Summer users often read dull or tired in this.
> - `#8FA5A5` (Soft Summer Dusty Blue-Green) — classic Soft Summer face-framing; Soft Autumn users often read greenish or washed in this.
>
> **Testing plan:** Try two of these at the face in natural daylight. Come back with what happened — which made your face come alive, which made you look tired, any others' compliments. I can refine from there.
>
> Note: this is exactly the kind of case where in-person professional analysis with physical fabric draping would resolve the ambiguity faster than remote iteration. If you have access to a certified analyst, it's worth the cost.
