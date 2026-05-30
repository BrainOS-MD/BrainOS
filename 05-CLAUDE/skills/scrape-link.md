# Skill: Scrape Link

**Trigger phrases:** "scrape [URL]" / "read this link [URL]" / "file this [URL]" / any message that contains a raw URL without other context

## What this does

When Nick drops a URL (from his phone, browser, or AirDrop), this skill fetches the page, strips all the clutter (ads, nav, footers, boilerplate), extracts the signal, and files a clean summary into `00-INBOX/` for `process-inbox` to sort.

This is the link-to-intelligence pipeline. Zero friction at capture time.

## Process

### Step 1: Fetch and defuddle

Fetch the full page content from the URL.

Apply defuddle logic — strip:
- Navigation menus and header/footer boilerplate
- Cookie banners, subscription overlays
- Social share buttons, author bylines (keep author name)
- Advertising text and sponsored content
- "Related articles" / recommendation blocks
- Legal fine print at page bottom

Keep:
- Article title
- Author name and publication
- Publication date
- The full article body text
- Any specific statistics, data points, or quotes
- Any named companies, people, or events

Target: 40–60% token reduction from raw page to cleaned content.

### Step 2: Extract the intelligence

From the cleaned content, identify:

**Primary claim:** What is the single most important thing this article/page says?
**Key data points:** Any specific numbers, percentages, dates, or figures
**Named entities:** Companies, people, products, regulations mentioned
**BALBOA1 relevance score (1–5):**
- 1 = tangentially related to Nick's world
- 2 = in Nick's broader domain (fintech, shipping, crypto)
- 3 = directly relevant to BALBOA1's market or thesis
- 4 = a proof point or threat or market signal Nick needs to know
- 5 = immediately actionable (use in outreach, content, or fundraising)

### Step 3: Create an INBOX note

Save as `00-INBOX/_YYYY-MM-DD-[source-name]-scrape.md`:

```markdown
---
source-url: [URL]
scraped: YYYY-MM-DD
author: [if available]
publication: [if available]
b1-relevance: [1-5]
type: scraped-link
---

# [Article Title]

**Source:** [Publication] — [Date]
**Primary claim:** [one sentence]

## Key Intelligence

[2–4 bullet points with the most important facts, numbers, or signals. Specific and concrete only.]

## Notable Quotes or Data
[Any direct quotes or specific statistics worth preserving verbatim]

## BALBOA1 Signal
[If b1-relevance ≥ 3: why this matters, what to do with it. Be specific.]

## Raw Notes
[Any additional context Nick might want. 3–5 sentences max.]
```

### Step 4: Report back

```
🔗 Scraped: [Article Title]
Source: [Publication] ([Date])
B1 Relevance: [X/5]

Primary claim: [one sentence]

[If ≥ 4]: ⚡ High relevance — suggest adding to BALBOA1 proof stack or using in content
[If ≥ 3]: → Filed to INBOX for processing. Run "process inbox" to classify.
[If < 3]: → Filed to INBOX. Low B1 relevance but useful for context.
```

## Handling special cases

**Paywalled content**: Note "content behind paywall — extracted what was visible" and file whatever was accessible (headline, subhead, preview).

**PDF links**: Extract text from the PDF if possible. File as normal.

**Twitter/X links**: Extract the tweet text + any linked content if visible. Note the author handle.

**LinkedIn posts**: Extract text if accessible. Note the author name and company.

**YouTube**: Can't watch video — extract: title, description, and any transcript if the URL provides one. Note the channel name.

**AirDropped .md or .txt files**: If a file arrives directly (not a URL), read it as-is and file directly to INBOX after adding the frontmatter template above.

## AirDrop auto-routing

When a `.md` or `.txt` file arrives in the Mac Downloads folder via AirDrop from Nick's phone, the `watch-inbox.sh` script (see `JARVIS_SETUP.md`) automatically moves it to `00-INBOX/`. You'll pick it up next time you process the inbox.

For URLs from the phone: Nick can AirDrop a `.txt` file containing just the URL, or paste the URL directly into a Claude Code session.
