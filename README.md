# slop-check

A Claude Code skill that audits content for AI slop patterns and scores it across 8 dimensions. Built on the Awwra anti-slop framework (last updated April 2026).

---

## What it does

Paste any content — a tweet, reply, thread, or article — and get back:

- Every Tier 1 violation with the exact offending quote
- Pass/fail on 3 quality gates (adds value, takes position, stops scroll)
- Scores across 8 dimensions (1–10 each)
- Top 3 issues with actionable rewrite directions
- A final verdict: **PASS**, **NEEDS REWRITE**, or **REWRITE**

---

## Install

```bash
npx skills add ./slop-check -y -g
```

Or drop the `slop-check` folder directly into your `~/.agents/skills/` directory.

---

## Usage

```
/slop-check
```

Then paste the content you want audited. The skill will ask if you don't provide it upfront.

You can also specify the platform:

```
/slop-check [X post]
/slop-check [ViewFT article]
/slop-check [LinkedIn post]
```

If not specified, the skill infers the platform from content length and style.

---

## Scoring

| Dimension | What it measures |
|-----------|-----------------|
| `original_take` | Says something non-obvious |
| `no_ai_tells` | Free of banned vocab, phrases, formatting |
| `voice_match` | Sounds like a specific human, not a newsletter |
| `platform_fit` | Appropriate for the target platform |
| `keyword_density` | Low jargon-to-insight ratio |
| `no_engagement_bait` | No hollow CTAs or "Thoughts?" closers |
| `no_emotional_inflation` | No hype vocabulary or overclaiming |
| `humanness` | Chaotic variation, rough patches, genuine texture |

`no_ai_tells` and `humanness` are weighted 1.5x in the overall score.

**Thresholds:**
- ≥ 8: PASS
- 6–7: NEEDS REWRITE (fixable)
- < 6: REWRITE (don't post as-is)

---

## What it checks

### Tier 1 — Automatic disqualifiers
Any single violation here means rewrite before posting.

- Banned formatting: em dash, bold markdown, emoji closers
- Banned openers: sycophantic agreement, restating the original post
- Banned filler phrases: "It's worth noting", "At the end of the day", "Furthermore,", etc.
- Banned vocabulary (3 layers):
  - **Original:** pivotal, robust, delve, tapestry, synergy, certainly, etc.
  - **2026 general:** game-changer, move the needle, narrative, in this space, etc.
  - **April 2026 crypto/AI:** execution risk, price action, conviction, flywheel, moat, macro tailwinds, etc.
- Banned structural patterns (3 layers):
  - **Original:** symmetric takes, three bullet points, generic conclusions, engagement bait, etc.
  - **2026 general:** "we're early" safe harbor, authenticity performance, definition opener, uniform sentence weight
  - **April 2026:** hourglass close, even paragraphing, template paragraph structure, definition stacking, policy voice without specifics, false certainty, consensus-adjacent take, asymmetric polish, fake burstiness

### Tier 2 — Quality gates
- **Gate 1:** Adds at least one specific data point, named example, reframe, prediction, or first-person observation
- **Gate 2:** Takes a falsifiable position — someone smart could push back
- **Gate 3:** First 8 words earn the read — no context-setting openers

---

## The core test

> "Would a sharp human who actually lives in this space, with strong opinions, say exactly this?"

If the answer is "probably not" or "it's fine" — that's a 5. Fine is slop.

---

## April 2026: second-generation slop

Newer models (GPT-5.1, Claude 4) suppress the obvious tells — em dash, "delve", three bullet points — by default. The slop hasn't gone away. It's gone underground.

The patterns to watch now:

- **Fake burstiness** — models trained to vary sentence length produce mechanical short-long-short-long alternation. Real human variation is chaotic. Read the draft aloud: if it sounds like a metronome, rewrite it.
- **Asymmetric polish** — intro and outro are fluent, middle is thin. Uniform polish throughout is itself a texture tell.
- **Consensus-adjacent take** — sounds opinionated but reflects the median view. AI defaults to the broadly acceptable middle ground.
- **Even paragraphing** — all paragraphs the same length. Humans don't distribute information symmetrically.
- **Hourglass close** — every post ends with a zoom-out synthesis. Humans often just stop when they've said the thing.

The suppressed-tell trap: a post conspicuously free of classic tells + second-gen patterns present is itself a signature. CT readers have calibrated for this since 2024.

---

## Platform notes

- **X / Twitter:** Short posts under 100 chars skip even-paragraphing and template structure checks.
- **ViewFT articles:** `humanness` and `original_take` weighted higher — the citation economy (ChatGPT, Perplexity, Grok) requires specificity, not just slop-free text.
- **Threads:** First tweet scored for scroll-stopping; full thread scored for structural patterns.
- **Replies:** Gate 1 requires something the original tweet didn't already have.

---

## Credits

Built by [Viewfin Labs](https://viewft.com) — the team behind [ViewFT](https://viewft.com) and [Awwra](https://awwra.app).

- **ViewFT** — credibility-first publishing with ViewCred score
- **Awwra** — AI creator growth platform for crypto/AI/SaaS creators

Anti-slop framework developed for the `@A11anTa` and `@viewftcom` content pipelines.

---

## License

MIT
