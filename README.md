# Responsible Machine Learning Capstone Project

## Overview
This project presents an end-to-end Responsible Machine Learning audit using the 2024 Home Mortgage Disclosure Act (HMDA) Loan Application Register (LAR) dataset. The goal is not only to build predictive models for mortgage approval decisions, but also to evaluate fairness, reliability, explainability, and deployment risks in a real-world lending context.

The project was completed for **DNSC 6330 – Responsible Machine Learning** at **George Washington University (Spring 2026)**.

---

## Team Members
- Surafel Debebe  
- Xiaowei Cen  
- Percy  
- Suzy  
- Ramin  

---

## Dataset
- **Source:** 2024 HMDA LAR dataset  
- **Size Used:** 150,000 filtered records  
- **Target Variable:**  
  - Action Taken = 1 or 2 → Approved (1)  
  - Action Taken = 3 → Denied (0)

---

## Project Objectives
The project focuses on five major responsible ML questions:

1. Optimization objective  
2. Known failure modes  
3. Subgroup fairness measurement  
4. Bias mitigation and residual risk  
5. Deployment defensibility  

---

## Models Used
- Logistic Regression (interpretable baseline)
- Gradient Boosting Classifier (higher-capacity model)

---

## Methods

### Data Processing
- Missing value imputation
- One-hot encoding for categorical variables
- Feature scaling for numerical variables
- Train/test split with reproducible random seed

### Fairness Evaluation
The project evaluates fairness across:
- Race
- Sex
- Ethnicity
- Race × Sex intersectional groups

Metrics used:
- Adverse Impact Ratio (AIR)
- Marginal Effect (ME)
- Standardized Mean Difference (SMD)

---

## Explainability
The notebook uses SHAP analysis to identify important features and potential proxy discrimination risks. Important proxy-related features such as loan purpose and loan type were reviewed during the audit.

---

## Key Findings
- Gradient Boosting achieved better predictive performance overall.
- However, the Gradient Boosting model also showed stronger subgroup disparities.
- Black female applicants under the GBT model had an AIR below the four-fifths threshold (0.7913), raising fairness concerns.
- The project demonstrates that the model with the highest AUC is not always the most deployable or defensible model.

---

## Bias Mitigation
Two mitigation policies were evaluated:
- Global threshold adjustment
- Group-specific threshold analysis

The project concludes that fairness improvements must still satisfy governance and legal defensibility requirements before deployment.

---

## Technologies Used
- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- SHAP
- Google Colab


## Conclusion
This project demonstrates how responsible machine learning extends beyond model accuracy. A model must also be explainable, fair across subgroups, robust to failure modes, and defensible for real-world deployment decisions.


