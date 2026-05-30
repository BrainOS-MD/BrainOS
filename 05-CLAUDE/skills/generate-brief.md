# Skill: Generate Brief

**Trigger phrases:** "generate a brief for [topic/connection]" / "brief this connection" / "make a brief" / "brief [connection title]"

## What this does

Takes a connection note or a topic and produces a fully structured content brief in `03-BRIEFS/`. By the time you leave this skill, Nick needs to write the content — not figure out what to write.

## Process

### Step 0: Auto-research

Before building the brief, run one round of `auto-research` scoped to the brief's topic.

Extract the topic from: the connection note title, the capture slug, or Nick's trigger phrase.

Run 2 targeted searches:
1. `[topic] recent evidence OR data OR case study [year]` — find external proof that strengthens or challenges the One Thing
2. `[topic] counter-argument OR criticism OR failed attempt` — find the strongest objection to pre-empt

Inject findings directly into the brief:
- Strong external evidence → add to **PROOF** section alongside vault evidence
- Counter-argument → add to **Research Gaps** as a pre-emption note

If searches return nothing useful: log "Auto-research: no new external evidence found" and proceed with vault sources only.

Do not save a separate research file — the findings get embedded in the brief itself.

---

### Step 1: Find the source

If Nick names a connection: find it in `02-CONNECTIONS/`. Read it fully plus all linked source notes.

If Nick names a topic without a connection note: do a mini connection session right now — read recent captures related to this topic and find the strongest angle.

### Step 2: Build the brief

The brief has exactly these 7 fields:

**ONE THING**
The single insight this piece is built around. One sentence. If it cannot be stated in one sentence, the idea is not ready. Challenge Nick: "What's the one thing a reader should know after reading this?" Push back if the one thing is fuzzy.

**PROOF**
The most specific real example, number, or result that proves the One Thing. Vague proof invalidates the brief. Must have a real figure or a named example from the source notes. If the proof is weak, flag it: "⚠️ Proof is thin — suggest capturing X data before writing this."

**READER TRANSFORMATION**
What does the reader know or feel at the end that they didn't before? If this cannot be stated clearly, the piece has no reason to exist.

**THREE HOOKS (ranked)**
- Hook 1 (Aggressive): challenges a belief, makes a claim that creates tension
- Hook 2 (Curious): opens a question the reader wants answered
- Hook 3 (Personal): Nick's specific experience as the entry point
Rank by scroll-stopping power. Hook 1 should be the most aggressive.

**THREE CLOSERS (ranked)**
The closer is written before the body. It's what the reader will remember.
- Closer 1: the reframe (makes them see the One Thing differently)
- Closer 2: the call to act (what should they do with this information)
- Closer 3: the zoomed-out statement (makes the One Thing feel bigger)

**PLATFORM FIT**
Rank which platforms this brief works best for, with one-line rationale:
- X thread: yes/no + reason
- LinkedIn personal: yes/no + reason
- Substack: yes/no + reason
- LinkedIn company (BALBOA1): yes/no + reason — add flag if any claims need compliance review
- Company blog: yes/no + reason

**RESEARCH GAPS**
What would make this brief stronger? List 1-3 specific things worth finding before writing (data, examples, counter-arguments).

### Step 3: Save the brief

Save as `03-BRIEFS/YYYY-MM-DD-[slug].md`. Tag it `#ready-to-write`.

```markdown
---
date: YYYY-MM-DD
status: ready-to-write
source-connection: [[connection title]]
platforms: [x, linkedin-personal, substack]  (only ones ranked "yes")
---

# Brief: [Title]

## One Thing
[single sentence]

## Proof
[specific number, example, or named case]

## Reader Transformation
[what they know/feel at the end they didn't before]

## Hooks (ranked)
1. [Aggressive]
2. [Curious]
3. [Personal]

## Closers (ranked)
1. [Reframe]
2. [Call to act]
3. [Zoomed out]

## Platform Fit
- X thread: ✅ [reason]
- LinkedIn personal: ✅ [reason]
- Substack: ✅ [reason]
- LinkedIn company: ✅/⚠️ [reason + compliance flag if needed]
- Company blog: ✅/❌ [reason]

## Research Gaps
- [ ] [specific thing worth finding]
- [ ] [optional second thing]
```

### Step 4: Tell Nick

```
📋 Brief Generated: [Title]

One Thing: [the sentence]
Strongest hook: [Hook 1]
Best platform: [top 1-2 recommendations]

Saved to 03-BRIEFS/[filename]

Next: run "write the brief for [title]" to produce the full draft.
```

## Quality bar

A brief is only complete if every field is filled with something specific. No placeholders. No "TBD." If something can't be filled, flag it explicitly and explain what's needed first.
