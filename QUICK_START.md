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

## Step 7 — Configure your target site

**Option A — Single site (.env)**

Edit `.env` and set `TARGET_URL` and `BASE_URL`. Then run:
```bash
python3 scraper.py
```

**Option B — Multi-site (sites.yaml)**

```bash
cp sites.example.yaml sites.yaml
# Edit sites.yaml and add your target sites
python3 scraper.py --site my-site-name --limit 1   # test first
python3 scraper.py --all --append                    # run all sites
```

Tell Claude: *"The target site is [URL]. Add it to sites.yaml with the correct selectors."* Claude will inspect the HTML, find the real selectors, and configure the entry.

---

## Step 8 — Run and verify

```bash
python3 scraper.py --limit 1      # test on first page only
head -5 output/leads.csv           # check the output
python3 scraper.py --append        # full run, skip duplicates
cat output/runs.log                # see run history
```

---

## Step 9 — Set up the scheduled n8n pipeline

1. In n8n → Import from file → `n8n/workflow-scheduled.json`
2. Update the two file paths
3. Set your schedule (default: every Monday 9am)
4. Connect your destination: Google Sheets, CRM, Airtable
5. Activate

Deduplication runs automatically on every scheduled run.

---

## Done

Your leads pipeline is live — runs on schedule, skips duplicates, pushes to your destination automatically. See `docs/workflows.md` for all available commands.

---

👉 **[Purchase at agentbuilderacademy.com](https://agentbuilderacademy.com)**

---

Built with the ABA Starter Kit — Agent Builder Academy
agentbuilderacademy.com
