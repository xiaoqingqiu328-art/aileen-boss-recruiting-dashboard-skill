# Privacy And Release Checklist

Use this checklist before sharing the skill or the recruiting assistant on GitHub.

## Must Redact

- Private company names, brand names, store names, and internal aliases.
- Real candidate names, resumes, phone numbers, WeChat IDs, emails, URLs, and screenshots.
- API keys, model provider tokens, cookies, session files, and localStorage exports.
- Chrome profile folders such as `chrome-profile/` and `chrome-profile-auto/`.
- Browser cookies folders such as `cookies/`.
- Logs and reports containing real candidate data.
- Absolute local user paths in public docs.

## Safe To Keep

- Generic feature descriptions.
- Synthetic examples.
- Rule templates and keyword lists.
- UI workflow instructions.
- Non-sensitive code patterns.
- Public installation notes that do not include credentials.

## Suggested Public Positioning

Position the tool as a local-first recruiter productivity assistant:

- Batch candidate screening from copied BOSS/Zhipin text.
- AI-assisted scoring and greeting drafts.
- Configurable role-specific filters, including accounting/finance-only matching.
- Follow-up funnel and outreach workbench.
- Privacy-conscious: data stays local unless the user configures an AI provider.

Avoid claiming fully automated scraping or unattended message sending. Safer wording:

- "Human-in-the-loop"
- "Local-first"
- "Copy/paste import"
- "Recruiter-controlled outreach"
- "AI-assisted screening"
