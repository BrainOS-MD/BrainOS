# Skill: Weekly Connections

**Trigger phrases:** "run connection session" / "find this week's connections" / "weekly connections" / "what connects?"

## What this does

Finds non-obvious relationships across recent captures. Creates connection notes in `02-CONNECTIONS/` that become the raw material for content briefs.

Uses `vault-index.md` to pre-filter before reading any full files — dramatically reducing the number of full reads needed.

---

## Step 0: Index-first filtering

**Do not read full capture files yet.**

1. Read `05-CLAUDE/vault-index.md` (single file, all summaries and tags)
2. Filter to entries with dates in the last 7 days
3. From summaries and tags alone, identify the 8–12 most promising candidates — look for:
   - Entries with shared or adjacent tags across different types
   - Entries that seem to contradict each other (productive tension)
   - Entries whose summaries suggest they share an underlying mechanism
   - Any entries tagged `#b1-proof`, `#b1-content`, or `#b1-question`
4. Read `02-CONNECTIONS/` index (or list files) to note which connection slugs already exist — exclude already-documented connections from the candidate set

Log: "Index-first filter: [N] entries from last 7 days → [N] candidates selected for full read"

**Only read full file content for the selected 8–12 candidates.** Do not read every file from the last 7 days.

---

## Step 1: Load candidate files

Read the full content of the 8–12 candidate captures identified in Step 0.

Also read any existing connection notes in `02-CONNECTIONS/` briefly to avoid surfacing connections already documented.

---

## Step 2: Run the connection search

A strong connection is one of four types:

**TYPE A — Same principle, different domains**
The same underlying mechanism appears in two genuinely different contexts. Not obvious at first glance.
Example: "Schelling points in currency adoption (why USDT is the default despite USDC being safer) is the same principle as why QWERTY beat better keyboards — network effects beat merit when switching costs are high."

**TYPE B — Productive contradiction**
Two captures that appear to disagree, where the tension creates something more interesting than either note alone.
Example: "Institutional OTC desks won't switch from USDT without massive incentive" vs. "Panama compliance trail solves the debanking problem that kills crypto businesses." The tension: switching cost is behavioral, but the compliance angle is existential — different motivations, different sales.

**TYPE C — Emergent pattern**
Three or more captures that individually seem unrelated but together point at an unnamed insight.

**TYPE D — Question answered by accident**
A question from one note is answered (or partially answered) by information in a different note Nick never consciously connected.

---

## Step 3: For each strong connection

**A. Name the connection type (A/B/C/D).**

**B. Write the bridge** — one sentence explaining WHY these are connected in a non-obvious way.

**C. Write a content hook** — the compelling angle for a post.

**D. Score it 1–10:**
- Novelty (would this surprise the person who wrote the notes?): /5
- Applicability to Nick's goals (raise, content, network): /5

Only surface connections with total score ≥ 7.

**E. Create a connection note in `02-CONNECTIONS/`:**

```markdown
---
type: connection
date: YYYY-MM-DD
source-notes: [[note1]], [[note2]]
connection-type: A/B/C/D
score: X/10
status: unprocessed
---

# [Title of the connection insight]

## The Bridge
[One sentence — why these are connected in a non-obvious way]

## Why It Matters
[2-3 sentences. What does this tell Nick about the world, his business, or his audience?]

## Content Angle
[The hook. What would make someone stop scrolling if this were a post?]

## Source Notes
- [[link to note 1]] — [one-line summary]
- [[link to note 2]] — [one-line summary]
```

---

## Step 4: Report

```
🔗 Connection Session — [Date]

Index-first filter: [N] entries scanned → [N] candidates read in full
[N] connections found above threshold (7+/10)

━━━━━━━━━━━━━━━━━━━━━━

Connection 1: [Title] — Type [A/B/C/D] — Score: [X/10]
[Bridge sentence]
Angle: [One-line content hook]

Connection 2: ...

━━━━━━━━━━━━━━━━━━━━━━

Strongest connection this week:
[Pick the one that would produce the best content. Explain in 2 sentences why.]

Suggested next step:
[Either "run generate-brief on Connection X" or "capture more material on [gap]"]
```

---

## Quality bar

If the connection is obvious, it doesn't qualify. The test: if Nick read both notes back-to-back, would the connection be immediate? If yes, skip it.

Minimum: 3 connections. Maximum: 5. Quality beats quantity.
