# Skill: think-deep

**Trigger:** `think-deep [problem, question, or decision]`

## What this does

Runs a structured think → research → synthesize loop on any problem or decision. Combines internal reasoning with targeted external research only where facts are actually missing. Produces a decision brief with the full reasoning trail attached.

**Use this when you need to decide something, not just know something.**
For pure fact-gathering on a topic, use `auto-research` instead.

---

## Phase 1 — Think (internal reasoning only, no searches yet)

Before looking anything up, work through what's already known.

**OBSERVE**
State the problem as pure facts — no interpretation. What is actually happening? What is actually being asked? Strip adjectives and strip assumptions. Write it out.

**OBSERVE (again)**
Read what you just wrote. What is hiding as a fact that is actually an assumption? What are you not seeing because you're too close to it? What would a skeptic say is wrong with the framing?

**LISTEN**
Check the vault before going external:
- Read `05-CLAUDE/vault-index.md` — filter for entries relevant to this problem by tags and summary
- Check `05-CLAUDE/hot-cache.md` — what recent context is live?
- Note any captures, connections, or briefs that bear on this question

What signals already exist? What has already been observed or researched on this topic?

**THINK**
Now reason through the problem with everything in hand. What is the logical structure? What are the key variables? What would have to be true for each possible answer to be correct?

**CONNECT**
Link to other things you know. What parallel situations exist — in business, in history, in what you've built before? What has worked or failed in similar cases?

**CONNECT (BALBOA1)**
Specifically: how does this relate to the raise, the product, the GTM, the content pipeline, or the CRM? What is at stake for BALBOA1 in this decision?

**Sort remaining unknowns:**
After thinking, explicitly sort what's left into two buckets:

| Judgment calls | Researchable gaps |
|---|---|
| Can't be researched — require a decision | Specific facts that would materially change the answer |
| Example: "Should I take the meeting?" | Example: "What is Anchorage's current custody fee structure?" |

If there are no researchable gaps → skip Phase 2 entirely and go to Phase 3.

---

## Phase 2 — Research (only if researchable gaps exist)

Run targeted searches on the researchable gaps identified in Phase 1. Do not search broadly. Do not open new threads.

- Max 3 searches total
- Each search targets one specific gap — use the most precise phrasing
- After each search: does this resolve the gap? If yes, stop. If no, try one rephrasing, then mark as "unresolved" and move on
- Any new questions that emerge → add to Open Questions in output. Do not chase them now.

---

## Phase 3 — Synthesize (reach the verdict)

**ACCEPT**
Integrate everything — what you knew, what the research confirmed or changed. What is true, even if uncomfortable? Name the real tradeoffs. Don't soften them.

**CREATE**
What is the actual answer, recommendation, or action? Be specific. State the verdict in one sentence.

If the answer genuinely is "it depends" — specify exactly what it depends on and what would tip it each way. A decision tree is acceptable. Vague hedging is not.

**GROW**
What does this change going forward? Does any assumption in the vault need updating? Is there a capture, connection, or brief that should be revised based on this conclusion?

---

## Output

Save to `00-INBOX/_YYYY-MM-DD-think-deep-[slug].md`:

```markdown
---
type: think-deep
date: YYYY-MM-DD
problem: [one sentence]
verdict: [one sentence answer]
confidence: [High / Medium / Low]
research-rounds: [N searches / "none — internal only"]
---

# Think-Deep: [Problem Title]

## Problem
[What was actually being decided or resolved — after stripping assumptions]

## What Was Already Known
[Key facts and signals from vault, hot-cache, recent context. Specific. No vague claims.]

## Assumptions Surfaced
[Things that were passing as facts — now named explicitly]

## Key Tensions
[The real tradeoffs or contradictions that made this hard]

## Research Used
[What was searched, what it resolved — or "none needed: internal reasoning was sufficient"]

## Verdict
**[The answer. One sentence. No hedging.]**

## Tradeoffs
[What you give up with this choice. Honest.]

## What Changes
[What assumption or direction in the vault/hot-cache/active plans this updates]

## Open Questions
[What remains unresolved — for future research or a separate think-deep]
```

---

## Quality bar

- If Phase 1 produces a clear answer without needing research: good. Don't search for the sake of searching.
- A verdict of "it depends" without a decision tree = failure. Push to a verdict.
- If the problem is genuinely unresolvable today (missing information that can't be searched): say that explicitly, name what's needed, and output what IS known so far.
- The reasoning trail matters as much as the verdict — if Nick re-reads this in 3 weeks, he should be able to follow exactly why this conclusion was reached.
