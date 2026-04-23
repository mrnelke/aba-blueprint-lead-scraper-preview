# Quick Start — 15 Minutes to First Leads

> **This is a preview.** Full access — including the working scraper, all docs, and the n8n workflow — is available after purchase.
> 👉 **[Get Access — agentbuilderacademy.com](https://agentbuilderacademy.com)**

---

Here is exactly what the setup looks like after purchase.

---

## What you need first

- Mac with [Homebrew](https://brew.sh) installed
- [Claude Code](https://claude.ai/code) installed
- The target website URL you want to scrape

---

## Step 1 — Install system tools (once per machine)

```bash
brew install python pipx
pipx install pre-commit
pipx install detect-secrets
```

---

## Step 2 — Clone the blueprint (after purchase)

You will receive access to the private repository. Then:

```bash
git clone https://github.com/mrnelke/aba-blueprint-lead-scraper-starter.git
cd aba-blueprint-lead-scraper-starter
```

---

## Step 3 — Set up the Python environment

```bash
python3 -m venv venv
source venv/bin/activate
pip3 install -r requirements.txt
playwright install chromium
pip3 install -r requirements-dev.txt
```

---

## Step 4 — Set up security hooks

```bash
detect-secrets scan > .secrets.baseline
pre-commit install
```

---

## Step 5 — Configure your target site

```bash
cp .env.example .env
```

Open `.env` and fill in your values:

```
TARGET_URL=https://your-target-site.com/directory-page/
BASE_URL=https://your-target-site.com
OUTPUT_FILE=output/leads.csv
HEADLESS=true
```

---

## Step 6 — Open in Claude Code

```bash
claude
```

Claude reads `CLAUDE.md` and `MEMORY.md` automatically and knows the full project context from the first message.

---

## Step 7 — Adapt the scraper to your site

Tell Claude:

> "The target site is [URL]. Please inspect the HTML and update the selectors in scraper.py to extract name, email, phone, website, and address."

Claude will dump the rendered HTML, find the real CSS selectors, update the extraction logic, and handle any blockers it hits.

---

## Step 8 — Run the scraper

```bash
python3 scraper.py
```

```bash
head -5 output/leads.csv
```

---

## Done

Your leads are in `output/leads.csv` — open in Excel, import into your CRM, or connect to n8n using the included `n8n/workflow.json`.

---

👉 **[Purchase at agentbuilderacademy.com](https://agentbuilderacademy.com)**

---

Built with the ABA Starter Kit — Agent Builder Academy
agentbuilderacademy.com
