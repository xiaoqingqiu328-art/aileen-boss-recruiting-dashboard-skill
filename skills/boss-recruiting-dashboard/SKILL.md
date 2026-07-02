---
name: boss-recruiting-dashboard
description: Build, audit, customize, or operate a privacy-safe BOSS/Zhipin recruiting dashboard and Chrome-extension workflow for high-volume candidate screening. Use when Codex is asked to work on a local recruiting HTML dashboard, batch candidate parsing from BOSS pages, AI candidate scoring, greeting scripts, follow-up status funnels, accounting/finance-only matching rules, bookmarklet-based unread extraction, Chrome extension scanning, or GitHub-ready packaging of this recruiting assistant without exposing private company, candidate, cookie, or API-key data.
---

# BOSS Recruiting Dashboard

## Purpose

Use this skill to help maintain and improve a local-first recruiting assistant for BOSS/Zhipin workflows. The product pattern is:

1. A recruiter manually copies candidate or unread-chat text from a real logged-in browser.
2. A local HTML dashboard parses, deduplicates, classifies, scores, and tracks candidates.
3. AI scoring and greeting generation are optional and user-configured.
4. Follow-up status is managed in a funnel from pending to hired/rejected.
5. Browser automation that touches BOSS should stay conservative because account-safety risk is high.

Keep all public-facing output generic. Do not expose private company names, brands, candidate records, cookies, local Chrome profiles, API keys, or screenshots containing real personal data.

## Quick Triage

When asked to analyze or modify the dashboard, first identify which surface is involved:

- **Dashboard HTML**: usually `dashboard/*.html` or a renamed local HTML file. Handles parsing, localStorage persistence, rules, AI scoring, processing mode, import/export.
- **Chrome extension**: usually `boss-extension-optimized/`. Handles in-page scanning, floating panel, highlighting, and optional greeting fill/send flows.
- **Python MCP/server scripts**: usually `server.py`, `run_daily.py`, `scraper.py`, `browser.py`, `candidate_db.py`, `search_profile.yaml`. Treat live BOSS automation as fragile and account-sensitive.
- **Public GitHub packaging**: create neutral docs and skill resources; strip company names, candidates, cookies, API keys, profiles, and logs.

Read only the reference file needed for the task:

- For implemented product capabilities and workflows, read `references/dashboard-workflows.md`.
- For screening rule design, especially accounting/finance-only matching, read `references/rule-configuration.md`.
- For public sharing and privacy redaction, read `references/privacy-and-release.md`.

## Operating Principles

- Prefer local-first, human-in-the-loop workflows over unattended scraping or message sending.
- Keep BOSS interactions as user-driven copy/paste, bookmarklet extraction, or explicitly confirmed extension actions unless the user asks for automation and accepts the risk.
- Treat AI output as a ranking aid, not an authority. Rules should still enforce hard constraints such as accounting/finance-only matching, age, education, internships, and exclusion keywords.
- Persist recruiter settings locally via `localStorage` for the standalone HTML dashboard.
- Preserve candidate data on edits. Back up the dashboard before structural migrations.
- Never commit or include `cookies/`, `chrome-profile*/`, logs with real candidate data, exported candidate JSON, screenshots, API keys, or local personal paths in a GitHub release.

## Common Tasks

### Add or adjust screening rules

1. Locate the rules defaults and `classify(candidate)` logic in the dashboard HTML.
2. Add a visible settings entry if the rule should be recruiter-editable.
3. Store settings with a versioned `localStorage` key.
4. Ensure AI grades cannot bypass hard filters. For example, if accounting-only mode is enabled, candidates without accounting/finance hits must not enter strong match or backup buckets even if AI returns A/B.
5. Re-render all candidate buckets after saving settings.
6. Run a JavaScript syntax check by extracting the inline script and using `node --check`.

### Prepare a public GitHub version

1. Rename or describe the product generically, for example "BOSS Recruiting Dashboard" or "Local Recruiting Screening Assistant".
2. Redact private names and examples. Use fake companies and synthetic candidates.
3. Remove generated data, cookies, Chrome profiles, screenshots, local logs, and API keys.
4. Keep skill files concise: `SKILL.md`, optional `agents/openai.yaml`, and focused `references/`.
5. Add a release note or GitHub README outside the skill folder only if the user explicitly asks for repository marketing material.

### Diagnose mismatched results

Check these in order:

1. Whether the active job mode matches the role, such as accounting/finance-only versus ecommerce-operations.
2. Whether localStorage contains old rule settings overriding new defaults.
3. Whether AI grades are overriding hard filters.
4. Whether parsing is missing important resume sections, causing candidates to fall into "needs details".
5. Whether status filters or bucket filters are hiding rows.

## Validation Checklist

- `SKILL.md` has only `name` and `description` in frontmatter.
- No private company or brand names are present in the skill.
- No candidate names, phone numbers, resumes, cookies, API keys, logs, or browser profiles are included.
- `agents/openai.yaml` default prompt explicitly mentions `$boss-recruiting-dashboard`.
- References are short, task-focused, and directly linked from `SKILL.md`.
