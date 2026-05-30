# Skill: Weekly Performance Digest

**Trigger phrases:** "weekly digest" / "what's working" / "performance review" / "content report"

## What this does

Pulls engagement data from `04-PUBLISHED/`, computes what's working across platforms and hook types, and surfaces patterns Nick can use to write better content next week. Output: one markdown report in `00-INBOX/`.

Requires Nick to have logged engagement numbers in `04-PUBLISHED/` notes. If no data exists, it says so and stops — it does not fabricate metrics.

---

## Process

### Step 1: Read all published notes

Scan `04-PUBLISHED/`. For each note, extract:
- Date published
- Platform
- Hook type (aggressive / curious / personal — from the source brief if available)
- Engagement data Nick logged (likes, comments, reposts, replies, DMs, clicks — whatever exists)
- Content pillar (building in Web3 / maritime / stablecoin infrastructure / systems-building)

If a published note has no engagement data logged: include it in the report as `[no data — log metrics to improve future analysis]`.

---

### Step 2: Compute patterns

Only compute stats where N ≥ 3 data points exist. Flag anything below that threshold as "insufficient data."

**By platform:** Which platform is producing the most engagement per post?

**By hook type:** Aggressive vs. curious vs. personal — which hook type gets the most response?

**By content pillar:** Which of the 4 pillars is resonating most?

**By post age:** Is engagement front-loaded (first 24h) or does it build over time? Note if any post is still gaining traction.

**Top 3 posts this week:** By total engagement. For each: what made it work (hook, topic, timing)?

**Bottom 3 posts:** What fell flat and why (thin proof, weak hook, wrong platform, off-topic)?

---

### Step 3: Write the report

Save to `00-INBOX/_YYYY-MM-DD-weekly-digest.md`:

```markdown
# Weekly Content Digest — Week of [Date]

## What's Working

**Top platform:** [Platform] — avg [N] engagements/post vs. [N] overall avg
**Best hook type:** [Type] — [N]% higher engagement than other types
**Strongest pillar:** [Pillar] — [N] posts, [N] avg engagement

## Top 3 Posts
1. **[Title]** ([Platform], [Date]) — [N] engagements
   Why it worked: [1 sentence — specific]
2. **[Title]** — [N] engagements
   Why it worked: [1 sentence]
3. **[Title]** — [N] engagements
   Why it worked: [1 sentence]

## What Fell Flat
1. **[Title]** ([Platform]) — [N] engagements
   Likely reason: [1 sentence — specific]
2. ...

## Patterns This Week
- [Specific observation — e.g. "Threads with a real number in tweet 1 outperformed by 2x"]
- [Specific observation]
- [Specific observation]

## Recommendation for Next Week
[2-3 bullets — specific, actionable, based on data above. Not generic advice.]

## Data Coverage
Posts with engagement data: [N] of [total published]
Posts missing data: [list slugs]
Platforms covered: [list]
```

---

### Step 4: Tell Nick

```
📊 Weekly Digest ready: 00-INBOX/_[date]-weekly-digest.md

[N] posts analyzed across [platforms].
Top performer: [title] ([N] engagements)
Weakest: [title] ([N] engagements)

[If data is thin]: Only [N] posts have logged metrics — log more engagement data in 04-PUBLISHED/ for better pattern detection.
```

---

## Quality bar

Do not summarize without data. Every pattern claim must be backed by a specific number or named post. "X tends to perform better" without a number is not a finding — it is a guess. If the data is too thin to draw conclusions, say so explicitly and tell Nick what to log.
