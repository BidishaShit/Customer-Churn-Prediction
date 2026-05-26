# Customer Churn Prediction using XGBoost

## Project Overview

This project is a Machine Learning-based Customer Churn Prediction System developed using Python and XGBoost. The goal of the project is to predict whether a customer is likely to churn based on customer demographics, subscription details, engagement behavior, and spending patterns.

The system helps businesses identify high-risk customers and take proactive retention actions to reduce customer loss and improve customer satisfaction.

---

# Objective

The main objective of this project is to:

- Predict customer churn accurately
- Analyze customer behavior patterns
- Identify important churn-driving features
- Segment customers based on churn risk
- Suggest retention strategies for businesses

---

# Technologies Used

| Technology | Purpose |
|---|---|
| Python | Programming Language |
| Pandas | Data Manipulation |
| NumPy | Numerical Operations |
| Matplotlib | Data Visualization |
| Scikit-learn | Machine Learning Utilities |
| XGBoost | Classification Algorithm |
| Joblib | Model Serialization |

---

# Dataset Information

The project uses two datasets:

- `customer_churn_dataset-training-master.csv`
- `customer_churn_dataset-testing-master.csv`

Both datasets are merged before preprocessing and training.

---

# Features Used

## Original Features

- CustomerID
- Age
- Gender
- Tenure
- Usage Frequency
- Support Calls
- Payment Delay
- Subscription Type
- Contract Length
- Total Spend
- Last Interaction
- Churn (Target Variable)

---

# Data Preprocessing

The following preprocessing steps were performed:

## 1. Dataset Merging

Training and testing datasets were combined into a single dataframe.

## 2. Data Shuffling

The dataset was shuffled randomly to remove ordering bias.

## 3. Missing Value Handling

- Removed rows with missing churn values
- Dropped remaining missing values

## 4. Removing Unnecessary Columns

`CustomerID` was removed because it does not contribute to prediction.

## 5. One-Hot Encoding

Categorical columns were converted into numerical format using one-hot encoding.

Encoded columns:
- Gender
- Subscription Type
- Contract Length

---

# Feature Engineering

Additional features were created to improve model performance.

## Avg Monthly Spend

Measures average customer spending per month.

```python
Avg Monthly Spend = Total Spend / (Tenure + 1)
```

---

## Engagement Score

Measures customer engagement level.

```python
Engagement Score = Usage Frequency / (Last Interaction + 1)
```

---

## Customer Value Score

Measures customer contribution to business value.

```python
Customer Value Score = Total Spend * Usage Frequency
```

---

## Inactivity Score

Measures inactivity relative to customer usage.

```python
Inactivity Score = Last Interaction / (Usage Frequency + 1)
```

---

# Machine Learning Model

The project uses the **XGBoost Classifier** for churn prediction.

## Why XGBoost?

XGBoost was selected because:

- High accuracy on structured datasets
- Handles overfitting efficiently
- Fast and scalable
- Provides feature importance
- Supports probability prediction
- Performs well with engineered features

---

# Model Parameters

```python
model = XGBClassifier(
    n_estimators=150,
    learning_rate=0.05,
    max_depth=4,
    subsample=0.8,
    colsample_bytree=0.8,
    random_state=42,
    eval_metric='logloss'
)
```

---

# Train-Test Split

The dataset was divided into:

- 80% Training Data
- 20% Testing Data

Stratified sampling was used to maintain balanced churn distribution.

```python
train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42,
    stratify=y
)
```

---

# Model Evaluation Metrics

The model was evaluated using:

- Accuracy Score
- Classification Report
- Confusion Matrix
- ROC Curve
- AUC Score

---

# Confusion Matrix

The confusion matrix helps evaluate:

- True Positives
- True Negatives
- False Positives
- False Negatives

---

# ROC Curve & AUC Score

ROC-AUC was used to measure the model’s ability to distinguish between churn and non-churn customers.

Higher AUC indicates better classification performance.

---

# Feature Importance

Feature importance analysis was performed to identify the most influential features affecting customer churn.

The project visualizes feature importance using horizontal bar charts.

---

# Customer Risk Segmentation

Customers were categorized into three risk levels based on churn probability.

| Churn Probability | Risk Level |
|---|---|
| Less than 0.30 | Low Risk |
| 0.30 – 0.70 | Medium Risk |
| Greater than 0.70 | High Risk |

---

# Retention Strategy System

The project also recommends retention actions based on churn risk.

## High-Risk Customers
- Offer special discounts
- Provide loyalty rewards
- Assign relationship managers

## Medium-Risk Customers
- Improve engagement
- Send promotional offers

## Low-Risk Customers
- No immediate action required

---

# Sample Customer Prediction

The project includes prediction for a manually created sample customer profile.

The system predicts:
- Whether the customer will churn
- Churn probability
- Risk level
- Suggested retention strategy

---

# Output Generated

The project generates:

- Churn predictions
- Churn probability scores
- Customer risk levels
- Feature importance visualization
- ROC curve visualization
- CSV export file

---

# Output File

```bash
churn_prediction_results.csv
```

This file contains:
- Actual churn values
- Predicted churn values
- Churn probabilities
- Customer risk levels

---

# Project Workflow

```text
Data Collection
       ↓
Data Cleaning
       ↓
One-Hot Encoding
       ↓
Feature Engineering
       ↓
Train-Test Split
       ↓
Model Training (XGBoost)
       ↓
Prediction
       ↓
Model Evaluation
       ↓
Risk Segmentation
       ↓
Retention Strategy
       ↓
CSV Export & Visualization
```

---

# Installation

Install the required libraries using:

```bash
pip install pandas numpy matplotlib scikit-learn xgboost joblib
```

---

# How to Run the Project

```bash
python churn_prediction.py
```

---

# Expected Outputs

After running the project, the following outputs will be displayed:

- Model Accuracy
- Classification Report
- Confusion Matrix
- Feature Importance Table
- ROC-AUC Score
- Churn Prediction Results
- Retention Recommendations

---

# Real-World Applications

This project can be used in:

- Telecom Industry
- SaaS Platforms
- Banking Systems
- OTT Platforms
- E-commerce Businesses
- Insurance Companies
- Subscription-Based Services

---

# Future Improvements

Possible future enhancements:

- Hyperparameter tuning
- Cross-validation
- SHAP Explainability
- Streamlit dashboard integration
- Real-time prediction API
- Deep learning implementation
- Cloud deployment
- Automated retraining pipeline

---

# Key Learnings

Through this project, the following concepts were learned:

- Data preprocessing techniques
- Feature engineering
- Classification algorithms
- XGBoost implementation
- Model evaluation metrics
- ROC-AUC analysis
- Business-oriented machine learning
- Customer analytics and retention systems

---

# Conclusion

This project demonstrates how Machine Learning can be applied to customer retention problems using predictive analytics and behavioral data.

By combining data preprocessing, feature engineering, and the XGBoost algorithm, the system effectively predicts customer churn and provides actionable business insights for improving customer retention.

---

# Author

Developed as a Machine Learning Customer Churn Prediction Project using Python and XGBoost.
