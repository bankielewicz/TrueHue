# Good Photo Examples — Verbal Reference Guide

This reference helps Claude identify whether submitted photos meet the protocol. It's organized by the five required shots plus a device-specific failure section. Claude uses this to (a) evaluate submitted photos and (b) describe specific failure modes when rejecting photos.

Claude should consult this reference during Phase 2 (quality gate) for every submitted photo.

---

## Shot 1: Front-of-face with white paper reference

### What "passing" looks like

- Face fills the middle third of the frame, chin to hairline visible
- Neutral expression, mouth closed but relaxed
- Both eyes open and looking at the camera
- Even illumination across the face — no harsh shadow on one cheek
- Background is plain and neutral (wall, curtain, door) — not a colored wall
- White printer paper held at cheek level, fully visible in frame, in the same light as the face
- The paper reads as close-to-neutral white in the photo (not yellow, blue, or pink)
- Hair pulled back — not a single strand crossing the face
- Shoulders covered in plain white or gray fabric

### Diagnostic checks Claude should perform

- **Sample the paper**: if the white paper appears yellow-tinted, the ambient light was warm (indoor bulb). Skin reading unreliable.
- **Sample the paper**: if it appears blue-tinted, the ambient light was overcast sky through a north window with too cool a cast, OR the camera overcorrected.
- **Check whites of eyes**: in properly lit photos, the sclera reads close to white. If it reads yellow, there's a warm lighting contamination.
- **Check shadow side of face vs. lit side**: the difference should be gentle. Dramatic difference means directional light, not diffuse.

### Common failures

1. **Warm indoor bulb**: paper reads yellow/orange, whole image has an amber cast, face looks deceptively warm. Reject.
2. **Flash fired**: face appears flattened, harsh bright spot on forehead/nose tip, pupils are pinpoint-small, red-eye or retinal reflection visible. Reject.
3. **Backlit**: face is in shadow, background is bright. Skin detail lost. Reject.
4. **Side-lit**: one half of face bright, other half in shadow. Skin reading is only valid on the lit side. Reject.
5. **Makeup on**: foundation is visible as a slight mask around the jawline, eyelashes appear thicker from mascara, lips have more color than natural, brows are filled in. Reject.
6. **Beauty filter on**: pores entirely absent, skin texture plastic-smooth, eyes enlarged relative to face geometry, jawline unnaturally narrow. Reject.
7. **No white paper**: can't calibrate. Request this shot specifically.
8. **Colored shirt visible**: color is bouncing onto the neck/jaw. Reject.

---

## Shot 2: Side profile

### What "passing" looks like

- Face turned 90 degrees (or close) from the camera
- Full profile visible from hairline to chin
- Ear visible and unobstructed by hair
- Same lighting conditions as shot 1 (don't retake just this one in different light)
- Neck clearly visible down to collar area

### Diagnostic checks Claude should perform

- **Jawline undertone**: the side view shows jawline skin that gets less sun than the front of the face. Undertone often reads more honestly here.
- **Behind-ear skin**: even less sun exposure. Look for the undertone there.
- **Neck vs. face comparison**: if face is significantly redder or tanner than neck, face is showing sun damage, not true undertone. Read the neck.

### Common failures

1. Hair covering the ear or jawline
2. Shoulders turned but head still mostly forward (not a true profile)
3. Different lighting than shot 1 (moved between shots)
4. Shadow across the jaw blocking the reading

---

## Shot 3: Eye close-up

### What "passing" looks like

- Both eyes visible, open, looking at camera
- Framed tight enough that the irises are clearly detailed — a viewer can see pigment variation, flecks, rings
- Sharp focus on the eyes specifically
- Natural daylight (not flash, not ring light reflection in the eye)
- No makeup on the eyes

### Diagnostic checks Claude should perform

- **Limbal ring**: is there a dark ring at the outer edge of the iris? Prominence indicates higher contrast coloring.
- **Flecks**: are there spots of different color in the iris? Hazel eyes often have flecks — indicates muted chroma (complex eye color).
- **Central color vs. outer color**: many eyes have different colors radiating from the pupil outward. Note the dominant color.
- **Clarity**: is the iris color decisive (clearly blue, clearly brown) or complex (reads different in different lights)? Decisive = bright chroma indicator. Complex = muted chroma indicator.
- **Sclera color**: should be near-white. Yellowish sclera could indicate warm lighting contamination OR could be a health signal (unrelated to color analysis but worth noting respectfully if pronounced).

### Common failures

1. One or both eyes partially closed
2. Camera flash reflection dominates the iris
3. Out of focus — iris detail not visible
4. Eyes looking away from camera, hiding iris
5. Mascara, liner, or eyeshadow visible
6. Pupils dilated so much from dim light that iris is barely visible

---

## Shot 4: Inner wrist, palm-up

### What "passing" looks like

- Wrist clearly visible, palm facing up
- Natural daylight illumination
- Veins visible enough to read their color
- No wristwatch, bracelet, or tattoo covering the test area
- The person's other hand or arm is not reflecting color onto the wrist

### Diagnostic checks Claude should perform

- **Vein color**: blue/purple = likely cool undertone; green = likely warm; mixed = neutral
- **Skin cast**: if veins aren't easily visible (common in deep skin), read the surrounding skin — does it show peachy/golden warmth, pink/rosy coolness, or olive/balanced neutrality against the white paper?

### IMPORTANT: Reliability caveat

The vein test is most reliable on fair-to-medium skin where veins read clearly. On deeply pigmented skin, veins are often not visible enough to call reliably. In that case, **do not force a vein reading** — rely on the other undertone signals (see `undertone_cross_checks.md`). Explicitly tell the user: "Your vein test wasn't decisive because of natural melanin depth — I'm relying on other cross-checks instead."

### Common failures

1. Veins not visible (normal for deep skin — don't penalize)
2. Lighting too dim to see vein color
3. Wrist too tense, compressing veins
4. Tattoo or birthmark covering the reference area
5. Camera too close, out of focus

---

## Shot 5: Back of hand on white paper

### What "passing" looks like

- Hand laid flat, back of hand facing camera
- Hand fully on a sheet of white printer paper (for reference background)
- Natural daylight
- No rings, bracelets, watch
- Nails unpainted (or if painted, the hand itself is what's being read, so nail polish is tolerable)

### Diagnostic checks Claude should perform

- **Skin vs. paper**: the contrast between skin and pure white paper reveals undertone. Warm skin reads golden/peachy against white. Cool skin reads pink/rosy against white. Neutral reads balanced.
- **Knuckle area**: often shows the clearest undertone reading — less sun, concentrated skin
- **Vein visibility on hand**: often easier to see than wrist, especially on deeper skin
- **Depth check**: this photo also helps establish overall skin depth for Value dimension

### Common failures

1. Paper cream-colored, not pure white (breaks the reference)
2. Hand cropped out of frame
3. Harsh shadow across the hand
4. Bright lamp nearby adding warm cast

---

## Device-specific failures

Modern phones aggressively auto-correct photos, which sabotages color analysis. Claude should ask about device/settings when rejecting for white-balance issues.

### iPhone
- **Smart HDR** (enabled by default on iPhone 12+) blends multiple exposures and subtly adjusts color. Generally not a fatal problem but can shift skin tones.
- **Photographic Styles** (iPhone 13+) applies a persistent color preset (Rich Contrast, Vibrant, Warm, Cool). Must be set to Standard.
- **Portrait mode** applies skin smoothing. Must be off.
- **Night mode** activates in low light and crushes color fidelity. Only shoot in daylight.

### Samsung / Android
- **Scene Optimizer** (Galaxy series) applies automatic enhancement including skin smoothing and saturation boost. Must be off.
- **Beauty filter** (default on selfie camera for many Android brands) is usually aggressive. Must be off.
- **AI Photo** features (increasingly common) modify the image after capture. Must be off.

### Front camera vs. rear camera
- Rear cameras are generally higher quality and less prone to auto-beautification
- If the person is shooting selfies alone, they probably need the front camera. Accept this but be more skeptical of white balance.
- If possible, have a family member or friend take the rear-camera shots.

### Computer/laptop webcam
- Most are low quality and auto-correct aggressively for video call context
- **Reject webcam photos** — quality is insufficient for color analysis

---

## Special guidance

### Sunburn or recent sun exposure

If the user has a current sunburn or heavy recent tan:
- The face photos will NOT reflect their baseline coloring
- Reschedule the analysis for 4-6 weeks after sun exposure ends, OR
- Use the inner arm / inside of upper arm as the skin reference (less sun-exposed area)

### Rosacea, acne, or skin conditions

- Don't let these throw the analysis off
- The undertone exists beneath visible skin conditions
- Cite the user's questionnaire answers more heavily (what colors make them look tired, jewelry test)
- Note respectfully in the confidence section: "I read past the visible redness from your rosacea to assess undertone; if the results feel off, a re-analysis after a flare has calmed may give additional confidence"

### Glasses and contact lenses

- Tinted or prescription-tinted lenses alter apparent eye color — ask the user to remove them for the eye close-up
- Clear prescription glasses can reflect light and wash out eye detail — remove for shot 3
- Colored contact lenses must be noted — Claude analyzes based on natural eye color, not the contact

### Vitiligo, birthmarks, scars

- These do not change the person's underlying color season
- Read the skin in the unaffected areas
- In the deliverable, note if certain face-framing colors might emphasize affected areas and offer alternative placement strategies (accessories, scarves) for coverage if desired

### Age and hair changes

- Grey hair doesn't necessarily shift someone's season, but it does shift their apparent value (lighter overall)
- Someone who was a Deep Autumn with dark brown hair may function better as a Soft Autumn after fully greying — their palette can be adjusted rather than changing their underlying season
- Note this in the deliverable: "As your hair continues to grey, you may find the lighter side of this palette works better."

---

## Overall quality principle

When in doubt between "proceed with analysis" and "request re-shoot":

- If there's ONE fixable issue (wrong lighting in one shot) → request specific re-shoot
- If there are TWO OR MORE issues → request full re-shoot
- If the white paper reference is bad → always request at minimum the front-of-face re-shoot
- If the user expresses frustration with the re-shoot request, acknowledge it, explain the reason briefly, and offer to proceed with stated lower confidence rather than abandoning the session

The goal is rigor, but not at the cost of the user giving up. A Moderate-confidence analysis with clear caveats beats no analysis at all.
