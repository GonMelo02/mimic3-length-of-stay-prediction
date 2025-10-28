# ICU Length of Stay Prediction using MIMIC-III

## Overview
This project presents a complete data analysis and machine learning pipeline using the **MIMIC-III** (Medical Information Mart for Intensive Care III) database.  
The primary goal is to **predict ICU Length of Stay (LOS)** for patients diagnosed with Atrial fibrillation , based on their clinical and physiological data collected during hospitalization.

This project demonstrates the full development cycle of a real-world ML system in healthcare — including data wrangling, preprocessing, model training, and interpretability — while highlighting the challenges inherent to medical data modeling.

---

## Project Structure
The notebook is organized into modular sections that reflect a standard data science workflow:

1. **Data Loading & Dictionaries** – Initial data import and exploration of metadata tables.  
2. **Disease Selection** – Choice of a target condition based on ICD-9 codes.  
3. **Cohort Construction** – Integration of patient, admission, and ICU stay data.  
4. **Exploratory Data Analysis (EDA)** – Statistical summaries and visualization of key patterns.  
5. **CHARTEVENTS Preprocessing** – Handling of time-series measurements and event filtering.  
6. **Feature Engineering** – Aggregation of clinical signals into interpretable features.  
7. **Data Preparation** – Cleaning, scaling, and train-test split.  
8. **Model Training & Optimization** – Evaluation of Gradient Boosting and other baseline models.  
9. **Model Interpretation (SHAP)** – Feature importance analysis and explanation of predictions.  
10. **Conclusions** – Discussion of limitations, insights, and future directions.

---

## Methodology
A traditional ML pipeline was implemented:
- **Preprocessing:** Filtering ICU stays, handling missing data, and normalization of numeric features.  
- **Feature Engineering:** Aggregation of time-dependent clinical variables  
- **Modeling:** Gradient Boosting Regressor optimized via cross-validation.  
- **Evaluation:** Mean Absolute Error and visual inspection of prediction residuals.  
- **Interpretability:** SHAP values were computed to identify key drivers behind LOS predictions.

---

## Key Insights
Despite extensive optimization, predicting LOS remains a **highly complex and unstable task**, due to:
- The **heterogeneity** of patient trajectories and comorbidities.  
- **Incomplete or noisy data** (measurement gaps, missing timestamps, or inconsistent coding).  
- **Feature limitations**, as not all clinically relevant variables are captured in MIMIC-III.  

However, SHAP analysis provided valuable interpretability:
- **Pulmonary Artery Pressure (systolic)**, **PEEP set**, and **Respiratory Alarm (High)** emerged as the most influential variables.  
- High values of these features tended to push the model toward predicting **longer ICU stays**, aligning with clinical intuition.  

These results reinforce both the **potential and the limits** of machine learning in clinical outcome prediction.

---

## Technologies Used
- **Python**
- **Pandas**, **NumPy**, **Matplotlib**, **Seaborn**
- **Scikit-learn**
- **SHAP**
- **MIMIC-III Clinical Database**

