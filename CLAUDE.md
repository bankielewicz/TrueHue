# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

This is the source repository for **True Hue**, a Claude Code plugin that performs professional-grade 12-season personal color analysis. It's published at https://github.com/bankielewicz/TrueHue.

The repo root *is* the plugin root — no `src/` wrapping. Layout:

```
.claude-plugin/
├── plugin.json            (plugin manifest; name=true-hue, v3.0.0, MIT)
└── marketplace.json       (single-plugin marketplace index)
skills/
└── true-hue/              (the skill itself — SKILL.md + assets + references + evals)
    ├── SKILL.md
    ├── assets/            (8 templates)
    ├── references/        (10 reference docs)
    └── evals/evals.json   (ships in source; runtime ignores)
docs/
├── v3-plan.md             (human-reviewable plan for the v3 build)
├── v3-spec.md             (AI-executable spec used to build v3)
└── (user-facing guides: getting-started.md, modes.md, faq.md, ...)
dist/
├── true-hue-v2.skill      (historical v2 skill-creator archive)
└── true-hue-v3.skill      (v3 skill-creator archive)
README.md
LICENSE                    (MIT)
```

## Working on the skill

All skill content lives under `skills/true-hue/`. Edits go there directly — there's no parallel workspace to sync.

Validate with skill-creator:

```
cd ~/.claude/plugins/marketplaces/claude-plugins-official/plugins/skill-creator/skills/skill-creator
python3 -m scripts.quick_validate /mnt/c/Projects/TrueHue/skills/true-hue
```

Expected: `Skill is valid!`

Re-package a `.skill` ZIP if needed:

```
python3 -m scripts.package_skill /mnt/c/Projects/TrueHue/skills/true-hue
```

The output goes to the packager's cwd — copy it to `dist/` with an appropriate name if you want to archive it.

## Installing the plugin locally

From this working directory:

```
/plugin marketplace add /mnt/c/Projects/TrueHue
/plugin install true-hue@truehue-marketplace
```

Public install (once a release tag exists):

```
/plugin marketplace add https://github.com/bankielewicz/TrueHue
/plugin install true-hue@truehue-marketplace
```

## Cross-cutting constraints

These invariants apply to every content change inside `skills/true-hue/`:

- `SKILL.md` frontmatter `description:` field stays under **1024 characters**. Verify: `awk '/^description:/ {print length($0)}' skills/true-hue/SKILL.md`.
- No development markers: `grep -rn "NEW:\|TODO\|FIXME" skills/true-hue/` must return zero. (`XXX` hits the `#XXXXXX` hex placeholders in `deliverable_template.md` — exclude it from the check.)
- Season naming standardizes on **Deep** (not Dark) and **Warm/Cool** (not True). Variants are acknowledged in the disclaimer at the top of `references/twelve_seasons.md`. Keep consistent with `references/palette_library.md`.
- No orphan references: every path mentioned inside `SKILL.md` or a reference doc must resolve. Every file in `assets/`, `references/`, `evals/` should be reachable from `SKILL.md` directly or transitively.
- No new brand or retailer names beyond the deep-skin foundation brands already in `assets/deliverable_template.md`.

## History and build record

`docs/v3-plan.md` and `docs/v3-spec.md` are the build record for the v3 rewrite. v3 introduced Phase 0 consultation prep, Phase 7 delivery walkthrough, Phase 3.5 question library, between-seasons protocol, color-blind accessibility, inclusive heritage descriptions, solo-photographer protocols, lifestyle/climate intake, pattern and fabric guidance, post-delivery validation workflow, evals, self-evaluation rubric, and sample intakes for quality-gate calibration. Total scope was 22 tasks across 4 tiers; the spec in `docs/v3-spec.md` has the full execution record.

Future major changes should follow the same pattern: human-reviewable plan in `docs/`, AI-executable spec alongside it, and final report summarizing deviations and resolutions.

## Path conventions

Paths in this repo use forward slashes. The working directory on the author's machine is `/mnt/c/Projects/TrueHue/` (WSL view of `c:\Projects\TrueHue\`).
