# Group-4-responsible-ml-capstone
Capstone project on fairness analysis and mitigation using the COMPAS dataset
Responsible ML Capstone Project
Overview

This project builds a machine learning model to predict mortgage approval using the 2024 HMDA dataset. The goal is not only to achieve good performance but also to evaluate fairness and potential risks in the model.

Dataset
Source: 2024 HMDA Loan Data
~150,000 records after cleaning
Target:
1 = Approved
0 = Denied

Protected attributes used for fairness analysis:

Race
Sex
Ethnicity
Models
Logistic Regression (baseline)
Gradient Boosting (better performance)

Both models use preprocessing pipelines (imputation, encoding, scaling).

Results
Logistic Regression AUC ≈ 0.88
Gradient Boosting AUC ≈ 0.91

Gradient Boosting performs better.

Fairness Analysis

We evaluated fairness using:

AIR (80% rule)
ME (statistical difference)
SMD (effect size)
Key findings:
Black applicants have lower approval rates
Intersectional groups (e.g., Black female) are more affected
Multiple groups were flagged for disparity
Failure Modes

Main risks identified:

Class imbalance (approval rate is high)
Missing data impact
Threshold sensitivity
Temporal drift
Mitigation

We applied threshold adjustment:

Lower threshold improves fairness
Group-specific thresholds improve results further

However:

May increase false positives
May raise legal concerns
Deployment
Logistic Regression → Conditional
Gradient Boosting → Better performance

Group-specific thresholds are not recommended for deployment due to legal risk.

Conclusion

The model performs well but has fairness issues.
Mitigation improves fairness, but trade-offs remain.
Careful monitoring is required before deployment.
