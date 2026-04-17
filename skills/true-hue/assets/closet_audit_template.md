# Closet Audit Workflow (Mode 2)

Use this workflow when the user already knows their season and wants items from their current wardrobe evaluated. Do NOT run the full analysis — the user has already had one.

---

## When to use Mode 2

Trigger phrases:
- "I'm a Soft Autumn — can you tell me if this sweater works?"
- "Here are some items from my closet — which are on-palette?"
- "I want to clean out my wardrobe — what should I keep?"
- "Is this color from my palette?"

If the user has NOT been typed yet, direct them to Mode 1 (full analysis) first. If they mention a season but aren't sure, clarify: "Did you get this typing from a professional analysis, a self-test, or a guess? The confidence of your audit depends on the confidence of the typing."

---

## Batch size — ask the user

Before proceeding, ask:

> "How would you like to handle your items? I can evaluate them in a batch (send me photos of multiple items at once and I'll produce a table) or one at a time (each item gets its own detailed assessment). Batch is more efficient; one-at-a-time lets us go deeper on each."
>
> For batch mode, I can handle up to [X] items in one pass. Past that, we'll need to split into multiple batches.

Give the user a realistic batch ceiling. In practice:
- Up to 10 items: comfortable single batch
- 10-20 items: possible but detail per item will be shorter
- 20+ items: recommend splitting into batches of 10-15

---

## Photo requirements for items

### For each item, user should provide:

- Item laid flat or on a plain neutral background
- Natural daylight
- Item occupies most of the frame
- For multi-color items: photos from multiple angles showing all colors
- Label the photo by number if batching (Item 1, Item 2, etc.)

### What makes an item photo unusable:

- Colored background that reflects onto the item
- Harsh shadow obscuring part of the color
- Flash creating a shine spot
- Filter applied
- Item worn on a body under poor lighting (color will be misread)
- Low resolution or blurry

If items are submitted with bad photos, request re-shoots for those specific items.

---

## Evaluation framework per item

For each item, assess:

1. **Dominant color hex** — Claude estimates the primary color as a hex code
2. **Palette match** — compare against the user's season palette:
   - **On palette**: within the hex range of the user's palette (ideal)
   - **Adjacent-borrowable**: in a neighboring season's palette that the user can borrow from (wearable)
   - **Off-palette**: outside their palette (not ideal but may work for non-face-framing)
   - **Clashing**: actively fights their coloring (donate/reconsider)
3. **Role**: what wardrobe role does this item fill (neutral, mid, dark, accent, statement)?
4. **Placement**: is this best face-framing, or better as a bottom/accessory?
5. **Verdict + reasoning**: keep, keep-with-caveat, consider-donating

---

## Output format for batch mode

Produce a table like this:

```markdown
# Closet Audit — [User's Season]

## Summary
- **Total items reviewed:** 12
- **Keep, on-palette:** 7
- **Keep, borrow from adjacent:** 2
- **Reconsider or donate:** 3

## Item-by-item

| # | Item | Dominant Color | Match | Role | Verdict |
|---|---|---|---|---|---|
| 1 | Olive sweater | #7D8B5A | On palette | Mid/face-framing | KEEP — this is a signature color for you |
| 2 | Navy blazer | #2C3E50 | Clash | — | RECONSIDER — too cool and blue-based for Soft Autumn; consider a warm brown or deep moss alternative |
| 3 | Cream blouse | #F0E6D2 | On palette | Neutral/light | KEEP — your ideal "white" substitute |
| 4 | ... | | | | |

## Keep with adjustments
- **Item 5 (mustard dress)**: on-palette but at higher saturation than typical for you; best for special occasions when you want more energy, not everyday
- **Item 8 (rust cardigan)**: borrowed from Warm Autumn, slightly stronger than your ideal — wear with softer colors around the face to balance

## Recommend donating
- **Item 2 (navy blazer)**: fundamentally wrong temperature for your season
- **Item 9 (hot pink scarf)**: cool and saturated, fights on both axes
- **Item 11 (pure black turtleneck)**: too harsh near your face at low contrast

## Gaps to fill
Based on what you kept, here's what's missing from your core palette:
- A warm taupe or mushroom neutral (for pants/bottoms)
- A medium warm brown (for outerwear)
- A face-framing statement piece in deep rust or sage

I can make specific suggestions if you want to use this for targeted shopping.
```

---

## Output format for one-at-a-time mode

For each item:

```markdown
## Item [N]: [Brief description]

**Photo analysis:** The dominant color reads as approximately `#HEXCODE`. [If multi-color: secondary color is `#HEXCODE`.]

**Palette comparison:** 
- Against your Soft Autumn palette: [on-palette / adjacent / off-palette / clashing]
- Closest palette match: `#HEXCODE` ([color name])
- Distance from palette (qualitative): very close / moderate / far

**Why this works / doesn't work:**
[2-3 sentences of reasoning specific to the item]

**Wardrobe role:** [neutral / mid / dark / accent / statement]

**Placement recommendation:** 
- Face-framing: [yes / with caveats / better as non-face-framing]
- Best pairings: [specific palette colors to pair with]

**Verdict:** KEEP / KEEP WITH CAVEATS / CONSIDER DONATING

[One-sentence actionable summary]
```

---

## Edge cases

### Patterned items (prints, plaids, florals)

- Identify each dominant color in the pattern
- An item passes if the dominant and secondary colors are both on-palette
- If one dominant color clashes and others are fine, verdict depends on how visually dominant the clashing color is

### Items the user feels emotionally attached to

- If the user says "I love this dress — please tell me it works," be honest but kind
- If it doesn't work: "This color fights your palette in [specific way]. You'll likely find it makes you look tired in photos. Options: wear it for occasions where color is less important (night out, dim restaurants), pair it with a scarf in your palette near your face to balance, or retire it."
- Don't pretend something clashes doesn't.

### Monochrome/neutral items that seem "safe"

- Grey, black, navy, white, beige — these all have seasonal temperature readings
- "Safe" neutral items often have the wrong temperature for the user
- Example: a classic-looking charcoal suit might be fine for Deep Winter but too cool for Warm Autumn, where warm charcoal or deep brown would work better

### User wants to re-evaluate something Claude previously rejected

- If they push back with new information ("I actually got compliments in that navy dress"), consider whether the original reading was wrong or whether the compliments were about fit/style rather than color
- Don't reverse verdict just because user disagrees, but adjust if new evidence warrants it

---

## What NOT to do in audit mode

- Don't re-analyze the user's season. They already have one.
- Don't produce a full 30-40 color palette. They already have one.
- Don't ask the intake questionnaire. They already went through it.
- Don't include makeup/grooming advice. Audit is about wardrobe items.

If the user seems to actually want a full re-analysis (says things like "maybe I'm not really a Soft Autumn after all"), ask directly: "Would you like me to run a fresh analysis, or continue auditing items under your current typing?"
