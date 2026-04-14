# ICU Length of Stay Prediction — MIMIC-III

End-to-end ML pipeline predicting ICU Length of Stay (LOS) for 
atrial fibrillation patients using the MIMIC-III clinical database, 
with SHAP-based model interpretability.

## Results

| Metric | Value |
|--------|-------|
| MAE (test) | 1.96 days |
| RMSE (test) | 2.93 days |
| R² (test) | 0.26 |
| Best CV MAE | 2.05 days |

Best params: GradientBoosting (lr=0.05, max_depth=5, n_estimators=300)

Low R² is expected in LOS regression tasks — literature reports 
similar values (0.15–0.35) on MIMIC-III without temporal models. 
SHAP analysis identifies Pulmonary Artery Pressure (systolic), 
PEEP set, and Respiratory Alarm (High) as top predictors.

## Pipeline
- Cohort construction from MIMIC-III (ICD-9: atrial fibrillation)
- CHARTEVENTS preprocessing + feature engineering from 
  time-series clinical measurements
- KNN imputation + StandardScaler + RFE feature selection
- GridSearchCV tuning of Gradient Boosting Regressor (540 fits)
- SHAP TreeExplainer for global and local interpretability

## Stack
Python · scikit-learn · shap · pandas · matplotlib · seaborn

## Run locally
pip install -r requirements.txt
jupyter notebook mimic3_los_prediction.ipynb

