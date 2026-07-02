# BOSS Recruiting Dashboard Skill

> A privacy-safe Codex skill for building and improving a local-first BOSS/Zhipin recruiting dashboard.

![Local First](https://img.shields.io/badge/local--first-yes-10b981)
![AI Assisted](https://img.shields.io/badge/AI-assisted-7c3aed)
![Human In The Loop](https://img.shields.io/badge/human--in--the--loop-safe-0369a1)
![Codex Skill](https://img.shields.io/badge/Codex-Skill-111827)
![GitHub stars](https://img.shields.io/github/stars/xiaoqingqiu328-art/aileen-boss-recruiting-dashboard-skill?style=social)
![GitHub forks](https://img.shields.io/github/forks/xiaoqingqiu328-art/aileen-boss-recruiting-dashboard-skill?style=social)

## Why This Exists

Recruiting on BOSS/Zhipin gets painful fast:

- hundreds or thousands of candidates to screen
- repeated copy/paste judgment work
- scattered follow-up status
- risky automation that can trigger account restrictions
- role-specific filters that are hard to keep consistent

This skill helps Codex maintain a safer workflow: **copy candidate data manually, screen locally, use AI for judgment support, and keep outreach recruiter-controlled.**

## What It Helps You Build

- Batch candidate parsing from copied BOSS/Zhipin pages
- Local candidate dashboard with deduplication
- Configurable screening rules
- Accounting/finance-only hard matching
- AI-assisted candidate scoring
- Personalized greeting drafts
- Follow-up funnel tracking
- Bookmarklet-based unread conversation extraction
- Chrome-extension-assisted page scanning
- GitHub-safe packaging without leaking private data

## Safety Positioning

This is not positioned as a black-box auto-scraper.

Recommended wording:

- local-first
- recruiter-controlled
- human-in-the-loop
- AI-assisted screening
- copy/paste import
- account-safety conscious

Avoid promising unattended scraping or automatic mass messaging. Those workflows can be fragile and risky on BOSS/Zhipin.

## Install As A Codex Skill

Copy the skill folder into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
cp -R skills/boss-recruiting-dashboard ~/.codex/skills/
```

Then use it in Codex:

```text
Use $boss-recruiting-dashboard to improve my local BOSS recruiting dashboard and screening rules.
```


## Want To Know If People Use It

As the repository owner, you can track adoption without adding invasive analytics:

- **Stars**: quick signal that people like or save the skill
- **Forks**: signal that people want to customize it
- **Issues**: users can open an `I use this skill` issue to share how they use it
- **GitHub Insights → Traffic**: repository views and clones, visible to maintainers only

If this skill helps you, please star the repo or open a short usage issue. That feedback helps prioritize future templates and screening workflows.

## Skill Contents

```text
skills/boss-recruiting-dashboard/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── dashboard-workflows.md
    ├── privacy-and-release.md
    └── rule-configuration.md
```

## Example Prompts

```text
Use $boss-recruiting-dashboard to add an accounting-only screening mode.
```

```text
Use $boss-recruiting-dashboard to audit my dashboard before I share it on GitHub.
```

```text
Use $boss-recruiting-dashboard to redesign my candidate buckets for a finance role.
```

```text
Use $boss-recruiting-dashboard to check whether AI grades can bypass hard filters.
```

## Public Release Checklist

Before publishing any recruiting assistant code, remove:

- company names and brand names
- real candidate data
- screenshots with personal information
- API keys and model provider tokens
- cookies and session files
- Chrome profile folders
- local logs and exported candidate JSON
- absolute local paths

This repository contains only the neutral Codex skill guidance. It does not include real candidate data, credentials, browser profiles, or private company details.

## License

MIT
