---
name: ml-data-pipeline-cleaner
description: Automates end-to-end data sanitization, missing value imputation, outlier detection, and feature engineering for machine learning pipelines.
---

# Autonomous ML Data Cleaning & Feature Engineering

This skill directs automated, leak-free data preprocessing, anomaly mitigation, and feature transformation workflows in Python (Pandas, Polars, Scikit-Learn).

## 1. Leakage-Free Preprocessing Pipeline

1. **Split-Before-Transform Discipline**:
   - Strictly perform train/validation/test splits *before* fitting any scalers, encoders, or imputers to prevent test set data leakage.
2. **Missing Value Imputation**:
   - Numeric: Median or KNN imputation based on distribution skewness; create explicit binary indicator flags (`is_missing_<col>`) when missingness itself carries predictive signal.
   - Categorical: Mode or explicit `'Unknown'` class token.
3. **Outlier Mitigation**:
   - Detect extreme outliers via Interquartile Range (IQR) or Z-scores. Apply robust winsorization (clipping at 1st/99th percentiles) rather than arbitrary row deletion.

## 2. Feature Engineering & Encodings
- High-cardinality categoricals: Target encoding with cross-validation smoothing or frequency encoding.
- Low-cardinality categoricals: One-hot encoding with `handle_unknown='ignore'`.
- Skewed numericals: Log1p or Yeo-Johnson power transformations.
