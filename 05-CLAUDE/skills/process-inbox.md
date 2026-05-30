# Skill: process-inbox

**Trigger phrases:** "process inbox" / "run morning capture" / "clear the inbox" / "sort my captures"
**Also runs automatically at the start of every session.**

## What this does

Reads unprocessed captures in `00-INBOX/`, sharpens each note, files it to the correct subfolder in `01-CAPTURES/`, updates the vault index, and reports what it found.

---

## Step 0: Pre-filter (before reading any file content)

List all files in `00-INBOX/`. Build the candidate list by **excluding**:

| Exclude | Reason |
|---|---|
| Files starting with `_` | Bot-generated outputs — never process these |
| Non-markdown files: `.jpg`, `.jpeg`, `.png`, `.pdf`, `.mov`, `.heic`, `.gif`, `.mp4`, `.csv`, `.rtf`, `.xlsx`, `.zip` | Not captures — skip unless Nick explicitly asks to process a PDF |
| `.gitkeep`, `.DS_Store`, `.gitignore` | System files |
| Filenames already present as a slug in `05-CLAUDE/vault-index.md` | Already processed in a prior session |

Only read the content of files that pass all four filters. Do not open skipped files.

Log: "Pre-filter: [total files in inbox] found → [N] skipped (bot outputs + media + already indexed) → [N] candidates to process"

---

## Step 1: For each candidate file

Read the full content.

**A. Detect capture type:**

| Type | Signs |
|---|---|
| `observations/` | Something noticed, a thing that happened, a market signal |
| `reactions/` | Gut response to news/article/post |
| `patterns/` | Same principle in two different domains, "this reminds me of X" |
| `questions/` | Open question, genuinely unresolved |
| `numbers/` | Specific data point or metric — must have a concrete figure |

If a note contains a raw URL not yet fetched: run the `scrape-link` skill on it first, then classify based on fetched content.

**B. Sharpen to one punchy sentence (two max).**

Sharpness test: a stranger should understand exactly what was observed without additional context. If it still needs explanation, rewrite it.

Bad: "Interesting thing about SWIFT and trade"
Good: "SWIFT takes 3–5 days and $200–400 per wire on Panama maritime routes — that's dead capital for vendors who've already delivered."

**C. Add exactly three tags.** Format: `#[domain]/[subtopic]`
Examples: `#maritime/settlement` `#payments/friction` `#balboa1/proof-point`

**D. Add BALBOA1 relevance flag** (only if genuinely relevant):
- `#b1-proof` — can be used as a proof point in cold outreach
- `#b1-content` — strong candidate for content
- `#b1-question` — should be in the FAQ/objection responses

**E. Move to the correct subfolder.** Rename: `YYYY-MM-DD-[3-word-slug].md`

Write the sharpened note with frontmatter:
```markdown
---
type: [observation/reaction/pattern/question/number]
date: YYYY-MM-DD
tags: [#tag1, #tag2, #tag3]
b1: [#b1-proof / #b1-content / #b1-question — if applicable]
source: [original filename or URL]
---

[Sharpened one-sentence summary]

[Any additional context worth preserving — 2-3 sentences max]
```

---

## Step 2: Process report

After filing all captures, output:

```
📥 Inbox Processed — [Date]

Pre-filter: [N] total → [N] skipped → [N] processed

Filed [N] captures:
  observations/: [N] notes
  reactions/: [N] notes
  patterns/: [N] notes
  questions/: [N] notes
  numbers/: [N] notes

Patterns noticed across today's batch:
[2-3 bullets — specific recurring themes, not generic]

One connection worth exploring:
[The single most interesting non-obvious link between today's captures]

BALBOA1-relevant captures:
[Any tagged #b1-proof, #b1-content, #b1-question — one line each]
```

---

## Step 3: Update vault-index.md

For every capture filed this session, append a new row to `05-CLAUDE/vault-index.md`.

Format — one row per capture:
```
| YYYY-MM-DD | [type] | [slug-without-date] | [tag1] [tag2] [tag3] | [sharpened summary, max 100 chars] |
```

If `vault-index.md` does not exist yet: create it with the header row first:
```markdown
# JARVIS Vault Index
*Auto-maintained by process-inbox. Last updated: YYYY-MM-DD*
*Use this file during connection sessions and auto-research to pre-filter before reading full captures.*

| Date | Type | Slug | Tags | Summary |
|---|---|---|---|---|
```

Do not re-index files already in the index. Append only new entries.

---

## Step 4: Prune hot-cache.md if needed

Check the line count of `05-CLAUDE/hot-cache.md`.

If **≤ 150 lines**: no action.

If **> 150 lines**:
1. Read the full file
2. Identify and preserve:
   - Current post queue section
   - Current CRM action queue
   - Last 2 dated session blocks (most recent)
   - JARVIS upgrade queue
3. Append everything else to `05-CLAUDE/hot-cache-archive-YYYY-MM.md` (create if needed, append if exists)
4. Rewrite `hot-cache.md` with only the preserved sections, plus this header:
   ```
   # JARVIS Hot Cache
   *Pruned [date] — older entries in hot-cache-archive-[month].md*
   ```
5. Log: "hot-cache.md pruned: [X] → [Y] lines. Archive: hot-cache-archive-[month].md"

---

## Quality bar

The sharpened note must be specific enough that a stranger understands it without additional context. If it still needs explanation, rewrite it.

The "one connection worth exploring" must genuinely surprise. If it's obvious ("two fintech notes are related") it doesn't count.
