# Census Income Classification (Tabular ML)

This project predicts whether a person's income exceeds 50K using the UCI Census Income dataset.

## Problem
Binary classification with severe class imbalance (~6% positive class).

## Models Compared
- Logistic Regression (baseline)
- XGBoost (final model)

## Final Results (XGBoost)
- ROC-AUC: 0.95
- PR-AUC: 0.67
- Decision Threshold: 0.7

Threshold tuning was applied to improve the precision–recall tradeoff under class imbalance.

## Model Interpretation
SHAP was used to analyze feature importance and confirm that predictions are driven by meaningful features.

![SHAP Summary](reports/figures/shap_summary.png)

## How to Run
Install dependencies:

