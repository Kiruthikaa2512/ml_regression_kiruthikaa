# Peer Review

**Reviewed Notebook:** [Final Project – Regression Analysis by Blessing Aganaga](https://github.com/teflxndxn/ml_regression_blessing/blob/main/notebooks/regression_blessing.ipynb)  


## 1. Clarity & Organization
The notebook is clearly structured, beginning with data loading, exploration, feature selection, and then modeling. Headings and reflections after each major step make the workflow easy to follow. Visualizations (histograms, boxplots, count plots, heatmap) are well chosen. One improvement would be to add short explanatory captions under each plot to connect the visualization directly to the modeling decisions. I see assignment required reflections are written well however adding somere extra details about the plots will be more helpful.


## 2. Feature Selection & Justification
The chosen features (age, BMI, children, smoker, region, sex) are appropriate for predicting medical costs. The justification for including smoker and BMI as strong predictors is well explained. Encoding categorical variables with `pd.get_dummies` was correctly applied. A constructive suggestion would be to explore engineered features (e.g., BMI × smoker interaction, or grouping BMI into categories) to capture nonlinear effects more explicitly.


## 3. Model Performance & Comparisons
Three models were compared: baseline Linear Regression, Pipeline 1 (with scaling), and Pipeline 2 (with polynomial features). Results are reported with R², MAE, and RMSE, which makes the comparison clear. Pipeline 2 showed improved performance, but the risk of overfitting was acknowledged. To strengthen this section, residual plots or error distribution visualizations could be added to show where predictions deviate most. Including regularized models (Ridge/Lasso) would also provide a useful comparison.


## 4. Reflection Quality
Reflections are thoughtful and placed after each major step, highlighting dataset cleanliness, feature importance, and model behavior. The recognition of smoking status as the strongest predictor is accurate and well supported. The discussion of challenges (balancing complexity vs. overfitting) is realistic. To improve, reflections could connect findings more explicitly to real-world implications (e.g., how insurers or policymakers might use these insights). This would bridge technical results with practical applications.


## Overall Feedback
This notebook demonstrates strong technical execution and clear organization. Improvements could include:  
- Adding explanatory captions under visualizations.  
- Exploring engineered features to capture nonlinear effects.  
- Expanding performance evaluation with residual/error plots.  
- Linking reflections more directly to stakeholder impact.  

These changes would make the project even more robust and insightful.