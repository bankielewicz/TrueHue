# Sample Intakes — Quality-Gate Calibration

Textual descriptions of sample intake submissions at different quality levels. Claude can use these as reference points when making quality-gate decisions in Phase 2. Having a calibrated sense of what "textbook clean," "fixable flaw," and "reject" look like reduces inconsistency across sessions.

These samples describe intakes in words only — there are no actual images. The purpose is to anchor quality-gate judgment, not to train on images.

---

## Sample 1 — Textbook clean intake (PASS)

**Context:** A user who read the intake protocol carefully before taking photos.

**Photo submissions:**

- **Shot 1 (front of face):** Taken near a north-facing window on an overcast morning. User is in a medium-gray T-shirt. Hair is pulled back tightly into a low ponytail; ears are visible. No makeup, no lip balm, no visible moisturizer shine. A letter-sized sheet of plain white printer paper is held at the cheek level with one hand; the paper shows as neutral white in the photo (no yellow, blue, or pink cast). Face is evenly lit; no shadow across one side. EXIF shows no flash.
- **Shot 2 (side profile):** Same lighting, same day, same setup. Captures the jawline and ear area clearly. Hair still pulled back.
- **Shot 3 (eyes close-up):** Both eyes open, looking directly at the camera. No glasses. Iris detail is clearly readable — user has hazel eyes with a visible limbal ring and gold flecks. Sharp focus.
- **Shot 4 (inner wrist):** Palm-up, in natural light. Wrist veins are visible and readable as green. Skin depth is fair-medium.
- **Shot 5 (back of hand on white paper):** Hand flat, palm-down, on a letter-sized sheet of white printer paper. Skin-against-paper contrast is readable.
- **Shot 6 (inner forearm — optional, submitted):** Inner forearm flat on white paper; less sun-exposed than face and confirms baseline undertone.
- **Shots 7 and 8 (fabric draping — optional, submitted):** User draped a pure white pillowcase and a cream/ivory pillowcase at the shoulders in the same lighting. Photos capture face response to each.

**Questionnaire:**

All 15+ items answered (original 14 plus 12b, 12c, 13a, 13b, 13c if the intake added them):

- Natural hair: "Dark blonde with golden tones, never dyed."
- Sun response: "Burn first, then tan to light golden. Freckle on nose and shoulders."
- Jewelry: "Gold harmonizes — silver makes skin look slightly grey."
- Fabric draping: "Cream flattered clearly; pure white made me look tired."
- Compliments: Three specific colors named with context.
- Fails: Three specific colors named with context.
- Foundation history: Not applicable (user doesn't wear foundation).
- Eyes: "Hazel, green in sunlight, brown indoors, with gold flecks."
- Veins: "Green on inner wrist."
- Heritage: "Irish and German."
- Current life factors: "None currently."
- Skin variation: "Face and hands slightly darker than inner arm from sun exposure."
- Color vision: "No known issues."
- Context: "Wardrobe planning."
- Lifestyle: "Business casual, four-season climate, 60% business casual / 30% everyday / 10% formal."
- Grooming categories: Specific selections checked.

**Expected Claude quality-gate decision:** PASS. All required photos present and within protocol. White paper reads neutral. No makeup, no filters, no flash. Questionnaire is complete with specific answers. Proceed directly to Phase 3.

**Narrative for calibration:** This is what a submission should look like. No re-shoots needed, high confidence achievable. When you see this pattern, move efficiently to Phase 3 without extra hand-holding. Don't insert unnecessary preamble or disclaimers — the user did the work, honor it by moving forward.

---

## Sample 2 — Fixable single flaw (PARTIAL ACCEPTANCE)

**Context:** A user who mostly followed the protocol but made a single correctable mistake.

**Photo submissions:**

- **Shots 1, 2, 3, 5:** All clean. Natural daylight, no flash, white paper reads neutral, protocol followed. No makeup, hair pulled back.
- **Shot 4 (inner wrist):** The user took this one near a window with a yellow-toned lampshade partially in the light path. The white paper held adjacent to the wrist in this photo reads with a visible yellow cast. Wrist veins still visible, but the undertone signal is contaminated by the lighting.

**Questionnaire:** Fully and specifically answered.

**Expected Claude quality-gate decision:** PARTIAL ACCEPTANCE. Accept Shots 1, 2, 3, 5 and the questionnaire. Request a re-shoot of Shot 4 only, using one of:

- The same window without the yellow lamp in view
- A different window entirely
- Outdoors in open shade

Response should be specific: "Shot 4 has a yellow cast from the lamp in the background. Could you re-shoot just that one photo using a lamp-free window? The other four are fine, don't redo them."

**Narrative for calibration:** This is the most common pattern. The user did most of it right. Reject only the failing photo, preserve the rest. Don't make the user redo the whole session when one re-shoot is enough. Be direct and specific about what failed; don't soften the feedback so much that the user doesn't know exactly what to fix.

---

## Sample 3 — Multiple flaws, full reject (FULL REJECT)

**Context:** A user who submitted quickly without reading the protocol.

**Photo submissions:**

- **Shot 1:** Flash fired (visible catchlight in eyes, hard light on forehead, shadow behind). Face has visible tinted moisturizer and mascara. Taken indoors under mixed lighting (ceiling light + window). No white paper reference.
- **Shot 2 (side profile):** Hair partially covers the jawline. Fine hairs across ear. Background is a red painted wall — color reflecting onto the neck area.
- **Shot 3 (eyes):** Acceptable focus, but eyes have visible eyeliner and mascara.
- **Shot 4 (inner wrist):** Taken under a warm-yellow bathroom bulb. Veins not clearly readable, skin reads yellow-cast against what should be neutral.
- **Shot 5:** Missing entirely — user did not submit this photo.

**Questionnaire:** Several items say "not sure" or are blank:

- Natural hair: "I think dark."
- Sun response: Blank.
- Jewelry: "I like silver."
- Compliments: "People say I look good in lots of stuff."
- Fails: Blank.
- Foundation history: Blank.
- Eyes: "Brown."
- Veins: "I dunno I can't see them."
- Heritage: Blank.
- Dye history: Blank.
- Current life factors: Blank.
- Context: "Just curious."
- Grooming categories: Nothing checked.

**Expected Claude quality-gate decision:** FULL REJECT. Specific feedback for each issue:

1. Shot 1: Flash fired — please re-shoot without flash. Natural daylight, no ceiling lights, no flash.
2. Makeup visible — please re-shoot with no makeup (including tinted moisturizer).
3. No white paper reference in any shot — please hold white printer paper at your cheek in Shot 1.
4. Shot 2: Red wall background is reflecting onto your neck. Please shoot against a plain white, gray, or neutral wall.
5. Shot 4: Bathroom light is yellow. Please take in natural window light.
6. Shot 5 missing — please include hand-on-white-paper photo.
7. Questionnaire needs more specific answers. Particular items to revise: Sun response, jewelry (which makes skin *glow*, not just preference), compliments (specific colors), fails, foundation history (if applicable), heritage.

Resend the full intake after fixes.

**Narrative for calibration:** This user submitted quickly without reading the protocol. Help them understand what's needed — don't just reject, guide. Tone should be direct but not condescending. The request is real work for them, but the alternative (a false-confidence analysis based on bad inputs) is worse. Avoid phrases like "unfortunately" or "I'm sorry" that frame the user's effort as problematic; frame the re-shoot as a normal part of the process.

---

## Sample 4 — Deep-skin intake with appropriate vein-test skip (PASS)

**Context:** A deeply-pigmented-skin user who followed the deep-skin protocol guidance.

**Photo submissions:**

- **Shots 1, 2, 3, 5:** All clean. Natural daylight, no flash, white paper reads neutral. No makeup, hair pulled back. Clear focus. User's skin depth is clearly Fitzpatrick V-VI.
- **Shot 4 (inner wrist):** Palm-up, in natural light. Wrist veins are not clearly visible due to natural melanin depth — a well-understood and expected characteristic for this skin depth. The user noted in the questionnaire: "veins not visible." The photo itself shows clean skin with good lighting and no color cast.
- **Shots 7 and 8 (fabric draping, optional — submitted):** User draped pure white fabric and cream fabric; the cream flattered while pure white made them look slightly grey.

**Questionnaire:**

- Natural hair: Specific description.
- Sun response: "I don't burn; I darken slightly in sustained sun."
- Jewelry: "Gold harmonizes with my skin — I notice silver pulls grey into my face."
- Fabric draping: "Cream definitely flatters; pure white drains."
- Compliments: "Rich mustard blouse, deep forest green dress, burnt orange blazer."
- Fails: "Cool-toned pinks always look off. Pure bright white drains me."
- Foundation history: "Fenty 490 works perfectly. Maybelline 380 oxidizes to grey/orange. Pat McGrath in warm family works; cool family doesn't."
- Eyes: "Deep warm brown with amber undertone."
- Veins: "Not visible."
- Heritage: "West African."
- Current life factors: "None."
- Color vision: "No known issues."
- Context: "Professional wardrobe refresh."

**Expected Claude quality-gate decision:** PASS. Proceed to Phase 3 with the vein test skipped per the deep-skin protocol in `references/undertone_cross_checks.md`. The fabric draping result, jewelry harmony, foundation history, and compliment pattern converge on a strong warm-undertone reading without requiring the vein test.

In Phase 3 output, Claude should:

- Explicitly note: "Vein test skipped per deep-skin protocol — alternative tests converged on warm undertone."
- Cite foundation history prominently as a powerful signal.
- Use the cream-flatters-over-white result as a primary undertone anchor.

**Narrative for calibration:** Correct handling. Vein invisibility is not a defect in the submission — it's an expected characteristic of deep skin, and the alternative undertone signals in this submission are strong. Do not apologize or caveat about the skipped vein test. Do not reduce confidence because of it. Deep-skin analysis is first-class, not second-class; treat it that way.

---

## Using these samples

- **Before your first quality-gate decision in a session**, skim these four samples to calibrate what each decision type looks like.
- **When a submission is borderline**, compare against Sample 2 (fixable) vs. Sample 3 (full reject). The threshold: can a single re-shoot fix it, or are there enough issues that re-shooting piecemeal would be worse than starting over?
- **For deep-skin submissions**, Sample 4 is the calibration — vein invisibility does not degrade the analysis when other signals are present.
- **Do not refer the user to these samples directly.** They're internal calibration for Claude's quality-gate judgment, not part of the user-facing intake experience.
