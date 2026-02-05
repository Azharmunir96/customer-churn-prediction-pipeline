# Task 2: End-to-End Customer Churn Prediction Pipeline

## 📌 Project Overview
Customer churn is a critical problem for subscription-based businesses, especially in industries like telecommunications. Manually identifying customers who are likely to leave is inefficient and often too late.

This project implements a **production-ready, end-to-end machine learning pipeline** that predicts the likelihood of customer churn. The solution bundles **data preprocessing and model inference** into a single, deployable pipeline, ensuring consistency, scalability, and ease of integration with real-world systems.

---

## 🎯 Problem Statement & Objective

### Problem
Customer attrition (churn) significantly impacts revenue and growth in subscription-based businesses. Traditional, manual approaches to identifying high-risk customers are reactive and inefficient.

### Objective
To build a **robust and modular machine learning pipeline** that:
- Accurately predicts whether a customer is likely to churn.
- Handles raw data automatically without manual preprocessing.
- Is suitable for deployment in production environments.

---

## 📂 Dataset Loading & Preprocessing

### Dataset Source
- **IBM Telco Customer Churn Dataset** (Raw CSV format)

### Data Cleaning
- Converted `TotalCharges` from object type to numeric.
- Handled missing values appropriately.
- Dropped non-predictive identifiers such as `customerID` to reduce noise.

### Feature Engineering (Scikit-learn Pipeline)
To ensure consistent preprocessing during training and inference, a unified pipeline was used:

#### Numerical Features
- Applied `StandardScaler` to normalize features such as:
  - `tenure`
  - `MonthlyCharges`

#### Categorical Features
- Used `OneHotEncoder` to convert categorical variables (e.g., contract type, internet service) into binary vectors.

#### ColumnTransformer
- Combined numerical and categorical transformations into a single `ColumnTransformer`.
- Ensured identical preprocessing for both training and test data.

---

## 🤖 Model Development & Training

### Algorithm
- **Random Forest Classifier**
- Chosen for its:
  - Robustness to outliers
  - Ability to model non-linear relationships
  - Strong performance on tabular data

### Hyperparameter Tuning
- Performed using `GridSearchCV` with **5-fold cross-validation**.

### Best Hyperparameters
- `n_estimators`: 50  
- `max_depth`: 10  

### Model Serialization
- The final optimized pipeline was saved using **Joblib** as:

```bash
churn_pipeline_model.joblib




