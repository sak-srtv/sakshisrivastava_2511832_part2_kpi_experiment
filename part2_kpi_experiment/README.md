# Onboarding & Activation Campaign Experiment

## 1. Business Context

This analysis evaluates whether a new onboarding and activation campaign should be launched across all users for a subscription-based digital product. The campaign aims to improve early conversion and engagement, which impacts trial activation, paid conversion, and retention. The decision affects product, growth, customer success, and revenue teams.

## 2. Dataset Description

- Source: `data/campaign_experiment_data.xlsx`
- Cleaned dataset: `analysis/experiment_analysis.xlsx`
- Summary output: `outputs/experiment_summary.xlsx`
- Key columns: `user_id`, `experiment_group`, `region`, `device_type`, `traffic_source`, `plan_type`, `visited_landing_page`, `started_trial`, `completed_onboarding`, `converted_to_paid`, `revenue_30d`, `support_tickets_30d`, `refund_requested`, `days_to_convert`, `engagement_score`
- Total observations: 1,408 users

## 3. North Star Metric Selected

- **North Star:** Onboarding completion rate
- **Why:** The dataset does not contain a direct activation-in-week-one metric, so onboarding completion serves as the strongest proxy for early activation and product adoption.
- **Business connection:** Higher onboarding completion should feed trial activation, paid conversion, and longer-term retention.

## 4. KPI Tree Summary

- North Star metric: onboarding completion rate
- Primary drivers: onboarding flow completion, early feature use, first session depth
- Sub-drivers: step clarity, progress guidance, first action completion, setup success, time to first action, session engagement score
- Guardrails: refund rate, support ticket rate, engagement score, days to convert, revenue quality, segment balance
- Visual artifact: `outputs/kpi_tree.png`, preview at `screenshots/kpi_tree_preview.png`

## 5. Experiment Analysis Approach

- Cleaned the raw dataset and validated key fields.
- Removed duplicate `user_id` rows and kept the first occurrence.
- Checked missing values for demographic and behavioral variables.
- Validated binary fields and coerced them into numeric values.
- Applied IQR-based outlier detection to `revenue_30d` and created a capped revenue field.
- Compared Control vs Treatment metrics overall and by segment.
- Performed a one-tailed hypothesis test on onboarding completion.

## 6. Hypothesis Test Summary

- Null hypothesis: Treatment onboarding completion rate is the same or lower than control.
- Alternate hypothesis: Treatment onboarding completion rate is higher than control.
- Test type: one-tailed.
- Significance level: 0.05.
- Result: Control = 15.65%, Treatment = 21.13%.
- Z statistic: 2.641.
- P-value: 0.00413.
- Conclusion: reject H0; the treatment shows statistically significant improvement in the primary metric.
- Evidence image: `screenshots/hypothesis_test_output.png`

## 7. Guardrail Metrics Considered

- Refund rate: increased from 0.00% to 0.42%.
- Support ticket rate: increased from 14.78% to 24.79%.
- Engagement score: improved from 57.03 to 62.94.
- Days to convert: improved from 8.86 to 6.40 for converters.
- Paid conversion rate: improved from 3.19% to 7.04%.
- Average revenue per user: improved from 51.97 to 54.25.

## 8. Final Recommendation

Launch the new onboarding campaign broadly while closely monitoring support ticket volume and refund activity. The treatment improves onboarding completion and engagement, but operational guardrails should be observed during rollout.

## 9. Assumptions and Limitations

- Assumes onboarding completion is an acceptable proxy for early activation.
- The dataset lacks a direct activation-in-week-one variable.
- Revenue outliers were capped rather than removed, which may affect average revenue metrics.
- The analysis does not include long-term retention or lifetime value beyond early conversion.
- Segment-specific differences may still emerge after rollout.

## 10. Screenshots Included

- `screenshots/hypothesis_test_output.png`
- `screenshots/summary_metrics.png`
- `screenshots/kpi_tree_preview.png`

## Additional Files

- `analysis/hypothesis_test_notes.md`
- `analysis/data_cleaning_log.txt`
- `outputs/recommendation_memo.md`
- `outputs/experiment_summary.xlsx`
