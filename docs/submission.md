# Submission Prep — Anthropic Plugin Directory

Copy-paste-ready content for the external plugin submission form at
https://clau.de/plugin-directory-submission.

The form fields are inferred from Anthropic's
[plugin directory README](https://github.com/anthropics/claude-plugins-official).
Fill what applies; skip fields the form doesn't ask for.

---

## Basics

| Field | Value |
|---|---|
| **Plugin name** | `true-hue` |
| **Tagline** | Professional-grade personal color analysis for Claude Code. The rigorous kind. |
| **Repository** | https://github.com/bankielewicz/TrueHue |
| **Project site** | https://bankielewicz.github.io/TrueHue/ |
| **Homepage** | https://github.com/bankielewicz/TrueHue |
| **Author name** | Bryan Ankielewicz |
| **Author email** | bryan.ankielewicz@live.com |
| **License** | MIT |
| **Version** | 3.0.0 |
| **Suggested category** | `personal-style` (see "Category fit" note below) |

## Install commands

```
/plugin marketplace add https://github.com/bankielewicz/TrueHue
/plugin install true-hue@truehue-marketplace
```

## Short description (≤ 200 chars)

Rigorous 12-season personal color analysis for Claude Code — five-photo intake, four-dimension analysis with evidence, mandatory check-in, and a full palette with hex codes and starter capsule.

## Longer description

True Hue runs the protocol a certified color analyst runs in a $300–$400 in-person consultation. That means five calibrated photos, a 15+ item questionnaire, and four-dimension analysis (undertone, value, chroma, contrast) with evidence cited from specific photos and answers. Before a season is named, a mandatory mid-analysis check-in catches misreads. After draping comparison against both adjacent seasons, you get the full deliverable: ~36 hex codes by wardrobe role, colors to avoid with reasons, metals, neutrals specifically tailored ("your black," "your white," "your navy"), pattern and fabric guidance, and a shoppable starter capsule at two budget tiers.

The plugin covers four modes — full analysis, closet audit, single-item check, palette refinement — and honors genuine ambiguity with a between-seasons protocol instead of forcing binary verdicts. Deep skin and olive complexions are first-class cases, not afterthoughts. Color-blind users get an opt-in accessible deliverable format. Privacy guidance is presented before photo intake.

## Example use cases

**1. First-time color analysis (core flow).** A user who has never been professionally color-typed takes five photos in natural daylight and fills out the intake questionnaire. True Hue runs the full protocol and delivers their season, a ~36-color palette organized by wardrobe role, avoid colors with reasons, metals, grooming guidance for their selected categories, and a starter capsule at both a ~$500 budget tier and a $1500–$3000+ investment tier. Start-to-finish: ~25 minutes plus photo capture time.

**2. Single-item purchase check.** A user already typed as Bright Winter asks whether a rust-colored cardigan they're about to buy is on palette. True Hue identifies the hex, compares against the Bright Winter palette, and returns a structured verdict: on-palette, conditionally borrowable (and under what conditions — face-framing vs. distance, what to pair it with), or off-palette with a specific hex alternative from the palette that serves the same wardrobe role. Takes 2–5 minutes.

**3. Closet audit against an established season.** A user typed as Soft Autumn a year ago photographs eight sweaters and five pairs of pants from their closet. True Hue evaluates each item individually: which colors are on-palette and where to wear them, which are borrowable at distance (OK for bottoms, not face-framing), and which are off-palette enough to deprioritize or donate.

**4. Palette refinement — adjacent-season borrowing.** A user typed as Deep Winter asks what they can safely borrow from Bright Winter and Cool Winter when a trending color catches their eye. True Hue provides 5–10 borrowable hex codes per neighboring season with explicit conditions (intensity caps, pairing rules, face-framing vs. distance), plus specific colors that are not borrowable even at low intensity.

**5. Between-seasons ambiguity handled honestly.** A user has gotten conflicting results from multiple online quizzes (Soft Summer twice, Soft Autumn once). True Hue runs the full intake protocol and finds the evidence genuinely balanced between the two candidates. Instead of forcing a single verdict, it presents both candidate palettes at reduced size, identifies 3–5 decisive test colors that would distinguish the two, and gives the user a testing protocol to resolve the ambiguity over 1–2 weeks of real wear.

**6. Deep-skin user with no visible veins.** A user with deeply pigmented skin (Fitzpatrick V–VI) submits intake photos. Their wrist photo shows no visible veins — expected and non-degrading on deep skin. True Hue skips the vein test per the deep-skin protocol, leans instead on the white-vs-cream fabric drape, foundation oxidation history ("Fenty 490 works, Maybelline 380 oxidized grey"), and compliment pattern for undertone determination, and notes in the final analysis which tests were used and which were skipped.

## What's different about it

- **Strict quality gate.** Rejects bad inputs (flash artifacts, contaminated white balance, makeup residue, colored backgrounds, missing shots) instead of fabricating results from them. Partial reshoots supported; degraded-mode fallback available with explicit confidence reduction.
- **Mandatory Phase 3.5 check-in.** Before a season is named, the four dimension readings are presented with evidence and two targeted questions drawn from a 23-question library designed to surface disagreement, not confirmation. Evidence-based pushback adjusts the reading. Preference-based pushback does not.
- **Honest confidence reporting.** High / Moderate / Low per dimension and overall. Edge-of-season notes when relevant. Explicit invitation to professional in-person analysis for high-stakes decisions.
- **Between-seasons handling.** When evidence genuinely points to two adjacent seasons with similar weight, the deliverable presents both at reduced size with decisive test colors and a disambiguation protocol rather than a false binary.
- **Inclusive by design.** Deep skin uses alternative tests (fabric draping, foundation behavior, compliment pattern) instead of the unreliable vein test. Olive complexions get their own undertone category. Cultural descriptions list heritage examples across multiple clusters, emphasizing the four dimensions over ethnic features. Color-blind accessibility format opt-in.

## Quality and safety signals

- **Validates clean under skill-creator.** `python -m scripts.quick_validate skills/true-hue` returns `Skill is valid!`
- **Bundled evals.** `skills/true-hue/evals/evals.json` has 6 test cases covering Mode 1 full flow, single-photo refusal, Mode 3 single-item, Mode 4 refinement, between-seasons ambiguity, and deep-skin vein-skip — with verifiable expectations per case.
- **Self-evaluation rubric.** `skills/true-hue/references/self_evaluation_rubric.md` codifies per-section quality criteria Claude applies before sending any deliverable, with specific red flags that trigger rework.
- **No external dependencies at runtime.** Pure markdown + JSON. No MCP servers, no hooks, no shell scripts, no network calls. Optional sibling-skill invocation (PDF generation, frontend-design for wallpaper PNGs) has documented fallbacks for environments where those skills aren't installed.
- **Privacy-aware.** Intake template includes a privacy section covering what Claude does with photos, how to minimize identifying information, and how to proceed if a user is uncomfortable submitting photos at all.
- **Licensed MIT.** Permissive. Forkable. Extendable.
- **No brand endorsements or affiliate content.** Brand names appear only where they convey functional capability (deep-skin foundation ranges like Fenty 490 and Pat McGrath's deeper lines, which have documented deep-skin shade range). No retailer links, no promotional language, no trend-chasing.

## Technical characteristics

| Attribute | Value |
|---|---|
| Plugin type | Skill-only (no commands, agents, hooks, MCP) |
| Files | SKILL.md + 8 templates + 10 reference docs + evals.json |
| Total content | ~4,100 lines of markdown + JSON |
| Network calls | None |
| File system writes | None (except user-opt-in PDF generation via sibling skill) |
| External services | None |
| User data handled | Photos and questionnaire responses in-session; subject to Anthropic's standard retention |

## Links to include in the review

Use absolute URLs when pasting into form fields:

- https://github.com/bankielewicz/TrueHue — repository
- https://bankielewicz.github.io/TrueHue/ — live project site
- https://github.com/bankielewicz/TrueHue/blob/main/README.md — user-facing overview and install
- https://github.com/bankielewicz/TrueHue/blob/main/docs/getting-started.md — turn-by-turn walkthrough of a first session
- https://github.com/bankielewicz/TrueHue/blob/main/docs/modes.md — the four workflows
- https://github.com/bankielewicz/TrueHue/blob/main/docs/faq.md — privacy, deep skin, color blindness, validation, quiz-app comparisons
- https://github.com/bankielewicz/TrueHue/blob/main/docs/v3-spec.md — full build specification (shows design rigor)
- https://github.com/bankielewicz/TrueHue/blob/main/skills/true-hue/SKILL.md — the skill itself
- https://github.com/bankielewicz/TrueHue/blob/main/skills/true-hue/evals/evals.json — test cases

## Category fit — honest note for reviewers

Every external plugin currently in the directory is a developer tool (LSPs, linters, framework helpers) or a service integration (GitHub, Linear, Asana, Discord, Firebase, etc.). True Hue is neither — it's a consumer/content plugin for personal color analysis, a category the directory hasn't covered yet.

The case for inclusion anyway: Claude Code users are the directory's audience, and a subset of them have the exact problem this solves — they've taken quiz-app color analyses and gotten hollow results, they've priced in-person consultations at $300–$400 and balked, and they'd genuinely benefit from a rigorous analysis they can run in their terminal. The plugin meets the technical bar (validates clean, no runtime dependencies, MIT-licensed) and carries none of the red flags (no network calls, no MCP, no hooks executing arbitrary code). It's also a demonstration of what skill-only plugins can do when the subject matter is craft-intensive and the content is the product.

If the right answer is "this belongs in a different category we haven't created yet" — happy to be the first entry in it.

## One-liner for the form's "Why should this be in the directory?" box

True Hue demonstrates that skill-only plugins can deliver serious craft-intensive consumer value without any runtime dependencies — it runs a complete 12-season color analysis protocol that matches the design rigor of a professional in-person consultation, and it's the kind of use case most Claude Code users don't realize the platform is capable of until they see it shipped.
