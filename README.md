# Cardiovascular Disease Risk Prediction – Machine Learning Models  

Comparing the performance of multiple classification algorithms to predict cardiovascular disease (CVD) from patient health data.  

---

## Overview  
This project evaluated five machine learning models (Logistic Regression, Support Vector Classifier, Random Forest, AdaBoost, and Gradient Boosting) on a dataset of ~70,000 patient records.  
The goal was to build reproducible models to predict CVD and identify the most important contributing factors.  

Key findings:  
- All models achieved accuracy around **72–73%** and F1-scores near **0.74**.  
- **Gradient Boosting** performed best overall, though the margin was small.  
- **Systolic blood pressure (ap_hi)** consistently dominated predictions, followed by **age** and **cholesterol**, while lifestyle variables (smoking, alcohol, physical activity) had little predictive impact.  

Cross-validation confirmed results were stable across folds. The project highlighted not only which model performed best, but also how different algorithms interpret the same dataset in different ways.  

---

## Repository Structure  
- `00_cardiovascular_disease_EDA.ipynb` → Data loading, cleaning, preprocessing, and exploratory data analysis  
- `01_cardiovascular_disease_modeling.ipynb` → Baseline models + hyperparameter tuning  
- `02_cardiovascular_disease_tree_modeling.ipynb` → Tree-based models with estimator tuning  
- `03_cardiovascular_disease_model_comparison.ipynb` → Model performance comparison and visualization  
- `model_utils.ipynb` → Utility functions for plotting graphs and saving outputs  

---

## Data Preprocessing and Exploration  
- Removed outliers (implausible blood pressures, unrealistic body measures, invalid cases).  
- Reduced dataset from ~70,000 to ~61,000 clean records.  
- Converted age from days → years for interpretability.  
- One-hot encoded blood pressure categories to analyze correlations.  

Exploration showed:  
- **Stage 2 hypertension** patients faced nearly an **80% likelihood** of CVD.  
- Patients **aged 60+** consistently had the highest risk across all groups.  

---

## Modeling  
- StandardScaler applied to continuous features using a `ColumnTransformer`; binary/dummy variables left unchanged.  
- Trained and compared Logistic Regression, SVC, Random Forest, AdaBoost, and Gradient Boosting.  
- Evaluated models with accuracy, precision, recall, and F1-score.  
- Hyperparameter tuning with **GridSearchCV (5-fold cross-validation)**.  
- Saved feature importances, coefficients, and permutation scores for each model before and after tuning.  
- For tree-based models, graphed how test error changed as the number of estimators increased.  

---

## Results & Key Insights  
- **Performance:**  
  - Logistic Regression: Accuracy ~72.2%, F1 ~75% (minimal change after tuning).  
  - SVC: Accuracy ~72.9%, F1 ~75% (stable after tuning).  
  - Random Forest: Biggest improvement from tuning; accuracy ↑ ~3.2%, F1 ↑ ~5%. Optimal estimators: ~60–75.  
  - AdaBoost: Accuracy ~71.6%, F1 ~74%; tuned model narrowed to only 3 features. Optimal estimators: ~9–10.  
  - Gradient Boosting: Accuracy ~72.8%, F1 ~74%; feature importance stable. Optimal estimators: ~150.  

- **Feature Importance:**  
  - **ap_hi (systolic blood pressure)** was dominant across all models.  
  - **Age** and **cholesterol** were consistent secondary predictors.  
  - Lifestyle variables (smoke, alco, active) had little predictive power.  

- **Interpretability vs. Power:**  
  - Logistic Regression and SVC → easier to interpret, coefficients/permutation scores show influence of each variable.  
  - Ensemble methods (Random Forest, AdaBoost, Gradient Boosting) → captured more complex interactions but relied on fewer, stronger predictors.  

- **Best Model:**  
  - **Gradient Boosting** provided the best balance of precision and recall, with the most stable performance.  

---

## Conclusion  
All models ended up in a similar performance range, but Gradient Boosting offered a slight edge. More importantly, the project showed how algorithms prioritize features differently: Random Forest shifted focus after tuning, AdaBoost cut down to just three predictors, and Gradient Boosting remained consistent.  

Cross-validation confirmed these results were reliable. Organizing the pipeline across modular notebooks and saving intermediate outputs ensured reproducibility and flexibility for future extensions.  

---

## Data Source  
[Kaggle – Cardiovascular Disease Dataset](https://www.kaggle.com/datasets/sulianova/cardiovascular-disease-dataset)  

---

## Repository Link  
Full code and notebooks: [GitHub – Cardiovascular Disease Project](https://github.com/yourusername/Cardiovascular-Disease-Project)  
