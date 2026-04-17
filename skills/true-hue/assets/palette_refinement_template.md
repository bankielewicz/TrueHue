# Palette Refinement Template (Mode 4)

Use this template when a user has a confirmed season and wants to refine, stretch, or interrogate the edges of their palette. Mode 4 is surgical — not a re-analysis. The user's season is given; you are explaining, testing, or expanding within and adjacent to it.

---

## When to use Mode 4

Route to this template when the user's opening message (or a clarifying reply during Phase 0) matches any of these patterns:

- "I'm already a [season], but I want to understand what I can borrow from [adjacent season]"
- "Can I wear [specific color outside my palette]?"
- "How far can I push my palette before things go wrong?"
- "I keep seeing [season name] colors I love — am I actually that season or can I borrow?"
- "I'm a [season] — what colors work for [specific occasion / climate / context]?"

If the user's season is not confirmed or their stated season seems unlikely from conversational evidence, surface this (see "Edge case handling" below) and offer Mode 1 instead.

---

## Input requirements

Before producing output, confirm the following with the user:

1. **Primary season** — what it is, and how it was determined:
   - Prior professional (draping) analysis — high confidence
   - Prior use of this skill (Mode 1) — high confidence
   - Self-identification from study or reading — medium confidence
   - Online quiz / app result — low-to-medium confidence; offer Mode 1 re-verification as an option
2. **The specific question or area to refine** — which of these three sub-modes applies:
   - Adjacent-season borrowing (general boundary-stretching)
   - Specific color check (one color in, one verdict out)
   - Palette expansion for an occasion (context-driven emphasis shift)
3. **Optional context for why** — new job, climate change, upcoming event, aesthetic evolution, desire to wear a trending color, etc. Context shapes which sub-mode's output gets emphasized.

Do not proceed until the season and sub-mode are clear.

---

## Output structure — Adjacent Season Borrowing

Use this sub-mode when the user asks what they can borrow from neighbors.

1. **Identify the two adjacent seasons** on the flow chart (consult `references/twelve_seasons.md` adjacency map).
2. **For each adjacent season, list 5–10 specific colors (hex codes) that are borrowable** at stated intensity:
   - Annotate each with a borrowability rating: "safe," "conditional," or "distance only"
   - Specify intensity: which variant of the color works (a muted version of a bright neighbor color, not the full-chroma version)
3. **Specify conditions:**
   - When to wear (face-framing vs. distance — borrows often work better below the shoulders)
   - Pairing rules (pair with primary-season neutrals to anchor the borrow)
   - How far the user can push before the borrow fails (e.g., "muted olive borrows safely, but once you hit full Warm Autumn pumpkin, it overpowers")
4. **Note colors that are NOT borrowable** even at low intensity — often the signature brights/deeps of the neighbor that define its distance from the user's primary.

---

## Output structure — Specific Color Check

Use this sub-mode when the user presents a specific color (hex, photo, or verbal description like "the deep burgundy from that shop").

1. **Identify the color's hex** — if provided, use it; if photo, estimate; if verbal, ask for a hex or reference image.
2. **Identify the closest match in the user's palette** — cite the palette hex and role.
3. **Classify the color:**
   - **On-palette** — already covered; point them to the palette
   - **Borrowable** — comes from an adjacent season and works at stated conditions
   - **Off-palette** — belongs to a distant season or fights a user's dimensions
4. **If borrowable, specify the conditions:**
   - Lighting it works under (daylight vs. indoor)
   - Proximity to face (face-framing vs. distance only)
   - Pairing rules (what to anchor it with)
5. **If off-palette, explain what fails** — which of the four dimensions it violates and by how much, with a specific substitute hex from the user's palette that occupies a similar visual role.

---

## Output structure — Palette Expansion for Occasions

Use this sub-mode when the user describes a context: formal event, tropical vacation, new professional setting, winter wedding, etc.

1. **Identify the palette roles emphasized for that context** — formal contexts lean on Darks + Neutrals; tropical contexts shift toward Lights + Mids; etc.
2. **Recommend which primary-season colors to emphasize** — cite 5–10 hex codes from the user's palette and explain why each fits the context.
3. **Recommend borrowed colors from adjacent seasons** specifically useful for the context (e.g., a Soft Autumn asked about a summer beach vacation can borrow Soft Summer's dusty blues for a coastal aesthetic).
4. **Note which palette colors to deprioritize** for the context — not "avoid," but "leave these at home this trip."

---

## Edge case handling — user-stated season was wrong

During Mode 4, evidence can accumulate that the user's stated season doesn't match their coloring. Common signals:

- Borrow requests consistently push in a direction suggesting a different primary season
- User reports their palette "isn't working" or specific roles (e.g., all the mids) are failing
- User's described features (undertone, value, chroma, contrast) don't align with the stated season's profile

Protocol:

1. **Surface the observation gently** — do not declare the user's season wrong; note the pattern. Example: "The colors you're reaching for are consistently warmer and deeper than Soft Autumn's range. That could mean you're using Mode 4 to expand, or it could mean your season reading was slightly off."
2. **Ask clarifying questions** — how was the season determined, what else has felt off.
3. **If evidence accumulates, offer Mode 1** — a fresh full analysis. Do not force it. Some users will want to continue Mode 4 with the stated season; respect that. Do surface the risk that Mode 4 within a wrong season produces compounding misdirection.

---

## Constraints

- **Do not produce a full 36-color palette.** Refinement is surgical. A Mode 4 output is typically 5–15 hex codes plus reasoning, not a comprehensive palette.
- **Do not re-run Phase 3.5 check-in.** The user's season is given. Check-in is for season determination, not refinement.
- **Do not produce a starter capsule.** That belongs to Mode 1 deliverables.
- **Be explicit about confidence.** Borrows carry uncertainty; occasional-use recommendations are less tested than standard palette. Say so.
- **Cite your reasoning.** "This works because X dimension aligns" beats "trust me."

---

## Worked snippet — "Can I wear the deep burgundy that's trending?"

**Scenario:** User is a confirmed Soft Autumn (from prior Mode 1 or professional analysis). She's seen a deep burgundy `#4C0A1F` everywhere this season and wants to know if she can wear it.

**Claude's response:**

> That burgundy `#4C0A1F` sits firmly in Deep Winter territory: very deep value, high saturation, cool-neutral undertone. Your palette's closest natural match is `#704214` (Deep Rust) — which is your Soft Autumn statement color and also warm and muted, not cool and saturated.
>
> **Verdict: Borrowable at distance only, with conditions.**
>
> - **Can't wear it face-framing.** Cool saturation at deep value next to your warm-muted-medium face will drain you. You'll read tired.
> - **Can wear it below the shoulders** — a long skirt, pants, handbag, boots — and it will mostly read as "dark red" at distance, where the cool-warm mismatch is invisible.
> - **Pair it with warm-cream or soft-camel tops** (`#E8DCC4` or `#D2C0A0`) near your face. Those anchor the outfit in your palette, so the burgundy reads as a trendy accent rather than a competing color zone.
> - **Don't pair it with black.** Black drains you on its own; black + cool burgundy doubles down on what doesn't flatter you.
>
> If what's drawing you to burgundy specifically is the "deep red" feel, your palette alternatives are Deep Rust `#704214` or Sienna `#A0522D` at depth. Those are face-framing-safe and produce a similar wardrobe energy without the cool-warm fight.

This snippet illustrates: hex-specific analysis, multi-condition borrow verdict, pairing rules, and on-palette alternative. Follow this structure for Specific Color Check outputs.
