# Post-Delivery Validation Template

Use this template when a user returns after receiving a deliverable and reports that something in the palette isn't working in lived practice. Validation is a structured feedback loop — collect the experience, interpret the pattern, respond with the right kind of adjustment (or surface that a deeper rework is needed).

This workflow is distinct from Mode 2 (closet audit) and Mode 1 (re-analysis). Audit evaluates new items against an established palette; validation responds to lived experience with the palette Claude already delivered.

---

## Trigger phrases

Route to this template when the user says something like:

- "I tried the palette and [X] happened"
- "The [specific color] isn't working for me"
- "I got compliments on [X] but not [Y]"
- "I think you got [dimension] wrong"
- "Can you re-analyze now that I have new info?"
- "Something's off — I followed the palette but I still feel like I look wrong"
- "My stylist/friend/partner said something different"

If the user is asking about a *new* item not in the palette, that's Mode 3 (single-item check), not validation. Route correctly.

---

## Feedback collection structure

Before responding with adjustments, collect the following from the user:

1. **Which specific colors failed.** Hex codes or palette names. "The rust" or "the muted olive" — not "the warm stuff."
2. **Which specific colors worked.** Same specificity. Compliments, self-perception, photo comparisons.
3. **Context when the failure was noticed.** Daylight vs. indoor, work vs. social, photo vs. mirror, alongside what other colors (hair, makeup, nearby clothing).
4. **Whether the failure was about color or about the item.** A color that looks wrong in a poorly-fitting piece may be the *fit*, not the hex. Ask: "Was the sweater itself flattering in silhouette and fit, or was that also off?"
5. **Pattern across failures, if any.** Are the failing colors all from one role (all Mids), one sub-range (all deep), or is it scattered? Pattern is diagnostic.
6. **Timeframe.** Recent pieces (new buys tested against the palette) vs. pieces they'd been wearing for a while that suddenly feel wrong.

Present these as a concise list of questions, not a questionnaire. Keep the exchange conversational.

---

## Decision tree for response

Use the pattern of failures to pick the right response level.

### Level 1 — Minor adjustment (1–2 specific colors failed; rest works)

Common and fixable. Typical cause: specific hex codes at the deep/saturated end of the season range pushed too far for this user's individual within-season position.

- Recommend alternative hex codes within the same season at a more muted or softer value
- Explain *why* those specific colors may have failed — usually slightly higher saturation than the user's within-season ideal, or a color at the border where the adjacent palette would have been a better fit
- Do not change the season determination
- Ask the user to try the substitutes and report back

### Level 2 — Partial season misdiagnosis (category of colors failed)

Example: "All the mids feel off, but neutrals and darks are fine." Signal of a partial reading error — often a chroma or contrast dimension that was slightly mis-read.

- Investigate whether the user may actually be an adjacent season
- Ask targeted questions drawn from `references/checkpoint_questions.md` focused on the suspected dimension (e.g., chroma questions if mid failures cluster around chroma mismatch)
- Do not yet switch the season — collect evidence first
- If evidence accumulates for an adjacent season, offer either a targeted palette adjustment (shift toward the neighbor) or a fresh Mode 1 with new photos

### Level 3 — Full misdiagnosis suspected (most of the palette fails)

Example: "Almost nothing from the palette works." Serious.

- Do not re-analyze from the same evidence that produced the failing result. The photos that led to a wrong answer won't lead to a right one.
- Recommend re-running Mode 1 with fresh photos — ideally in different lighting, with particular attention to the Quality Gate failures that may have slipped through the first time
- Ask whether anything about the original intake was rushed, degraded, or flagged with caveats
- Offer to recommend in-person professional analysis as a higher-accuracy alternative

### Level 4 — Lighting-dependent reports ("works in some lighting, not others")

Often not a palette problem — a lighting problem.

- Address the lighting variable first: natural daylight vs. indoor warm bulbs vs. fluorescent vs. screen
- Explain that the palette was calibrated for natural daylight; indoor bulbs can shift perceived color by a full temperature step
- Recommend the user evaluate pieces in natural daylight before concluding they don't work
- Only if the pattern persists across lighting conditions, move to Level 1 or 2

### Level 5 — Feels-right-but-others-disagree

User reports feeling great in pieces but getting ambivalent or negative feedback from others.

- Validate the user's own experience. Colors that make someone feel good often *are* on-palette; others' feedback is shaped by their own color biases, fashion preferences, and momentary judgment.
- Separate style feedback from color feedback. "That's not flattering" may be about fit or silhouette, not color.
- Only if the user themselves reports mismatched lived experience should you escalate to Level 1–3.

---

## When to recommend in-person consultation

Surface in-person analysis as the better option in any of these cases:

- Recurrent failures despite one round of Level 1 or Level 2 adjustments
- User's confidence in the palette has dropped significantly from the initial session
- High-stakes upcoming event (bridal, major career pivot, public-facing professional transition) where accuracy matters more than cost
- User lives near a certified analyst and can access in-person service
- The original analysis was flagged as Moderate or Low confidence and the user wants to close the uncertainty

Name this explicitly. Don't bury it.

---

## What not to do

- **Do not re-run the full Phase 1–5 protocol inside the walkthrough.** If the situation warrants Mode 1, route to Mode 1 explicitly. Validation is a lighter-weight conversation, not a re-analysis.
- **Do not apologize profusely** for a failed color recommendation. Treat it as information that improves the next iteration. Excessive apology frames the palette as wrong; validation frames it as an adjustable starting point.
- **Do not pressure the user to commit** to palette adjustments on the spot. Offer the information, invite them to test, and leave the conversation at a natural pause rather than demanding a decision.
- **Do not second-guess** a previously delivered analysis just because the user reports one failure. Palette failures are data; they don't automatically invalidate the analysis.

---

## Worked snippet — "The olive worked, the rust didn't"

**Scenario:** A Soft Autumn user returns a week after receiving her deliverable.

**User:**

> I wore the olive sweater you recommended — the one around `#7D8B5A` — and got three compliments. Great. But the rust cardigan in the statement color `#704214` felt off when I tried it. It emphasized the red in my face and I looked flushed, not warm. What gives?

**Claude's response (Level 1 minor adjustment):**

> Good data — that's actually pretty diagnostic. Rust at `#704214` sits at the deeper, more saturated end of your Soft Autumn palette. For you specifically, that saturation level appears slightly too high at the face-framing position.
>
> Two things may be happening:
>
> 1. **You're Soft Autumn closer to the Soft Summer border than to Warm Autumn** — which means the deep-rust statement color is slightly too warm/saturated for you. Colors like muted terracotta `#B5745E` or soft cinnamon `#A06B45` at the mid range may work where the full rust doesn't.
> 2. **Complexion-specific redness amplifier** — if you have any rosacea, recent sun, or broken capillaries, deep warm reds can pull out the red in your face. This is a face-physiology thing, not a palette mismatch per se.
>
> Two alternatives to try:
>
> - Soft cinnamon `#A06B45` — lives at a similar wardrobe role as your rust, lighter and less saturated. More forgiving.
> - Warm caramel `#8B6F47` — already in your palette (Section 3, Mids). Face-framing safe, close in color family to rust without the saturation that's emphasizing your redness.
>
> Try one of those face-framing and tell me whether you get the warm-autumn energy from them without the flushed reading. If both still emphasize redness, we'd want to look at whether your palette should shift slightly toward Soft Summer rather than Warm Autumn — but one color failure isn't enough evidence for that yet.

This snippet demonstrates: hex-specific diagnosis, Level 1 adjustment within the same season, explicit uncertainty about escalation, and an invitation to test without pressure.
