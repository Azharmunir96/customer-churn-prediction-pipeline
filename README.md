# Customer Churn Prediction Pipeline (End-to-End)

## 📌 Project Overview
This project implements a **production-ready machine learning pipeline** to predict customer attrition. By bundling data preprocessing and model inference into a single object, the system ensures consistency between training and real-world deployment.

## 🎯 Problem Statement & Objective
* **Problem:** Manual identification of at-risk customers is reactive and inefficient.
* **Objective:** Develop a modular pipeline to handle raw data automatically and predict churn likelihood accurately using the **IBM Telco Customer Churn Dataset**.

## 📂 Data Engineering & Preprocessing
* **Data Cleaning:** Handled missing values, converted `TotalCharges` to numeric, and removed non-predictive `customerID`.
* **Feature Engineering (via Scikit-learn Pipeline):**
    * **Numerical:** `StandardScaler` for `tenure` and `MonthlyCharges`.
    * **Categorical:** `OneHotEncoder` for service and contract types.
    * **Consistency:** Used `ColumnTransformer` to ensure identical transformations for training and inference.



## 🤖 Model Development
* **Algorithm:** Random Forest Classifier.
* **Optimization:** `GridSearchCV` with 5-fold cross-validation.
* **Best Parameters:** `max_depth: 10`, `n_estimators: 50`.
* **Serialization:** Exported the full pipeline as `churn_pipeline_model.joblib`.

## 📊 Evaluation & Metrics
* **Accuracy:** ~79%
* **Precision (Churn):** 0.62
* **Recall (Churn):** 0.49
* **F1-Score (Churn):** 0.55

## 📈 Key Insights
* **Feature Importance:** **Contract Type**, **Tenure**, and **Monthly Charges** are the strongest predictors.
* **Contract Risk:** Month-to-month contracts correlate with the highest churn rates.
* **Tenure Risk:** New customers are most vulnerable, suggesting a need for better onboarding.



## 🚀 Production Readiness
The use of the **Scikit-learn Pipeline API** allows this model to accept raw, uncleaned data and return predictions instantly, making it ready for integration into web or mobile applications.
