# Skill: auto-research

**Trigger:** `auto-research [topic or question]`
**Optional flag:** `--background` (spawns as background Task agent, results appear in 00-INBOX when complete)

## What this does

Runs a self-directed iterative research loop on any topic. Three explicit rounds: decompose → search → synthesize. Stops when confidence is high or rounds are exhausted. Writes a clean research file to `00-INBOX/`.

This is not a single web search. It is a reasoning loop that compounds on itself.

**Use this for fact-gathering on a specific topic.**
For decisions that require reasoning + research, use `think-deep` instead.

---

## Round 0 — Decompose (mandatory, before any search)

Do not run a single search until this round is complete.

**Check the vault first:**
Read `05-CLAUDE/vault-index.md` and filter for entries related to this topic by tags and summary. Note what's already captured. This prevents re-researching what's already known and sharpens the search angles.

**Then frame the question:**
1. Restate the research question in one clear sentence
2. List 3–5 sub-questions that must be answered to fully resolve it
3. Identify which sub-questions the vault already partially answers (skip those in Round 1)
4. List 2–3 search angles for the remaining gaps: what type of source would be most valuable? (news, company site, academic, forum, X thread, regulatory filing)
5. List any specific named sources worth checking directly

State this framing before proceeding to Round 1.

---

## Round 1 — Broad sweep

Run 2 web searches using the best angles from Round 0. Use different phrasings — don't repeat the same query twice.

After each search:
- Extract: key facts, named entities, numbers, dates, quotes worth keeping
- Flag: anything that contradicts other sources
- Note: what this search did NOT answer

**Gap check after Round 1:**
List explicitly:
- Sub-questions now answered with high confidence
- Sub-questions still unresolved
- New questions that emerged (add to Open Questions — do not chase mid-loop)

If ≥ 80% of Round 0 sub-questions are resolved → skip Round 2, go to synthesis.

---

## Round 2 — Targeted gap fill (only if needed)

Run 1–2 searches specifically targeting the gaps from the Round 1 gap check. Be precise — narrow queries, specific named sources, exact entity names.

After each search: does this resolve the gap? If yes, stop. If the gap is unresolvable via search, mark it as an Open Question and stop.

**Cap:** maximum 4 searches total across Rounds 1 and 2. Quality over quantity.

---

## Round 3 — Synthesis

Write the research output. Structure:

```
## [Research Topic]
*Researched: [date] | Vault check: [what was already known] | Confidence: [High / Medium / Low]*

### Core Finding
[1–3 sentences. The answer to the main question. Lead with the most important fact.]

### Key Facts
- [Specific fact — note source type: news / company site / X thread / etc.]
- [Specific number or date]
- [Named entity / company / person relevant to Nick's context]

### Relevant to Nick Because
[1–2 sentences connecting this to BALBOA1, maritime trade, or Nick's content pillars. Be specific or skip.]

### Open Questions
- [What this research did NOT resolve — honest gaps]
- [New questions that emerged mid-loop — for future research]

### Sources Used
- [Round 1, Search 1: query used → type of source found]
- [Round 1, Search 2: query used → type of source found]
- [Round 2, Search 1: query used → type of source found, if applicable]
```

---

## Output

Save to:
```
00-INBOX/_YYYY-MM-DD-research-[slug].md
```

Where `[slug]` is a 2–4 word kebab-case description of the topic.
Example: `_2026-05-29-research-panama-ibc-regulations.md`

Do NOT save to any other location. Do NOT print the full output inline if it's long — confirm it was written and give a 2-sentence summary.

---

## Token discipline

- Never run more than 4 searches per invocation
- Do not re-read the same source twice
- If a topic is too broad: stop after Round 0 and ask Nick to narrow it before proceeding
- Do not recurse into tangents — new questions that emerge go to Open Questions only
- Check vault-index.md first — always. Do not re-research what's already captured.

---

## Background mode

If Nick adds `--background` flag: spawn as a background Task agent. Confirm the task was spawned and the output path. Results appear in `00-INBOX/` when complete. Nick does not need to wait.

Example: `auto-research panama canal throughput 2025 --background`
