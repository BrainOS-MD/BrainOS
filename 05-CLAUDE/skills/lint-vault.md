# Skill: lint-vault

**Trigger phrases:** "lint the vault" / "vault health check" / "run lint" / "find orphans" / "clean up the vault"

## What this does

Scans the entire vault for structural problems. Auto-fixes what's clearly safe. Reports everything else with a suggested action. Saves a report to `00-INBOX/_YYYY-MM-DD-lint-report.md`.

Run this when things feel cluttered, after a batch of heavy sessions, or whenever the vault starts feeling slow.

---

## Step 1: Auto-fixes (run silently, no confirmation needed)

Execute these before reporting:

**A. Empty files**
Find any `.md` file in `01-CAPTURES/` or `03-BRIEFS/` that is 0 bytes. Delete them. Log count.

```bash
find "01-CAPTURES" "03-BRIEFS" -name "*.md" -empty -delete
```

**B. Bot outputs in wrong folders**
Any file with a `_` prefix found outside `00-INBOX/` → move to `00-INBOX/`. Log count.

**C. hot-cache.md pruning**
Check line count of `05-CLAUDE/hot-cache.md`. If > 150 lines:
1. Read the full file
2. Identify and preserve: current post queue, current CRM action queue, last 2 dated session blocks, JARVIS upgrade queue
3. Move everything else to `05-CLAUDE/hot-cache-archive-YYYY-MM.md` (append, don't overwrite)
4. Rewrite `hot-cache.md` with only the preserved sections + a header noting the archive date
Log: "hot-cache.md pruned from [X] → [Y] lines. Archive: hot-cache-archive-[month].md"

**D. vault-index gaps**
Read `05-CLAUDE/vault-index.md`. Find any `.md` file in `01-CAPTURES/` not present in the index. Append missing entries using the standard index row format.
Log count of entries added.

---

## Step 2: Diagnostic scans

### Scan A — Orphaned captures
Find files in `01-CAPTURES/` (all subfolders) that are not referenced by any `[[wikilink]]` in `02-CONNECTIONS/` or `03-BRIEFS/`.

Method:
1. List all capture filenames (slugs without `.md`)
2. Search all files in `02-CONNECTIONS/` and `03-BRIEFS/` for `[[slug]]` mentions
3. Any slug with zero mentions = orphaned

Report: filename, folder, date, tags, age in days.
Suggest: "run connection session" if < 14 days old; "consider archiving" if > 30 days old.

### Scan B — Dead brief links
Find files in `03-BRIEFS/` that contain `[[wikilinks]]` pointing to filenames that don't exist anywhere in the vault.

Report: brief path → dead link target.
Suggest: "remove dead link" or "recreate the connection note."

### Scan C — Briefs never written
Find files in `03-BRIEFS/` that are tagged `#ready-to-write` or have `status: ready-to-write` in frontmatter, but have no corresponding `-DRAFTS.md` file in `03-BRIEFS/`.

Report: brief title, date created, age in days.
Suggest: "write-content [brief]" or flag if stale (> 14 days = trend window likely closed).

### Scan D — Published with no performance data
Find files in `04-PUBLISHED/` that have no engagement metrics — look for absence of numbers, "views:", "likes:", "impressions:", or any performance data section.

Report: filename, publish date, platform.
Suggest: "add performance data so JARVIS can learn what works."

### Scan E — Missing tags
Find files in `01-CAPTURES/` with no `#` characters in content.

Report: filepath.
Suggest: "process inbox to add tags" or manually add during next session.

### Scan F — Stale inbox items
Find files in `00-INBOX/` that:
- Do NOT start with `_` (so not bot-generated)
- Are NOT images, PDFs, or media files
- Are older than 14 days (by file modification date)

Report: count, list of files, age.
Suggest: "run process-inbox to clear these."

---

## Step 3: Vault health score

Score out of 10:
- Start at 10
- -1 for every 5 orphaned captures (max -3)
- -1 if any briefs > 14 days old and never written (max -2)
- -1 if hot-cache was over limit
- -1 if > 20 stale inbox items
- -1 if any dead brief links found
- -1 if published files have no performance data

---

## Step 4: Write the report

Save to `00-INBOX/_YYYY-MM-DD-lint-report.md`:

```
🔍 Vault Lint Report — [Date]

## Auto-Fixed
- Empty files deleted: [N]
- Bot files relocated to 00-INBOX: [N]
- hot-cache.md: [pruned from X → Y lines / within limit]
- vault-index gaps filled: [N entries added]

## Issues Found

### Orphaned Captures ([N] files)
[list: path | age | tags | suggestion]

### Dead Brief Links ([N])
[list: brief → dead target | suggestion]

### Briefs Never Written ([N])
[list: brief | created | age | suggestion]

### Published Without Performance Data ([N])
[list: path | publish date | platform]

### Missing Tags ([N] captures)
[list: paths]

### Stale Inbox Items ([N] items)
[list: filename | age in days]

---

## Vault Health Score: [N]/10

[One sentence on overall health]

## Priority Action
[The single most impactful thing to do right now to improve vault health]
```
