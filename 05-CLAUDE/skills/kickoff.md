# Skill: kickoff

**Trigger:** `kickoff [project name]`

## What this does

Runs a structured co-founder planning pass before any building starts. Asks 5 targeted questions informed by Nick's existing context, waits for his answers, then generates a complete project skeleton: a project CLAUDE.md, context files, skill stubs, and automation candidates.

The skeleton is what Claude Code uses to build 10x faster. Without it, every session starts with a context re-dump. With it, you open the folder and start building immediately.

**Use this before starting any new sub-project.** CRA outreach system, Panama trip prep, marketbot framework, new research agent, anything. Do not skip the planning pass and jump straight to building.

---

## Step 0: Load context before asking anything

Read both of these before generating questions:
- `05-CLAUDE/SOUL.md` — Nick's identity, priorities, audience, active work
- `05-CLAUDE/hot-cache.md` — what's live right now, what's queued, what's in progress

Then ask: does this project already have any captures, connections, or briefs in the vault? Check `05-CLAUDE/vault-index.md` for relevant entries by project name and tags.

Do not generate generic questions. Every question must be informed by what's already known about Nick's situation. A question that could apply to any project is a bad question.

---

## Step 1: Five-question drill

Generate 5 questions specific to this project. Present all 5 at once. Wait for Nick's full answers before proceeding to Step 2 — do not start building the skeleton until he's answered.

**Question framework — adapt every question to the project:**

**Q1 — Outcome**
What does "done" look like? Not what the system *does* — what *changes* because it exists? What becomes possible or stops being a problem?

**Q2 — Inputs**
What does it consume? Data sources, people, files, systems, triggers. Where does the raw material come from, how often, and in what form does it arrive?

**Q3 — Outputs**
What does it produce and who or what consumes it? Be specific: format, destination, frequency. Who acts on the output?

**Q4 — Constraints**
What can't change? Hard deadlines, dependencies on other systems (JARVIS, balboa1-bot, the CRM sheet), budget limits, things already decided. What would break this if it went wrong?

**Q5 — Integration**
How does this connect to what already exists — JARVIS vault, balboa1-bot, the Google Sheets CRM, SOUL.md, the JARVIS bridge file? Should it be a JARVIS skill, a standalone Claude Code project, or an extension of the CRM bot?

---

## Step 2: Determine output location

Based on the answers, set the output location before writing any files:

| Project type | Default output location |
|---|---|
| JARVIS internal agent or research system | `05-CLAUDE/projects/[project-slug]/` |
| Standalone bot (own Claude Code project directory) | `~/[project-slug]/` |
| Extension of balboa1-bot | `/Users/chrissimon/balboa1-bot/skills/[project-slug]/` |
| Vault workflow or content pipeline | Create as a new JARVIS skill in `05-CLAUDE/skills/` |

If unclear from the answers, ask directly: *"Should this live inside the JARVIS vault, as a standalone project like balboa1-bot, or extend the CRM bot?"*

Create the directory before writing files.

---

## Step 3: Generate the skeleton

Write the following files immediately, based on Nick's answers. Every file must be specific to this project. No generic placeholder language — if something is genuinely unknown, mark it `[CONFIRM WITH NICK]` so it's visible and fixable.

---

### File 1: `[location]/CLAUDE.md`

The standing instructions file. This is the file Claude Code reads at the start of every session in this project.

```markdown
# [Project Name] — Standing Instructions

You are [agent identity in one sentence]. Your job is [what you do and for whom].

## What this does

[2–3 sentences: what this system produces, why it exists, what problem it solves for Nick]

## Context files

Read these before executing any command:
- `context/[project]-facts.md` — ground truth: decisions made, key numbers, named entities
- [any other context files, added as they're created]

## Commands

| Command | What it does |
|---|---|
| `[trigger phrase]` | [one-line description] |
| `[trigger phrase]` | [one-line description] |

## Hard rules

- [Non-negotiable constraint #1 specific to this project]
- [Non-negotiable constraint #2]
- [Add only rules that are genuinely project-specific — don't copy generic rules from JARVIS CLAUDE.md]

## Output format

[Where outputs go, exact filename pattern, what they contain]
```

---

### File 2: `[location]/context/[project-slug]-facts.md`

The ground truth file. Contains everything this project should never have to re-derive from Nick.

Structure it around what came out of the five-question answers:

```markdown
# [Project Name] — Facts & Decisions

## What this is
[One paragraph. What the project is, what it does, who it's for.]

## Key facts and numbers
[Specific figures, dates, names, metrics from Nick's answers]

## Decisions already made
[Things that are settled — don't re-question these]

## Named entities
[People, companies, systems, files this project interacts with]

## What this connects to
[How it integrates with JARVIS vault, balboa1-bot, CRM sheet, etc.]

## Open questions
[CONFIRM WITH NICK: anything not resolved in the five-question drill]
```

---

### File 3: `[location]/skills/` — stub files

For each major workflow or command identified in the answers, create a stub skill file. Create stubs for the 2–4 most important workflows. Build stubs only — full implementation comes in working sessions.

```markdown
# Skill: [skill-name]

**Trigger:** `[exact trigger phrase]`

## What this does
[One sentence]

## Inputs
[What it reads or receives]

## Steps
1. [High-level step]
2. [High-level step]
3. [High-level step]

## Output
[What it produces, where it saves, what format]

## Status: STUB — build out in first working session
```

---

## Step 4: Recommendations block

After writing all skeleton files, output this summary:

```
🛠 Kickoff Complete: [Project Name]
Skeleton written to: [location]

━━━━━━━━━━━━━━━━━━━━━━

## Files created
- [path/CLAUDE.md]
- [path/context/[slug]-facts.md]
- [path/skills/[skill-1].md] (stub)
- [path/skills/[skill-2].md] (stub)

## Suggested skills to build (priority order)
1. [Skill name] — [one sentence: what it does + why it's highest priority]
2. [Skill name] — [same]
3. [Skill name] — [same, if applicable]

## Automation opportunities
[For each: what to automate | tool (Make.com / N8N / Python / Claude Code hook) | complexity: low/medium/high]

## Claude Code or Claude.ai?
[Recommendation with reason — Claude Code for anything reading/writing files or running scripts; Claude.ai for one-off drafting or analysis]

## First session plan
[Exactly what to do when you open this project in Claude Code for the first time. One paragraph. Specific enough that no re-explanation is needed.]

## Connections to existing systems
[How this plugs into JARVIS vault, balboa1-bot, the CRM sheet, or SOUL.md]
```

---

## Quality bar

The skeleton passes if: Nick can open Claude Code in the new project folder, read CLAUDE.md, and start building immediately — no context re-dump required. If the CLAUDE.md still has gaps that would force a 10-minute catch-up explanation, the kickoff failed. Fix the gaps before closing the session.

The five questions fail if any of them could apply to a different project without modification. Specificity is the whole point.
