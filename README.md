# Census Income Classification (Imbalanced Learning Case Study)

## Project Overview

This project builds a binary classification model to predict whether an individual's annual income exceeds $50,000 using U.S. Census data.

The dataset is highly imbalanced:

- ≤50K: 93.8%
- >50K: 6.2%

Because of this imbalance, evaluation focuses on ROC-AUC, PR-AUC, and threshold optimization rather than accuracy alone.

---

## Dataset

- Samples: 199,523
- Features: 40 (after leakage removal)
- Target: Income >50K (1) vs ≤50K (0)

---

## Data Cleaning & Preprocessing

- Removed leading/trailing whitespace in categorical values
- Replaced "?" with NaN
- Removed potential leakage columns (e.g., instance_weight)
- Converted target to binary (0/1)
- Treated industry and occupation recodes as categorical (not numeric IDs)

### Imputation
- Numeric → Median
- Categorical → Most Frequent

### Encoding
- OneHotEncoding for categorical variables
- StandardScaler for numeric variables

---

## Class Imbalance Handling

Used:

- `class_weight="balanced"` in Logistic Regression
- Stratified 5-fold cross-validation
- Precision-Recall analysis
- Threshold tuning (final threshold = 0.85)

---

## Cross-Validation Results (5-Fold)

ROC-AUC mean: 0.9437  
ROC-AUC std: 0.0008  

PR-AUC mean: 0.6014  
PR-AUC std: 0.0057  

Model performance is stable across folds.

---

## Final Model Performance (Threshold = 0.85)

ROC-AUC: 0.946  
PR-AUC: 0.606  

Confusion Matrix:

[[36198  1231]  
 [  973  1503]]

Positive Class (>50K):

- Precision: 0.55
- Recall: 0.607
- F1-score: 0.577

---

## Key Insights

- Education level strongly correlates with high income.
- Non-filers and low education levels strongly correlate with low income.
- Treating categorical ID recodes as numeric leads to incorrect modeling behavior.
- Threshold tuning significantly improves precision for rare class detection.

---

## Skills Demonstrated

- Data Cleaning
- Leakage Detection
- Handling Imbalanced Data
- Logistic Regression with Pipeline
- Cross-Validation
- ROC & PR Curve Analysis
- Threshold Optimization
- Feature Importance Interpretation

---

## Repository Structure

- `01_eda.ipynb` — Exploratory Data Analysis
- `02_baseline_model.ipynb` — Modeling, evaluation, and interpretation


