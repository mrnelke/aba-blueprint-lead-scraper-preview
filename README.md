# BP002 — Lead Scraper Blueprint
### Agent Builder Academy — agentbuilderacademy.com

> **This is the public preview.** Full source code, documentation, and n8n workflow are available after purchase.
> 👉 **[Get Access — agentbuilderacademy.com](https://agentbuilderacademy.com)**

---

A production-ready blueprint for building a stealth lead scraper with Claude Code. Extract **name, email, phone, website, and address** from any target website and export to CSV — in under 15 minutes from setup to first leads.

Designed for solo automation builders who want a clean, secure, and n8n-ready foundation they can adapt to any site.

---

## What You Will Build

A Python scraper that:
- Opens a real browser in **stealth mode** (undetectable as a bot)
- Navigates to your target website and handles all pages automatically
- Handles common blockers: **cookie walls**, **"click to reveal" buttons**, **JS-obfuscated emails**
- Extracts: name, email, phone, website, address
- Writes results to `output/leads.csv`
- Connects to **n8n** via a ready-to-import workflow (no server needed)

---

## What's Included

```
bp002-lead-scraper/
├── scraper.py              # working stealth scraper, fully commented
├── n8n/workflow.json       # import-ready n8n workflow
├── .claude/skills/         # /security-check Claude Code skill
├── CLAUDE.md               # persistent agent context (ABA methodology)
├── MEMORY.md               # project diary template
├── QUICK_START.md          # 15 minutes to first leads
├── docs/
│   ├── adapting.md         # step-by-step for any new target site + checklist
│   ├── troubleshooting.md  # every real error with exact fixes
│   ├── architecture.md     # how it's built and why
│   ├── decisions.md        # every key decision with reasoning
│   └── workflows.md        # setup, run, commit, iterate
├── requirements.txt
├── .env.example
├── .pre-commit-config.yaml # automatic security checks on commit
└── LICENSE
```

---

## How Claude Code Is Used

This blueprint is built on the **ABA (Agent Builder Academy) methodology** — a structured approach that makes Claude persistent, focused, and production-ready from the first session.

### CLAUDE.md — Persistent Context
Claude reads the stack, architecture rules, and iteration model at the start of every session. You never re-explain the project.

### MEMORY.md — Project Diary
Every decision, discovered pattern, and open question is logged. New sessions pick up exactly where you left off.

### `/security-check` Skill
One command scans all staged files for secrets, hardcoded URLs, large files, and `.gitignore` gaps before you commit. A pass/fail verdict with file and line references.

### Iteration Model
The scraper is built one step at a time — write a function, run a live test, fix the blocker, commit, repeat. No debugging compound failures.

---

## Security Built In

Two layers protect secrets and scraped data from entering version control:

**Automatic** — git pre-commit hooks fire on every `git commit`:
| Hook | What it catches |
|------|-----------------|
| `detect-secrets` | Passwords, tokens, API keys |
| `detect-private-key` | PEM/RSA private keys |
| `check-added-large-files` | Files over 500 KB |
| `check-merge-conflict` | Unresolved conflict markers |

**Manual** — `/security-check` Claude Code skill for deeper review before sensitive commits.

Target URLs, credentials, and scraped lead data (PII) are always gitignored.

---

## n8n Integration

A ready-to-import `n8n/workflow.json` is included.

Import it → update two file paths → run. Leads arrive as structured JSON items. Add your destination: **Google Sheets, Airtable, a CRM API, Notion** — whatever comes next in your workflow.

No API server. No extra infrastructure. One Execute Command node and you're done.

---

## Adapting to Any Site

The included `docs/adapting.md` is a 9-step guide with a full checklist for pointing the scraper at any new target site. It covers:

- Finding real CSS selectors from the live rendered HTML (not AI guesses)
- Handling cookie walls, email obfuscation (4 patterns), click-to-reveal
- Pagination detection for arrows, numbered links, and infinite scroll
- A checklist to confirm everything works before committing

`docs/troubleshooting.md` documents every real issue hit during development — with the exact error message and fix for each.

---

## Prerequisites

| Tool | Version | Install |
|------|---------|---------|
| Python | 3.11+ | `brew install python` |
| pipx | any | `brew install pipx` |
| Git | any | pre-installed on Mac |
| Claude Code | latest | [claude.ai/code](https://claude.ai/code) |

---

## Get Access

👉 **[Purchase at agentbuilderacademy.com](https://agentbuilderacademy.com)**

After purchase you will receive access to the private repository containing the full source code, all documentation, and the n8n workflow. Follow `QUICK_START.md` and you will have your first leads within 15 minutes.

---

## Questions?

Open an issue in this repo or reach out at agentbuilderacademy.com.

---

Built with the ABA Starter Kit — Agent Builder Academy
agentbuilderacademy.com
