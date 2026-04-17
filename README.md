# True Hue

**Personal color analysis for Claude Code. The rigorous kind.**

Most online color analysis tools will hand you a season from one bad selfie in kitchen light. This plugin won't. It runs the same protocol a certified analyst runs when you pay $300–$400 for an in-person consultation: five calibrated photos, a thorough intake questionnaire, four-dimension analysis with citations, a mandatory check-in before anything gets finalized, and draping against both adjacent seasons. If your inputs aren't good enough, you'll get a reshoot request. If the evidence is genuinely ambiguous, you'll get an honest "you're between two seasons" instead of a forced verdict.

Plan on 20–30 minutes. What you get back is a palette of ~36 hex codes organized by wardrobe role, colors to avoid with specific reasons each one fails, metals, neutrals tailored to your coloring ("your black," "your white," "your navy"), pattern and fabric guidance, and a shoppable starter capsule at two budget tiers. Plus grooming sections — eyewear, watches, hair color, facial hair, ties, makeup — that match exactly what you selected in the intake. None of the things you didn't.

## Install

In Claude Code:

```
/plugin marketplace add https://github.com/bankielewicz/TrueHue
/plugin install true-hue@truehue-marketplace
```

That's it. The next time you ask Claude about color analysis, the skill takes over.

## Your first session

Tell Claude what you want. Anything like this works:

> "Can you walk me through a full personal color analysis?"

Claude opens with a couple of setup questions — have you been typed before, what's driving this, how much time do you have — and routes you to the right workflow. For a first-timer, that's the full Mode 1 protocol.

You'll need a few things ready:

- **Natural indirect daylight.** A north-facing window is ideal. An overcast day works. Midday but out of direct sun is fine. Lamps and ring lights don't work — they shift color dramatically.
- **A sheet of plain white printer paper.** Not cream, not off-white. It gets held at your cheek as a white balance reference.
- **A plain white or medium-gray top.** Or a neutral towel draped over your shoulders.
- **Bare skin.** No makeup, no tinted moisturizer, no lip balm with color.
- **Hair pulled back.** Off the face, ears, neck.
- **Your phone.** Any recent model. Rear camera is better than front.

If you're photographing yourself without a second person, Claude will show you four solo-photographer workarounds. Taping the paper to a mirror and using the rear camera is the one that usually wins.

After you submit, Claude runs a quality gate on the photos (rejecting anything with flash artifacts, makeup residue, bad lighting, or a contaminated paper reference), analyzes four dimensions separately — undertone, value, chroma, contrast — with evidence cited from specific photos and questionnaire items, then presents the readings and asks two targeted questions to catch anything that might be misread. You can push back. If there's genuine evidence the reading is off, Claude adjusts. If it's preference-based pushback ("I want to be a Spring"), Claude holds the analytical line and explains why.

Only after the check-in does a season get named. Then a draping comparison — why you're not the two neighboring seasons — then the full deliverable.

## Modes

**Mode 1 — Full analysis.** You've never been typed, or you want a fresh read from scratch. The default if you haven't been typed before.

**Mode 2 — Closet audit.** You know your season and you want multiple wardrobe items evaluated against it.

**Mode 3 — Single item check.** "I'm a Soft Autumn. Is this sweater on my palette?" Quick verdict with reasoning.

**Mode 4 — Palette refinement.** You're typed and want to know what you can safely borrow from neighboring seasons, or whether a specific trending color fits your palette.

Claude routes you automatically based on your opening message. The long version is in [docs/modes.md](docs/modes.md).

## What a deliverable actually contains

Every analysis includes, at minimum:

- Your season and confidence level (High / Moderate / Low — stated honestly)
- Four-dimension analysis with photo and questionnaire citations
- "Why not *[neighbor 1]*" and "Why not *[neighbor 2]*" reasoning
- ~36 hex codes organized into Neutrals, Lights, Mids, Darks, Accents, Statement
- Within-palette color pairing rules (what to pair with what for safe and high-impact outfits)
- Fabric sheen and weight guidance tied to your specific chroma and value readings
- Pattern and print recommendations based on your contrast level
- 8–12 colors to avoid, each with a specific reason it fails against your coloring
- Metals: primary, secondary, what to avoid near the face
- Your neutrals specifically — what plays the role of "black" for you, "white," "navy," "grey," "beige," "denim"
- Conditional grooming sections — included only if you selected the category
- A 10-item starter capsule at both a ~$500 budget tier and a $1500–$3000+ investment tier, with a six-month phased shopping order
- Confidence and caveats — edge-of-season notes, what could change the result, photo-based-analysis limitations, follow-up options

Optionally, Claude can generate PDF swatch cards — full-page reference, pocketable wallet card, or phone wallpaper — for shopping on the go.

## Deeper reading

- [docs/getting-started.md](docs/getting-started.md) — an annotated walkthrough of a first session with a sample exchange
- [docs/modes.md](docs/modes.md) — when to use each of the four modes, with examples
- [docs/faq.md](docs/faq.md) — common questions (can I skip photos, what about deep skin, how is this different from a quiz app, is my data safe)
- [docs/v3-plan.md](docs/v3-plan.md) — what changed in v3 and why
- [docs/v3-spec.md](docs/v3-spec.md) — the full build specification

## Before you start

A few honest caveats:

- **Photo-based analysis carries real uncertainty.** Somewhere around 15–20% of what you'd get from an in-person session with physical fabric draping is lost when we work from photos. The plugin reports confidence levels for exactly this reason. If you're making a high-stakes decision — bridal, a major wardrobe overhaul, a career pivot that hinges on personal brand — a real analyst for an hour is worth the money.
- **Bad photos produce bad analysis.** The plugin is strict at the quality gate because cheap tools aren't, and the results show. Expect to reshoot at least one photo on your first attempt. It's normal.
- **Deep skin gets first-class treatment.** The vein test is skipped (it's unreliable on highly pigmented skin), and the undertone read leans on fabric draping, foundation behavior, and compliment memory instead. No second-class workflow.

## About

True Hue exists because the mainstream AI color analysis apps hand out seasons like fortune cookies. Seasonal color analysis is a real craft — analysts spend years getting good at it — and a sixty-second quiz from one selfie doesn't get near the real thing. This plugin takes the process seriously: it rejects bad inputs, cites its evidence, handles edge cases (between seasons, olive complexions, sun damage, color blindness) as first-class concerns, and is honest about what it can and can't do.

Built on Anthropic's skill-creator framework. Licensed MIT. Issues, corrections, and reports of bad outputs all welcome at [github.com/bankielewicz/TrueHue/issues](https://github.com/bankielewicz/TrueHue/issues).

## Support

If True Hue saved you a $350 consultation fee, or just gave you the first palette that actually works for you, you can [buy me a coffee](https://buymeacoffee.com/devforgeai). Zero obligation — the plugin is MIT and free forever. It's just appreciated.
