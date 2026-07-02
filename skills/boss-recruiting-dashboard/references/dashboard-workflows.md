# Dashboard Workflows

## Implemented Capabilities

- Batch paste parsing for BOSS/Zhipin candidate lists and unread-chat lists.
- Accumulated local candidate database in browser `localStorage`.
- Fingerprint-based deduplication for repeated paste/import operations.
- Bucket classification: strong match, backup, needs details, manual review, not qualified.
- KPI cards and work summary for total candidates, pending outreach, replies, interviews, offers, and hires.
- Recruiting funnel status tracking: pending, greeted, replied, WeChat/contact exchanged, phone, interview, offer, hired, rejected, skipped.
- Detail expansion for raw text, notes, custom tags, full resume supplements, AI score summaries, and greeting scripts.
- Processing mode for rapid human-in-the-loop outreach: copy candidate name, copy greeting, open candidate link if available, mark status, advance to next person.
- Import/export candidate data as JSON.
- Bookmarklet-based unread conversation extraction from the BOSS chat page.
- Optional AI scoring and personalized greeting generation through user-configured model providers.
- Optional local collector/importer controls may exist, but public guidance should default to safe manual copy/paste because automated BOSS access can trigger account restrictions.

## Recommended User Flow

1. Open BOSS/Zhipin in the user's normal logged-in browser.
2. Copy a candidate list, recommendation page, or unread-chat list.
3. Paste into the dashboard and parse.
4. Review bucket counts and quality tips.
5. Configure rules for the active role.
6. Run AI scoring only after hard filters are correct.
7. Process strong matches first, then backups, then needs-details candidates.
8. Export data periodically for backup.

## Chrome Extension Flow

Use the extension when the user wants in-page scanning rather than paste parsing:

1. Open a BOSS candidate page.
2. Trigger extension scan from the popup.
3. Review the floating panel on the page.
4. Use highlight/open/send actions only when the user confirms the side effect.

Avoid presenting extension-triggered sending as fully automatic. It should be a controlled action with a visible candidate and draft message.
