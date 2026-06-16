# 🧠 LifeOS Suite

**A personal operating system of cooperating AI agents — knowledge, business, and life — that you run from your phone.**

LifeOS is three specialized agents that watch your real inputs (email, calendar, messages, research) and turn them into ranked daily actions, ready-to-send drafts, and gentle reminders — then learn from what you actually do. No SaaS subscriptions, no servers. It runs on your own Mac and talks to you through Telegram.

> Built by Nick Marton as a personal command center. This repo is the **public overview** — the operational code and personal data live in private repos.

---

## What it is, in one picture

![System architecture](diagrams/architecture.svg)

*Three agents share one brain. You talk to them through Telegram — Grace asks you questions and sends alerts; Saved Messages holds your briefs and reminders. Everything runs automatically on your Mac.*

| Agent | Nickname | What it owns |
|---|---|---|
| 🧠 **JARVIS** | the knowledge engine | Captures ideas and research, finds connections, drafts content. Lives in an Obsidian vault. |
| 💼 **BizBot** | the business engine | Runs your outreach CRM, ranks who to contact, writes personalized drafts, tracks what gets replies. |
| 🌙 **LifeBot** | the life engine | Triages your inboxes, manages your calendar, maintains a personal CRM of the people in your life, and protects your time. |
| 📱 **Grace** | the voice | The interactive layer. Asks you one-tap questions, takes commands by text, and sends notifications. |

---

## A day in the life

![Daily and weekly flow](diagrams/daily-flow.svg)

*You don't "use" LifeOS so much as receive it. The schedule does the work; you act on what arrives and answer the occasional question.*

**Your entire daily involvement:** read the morning dashboard (or listen to the voice note), work the top actions by copy-pasting drafts, glance at the evening brief, and reply to Grace when she asks something. ~10 minutes of decisions; the system does the rest.

---

## How it gets smarter

![Data flow between agents](diagrams/data-flow.svg)

*The agents feed each other. Your research personalizes your outreach. Your outreach results teach the system which angles work. The people you actually reply to shape who it reminds you about. Every week compounds.*

---

## The two-minute pitch

Most "AI assistants" are a chat box you have to remember to open. LifeOS is the opposite: it's **always running, acts in the tools you already use, and only interrupts you when it needs a decision.** It drafts the email and leaves it in your Drafts folder. It schedules the reminder and it fires at the right moment. It notices you've lost touch with a friend and hands you an opener. It asks "did this deal move?" and files your answer in the right place automatically.

It's three agents instead of one because **business, knowledge, and life are different jobs** — but they share context, so a news item you saved this morning can sharpen a sales message this afternoon.

---

## Documentation

- 📘 **[Quickstart](guide/quickstart.md)** — the daily & weekly rhythm, one page.
- 📗 **[Full Manual](guide/manual.md)** — every command, when to use it, how it works, troubleshooting.
- 🗺️ **[Diagrams](diagrams/)** — architecture, daily flow, data flow.

---

## Design principles

1. **Propose, don't auto-send.** Drafts wait for your approval. The system never speaks to anyone as you without you hitting send.
2. **One source of truth per thing.** The CRM sheet is the CRM; the vault is the knowledge; no duplicated state that can drift.
3. **Graceful degradation.** Any integration can be offline and the rest keeps working.
4. **Learn from outcomes, not opinions.** It measures what you actually sent and kept, and adapts.
5. **Privacy first.** Personal data stays on your machine and in your private accounts. This public repo contains none of it.

---

*LifeOS Suite is a personal project. The overview here is shared to show the architecture and ideas; the operational code and all personal data are private.*
