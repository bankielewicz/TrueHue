# FAQ

## Is this actually different from the free color analysis quizzes online?

Yes, and the difference shows up in two places.

First, the input requirements. Free quizzes typically take one selfie in whatever light you happened to be standing in, or ask you to pick your eye color from a grid and your hair color from another grid. That's not enough data to determine your season reliably, and the math those tools do on it is shallow. True Hue requires five calibrated photos in natural daylight, a 15+ item questionnaire, and — for a lot of people — a fabric draping test. It then works through four dimensions separately before concluding anything, with evidence cited at every step.

Second, the handling of ambiguity. Free quizzes always return a single season answer in under ten seconds, because a no-answer or "ambiguous" result doesn't feel like a product. True Hue will reject your inputs if they aren't good enough, state confidence levels honestly, acknowledge when evidence points genuinely between two seasons, and tell you when an in-person consultation would produce a better result than it can.

The honest comparison: a free quiz and True Hue are solving different problems. The quiz is entertainment. True Hue is trying to produce something useful you can shop from.

## How long does this actually take?

Budget 20–30 minutes for your first Mode 1 analysis. That's roughly 10–15 minutes for photos and questionnaire, plus 10–15 minutes of back-and-forth with Claude. Mode 2 (closet audit) is 5–15 minutes. Mode 3 (single item) is 2–5 minutes. Mode 4 (refinement) is 5–15 minutes.

If you hit a quality-gate reshoot or Phase 3.5 pushback exchange, add 5–10 minutes.

## Can I skip the photos?

You can. Quality will drop meaningfully. If you're genuinely uncomfortable submitting photos — some people are, for privacy reasons — say so at the start of the conversation. The analysis can run on the questionnaire alone, with explicit confidence reduction, and Claude will flag it as lower-accuracy.

The reason photos matter: there are specific signals (skin cast against white paper, vein color, eye clarity, feature value spread) that simply aren't accessible through verbal description. Losing them isn't fatal but it widens the uncertainty band.

## What about deep skin? The old Sci\ART tests don't work for me.

They mostly don't, and True Hue knows this. The vein test gets skipped (veins aren't reliably visible on Fitzpatrick V-VI skin), and the sun-response test gets de-weighted (deep skin doesn't burn in the same discriminating way). The undertone read leans instead on the white vs. cream fabric drape, foundation oxidation behavior, compliment pattern, and jewelry harmony — all of which work across skin depths.

Deep skin is first-class in the deliverable too. Brand recommendations for foundation include ranges that actually cover deep skin (Fenty, Pat McGrath, Make Up For Ever, Danessa Myricks). Blush recommendations explicitly note that saturation needs to be higher on deep skin to read visibly. The protocols and edge-case handling are built in, not retrofitted.

If the plugin ever feels like it's treating deep skin as an afterthought, file an issue. That would be a bug.

## What about olive complexions?

Olive is its own chapter. It's neither cleanly warm nor cleanly cool, and a lot of analysis systems miss it entirely or force it into a warm/cool binary. True Hue treats olive as a distinct undertone category — acknowledging that olive sits on top of a warm, cool, or neutral base — and gives palette adjustments specific to olive (favor greyed-down versions of palette colors, avoid pure pinks and pure yellows which emphasize the green cast, prefer palette-harmonized greens over clear bright greens).

Olive most commonly maps to Soft Summer, Soft Autumn, Deep Autumn, or Deep Winter, though it can appear elsewhere. The analysis will state your base underneath the olive cast and calibrate accordingly.

## Is my photo data safe? What happens to my pictures?

The intake template has a "Privacy notes" section that covers this specifically. The short version:

- Photos you submit are part of the chat session. When the conversation is deleted, they no longer persist to future sessions.
- Anthropic does not use chat content (including images) for training by default. Current policy is published by Anthropic.
- You can delete the conversation from your chat history at any time.
- Anything you screenshot and share outside Claude is outside Claude's and Anthropic's privacy controls.

You can also crop photos tightly to show only the face/skin area and avoid identifying backgrounds, jewelry, clothing logos, or name tags. That doesn't reduce analysis quality.

This is accurate for Anthropic's direct products (claude.ai, Claude Code). Third-party developer applications built on the Claude API may have different policies — so if you're using a Claude-powered app built by someone else, check their policies separately.

## I'm colorblind. Can I use this?

Yes. The intake questionnaire asks about color vision deficiency. If you indicate deuteranopia, protanopia, tritanopia, monochromacy, or general color confusion, the deliverable includes a color-blind accessible format — standardized color names, value tiers, saturation levels, and hex codes for reference — plus a section flagging palette pairs that may appear similar to you under your specific type of deficiency. You get practical shopping strategies too (rely on retailer app labels and descriptions, trust your lived compliment/fail memory over on-screen color, ask for help distinguishing near-neighbor colors in stores).

Color analysis is especially valuable to color-blind users, who often rely on others for clothing selection. The deliverable format shouldn't exclude you, and this one doesn't.

## What if I think Claude got it wrong?

The Phase 3.5 check-in is specifically designed to catch this before a season gets named. If something feels off in Claude's four-dimension reading — either the conclusion or the evidence cited — say so specifically. Evidence-based pushback ("the rust I said worked is actually more of a burnt orange with brown in it") will adjust the reading. Preference-based pushback ("I want to be a Spring") won't, and that's intentional.

If you get the full deliverable and only later discover it's not working — you've worn some of the palette and certain colors are failing — come back and say so. The [validation workflow](../skills/true-hue/assets/validation_followup_template.md) handles this. Possibilities: minor palette adjustment within the same season (most common), partial reconsideration of a specific dimension reading, or full Mode 1 rerun with fresh photos (rare but sometimes correct).

One thing that won't happen: Claude profusely apologizing and immediately flipping your season. Color failures are data; they don't automatically invalidate the analysis. Adjustments are made carefully, with evidence.

## Can I get this in a language other than English?

v3 is English-only. If non-English support matters to you, file an issue.

## How do I update the plugin when a new version drops?

```
/plugin update true-hue
```

The skill's internal version gets bumped in the frontmatter and in plugin.json.

## I have a suggestion / I found a bug / the output was bad for my case.

File an issue at [github.com/bankielewicz/TrueHue/issues](https://github.com/bankielewicz/TrueHue/issues). Bad-output reports are especially welcome — reference-case material helps future versions improve. Specifics beat generalities; if possible, include what you submitted (minus identifying photos), what you got back, and why it felt wrong.

## Why is this plugin licensed MIT instead of something more restrictive?

Because I want people to use it, extend it, fork it, and build things with it. The skill-creator framework is permissive. Seasonal color analysis is a craft worth democratizing rather than gatekeeping. If you do commercial work based on this, credit is nice but not required.
