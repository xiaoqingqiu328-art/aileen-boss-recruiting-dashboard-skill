# Rule Configuration

## Accounting/Finance-Only Mode

For accounting roles, matching should be strict:

- Only candidates with accounting or finance signals should count as matching.
- Non-accounting ecommerce operators should not enter strong match or backup buckets.
- AI grades must not override the accounting/finance hard gate.

Suggested accounting/finance match terms:

- 会计, 财务, 电商会计, 电商财务, 网店会计, 跨境财务
- 出纳, 总账, 成本会计, 税务, 报税, 开票, 发票
- 应收, 应付, 往来账, 对账, 结算, 核算, 审计
- 财务分析, 财务BP, ERP, 金蝶, 用友, 管家婆
- 初级会计, 中级会计, 注册会计, CPA

Implementation pattern:

```js
const requireAccounting = rules.jobMode === "accounting" || rules.requireAccounting;
const accountingHits = matchedWords(candidateText, activeAccountingWords());
const hasAccountingMatch = accountingHits.length > 0;

if (requireAccounting && !hasAccountingMatch) {
  bucket = "不符合";
}

if (candidate.aiGrade && requireAccounting && !hasAccountingMatch) {
  bucket = "不符合";
}
```

## Ecommerce-General Mode

Use ecommerce-general mode only when the role can accept ecommerce operators across platforms:

- 拼多多 / PDD
- 天猫 / 淘宝
- 京东
- 抖音 / 快手 / 小红书 / 唯品会
- 亚马逊 / Temu / cross-border platforms
- 电商会计 / 财务

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

## UI Requirements

If adding a rule, add all four pieces:

1. A default value in the rules defaults object.
2. A visible input in the rules settings panel.
3. Load/save logic for that input.
4. A short summary in the top rule band.
