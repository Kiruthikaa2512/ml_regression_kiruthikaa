# Project Summary: Regression Model

This document summarizes the key decisions, assumptions, and findings for this regression project.  
Complete each section clearly and professionally.  
When you modify this document, rename the title to: PROJECT_SUMMARY.md.  


## Problem Definition (Front Matter)

- **Project Title:** Medical Insurance Charges Prediction  
- **Author/Alias:** Kiruthikaa Natarajan Srinivasan  
- **Brief description of the business or analytical problem:**  
  Predicting medical insurance charges based on demographic and health-related features to understand cost drivers and improve planning.  
- **What decision or action the model is intended to support:**  
  Support insurers, policymakers, and individuals in estimating healthcare costs and identifying high-risk groups.  
- **Who would use this model:**  
  Insurance companies, healthcare analysts, policymakers, and potentially consumers seeking cost estimates.  


## 1. Identify the Target Variable

- **Target variable name:** `charges`  
- **Confirm target is continuous and numeric:** Yes, continuous numeric values.  
- **Unexpected values, missing values, or outliers:** No missing values; extreme outliers present at high charges.  
- **Why is this target meaningful for prediction:** Healthcare costs are critical for budgeting, premium setting, and policy planning.  


## 2. Review Feature Variables

- **Available features:** Age, BMI, smoker status, region, sex, children, engineered features (`bmi_smoker_interaction`, BMI categories).  
- **Type:** Mixed (numeric + categorical).  
- **Irrelevant/redundant features:** Dropped zero-variance columns (e.g., `region_northeast`).  
- **Restricted features:** None.  
- **Possible leakage:** Using post-treatment costs or claims data would leak future information.  
- **Example of leakage:** Including hospital bills after charges were already determined.  

## 3. Understand Relationships and Distributions

- **Patterns/correlations:** Smoking status and BMI interaction strongly correlated with charges; age shows upward trend.  
- **Multicollinearity:** Some correlation between BMI and BMI categories.  
- **Transformations needed:** Scaling applied; log transformation considered for skewed target.  
- **Outliers:** Present in high charges.  
- **Handling of outliers:** Not removed; acknowledged as limitation.  


## 4. Select the Regression Model

- **Baseline model:** Linear Regression.  
- **Why appropriate:** Simple, interpretable, strong baseline for continuous prediction.  
- **Assumptions:** Linearity, independence, constant variance.  
- **Assumptions met:** Approximately; skewness and outliers challenge variance assumption.  


## 5. Evaluate Model Performance

- **Metrics used:** R², MAE, RMSE.  
- **Why chosen:**  
  - R² measures variance explained.  
  - MAE gives average error magnitude.  
  - RMSE penalizes large errors, highlighting outliers.  
- **Performance:**  
  - Baseline & Pipeline 1: R² ~0.87, MAE ~2700, RMSE ~5900.  
  - Pipeline 2: R² ~0.83, higher errors due to overfitting.  
- **Reasonableness:** Strong fit for most cases; weaker for extreme charges.  
- **Errors matter more:** Underestimation is worse for insurers (financial risk); overestimation is worse for consumers (unfair premiums).  


## 6. Improve the Model

- **Alternate models/improvements tried:** Polynomial features (Pipeline 2).  
- **Why:** To capture nonlinear relationships.  
- **Improved performance:** Polynomial features captured curvature but reduced generalization.  
- **Why helped/failed:** Helped model interactions but overfit due to complexity.  
- **Future improvements:** Log-transform target, add Ridge/Lasso regularization, test tree-based models (Random Forest, Gradient Boosting).  


## 7. Validate and Compare Models

- **Comparison method:** Train/test split (80/20).  
- **Metrics compared:** R², MAE, RMSE.  
- **Best model:** Baseline and Pipeline 1 performed best.  
- **Generalization:** Yes, consistent across splits.  
- **Discussion:** Simpler models generalized better; polynomial expansion added noise.  


## 8. Real-World Interpretation

- **Feature influence:** Smoking status and BMI interaction are dominant predictors; age consistently increases charges.  
- **Practical insights:** Insurers can identify high-risk groups (smokers with high BMI, older individuals).  
- **Model stability:** Stable for typical cases; less reliable for extreme outliers.  
- **Limitations/caveats:** Skewed target distribution, limited features (no medical history), linear assumptions.  


## Final Notes

- **Key limitations:** Outliers reduce accuracy; linear regression limited in capturing complex nonlinearities.  
- **Future improvements:** Regularization, tree-based models, residual analysis, feature importance visualization.  
- **Open questions/assumptions:** Assumes demographic and lifestyle features are sufficient; ignores medical/genetic factors.  