# Skill: Write Content

**Trigger phrases:** "write the brief for [title]" / "write this brief" / "produce content from brief" / "write [slug]"

## What this does

Takes an approved brief from `03-BRIEFS/` and produces finished copy for each platform it's rated "yes" for. Drafts land in `03-BRIEFS/` next to the source brief, tagged `#written`.

## Process

### Step 0: Platform selection

Before writing anything, ask Nick which platform(s) to write for.

**Calculate source word count** — total words across: the brief file + all linked connection notes + all linked captures.

If source word count **> 400 words**: present all 5 platforms as options (longer-form platforms are viable):
```
Which platform(s) for "[Brief Title]"?
Source material: ~[N] words — all formats viable.

  1. X thread
  2. LinkedIn Personal
  3. Substack
  4. LinkedIn Company (compliance review required)
  5. Company Blog
  6. All of the above

Reply with numbers (e.g. "1, 2" or "6"):
```

If source word count **≤ 400 words**: recommend the short-form defaults, but let Nick override:
```
Which platform(s) for "[Brief Title]"?
Source material: ~[N] words — short-form recommended.

  1. X thread ← recommended
  2. LinkedIn Personal ← recommended
  3. Substack (thin for this length — will need expansion)
  4. LinkedIn Company (compliance review required)
  5. Company Blog (thin for this length — will need expansion)
  6. All of the above

Reply with numbers or press Enter for 1+2:
```

Only write drafts for the selected platform(s). Skip the rest.

---

### Step 1: Load the brief + source notes

Find the brief in `03-BRIEFS/`. Read it fully.
Follow the wikilinks to source connection notes in `02-CONNECTIONS/`.
Follow those links to source captures in `01-CAPTURES/`.

This is the full chain. The writing should feel like it emerges from real specific observations, not from a generic template.

### Step 2: Apply Nick's voice (non-negotiable)

From CLAUDE.md, the rules:
- Short sentences. Hard stops. Each idea gets its own line.
- Concrete > abstract. Real numbers always beat vague claims.
- No hedging. No apologizing for opinions.
- No AI-sounding language.
- Use the hook from the brief. Use one of the closers from the brief. The body is what connects them.

### Step 3: Write per platform (only platforms rated "yes" in the brief)

---

#### X Thread (@stupoorcycle)

Format: 5–8 tweet thread. Max 280 chars per tweet.
- Tweet 1: Hook 1 from brief, adapted. Must create tension or surprise.
- Tweets 2–5: One specific point per tweet. Each stands alone.
- Tweet 6–7 (optional): The nuance / counter-argument / zoom out
- Final tweet: Closer + follow CTA ("follow for more on [topic]")

Tone: casual, crypto-native, can be contrarian. Think "thread someone would save."

---

#### LinkedIn Personal

Format: 150–300 words. No headers. No bullet lists unless genuinely necessary. Prose.
- Opening line = Hook (never "I want to share" or "I've been thinking")
- 2–3 paragraphs making the One Thing concrete
- Closer from brief
- End with a question that invites reaction

Tone: sharp operator. High connection value. Smart without trying to sound smart.

---

#### Substack (Personal)

Format: 700–1500 words. This is the long-form.
- Header: the strongest hook from the brief
- Intro paragraph: the tension or question this essay addresses
- Section 1: The observation / what Nick saw
- Section 2: The deeper pattern / what it means
- Section 3: The implication / what to do with this
- Closing: the reframe closer
- Substack CTA: "Subscribe for the next one."

Tone: personal + analytical. Nick's specific experience + a clear point of view. Should feel like smart operator writing, not a hot take.

---

#### LinkedIn Company (Balboa Corp) — COMPLIANCE RULES

Format: 100–200 words. Data-backed. No speculation.

COMPLIANCE CHECKLIST before writing:
- [ ] Every claim sourced from `context/balboa1_facts.md` or Nick's vault
- [ ] No price speculation. No "stablecoins will replace X"
- [ ] No unverified traction claims — only what's actually signed/live
- [ ] "Regulated digital settlement" not "crypto"
- [ ] Never mention competitors by name disparagingly

Tone: institutional thought leadership. Cite real numbers. Sound like a well-run company, not a hype project.

---

#### Company Blog

Format: 800–2000 words. SEO-optimized.
Structure (from claude-blog's answer-first pattern):
1. **Title**: includes primary keyword + is specific (not clickbait)
2. **TL;DR**: 2-3 sentence summary at the top (answer-first)
3. **The Problem** (2-3 paragraphs): make the reader feel the friction
4. **The Insight** (2-3 paragraphs): the One Thing, with proof
5. **How it applies to Maritime/Trade Finance** (specific to Balboa Corp audience)
6. **What to Do Next** (CTA: pilot program, contact, subscribe)
7. **Meta description** (under 160 chars, includes keyword)

Tone: educational, trust-building. Written for: maritime operators, freight forwarders, OTC desk decision-makers who are smart but don't need to be sold to — they need to be informed.

---

### Step 4: Flag if compliance review needed

If the brief has any company LinkedIn or company blog content, append this at the bottom of the draft:

```
⚠️ COMPLIANCE REVIEW RECOMMENDED
Check before publishing:
- All factual claims verified against balboa1_facts.md: [ ]
- No unconfirmed pilot metrics stated as fact: [ ]
- No price speculation present: [ ]
- Legal name used consistently (Balboa Corp / BALBOA1): [ ]
```

### Step 5: Save drafts

Save as `03-BRIEFS/YYYY-MM-DD-[slug]-DRAFTS.md`. Tag: `#written`.

Structure the file with clear H2 headers per platform:
```markdown
# Drafts: [Brief Title]
Source brief: [[YYYY-MM-DD-slug]]
Written: YYYY-MM-DD

## X Thread
[tweets numbered 1–N]

## LinkedIn Personal
[draft]

## Substack
[draft]

## LinkedIn Company
[draft]

## Company Blog
[draft]

## Compliance Checklist
[if applicable]
```

### Step 6: Tell Nick

```
✍️ Content Written: [Title]

Platforms drafted: [list]
Strongest piece: [your honest assessment of which draft is best and why]
Watch for: [any compliance flags or things to double-check before posting]

Saved to 03-BRIEFS/[filename]

After you post: add engagement data to 04-PUBLISHED/ so JARVIS learns what works.
```
