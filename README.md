Credit Risk Analysis - Loan Approvals

Project Overview

This project aims to develop a predictive model to determine loan approvals and assess the likelihood of default for approved loans. Accurate loan approval predictions are critical for financial institutions to mitigate risk and avoid financial losses.

Author

Mai Trong Nghia Hoang

Data Source

Provider: Infinity

Dataset: Available on Kaggle

File: credit_risk_dataset.csv

License: Apache 2.0

Problem Statement

Can we predict whether a loan will be approved and assess the likelihood of default based on applicant and loan characteristics?

Objectives

Develop a predictive model for loan approval.

Identify key features contributing to loan approval decisions.

Evaluate model performance to ensure reliable predictions.

Dataset Description

The dataset contains 12 features and 32,581 records. Each row represents a loan applicant.

Features:

person_age: Applicant's age (numeric).

person_income: Annual income (numeric).

person_home_ownership: Home ownership status ("RENT", "OWN", "MORTGAGE").

person_emp_length: Employment length (years).

loan_intent: Purpose of the loan (e.g., "PERSONAL", "EDUCATION").

loan_grade: Credit grade assigned (A-G).

loan_amnt: Requested loan amount.

loan_int_rate: Interest rate (percentage).

loan_status: Loan approval status (1 = approved, 0 = denied).

loan_percent_income: Loan payment as a percentage of income.

cb_person_default_on_file: Applicant's history of default (Y/N).

cb_person_cred_hist_length: Credit history length (years).

Exploratory Data Analysis (EDA)

Data Cleaning

Removed outliers using the IQR method.

Handled missing values and inconsistencies in employment length, loan interest rate, and other features.

Insights

Loan approval and applicant income have a positive correlation.

Higher loan grades (A, B) have lower interest rates, aligning with standard lending practices.

Majority of applicants are young (22-30) with short credit histories.

Visualization

Distributions of features (age, income, loan amount, etc.)

Correlation heatmaps between numerical features.

Boxplots analyzing relationships (e.g., loan grade vs. interest rate).

Feature Engineering

Converted loan_int_rate to decimal format.

One-hot encoded categorical features: person_home_ownership, loan_intent, loan_grade, and cb_person_default_on_file.

Selected 12 optimal features using Recursive Feature Elimination (RFE).

Selected Features:

loan_amnt, loan_int_rate, loan_percent_income

person_home_ownership_OWN, person_home_ownership_RENT

loan_intent_EDUCATION, loan_intent_HOMEIMPROVEMENT, loan_intent_VENTURE

loan_grade_D, loan_grade_E, loan_grade_F, loan_grade_G

Predictive Modeling

1. Logistic Regression

Training Accuracy: 80.6%

Testing Accuracy: 80.5%

F1-Score: 61.4%

Optimal Features: 12 (selected using RFE).

2. K-Nearest Neighbors (KNN)

Best K: 9 (tuned using GridSearchCV).

Testing Accuracy: 89.3%

F1-Score: 69.2%

3. Neural Network (MLPClassifier)

Accuracy: 90.8%

F1-Score: 74.9%

ROC AUC: 89.2%

Key Results

Logistic Regression:

Achieves stable accuracy but shows room for improvement in recall.

KNN:

Best performance at K = 9 with strong accuracy (89.3%).

Neural Network:

Best overall performance with accuracy (90.8%) and F1-score (74.9%).

Threshold Tuning:

Adjusting thresholds can optimize recall or precision based on business needs.

Tools and Libraries

Python: pandas, numpy, scikit-learn, matplotlib, seaborn

Models: Logistic Regression, KNN, Neural Network (MLP)

Feature Selection: RFE

Hyperparameter Tuning: GridSearchCV

Conclusions and Recommendations

The Neural Network model performs best, achieving a balance between precision and recall.

Optimal thresholds can be chosen based on risk appetite (higher threshold for conservative approvals).

Focus on reducing false negatives to ensure valid loan applicants are not rejected.

Future Work

Experiment with ensemble methods (e.g., Random Forest, XGBoost).

Address class imbalance using SMOTE or similar techniques.

Integrate additional features like debt-to-income ratios or applicant location data.

File Structure

project_folder/
|-- credit_risk_dataset.csv       # Raw data
|-- final_data.csv                # Cleaned dataset
|-- credit_risk_analysis.ipynb    # Jupyter notebook
|-- README.md                     # Project documentation

License

This project is licensed under the Apache License 2.0. For details, refer to
