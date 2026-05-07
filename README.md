# Responsible Machine Learning Capstone Project

2026 Spring — DNSC 6330 Responsible Machine Learning  
George Washington University

Team Members:
- Surafel Debebe
- Xiaowei Cen
- Percy Rodriguez
- Suzy Tseng
- Ramin Gamzaev

---

## Project Overview

This project implements an end-to-end Responsible Machine Learning audit using the 2024 Home Mortgage Disclosure Act (HMDA) Loan Application Register (LAR) dataset.

The objective is not only to build predictive models for mortgage approval decisions, but also to evaluate whether those models are defensible under fairness, robustness, explainability, and deployment-governance standards.

The project follows the capstone framework from DNSC 6330 and addresses:

1. Optimization objective
2. Known failure modes
3. Subgroup fairness measurement
4. Bias mitigation and residual risks
5. Deployment defensibility

---

## Dataset

Source:
- 2024 HMDA Loan/Application Register (LAR)

Filtering:
- action_taken ∈ {1, 2, 3}

Label Definition:
- 1 and 2 → Approved (1)
- 3 → Denied (0)

Dataset size used:
- ~150,000 rows

---

## Models

Two models were evaluated:

### Logistic Regression (LR)
- Interpretable baseline model

### Gradient Boosting Classifier (GBT)
- Higher-capacity model with stronger predictive performance

---

## Features

Example features include:

- loan_amount
- income
- property_value
- debt_to_income_ratio
- loan_type
- loan_purpose
- occupancy_type
- applicant_age
- derived_loan_product_type
- construction_method

Protected attributes used for auditing:
- derived_race
- derived_ethnicity
- derived_sex
- race × sex intersection groups

---

## Responsible ML Analysis

### Explainability
The project uses:
- SHAP
- LIME
- Feature importance analysis

These methods help identify:
- key approval/denial drivers
- proxy features
- subgroup-specific model behavior

---

### Fairness Metrics

The following fairness metrics were evaluated:

- AIR (Adverse Impact Ratio)
- ME (Marginal Effect)
- SMD (Standardized Mean Difference)

Reference groups:
- Race → White
- Sex → Male
- Ethnicity → Not Hispanic or Latino
- Intersectional → White | Male

---

## Key Findings

### Model Performance
GBT achieved stronger predictive performance than Logistic Regression, but also produced larger subgroup disparities.

### Fairness Concerns
The strongest adverse-impact signal appeared in the intersectional race × sex analysis:

| Group | AIR |
|---|---|
| Black or African American \| Female | 0.7913 |
| American Indian or Alaska Native \| Male | 0.7944 |

These values fall below the four-fifths-rule threshold (0.80).

---

## Bias Mitigation

A post-processing threshold mitigation strategy was applied.

### Global Threshold Adjustment
A threshold sweep identified:

- Best threshold = 0.46

After mitigation:

| Group | AIR Before | AIR After |
|---|---|---|
| Black Female | 0.7913 | 0.8011 |
| AIAN Male | 0.7944 | 0.8312 |

This improved fairness while preserving a single global decision rule.

---

## Residual Risks

Even after mitigation, several risks remain:

- Temporal drift
- FPR/FNR disparity across groups
- Proxy-feature effects
- Missing-data sensitivity
- Threshold sensitivity
- Out-of-distribution loan products

The project concludes that fairness risks were reduced, but not fully eliminated.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- SHAP
- LIME
- Jupyter Notebook



