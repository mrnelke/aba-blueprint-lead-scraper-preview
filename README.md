# ABA — Lead Scraper Blueprint
### Agent Builder Academy — agentbuilderacademy.com

> **This is the public preview.** Full source code, documentation, and n8n workflows are available after purchase.
> 👉 **[Get Access — agentbuilderacademy.com](https://agentbuilderacademy.com)**

---

A production-ready blueprint for building a stealth lead scraper with Claude Code. Extract **name, email, phone, website, and address** from any target website and export to CSV — in under 15 minutes from setup to first leads.

Designed for solo automation builders who want a clean, secure, n8n-ready foundation they can run on a schedule across multiple sites.

---

## What You Will Build

A Python scraper that:
- Opens a real browser in **stealth mode** (undetectable as a bot)
- Handles all pages automatically with pagination detection
- Handles common blockers: **cookie walls**, **"click to reveal" buttons**, **JS-obfuscated emails**
- Extracts: name, email, phone, website, address
- **Deduplicates automatically** — never writes the same lead twice
- Runs **multiple target sites** from a single YAML config file
- Exports to CSV with a full **run log** (timestamp, new leads, skipped duplicates)
- Connects to **n8n** on a schedule via two ready-to-import workflows

---

## What's Included

```
bp002-lead-scraper/
├── scraper.py                    # stealth scraper with CLI, deduplication, multi-site
├── sites.example.yaml            # multi-site config template (3 documented examples)
├── n8n/
│   ├── workflow.json             # manual trigger workflow
│   └── workflow-scheduled.json  # scheduled pipeline (weekly, with cron reference)
├── .claude/skills/               # /security-check Claude Code skill
├── CLAUDE.md                     # persistent agent context (ABA methodology)
├── MEMORY.md                     # project diary template
├── QUICK_START.md                # 15 minutes to first leads
├── docs/
│   ├── adapting.md               # step-by-step guide for any new target site
│   ├── troubleshooting.md        # every real error with exact fixes
│   ├── architecture.md           # system design, selectors, email decoding
│   ├── decisions.md              # every key decision with reasoning
│   └── workflows.md              # all commands — single site, multi-site, n8n
├── requirements.txt
├── .env.example
├── .pre-commit-config.yaml       # automatic security checks on commit
└── LICENSE
```

---

## CLI — What You Can Run

```bash
# Single site (reads .env)
python3 scraper.py
python3 scraper.py --append               # skip duplicates
python3 scraper.py --limit 2             # first 2 pages only
python3 scraper.py --headless false      # watch the browser

# Multi-site (reads sites.yaml)
python3 scraper.py --site my-directory   # one named site
python3 scraper.py --all                  # all sites
python3 scraper.py --all --append         # all sites, skip duplicates
```

---

## How Claude Code Is Used

This blueprint is built on the **ABA (Agent Builder Academy) methodology** — a structured approach that makes Claude persistent, focused, and production-ready from the first session.

### CLAUDE.md — Persistent Context
Claude reads the stack, architecture rules, and iteration model at the start of every session. You never re-explain the project.

### MEMORY.md — Project Diary
Every decision, discovered pattern, and open question is logged. New sessions pick up exactly where you left off.

### `/security-check` Skill
One command scans all staged files for secrets, hardcoded URLs, large files, and `.gitignore` gaps before you commit.

### Iteration Model
The scraper is built one step at a time — write a function, run a live test, fix the blocker, commit, repeat.

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

**Manual** — `/security-check` Claude Code skill for deeper pre-commit review.

Target URLs, credentials, and scraped lead data (PII) are always gitignored. `sites.yaml` is gitignored — your target sites stay private.

---

## n8n Integration

Two workflows included:

**`n8n/workflow.json`** — manual trigger. Import → update paths → run.

**`n8n/workflow-scheduled.json`** — runs on a schedule (default: every Monday 9am). Includes:
- Configurable cron expression with a reference card
- `--append` flag built in — deduplication is automatic
- Destination slot ready to connect to Google Sheets, HubSpot, Airtable, or any HTTP endpoint

No API server. No extra infrastructure.

---

## Multi-Site Config

`sites.yaml` defines all your target directories in one file. Each site has its own selectors, email decoding strategy, pagination type, and output file.

Three selector strategies: **icon-anchored**, **CSS selector**, **semantic HTML**
Three email strategies: **TYPO3 JS decode**, **plain mailto**, **CSS selector**
Three pagination strategies: **arrow (→)**, **CSS selector**, **single page**

`docs/adapting.md` walks through all three with examples.

---

## Adapting to Any Site

`docs/adapting.md` is a 9-step guide with a full checklist:
- Dumping the real rendered HTML (not guessing selectors from AI)
- Handling cookie walls, email obfuscation (4 patterns), click-to-reveal
- Configuring `sites.yaml` for the new site
- Pagination patterns for any structure

`docs/troubleshooting.md` documents every real issue hit during development — exact error and fix for each.

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

After purchase you will receive access to the private repository with full source code, all documentation, and both n8n workflows. Follow `QUICK_START.md` and you will have your first leads within 15 minutes.

---

## Questions?

Open an issue in this repo or reach out at agentbuilderacademy.com.

---

Built with the ABA Starter Kit — Agent Builder Academy
agentbuilderacademy.com
