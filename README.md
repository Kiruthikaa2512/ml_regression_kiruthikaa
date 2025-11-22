# Final Project: Regression Analysis – Medical Insurance Charges Prediction

**Author:** Kiruthikaa Natarajan Srinivasan  
**Date:** November 22, 2025  

**Notebook** – [Click here to view the Jupyter Notebook](https://github.com/Kiruthikaa2512/ml_regression_kiruthikaa/blob/main/regression_ml_kiruthikaa.ipynb)  
**Peer Review** – [Click here to view the Peer Review Markdown file](https://github.com/Kiruthikaa2512/ml_regression_kiruthikaa/blob/main/peer_review.md)  

## Overview

This project applies regression modeling to predict **medical insurance charges** based on demographic and health-related features. The workflow includes data cleaning, feature engineering, model training, pipeline implementation, and evaluation using multiple metrics.  

Two main pipelines were implemented:  
- **Pipeline 1:** Imputer → StandardScaler → Linear Regression  
- **Pipeline 2:** Imputer → Polynomial Features → StandardScaler → Linear Regression  

The models were compared against a baseline linear regression to evaluate robustness and generalization.

## Objectives

- Preprocess and clean categorical and numerical features  
- Engineer new features (e.g., BMI × smoker interaction, BMI categories)  
- Implement regression pipelines with scaling and polynomial expansion  
- Compare model performance using:  
  - R² Score  
  - Mean Absolute Error (MAE)  
  - Root Mean Squared Error (RMSE)  
- Visualize feature relationships and model predictions  
- Reflect on scaling impact and model interpretability  

## Dataset

The **Insurance dataset** includes:  
- `age`, `sex`, `bmi`, `children`, `smoker`, `region` → Input features  
- `charges` → Target variable  

### Key preprocessing steps:
- Converted categorical variables into dummy/encoded features  
- Dropped duplicate or zero-variance columns  
- Created engineered features:  
  - `bmi_smoker_interaction`  
  - `has_children`  
  - BMI categories (normal, overweight, obese)  

## Feature Insights

- **Smoking status and BMI interaction** were the most impactful predictors of charges.  
- **Age** showed a consistent upward trend with charges.  
- **Region and sex** added demographic context but were weaker predictors.  
- **BMI categories** helped capture nonlinearity but were less powerful than continuous BMI × smoker interaction.  

## Model Performance Summary (Test Set)

| Model Type          | Features Used                          | R² Score | MAE    | RMSE   | Notes                                           |
|---------------------|----------------------------------------|----------|--------|--------|------------------------------------------------|
| Baseline Regression | age, bmi, smoker, region, sex, children| ~0.87    | ~2700  | ~5900  | Strong baseline, interpretable coefficients     |
| Pipeline 1          | Imputer + Scaler + Linear Regression   | ~0.87    | ~2700  | ~5900  | Similar to baseline, more robust preprocessing  |
| Pipeline 2          | Imputer + PolyFeatures + Scaler + LR   | ~0.83    | Higher | Higher | Captured nonlinearities but risked overfitting |

## Visualizations

- **Scatter plots:** Feature vs. charges (age, BMI, smoker, region, sex, children, BMI categories)  
- **Actual vs Predicted Charges:** Showed strong correlation, with wider error spread at high charges  
- **Model Performance Comparison (R²):** Baseline and Pipeline 1 outperformed Pipeline 2  

## Reflections

### Model Behavior
- Linear regression captured main trends effectively.  
- Polynomial expansion added complexity but reduced generalization.  
- Scaling was critical when polynomial features were introduced.  

### Challenges
- Handling skewed target distribution (`charges`) with extreme outliers.  
- Balancing interpretability vs. complexity in feature engineering.  
- Ensuring categorical encoding consistency.  

### Next Steps
- Apply log transformation to target variable to reduce skew.  
- Explore regularized regression (Ridge, Lasso) for multicollinearity.  
- Test tree-based models (Random Forest, Gradient Boosting, XGBoost).  
- Perform residual analysis and feature importance visualization.  

## Setup Instructions

To run this project locally:

### 1. Clone the repository
```bash
git clone https://github.com/Kiruthikaa2512/ml_regression_kiruthikaa.git
cd ml_regression_kiruthikaa