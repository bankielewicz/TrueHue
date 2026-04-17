# Modes — When to Use Which

True Hue has four distinct workflows. Claude picks the right one automatically from your opening message, but if you want to understand what you're getting routed to — or route yourself explicitly — this is the reference.

## Mode 1 — Full Analysis

**Use when:** You've never been professionally typed, or you want a fresh read from scratch.

**What it does:** Runs the complete protocol end-to-end. Photo intake, quality gate, four-dimension analysis with evidence citations, mandatory Phase 3.5 check-in, adjacent-season draping, full deliverable with 36-color palette, avoid list, metals, neutrals, grooming sections (tailored to your selections), starter capsule, confidence notes. Optional PDF swatch cards. Optional post-delivery walkthrough.

**Time:** 20–30 minutes of back-and-forth, plus the 10–15 minutes to take photos and fill out the questionnaire.

**Trigger phrases that route here:**

- "Can you do a full color analysis?"
- "What's my color season?"
- "I want to find out my seasonal palette."
- "Help me figure out what colors suit me."

**What to expect:** The long form. No shortcuts. If your photos aren't good enough you'll reshoot. If your evidence is ambiguous you'll get an honest "between two seasons" with a testing protocol rather than a forced answer.

---

## Mode 2 — Closet Audit

**Use when:** You know your season (from a prior professional analysis, a prior Mode 1 with this plugin, or confident self-knowledge) and you want multiple items from your wardrobe evaluated against your palette.

**What it does:** Skips the full intake. Takes your stated season as given. Evaluates each item you submit (photos or descriptions) against the palette — on-palette, borrowable, off-palette — with hex comparisons and placement recommendations (keep, donate, wear only at distance, etc.).

**Time:** 5–15 minutes depending on how many items.

**Trigger phrases that route here:**

- "I'm a Soft Autumn. Can you audit some items from my closet?"
- "I'm a Deep Winter, here are 10 things I own — what's on palette and what isn't?"
- "Help me decide what to keep from my wardrobe."

**What to expect:** Claude will ask how you were typed (professional vs. prior Mode 1 vs. self-identified) to calibrate confidence, then ask for the items. The audit format is consistent per item: the hex code closest to what you submitted, the verdict, and the reasoning tied to your palette's character.

**Note:** If your typing was from an online quiz you don't fully trust, Claude may suggest running Mode 1 first to verify before auditing a whole closet against a potentially wrong season.

---

## Mode 3 — Single Item Check

**Use when:** You have one specific item — a sweater, a suit, a tie, a bag — and you want a quick yes/no with reasoning.

**What it does:** Same as Mode 2 but for one item. Faster, tighter. Verdict + hex comparison + where it fits in your palette (or where it fails).

**Time:** 2–5 minutes.

**Trigger phrases that route here:**

- "I'm a Cool Winter. Is this dress on my palette?"
- "Quick check — does this tie work for a Soft Autumn?"
- "Would this color work for me? [hex / photo]"

**What to expect:** Claude will confirm your season and ask for the item (photo or hex). The response is direct: on-palette / borrowable with conditions / off-palette, with one or two sentences of reasoning. If borrowable, specific conditions (face-framing vs. distance, pairing rules). If off-palette, a nearby palette-hex substitute that plays the same wardrobe role.

---

## Mode 4 — Palette Refinement

**Use when:** You're confident about your season and you want to push the edges. Adjacent-season borrowing. Checking whether a trending color works for you. Figuring out how to handle a new context (tropical vacation, formal wedding, career pivot) with your palette.

**What it does:** Treats your season as given. Does surgical analysis, not a full re-read. Three sub-modes:

- **Adjacent-season borrowing.** "I'm a Soft Autumn — what can I borrow from Warm Autumn?" Output: 5–10 specific hex codes from each neighboring season with borrowability ratings, intensity conditions, and pairing rules.
- **Specific color check.** "Can I wear this trending deep burgundy?" Output: hex evaluation, classification, conditions if borrowable, nearby palette alternatives if not.
- **Palette expansion for an occasion.** "I'm going to Greece in July — which part of my palette works best?" Output: role emphasis, which palette colors to favor, which adjacent-season colors to borrow for the context, which palette colors to leave home.

**Time:** 5–15 minutes.

**Trigger phrases that route here:**

- "I'm a Deep Winter — can I wear emerald green?"
- "I'm a Soft Autumn. What can I safely borrow from Warm Autumn?"
- "I keep seeing Cool Summer colors I love. How much can I push my palette?"
- "I'm a Bright Spring and I'm going to a winter wedding. What should I wear?"

**What to expect:** No full 36-color palette. No starter capsule. No Phase 3.5 check-in (your season is given, not being determined). Just targeted output with specific hex codes and reasoning for the question you asked.

**Edge case:** If you're using Mode 4 and your requests consistently push in a direction that suggests your stated season might actually be wrong — the pattern accumulates across multiple asks, not just one — Claude will gently surface the observation and offer Mode 1 as a reset. Not forced. Your call.

---

## How Claude decides

The router looks at your opening message for clear signals:

- No prior typing, full analysis requested → Mode 1
- Stated season + multiple item evaluations → Mode 2
- Stated season + single item question → Mode 3
- Stated season + border question, borrowing, occasion, or specific color in/out → Mode 4
- Ambiguous → one follow-up question, not a forced choice

If you want to override — say so explicitly. "Skip the setup questions, I want a full analysis" and Claude will proceed. "I want Mode 4, not Mode 1" works too.

## What doesn't fit in any mode

Post-delivery validation — when you've completed a Mode 1 analysis, worn some of the palette, and something isn't working — isn't one of the four modes. It's a separate follow-up workflow. Just come back, tell Claude what happened and which specific colors failed, and the [validation workflow](../skills/true-hue/assets/validation_followup_template.md) kicks in. It might result in a small palette adjustment, a partial reconsideration, or a full Mode 1 rerun with fresh photos — depends on the pattern of what failed.
