---
name: slop-check
description: Audit drafts for AI-slop patterns before publishing. Use when checking, scoring, rewriting, or humanizing content for AI tells, generic writing, over-polished prose, filler phrases, weak hooks, fake balance, synthetic specificity, didactic endings, or other low-signal writing patterns in posts, replies, articles, landing pages, essays, newsletters, and social content.
---

# Slop Check

Use this skill to audit writing before publication. Be strict. The goal is not to prove whether text was written by AI; the goal is to remove patterns that make writing feel generic, synthetic, over-polished, or low-signal.

## Workflow

1. Read the content and infer the platform if not provided.
2. Scan for Tier 1 rewrite flags.
3. Scan for second-generation 2026 slop patterns.
4. Run the three quality gates.
5. Score the 8 dimensions.
6. Give the top fixes with concrete rewrite direction.
7. Return a PASS, NEEDS REWRITE, or REWRITE verdict.

If no content is provided, ask for it.

## Tier 1 Rewrite Flags

Quote the exact phrase or structure when found.

### Formatting

- Em dash used as a default rhythm crutch
- Bold markdown used to manufacture emphasis
- Emoji closers used as punctuation
- Excessive bullets for a post that needs an argument
- Perfectly even paragraph lengths throughout
- Template-like headings in short content

### Openers

- "Great point"
- "Excellent take"
- "Exactly"
- "This is important"
- "This is fascinating"
- "100%"
- "Let's dive in"
- "Here's what you need to know"
- "In today's landscape"
- "Unpopular opinion"
- "Hot take"
- Definition opener when the reader already knows the topic
- Restating the original post before adding anything new

### Filler Phrases

- "It's worth noting"
- "It's important to remember"
- "At the end of the day"
- "The reality is"
- "Ultimately"
- "Furthermore"
- "Moreover"
- "Additionally"
- "In conclusion"
- "To summarize"
- "In other words"
- "To put it simply"
- "This serves as a reminder"
- "Stands as a testament"
- "Marks a pivotal moment"
- Vague attribution such as "some experts argue" without naming a source

### Vocabulary Slop

Flag these when they replace a concrete claim:

```text
delve, tapestry, intricate, underscore, leverage, utilize, robust,
seamless, holistic, transformative, pivotal, unprecedented,
groundbreaking, cutting-edge, paradigm, synergy, ecosystem, realm,
landscape, journey, interplay, treasure trove, empower, unleash,
foster, cultivate, showcase, garner, navigate, illuminate, shed light,
resonate, game-changer, move the needle, unlock value, drive impact,
at scale, flywheel, moat, structural tailwind, macro tailwinds
```

### Structural Slop

- Fake balance: "On one hand... on the other hand... truth is in the middle."
- Corrective antithesis: "It's not just X, it's Y" or "Not just X, but Y."
- Generic rule of three: "speed, efficiency, and scalability" with no specific proof.
- Template paragraphing: every paragraph follows claim, evidence, implication.
- Hourglass close: broad intro, narrow body, broad inspirational zoom-out.
- Consensus-adjacent take: sounds bold but repeats the median opinion.
- Policy voice without specifics: authoritative language any account could post.
- Fake burstiness: mechanical short-long-short-long rhythm.
- Staccato chain: two or more consecutive fragments under 8 words.
- Definition stacking: multiple clean definitions with no lived example.
- Screenshot-as-proof: using output or screenshots as if they are the insight.
- Authenticity performance: "just being real", "I almost didn't share this", or similar fake vulnerability.

## Second-Generation 2026 Patterns

Look for these after the obvious tells are gone:

- **Didactic moral closure:** every post ends with a tidy lesson.
- **Synthetic specificity:** precise numbers, named studies, or citations with weak source trails.
- **Forced persona:** sass, founder voice, analyst voice, or contrarian voice without earned context.
- **Over-clean coherence:** every transition is smooth and no sentence feels lived-in.
- **Average-internet opinion:** 1,000 accounts could post it unchanged.
- **Hollow emotional language:** "powerful", "profound", "stunning", "deeply human" without concrete evidence.
- **Over-structured formatting:** headings and bullets doing more work than the idea.
- **Model-collapse tropes:** repeated stock names, archetypes, cozy moral arcs, or familiar metaphors in creative writing.

## Quality Gates

All three must pass.

### Gate 1: Adds Value

At least one must be true:

- Specific data point, date, source, or named example
- Reframe that changes how the reader sees the topic
- Prediction with a clear condition
- First-person observation from doing the work
- Named tradeoff others are avoiding

### Gate 2: Takes A Position

The claim must be falsifiable. Someone smart should be able to disagree.

### Gate 3: Stops The Scroll

The first 8 words must earn attention. Context-setting openers fail.

## 8-Dimension Score

Score each 1-10:

- `original_take`
- `no_ai_tells`
- `voice_match`
- `platform_fit`
- `specificity`
- `position`
- `no_emotional_inflation`
- `humanness`

Overall target: 9.0+. If any dimension is below 8, recommend rewriting that part.

## Report Format

```text
SLOP CHECK REPORT

Platform:

TIER 1 VIOLATIONS
- [Exact quote] -> [why it fails]

SECOND-GENERATION PATTERNS
- [Pattern found] -> [rewrite direction]

QUALITY GATES
Gate 1 Adds value: PASS/FAIL
Gate 2 Takes position: PASS/FAIL
Gate 3 Stops scroll: PASS/FAIL

SCORES
original_take:
no_ai_tells:
voice_match:
platform_fit:
specificity:
position:
no_emotional_inflation:
humanness:
overall:

TOP FIXES
1.
2.
3.

VERDICT
PASS / NEEDS REWRITE / REWRITE
```

## Verdict Thresholds

- 9-10: PASS
- 8-8.9: PASS with minor edits
- 6-7.9: NEEDS REWRITE
- Below 6: REWRITE

## Core Test

Ask:

```text
Would a sharp human with lived context, taste, and a real stake say this exact thing?
```

If the answer is "maybe", "it's fine", or "it sounds professional", the draft is not done.

Fine is slop.
