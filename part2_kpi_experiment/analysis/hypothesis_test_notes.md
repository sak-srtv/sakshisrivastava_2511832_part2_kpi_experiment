# Hypothesis Test Notes

## Business Decision Context

The business must decide whether the new onboarding and activation campaign should be launched to all users. The experiment compares the treatment group against the existing onboarding experience in the control group.

## Metric Being Tested

- **Metric:** Onboarding completion rate
- **Reason for choosing this metric:** The dataset does not contain a direct "activation within the first week" variable, so onboarding completion is the closest available proxy for early activation and product engagement.

## Hypotheses

- **Null hypothesis (H0):** The treatment group has the same or lower onboarding completion rate compared to the control group.
- **Alternate hypothesis (H1):** The treatment group has a higher onboarding completion rate compared to the control group.

## Test Direction

- **Test type:** One-tailed test
- **Reason:** The decision is concerned with whether the treatment improves the primary metric, not whether it is merely different.

## Significance Level

- **Significance level:** 0.05 (5%)
- **Reason:** This is a standard threshold for business experiments, balancing the risk of false positives with the need for actionable insight.

## Interpretation Logic

- If the test result is statistically significant at the 5% level and shows a higher onboarding completion rate for the treatment group, it supports broader rollout of the campaign.
- If the result is not statistically significant or the treatment does not show improvement, the campaign should not be launched broadly without further refinement.
- The decision should also account for guardrail metrics such as refund rate, support ticket rate, days to convert, engagement score, and revenue quality, to ensure the improvement is not offset by user experience or financial risk.

## Test Output

- Control onboarding completion rate: 15.652% (108 / 690)
- Treatment onboarding completion rate: 21.127% (150 / 710)
- Z statistic: 2.641
- P-value (one-tailed): 0.00413
- Significance level: 0.05
- Decision rule: Reject H0 if p < 0.05
- Result: **Reject H0** — the treatment group shows a statistically significant improvement in onboarding completion rate.

## Business Interpretation

The test indicates the new onboarding campaign is likely to improve early activation proxy performance. Because onboarding completion is strongly linked to user activation and retention, this result supports scaling the campaign if guardrail metrics remain acceptable.

## Guardrail Evidence

- Refund rate: increased from 0.00% in Control to 0.42% in Treatment.
- Support ticket rate: increased from 14.78% in Control to 24.79% in Treatment.
- Engagement score: improved from 57.03 to 62.94.
- Average days to convert among converters: improved from 8.86 to 6.40.
- Paid conversion rate: improved from 3.19% to 7.04%.
- Average revenue per user: increased from 51.97 to 54.25.

## Segment Insight

The treatment improved onboarding completion across `region`, `device_type`, and `traffic_source` segments, with especially strong relative gains for Organic and Referral traffic sources.
