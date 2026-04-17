# Privacy Policy — True Hue

**Effective date:** April 17, 2026

True Hue is an open-source Claude Code plugin maintained by Bryan Ankielewicz. The plugin is content — markdown files and JSON — shipped as a Claude Code skill. It has no backend, no servers, no databases, and nothing that phones home. This document describes the very short privacy story.

## What the plugin is

The repository at https://github.com/bankielewicz/TrueHue contains the skill files, a static promo site, and documentation. That's the whole thing. There is no hosted service, no API, no login system, no account. Installing the plugin brings those files into your Claude Code environment. Using the plugin means Claude reads them at the appropriate moments during your conversation.

## What the plugin author collects about you

Nothing.

I don't run analytics. I don't have access to your Claude conversations. I don't see your photos, your questionnaire answers, your color analysis results, your IP address, or anything else you produce while using the plugin. I couldn't access any of it even if I wanted to — the skill is pure content, executed inside your Claude session, and no data ever leaves that session on my account.

If you file a GitHub issue to report a problem, I'll see whatever you type into that issue (your GitHub username, the text you write, any images you attach). That's a GitHub interaction, not a True Hue interaction, and it's governed by GitHub's own privacy policies.

## What happens inside Claude Code

When you use True Hue, you're interacting with Claude — Anthropic's assistant. The photos you upload, the questionnaire answers you type, and the whole conversation that produces your color analysis all live inside that Claude session. Handling of that data is covered by [Anthropic's Privacy Policy](https://www.anthropic.com/legal/privacy) and the terms you accepted when you started using Claude Code.

The skill's intake template includes a privacy section summarizing the current Anthropic-side facts as of the plugin's authoring. Policies can change. The source of truth for what Anthropic does with your data is Anthropic's own published policies, not this plugin's description of them.

## The promo site (bankielewicz.github.io/TrueHue)

The landing page at https://bankielewicz.github.io/TrueHue/ is static HTML hosted on GitHub Pages. It does a few things worth being explicit about:

- **Google Fonts** are loaded from `fonts.googleapis.com`. Google sees your IP address when the fonts load. I don't receive that data; Google does. If this matters to you, see [Google's Privacy Policy](https://policies.google.com/privacy).
- **The "Buy me a coffee" button image** loads from `cdn.buymeacoffee.com`. Same deal — their CDN sees your IP, I don't.
- **GitHub Pages hosting** logs standard request data (IP, user agent, timestamp) on GitHub's infrastructure. See [GitHub's Privacy Policy](https://docs.github.com/en/site-policy/privacy-policies).

No cookies are set by the site itself. No trackers. No analytics. No forms collecting contact info. The install command block on the site is a copy-to-clipboard button that runs entirely in your browser via the Clipboard API — nothing gets submitted anywhere.

## The GitHub repository

Standard GitHub-hosted public repo. If you star it, fork it, open issues, or comment on commits, those actions are recorded by GitHub, on GitHub. Covered by GitHub's policies.

## Your data rights

Because I don't hold any data about you, there's nothing for me to delete, export, or correct on request. If you have a data-rights request about your Claude conversations, direct it to Anthropic. For GitHub activity, direct it to GitHub. For anything Google or Buy Me a Coffee might have logged from you visiting the promo site, direct it to them.

## Children

True Hue isn't designed for or marketed to children under 13. If you're a parent and you think a child has used the plugin in a way you'd like addressed, contact Anthropic — the session data lives on their side, not mine.

## Changes to this policy

If the plugin ever starts collecting data, this policy gets updated before those features ship. Material changes get a new effective date at the top of this file and a short note in the repo's CHANGELOG or release notes explaining what changed. You can also watch the repo to be notified on any update.

## Contact

Bryan Ankielewicz — bryan.ankielewicz@live.com

GitHub issues are welcome for questions about how the plugin handles data: https://github.com/bankielewicz/TrueHue/issues
