# JARVIS Command Reference

Everything you can ask JARVIS to do, how to ask for it, and when to use it.

---

## Quick Reference

| Command | What It Does | When to Run |
|---|---|---|
| `process inbox` | Triage, sharpen, and file raw captures | Session start (auto) or after a big dump |
| `scrape [URL]` | Fetch, clean, and file a link as intelligence | Any time you drop a link |
| `run connection session` | Find non-obvious relationships across recent captures | Weekly, after 5+ new captures |
| `generate a brief for [topic]` | Turn a connection into a structured content brief | When a connection feels post-worthy |
| `write the brief for [slug]` | Produce finished copy from an approved brief | When a brief is ready to post |
| `jarvis-to-balboa` | Push top briefs to BizBot for outreach | Before running BizBot outreach |
| `auto-research [topic]` | Iterative 3-round research loop on any question | Fact-gathering on a specific topic |
| `think-deep [problem]` | Reason + research + synthesize for a decision | Decisions, not just facts |
| `lint the vault` | Health check + auto-fix structural problems | Monthly or when things feel cluttered |
| `kickoff [project name]` | Co-founder planning pass before any new build | Before starting anything new |

---

## Commands — Full Detail

---

### 1. Process Inbox

**What it does:**
Reads unprocessed captures in `00-INBOX/`, sharpens each note, files it to the correct subfolder in `01-CAPTURES/`, updates `vault-index.md`, and writes a report.

**Runs automatically at the start of every session.** Only invoke manually if you've done a big drop mid-session.

**Trigger phrases:**
- `process inbox`
- `run morning capture`
- `clear the inbox`
- `sort my captures`
- `process the inbox further` ← if files were untouched last pass

**Examples:**
```
process inbox
clear the inbox, I just AirDropped a bunch of notes
process the inbox further, there were files that were untouched last pass
```

**What gets filed:**
| Subfolder | What goes there |
|---|---|
| `01-CAPTURES/observations/` | Things noticed, market signals, things that happened |
| `01-CAPTURES/reactions/` | Gut responses to news, posts, articles |
| `01-CAPTURES/patterns/` | Same principle appearing in two different domains |
| `01-CAPTURES/questions/` | Open questions, genuinely unresolved |
| `01-CAPTURES/numbers/` | Real data with specific figures attached |

**What gets skipped:**
- Files starting with `_` (bot outputs)
- Media files (images, PDFs, video, CSV)
- Files already indexed in `vault-index.md`

**Recommendation:**
Drop everything into `00-INBOX/` with zero friction — voice notes, screenshots, half-sentences, raw URLs. JARVIS cleans it up. Don't self-edit before capturing.

---

### 2. Scrape Link

**What it does:**
Fetches a URL, strips all noise (ads, nav, footers, cookie banners), extracts the core intelligence, and files a clean summary in `00-INBOX/` for process-inbox to sort.

**Trigger phrases:**
- `scrape [URL]`
- `read this link [URL]`
- `file this [URL]`
- Just drop a raw URL — JARVIS picks it up

**Examples:**
```
scrape https://x.com/cyrilxbt/status/2056555832805089310
read this link https://techcrunch.com/2026/05/30/genius-act-update
file this https://nytimes.com/...
```

**What it extracts:**
- Primary claim (single most important thing)
- Key data points (numbers, percentages, dates)
- Named entities (people, companies, events)
- One-line JARVIS summary for filing

**Recommendation:**
Use this instead of copy-pasting article text. Cleaner, faster, and produces a better-formatted capture. Works on X threads, news articles, Substack posts, regulatory filings. If a URL 403s or blocks fetch, note it in the Chrome queue for manual review.

---

### 3. Run Connection Session

**What it does:**
Reads recent captures across the vault, finds non-obvious relationships between them, and creates connection notes in `02-CONNECTIONS/`. These become the raw material for content briefs.

**Trigger phrases:**
- `run connection session`
- `find this week's connections`
- `weekly connections`
- `what connects?`
- `run connections on my recent captures`

**Examples:**
```
run connection session
find this week's connections
what connects across the last 7 days?
run connections — focus on B1-tagged captures
```

**What it produces:**
- `02-CONNECTIONS/YYYY-MM-DD-[slug].md` for each strong connection found
- Each note includes: the two source captures, the non-obvious link, and why it matters
- Only surfaces connections not already documented

**Recommendation:**
Run after you've had 5+ new captures filed. Weekly cadence is right. The real value is in connections across domains — a regulatory note + a market observation + a personal experience = one unusually specific post nobody else is writing.

---

### 4. Generate Brief

**What it does:**
Takes a connection note (or names a topic) and produces a fully structured content brief in `03-BRIEFS/` — hook, closer, platform ratings, proof, and reader transformation already done. You write the post from the brief, not from scratch.

**Trigger phrases:**
- `generate a brief for [topic or connection title]`
- `brief this connection`
- `make a brief`
- `brief [connection slug]`

**Examples:**
```
generate a brief for the ETH narrative inflection / B1 corridor yield connection
brief this connection: andrew-trade-finance-pain-points + b1-programmable-escrow
make a brief on the GENIUS Act regulatory moat angle
brief the float piece
```

**What it produces:**
A `03-BRIEFS/YYYY-MM-DD-[slug].md` file containing:
- **One Thing** — the single insight the post is built around
- **Proof** — specific number or real example (if proof is weak, JARVIS flags it)
- **Reader Transformation** — what they know/feel after reading that they didn't before
- **Three Hooks** (ranked) — aggressive / curious / personal
- **Three Closers** (ranked) — reframe / call to act / zoomed out
- **Platform ratings** — which platforms this brief is suited for (X, LinkedIn, Substack)

**Recommendation:**
Don't skip to writing directly from a capture. The brief is the quality gate. If the One Thing can't be stated in one sentence, the idea isn't ready — the brief process surfaces that before you waste an hour writing.

---

### 5. Write Content

**What it does:**
Takes an approved brief from `03-BRIEFS/` and produces finished, platform-formatted copy in Nick's exact voice. Drafts land next to the source brief, tagged `#written`.

**Trigger phrases:**
- `write the brief for [slug]`
- `write this brief`
- `produce content from brief`
- `write [brief filename]`

**Examples:**
```
write the brief for 2026-05-30-float-arthur-hayes-style-draft
write this brief: jarvis-fundraise-operator-angle
produce content from the GENIUS Act moat brief
write the ETH corridor yield post
```

**What it produces:**
Finished drafts for each platform rated "yes" in the brief:
- **X Thread** — 5–8 tweets, each standing alone, Hook 1 leads
- **LinkedIn** — 600–900 words, scannable format, professional-direct tone
- **Substack** — 800–1,400 words, narrative structure, more depth

All copy follows Nick's voice rules: short sentences, concrete > abstract, no hedging, no AI-sounding language, no banned phrases.

**Recommendation:**
Only run this after a brief is approved — meaning you've confirmed the One Thing is sharp and the proof is real. Don't write from a weak brief. The finished copy is only as good as the brief underneath it.

---

### 6. Jarvis to Balboa

**What it does:**
Scores briefs in `03-BRIEFS/` by B1 relevance + freshness + strength, picks the top 3, and exports them to `03-BRIEFS/_balboa-bridge.md`. BizBot reads this file daily to inject current thinking into personalized investor messages and outreach drafts.

**Trigger phrases:**
- `jarvis-to-balboa`
- `sync to balboa`
- `export briefs`
- `push to outreach bot`
- `update the balboa bridge`

**Examples:**
```
jarvis-to-balboa
sync to balboa before I run outreach today
push the top briefs to BizBot
```

**What it produces:**
`03-BRIEFS/_balboa-bridge.md` containing:
- Top 3 current insights with B1 relevance explained
- Proof points BizBot can reference in DMs
- Content themes BizBot should reinforce
- Nick's current B1 narrative angle

**Recommendation:**
Run this before every BizBot outreach session. If you've had a productive capture week but haven't synced, BizBot is working with stale context. Fresh thinking → better personalization → higher response rates.

---

### 7. Auto-Research

**What it does:**
Runs a self-directed 3-round iterative research loop: decompose → broad sweep → targeted verification → synthesize. Checks the vault before going external, so it doesn't re-research what's already known. Writes a clean research file to `00-INBOX/`.

**Trigger phrases:**
- `auto-research [topic or question]`
- `research [topic]`
- `do a research loop on [question]`
- Add `--background` to run as a background task while you do other work

**Examples:**
```
auto-research GENIUS Act stablecoin compliance timeline
auto-research who are the top trade finance operators doing crypto settlement in LatAm
auto-research competitive stablecoin issuers in Panama jurisdiction
auto-research --background CRA landscape for B1 outreach
```

**What it produces:**
A `00-INBOX/research-[slug]-YYYY-MM-DD.md` file with:
- Primary findings and key data points
- Named sources with dates
- Vault cross-references (what was already known vs. what's new)
- Open questions for further research
- JARVIS summary row for vault-index

**Recommendation:**
Use for fact-gathering on a specific topic. Use `think-deep` instead if you need to make a decision. Add `--background` for longer research loops so you're not waiting — the file appears in `00-INBOX/` when complete.

---

### 8. Think Deep

**What it does:**
Runs a structured think → research → synthesize loop for decisions. Phases: Observe → Listen (vault check) → Think → Connect → Research (only where facts are missing) → Synthesize → Decide. Produces a decision brief with the full reasoning trail.

**Trigger phrases:**
- `think-deep [problem, question, or decision]`
- `think through [problem]`
- `help me decide [decision]`
- `run a think-deep on [question]`

**Examples:**
```
think-deep should I prioritize CRA outreach or OTC desk outreach this week
think-deep what's the right positioning for B1 vs. USDT given the ETH narrative collapse
think-deep should I post the Arthur Hayes-style float piece or lead with the operator angle
think-deep is the Robinhood AI execution launch a B1 content opportunity or just noise
```

**What it produces:**
A `00-INBOX/_YYYY-MM-DD-think-deep-[slug].md` decision brief with:
- The problem restated cleanly
- What was already known (from vault)
- The research findings (only where external facts were missing)
- The full reasoning chain
- A recommended decision with confidence level
- What would have to be wrong for this decision to be wrong

**Recommendation:**
Use when you're stuck, not just curious. `auto-research` gives you facts. `think-deep` gives you a decision. Good prompt = specific decision, not a broad topic. The more concrete the question, the sharper the output.

---

### 9. Lint Vault

**What it does:**
Scans the entire vault for structural problems: empty files, misplaced bot outputs, hot-cache bloat, vault-index gaps, orphaned captures, briefs without status tags. Auto-fixes what's clearly safe. Reports everything else with a suggested action.

**Trigger phrases:**
- `lint the vault`
- `vault health check`
- `run lint`
- `find orphans`
- `clean up the vault`

**Examples:**
```
lint the vault
run a vault health check
find all orphaned captures
clean up the vault, it's been a few weeks
```

**What it auto-fixes (no confirmation needed):**
- Empty `.md` files in `01-CAPTURES/` and `03-BRIEFS/` → deleted
- Bot outputs (files with `_` prefix) found outside `00-INBOX/` → moved to `00-INBOX/`
- `hot-cache.md` over 150 lines → pruned, overflow archived
- Captures in `01-CAPTURES/` missing from `vault-index.md` → added

**What it reports (requires your decision):**
- Briefs in `03-BRIEFS/` with no `#ready-to-write`, `#written`, or `#published` tag
- Files in `00-INBOX/` older than 14 days (candidates for deletion or filing)
- Captures with no tags
- Connection notes with broken wikilinks

**Recommendation:**
Run monthly or after heavy sessions. Don't wait until the vault feels broken — run it early and it stays fast. Takes ~2 minutes and prevents the vault from becoming the very thing it's meant to replace.

---

### 10. Kickoff

**What it does:**
Runs a structured co-founder planning pass before any new build. Asks 5 targeted questions specific to the project (informed by SOUL.md and hot-cache context), waits for your answers, then generates a complete project skeleton: CLAUDE.md, context files, skill stubs, and automation candidates.

**Trigger phrases:**
- `kickoff [project name]`
- `let's start [project name]`
- `plan out [project name]`

**Examples:**
```
kickoff marketbot framework
kickoff CRA outreach system
kickoff panama trip research agent
kickoff skool community agent
kickoff founder voice training pipeline
```

**What it produces:**
After you answer the 5 questions:
- A project `CLAUDE.md` (context file the sub-agent reads on open)
- Recommended folder structure
- Skill stubs for the main operations
- Automation candidates (what can run without you)
- A one-page project brief in `00-INBOX/_YYYY-MM-DD-kickoff-[project].md`

**Recommendation:**
Run this before starting anything new. Do not skip the 5-question drill and jump straight to building. The skeleton built in 10 minutes of planning saves 3 sessions of context re-dumps later. If you're tempted to skip it because the project "feels simple," that's exactly when it matters most.

---

## Tips

**Combine commands in sequence:**
The natural production chain is:
```
process inbox → run connection session → generate brief → write content → jarvis-to-balboa
```
You don't have to run all of these in one session — but that's the order they compound.

**Use --background for long research loops:**
```
auto-research --background stablecoin regulatory landscape Panama 2026
```
Runs in the background while you do other work. Result lands in `00-INBOX/` when complete.

**Specificity = quality:**
Every command works better with a specific target.
- Weak: `generate a brief`
- Strong: `generate a brief for the Andrew trade-finance pain points connection — angle it at the programmable escrow demo scenario`

**When in doubt, capture first:**
If something happened and you're not sure if it matters, capture it. Process-inbox will decide whether it's worth filing. The capture cost is near zero. The cost of losing something useful is not.
