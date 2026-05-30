# Skill: Jarvis to Balboa Bridge

**Trigger phrases:** "jarvis-to-balboa" / "sync to balboa" / "export briefs" / "push to outreach bot"

## What this does

Exports the top content briefs from JARVIS into a format the balboa-bot can read. This is how your thinking becomes your outreach — the connections you're making in your second brain feed directly into personalized investor DMs and content drafts.

## Process

### Step 1: Identify top briefs

Read all files in `03-BRIEFS/` tagged `#ready-to-write` or `#written` that have not yet been marked `#exported`.

Score each brief by:
- B1 relevance of source captures (how much does this connect to BALBOA1's story?)
- Freshness (briefs from last 7 days score higher)
- Content strength (is the One Thing sharp and usable?)

Pick the top 3.

### Step 2: Format for balboa-bot

Create or overwrite `03-BRIEFS/_balboa-bridge.md`:

```markdown
# JARVIS → Balboa Bridge
Generated: YYYY-MM-DD HH:MM

This file is read by the balboa-bot during the daily briefing.
It contains Nick's current thinking — use it to personalize networking messages
and ensure content drafts reflect what he's actively working through.

---

## Nick's Current Thinking (Top 3 Insights This Week)

### Insight 1: [Brief Title]
One Thing: [the single insight]
Why it matters for BALBOA1: [1 sentence connection]
Best hook: [Hook 1 from the brief]
Content angle: [which platform this works best for]

### Insight 2: [Brief Title]
One Thing: [...]
Why it matters for BALBOA1: [...]
Best hook: [...]
Content angle: [...]

### Insight 3: [Brief Title]
One Thing: [...]
Why it matters for BALBOA1: [...]
Best hook: [...]
Content angle: [...]

---

## Recent High-Relevance Captures (B1 Score ≥ 4)

[List any captures from the last 7 days with b1-relevance: 4 or 5]
- [YYYY-MM-DD]: [primary claim] — [source]
- [...]

---

## Live Questions Nick Is Working Through

[List any captures in 01-CAPTURES/questions/ from the last 14 days]
These are things Nick genuinely doesn't know the answer to.
They can become networking message hooks: "I've been thinking about X — curious your take."

- [Question 1]
- [Question 2]
```

### Step 3: Mark exported briefs

Add `#exported` tag to the briefs that were included. They won't be re-exported next time unless updated.

### Step 4: Tell Nick

```
🔁 Bridge Exported → Balboa-Bot

Included:
1. [Brief Title 1]
2. [Brief Title 2]
3. [Brief Title 3]

[N] high-relevance captures included.
[N] live questions included.

Saved to 03-BRIEFS/_balboa-bridge.md

The balboa-bot will read this automatically on the next "briefing" run.
Your current thinking will now show up in networking messages and content drafts.
```

## How the balboa-bot uses this

When the balboa-bot runs `briefing`, it checks for `[JARVIS_VAULT_PATH]/03-BRIEFS/_balboa-bridge.md`.

If found:
- Networking messages reference Nick's live questions as conversation hooks
- Content generation is seeded with the top insights instead of starting from scratch
- The pipeline snapshot can note "3 Jarvis briefs ready to write"

The bridge file path is configured in balboa-bot's `CLAUDE.md`:
```
JARVIS_BRIDGE_PATH = "~/JARVIS-vault/03-BRIEFS/_balboa-bridge.md"
```
