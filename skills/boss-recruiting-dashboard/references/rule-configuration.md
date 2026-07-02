# Rule Configuration

## Role Templates

The dashboard should support any hiring role. Treat job fit as configuration, not as a single hard-coded position.

A role template should include:

- Role name shown in the settings panel and top summary band.
- Required keywords that must appear for a candidate to count as a match.
- Preferred keywords that increase confidence but are not mandatory.
- Exclusion keywords that force manual review or rejection.
- Hard filters such as age, education, experience, location, internship status, and full-time degree requirements.
- Bucket thresholds for strong match, backup, needs details, manual review, and not a fit.

Suggested starter templates:

- Finance/accounting: accounting, finance, tax, invoice, settlement, reconciliation, ERP.
- Ecommerce operations: PDD, Taobao, Tmall, JD, Douyin, Kuaishou, Xiaohongshu, Amazon, Temu.
- Customer service: customer support, after-sales, online chat, complaints, service scripts.
- Sales: business development, sales conversion, client follow-up, negotiation, CRM.
- Admin/HR: administration, attendance, payroll, recruitment coordination, office support.
- Technical: frontend, backend, data, testing, operations, product, project delivery.
- Custom: recruiter-defined required, preferred, and exclusion keywords.

## Hard-Match Gate

When a role requires specific signals, AI grades must not bypass the hard gate.

Implementation pattern:

```js
const requiredHits = matchedWords(candidateText, activeRequiredWords());
const hasRequiredRoleMatch = !rules.requireRoleKeyword || requiredHits.length > 0;

if (!hasRequiredRoleMatch) {
  bucket = "不符合";
}

if (candidate.aiGrade && !hasRequiredRoleMatch) {
  bucket = "不符合";
}
```

Use this same pattern for any role, not just finance/accounting. For example, a customer service role may require customer-support signals, while an operations role may require platform-operation signals.

## Keyword Groups

Use separate groups so recruiters can tune the role without code changes:

- **Required keywords**: must match when the role needs a hard gate.
- **Preferred keywords**: add score or confidence.
- **Negative keywords**: reject or lower score.
- **Manual review keywords**: do not reject automatically; move to human review.
- **Equivalent terms**: synonyms and platform names, including Chinese/English variants.

## Hard Filters

Common hard filters:

- Over configured age limit
- Below required education
- Fresh graduate or currently in school
- Internship-only experience
- Non-full-time bachelor if the role requires full-time degree
- Custom exclusion keywords

Manual review flags:

- Local hometown/residence concerns
- Entrepreneurship/self-employed history
- Work instability or long gap
- Ambiguous education timeline
- Salary, commute, or schedule mismatch

## UI Requirements

If adding a rule, add all four pieces:

1. A default value in the rules defaults object.
2. A visible input in the rules settings panel.
3. Load/save logic for that input.
4. A short summary in the top rule band.

The UI should make the active role obvious and allow recruiters to switch or edit templates without changing code.
