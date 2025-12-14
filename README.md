# Predicting Survival Outcomes in Primary Biliary Cholangitis (PBC)

## Project Overview
Primary Biliary Cholangitis (PBC) is a chronic autoimmune liver disease with highly variable disease progression. Many patients are asymptomatic at diagnosis, making early risk identification challenging.  

This project formulates PBC survival prediction as a **binary classification problem**, where the goal is to predict whether a patient diagnosed with PBC survives or dies during the follow-up period (~4 years) using routinely collected clinical and laboratory data.

Using the **Cirrhosis Patient Survival Prediction dataset** from the UCI Machine Learning Repository (originating from a Mayo Clinic clinical study), multiple machine learning models were trained, evaluated, and interpreted. Special care was taken to address **missing data**, **class imbalance**, and **model interpretability**, which are critical in medical ML applications.

---

## Dataset
- **Source**: UCI Machine Learning Repository  
- **Observations**: 418 patients  
- **Features**: 17 demographic, clinical, and laboratory variables  
- **Key Challenges**:
  - Substantial missingness across clinically relevant features
  - Class imbalance between survival outcomes
  - Mixed feature types (numerical, ordinal, categorical)

---

## Modeling Approach
The following models were trained and evaluated:

- **Baseline Majority-Class Model**
- **Logistic Regression**
- **Support Vector Machine (SVM)**
- **Random Forest**
- **XGBoost**

### Preprocessing
All models (except the baseline) were trained using a unified preprocessing pipeline that includes:
- Iterative imputation for numerical features (Bayesian Ridge)
- Standardization of numerical and ordinal features
- Explicit ordinal encoding for disease stage and edema severity
- One-hot encoding for categorical features with missingness handled explicitly

Preprocessing and modeling were implemented using **scikit-learn Pipelines** to ensure reproducibility and prevent data leakage.

---

## Evaluation
- **Primary metric**: F1 score  
- **Secondary metric**: Accuracy  
- **Evaluation strategy**:
  - Hold-out test set
  - Bootstrap resampling (500 iterations) to estimate mean performance and variability

Model interpretability was assessed using:
- Permutation importance
- Model-specific feature importance (tree-based models)
- SHAP values for local explanations

---

## Saved Artifacts
The `results/` directory contains serialized versions of all trained models:

- `baseline.joblib`
- `logistic_regression.joblib`
- `svm.joblib`
- `random_forest.joblib`
- `xgboost.joblib`

Each saved model includes its full preprocessing pipeline (when applicable) and can be loaded directly for inference or further analysis.

---

## Reproducibility

### Python Version
- **Python**: 3.12.10

### Key Package Versions
The following packages were used during development:

- numpy==2.2.5
- pandas==2.2.3
- scikit-learn==1.6.1
- xgboost==3.0.0
- shap==0.47.2
- scipy==1.16.1
- matplotlib==3.10.1
- seaborn==0.13.2
- joblib==1.5.2

---

## Notes
- Results should be interpreted as exploratory and not as clinical decision tools.

---

## Author
James Hu  
Brown University  
Data Science
