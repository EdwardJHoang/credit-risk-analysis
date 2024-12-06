# Credit Risk Analysis

## Overview
This project aims to develop predictive models to address two critical objectives in loan application processing:
1. **Loan Approval Prediction**: Determine whether a loan application will be approved based on the applicant's personal and financial attributes.
2. **Default Risk Assessment**: For approved loans, predict the likelihood of default to assist financial institutions in managing risks effectively.

The dataset for this project was sourced from [Kaggle](https://www.kaggle.com/datasets/itshappy/ps4e9-original-data-loan-approval-prediction). The project explores key features like income, employment length, credit history, and loan intent to build accurate predictive models.

---

## Dataset
- **Source**: [Kaggle Dataset](https://www.kaggle.com/datasets/itshappy/ps4e9-original-data-loan-approval-prediction)
- **License**: Apache 2.0
- **Size**: 32,581 rows and 12 columns
- **Description**: Each row represents a loan application, and the features include both categorical and numerical data.

### Key Features
| **Feature**                   | **Description**                                                           |
|-------------------------------|---------------------------------------------------------------------------|
| `person_age`                  | Age of the applicant (numeric).                                           |
| `person_income`               | Annual income of the applicant (numeric).                                 |
| `person_home_ownership`       | Home ownership status (`RENT`, `OWN`, `MORTGAGE`, `OTHER`).               |
| `person_emp_length`           | Length of employment in years (numeric).                                  |
| `loan_intent`                 | Purpose of the loan (`PERSONAL`, `EDUCATION`, `MEDICAL`, etc.).           |
| `loan_grade`                  | Grade of the loan (`A`, `B`, `C`, etc.).                                  |
| `loan_amnt`                   | Loan amount requested (numeric).                                          |
| `loan_int_rate`               | Interest rate of the loan (numeric, as a percentage).                     |
| `loan_status`                 | Target variable (1 = approved, 0 = denied).                              |
| `loan_percent_income`         | Percentage of income allocated to loan repayment (numeric).               |
| `cb_person_default_on_file`   | History of default (`Y` = Yes, `N` = No).                                 |
| `cb_person_cred_hist_length`  | Length of credit history in years (numeric).                              |

---

## Objectives
1. **Primary Objective**: Predict whether a loan will be approved (`loan_status`).
2. **Secondary Objective**: Assess the likelihood of default for approved loans.

---

## Approach
### 1. **Exploratory Data Analysis (EDA)**
- Analyzed the data for missing values, outliers, and inconsistencies.
- Key observations:
  - Younger applicants (22–30 years) dominate the dataset.
  - Employment length and credit history strongly correlate with loan approvals.
  - Higher loan grades (`A`, `B`) are associated with lower interest rates.
- Visualizations included distribution plots, boxplots, and a correlation heatmap.

### 2. **Data Preprocessing**
- **Outlier Removal**: Used the IQR method to handle unrealistic values (e.g., ages > 100).
- **Missing Value Handling**: Imputed or removed rows with missing values for critical features.
- **Feature Engineering**:
  - Standardized numerical features using `StandardScaler`.
  - One-hot encoded categorical features for modeling.

### 3. **Model Development**
#### Models Applied:
1. **Logistic Regression**:
   - Balanced class weights to handle imbalanced data.
   - Recursive Feature Elimination (RFE) for selecting the top 12 features.
   - Achieved an accuracy of **80.5%** and an F1 score of **0.614**.

2. **K-Nearest Neighbors (KNN)**:
   - Tuned the `K` parameter using GridSearchCV.
   - Optimal `K = 7`, with accuracy **89.4%** and F1 score **0.696**.

3. **Neural Network (MLP)**:
   - Multi-Layer Perceptron with one hidden layer of 100 neurons.
   - Achieved accuracy **90.85%**, F1 score **0.750**, and ROC-AUC **0.892**.

### 4. **Model Evaluation**
- Neural Network outperformed other models, demonstrating its ability to capture complex patterns.
- Logistic Regression remained interpretable and reliable for baseline predictions.
- Threshold tuning in Neural Network provided insights into balancing precision and recall for different risk tolerances.

---

## Results
| **Model**                | **Accuracy** | **F1 Score** | **ROC-AUC** |
|---------------------------|--------------|--------------|-------------|
| Logistic Regression       | 80.5%       | 0.614        | N/A         |
| KNN (K=7)                 | 89.4%       | 0.696        | N/A         |
| Neural Network (MLP)      | 90.85%      | 0.750        | 0.892       |

---

## Insights
- **Loan Approval Trends**: Younger applicants (22–30 years) dominate loan applications, and higher loan grades (A, B) correlate with lower interest rates.
- **Risk Indicators**: Employment length and credit history strongly influence loan approval probabilities.
- **Model Performance**: Neural networks provided the best balance between accuracy (90.85%) and recall, indicating their ability to identify both approved and denied loans effectively.

---

## Conclusions
1. The developed predictive models can accurately classify loan approvals, with the neural network model demonstrating the best overall performance.
2. The correlation between income, loan grade, and approval likelihood suggests that these features are critical for risk assessment.
3. Logistic regression remains a useful baseline model due to its interpretability, particularly for explaining decisions to stakeholders.

---

## Recommendations
1. **Implement Neural Network for Automation**:
   - Use the neural network model to automate initial loan approval decisions due to its high accuracy and strong ability to identify potential defaults.

2. **Leverage Logistic Regression for Explainability**:
   - For borderline cases or regulatory requirements, utilize logistic regression to explain the key factors influencing loan decisions.

3. **Adjust Decision Thresholds**:
   - Fine-tune the classification threshold based on the institution’s risk tolerance:
     - **Higher Thresholds**: Focus on minimizing defaults by only approving highly qualified applicants.
     - **Lower Thresholds**: Expand loan approvals to capture a larger customer base, balancing higher risk with potential gains.

4. **Monitor High-Risk Groups**:
   - Pay close attention to applicants with:
     - Short credit histories.
     - High loan-to-income ratios.
     - Lower loan grades (`D`, `E`, `F`).

5. **Expand Features for Future Models**:
   - Incorporate additional features, such as:
     - Debt-to-income ratios.
     - External credit scores.
     - Geographic or regional economic data.
   - This would improve model accuracy and provide a broader risk assessment framework.

6. **Explore Ensemble Models**:
   - Investigate advanced techniques like Random Forest or Gradient Boosting to combine the strengths of different algorithms, potentially improving both accuracy and interpretability.

7. **Establish Regular Model Retraining**:
   - Retrain the models periodically with updated data to capture shifts in applicant behavior or macroeconomic changes, ensuring the models remain relevant.

---

## Dependencies
- Python 3.8+
- Key Libraries:
  - pandas
  - numpy
  - matplotlib
  - seaborn
  - scikit-learn
   -jupyter
