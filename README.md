# Credit Risk Analysis - Loan Approvals  
**Author**: Mai Trong Nghia Hoang  
**Data Source**: Provided by Infinity (Kaggle)  
**License**: Apache 2.0  

---

## Project Overview  
This project aims to develop a **predictive model** to assess:  
1. **Loan Approval**: Predict if a loan application will be approved.  
2. **Default Risk**: Estimate the likelihood of loan default for approved applications.  

Accurate loan approval predictions help financial institutions manage risk and reduce financial losses by identifying high-risk applicants.

---

## Objectives  
The primary objectives of this project are:  
1. Build a predictive model to classify loan approvals.  
2. Assess default risk based on applicant and loan features.  
3. Identify key features influencing loan approval decisions.  
4. Provide insights into loan distributions and lending patterns.  

---

## Problem Statement  
Can we predict whether a loan will be approved and estimate default probabilities based on features like:  
- Applicant income, employment length, and credit history.  
- Loan purpose, amount, grade, and interest rate.  

A successful model will help lenders balance **loan approvals** and **risk management** efficiently.

---

## Dataset Description  
The dataset comprises **32,581 records** and **12 features**, representing various loan applicants.  

### Key Features  
| **Feature Name**               | **Description**                                               | **Type**     |  
|--------------------------------|-------------------------------------------------------------|--------------|  
| `person_age`                   | Age of the loan applicant                                    | Numeric      |  
| `person_income`                | Annual income of the applicant                              | Numeric      |  
| `person_home_ownership`        | Home ownership status (`RENT`, `OWN`, `MORTGAGE`)           | Categorical  |  
| `person_emp_length`            | Employment length in years                                  | Numeric      |  
| `loan_intent`                  | Purpose of the loan (`PERSONAL`, `EDUCATION`, etc.)         | Categorical  |  
| `loan_grade`                   | Loan grade (A-G), indicating creditworthiness               | Categorical  |  
| `loan_amnt`                    | Loan amount requested                                       | Numeric      |  
| `loan_int_rate`                | Loan interest rate as a percentage                          | Numeric      |  
| `loan_status`                  | Approval status (`1` = Approved, `0` = Denied)              | Target       |  
| `loan_percent_income`          | Loan-to-income ratio                                        | Numeric      |  
| `cb_person_default_on_file`    | Default history (`Y` = Yes, `N` = No)                       | Categorical  |  
| `cb_person_cred_hist_length`   | Length of credit history in years                           | Numeric      |  

---

## Data Exploration and Insights  
### 1. **Data Cleaning and Preparation**  
- Outliers were removed to ensure data integrity and improve model performance.  
- Missing values were handled to maintain dataset consistency.  
- Categorical features like `loan_grade` and `loan_intent` were standardized for analysis.  

### 2. **Observations from Exploratory Data Analysis**  
- **Applicant Age**: Most loan applicants are **between 22-30 years** old, indicating a younger demographic seeking loans.  
- **Income**: The median income is skewed towards **lower ranges**, reflecting affordability concerns.  
- **Loan Amount**: Peaks are observed at **$5,000 and $12,000**, representing two common loan tiers.  
- **Interest Rates**: Higher grades (A, B) correspond to **lower interest rates**, aligning with lower credit risk.  
- **Credit History**: Most applicants have **short credit histories** (2-6 years), consistent with younger applicants.  

### 3. **Correlation Between Features**  
- **Loan Percent Income** is **negatively correlated** with income: Higher incomes lead to smaller loan-to-income ratios.  
- **Loan Grades** strongly influence interest rates: Higher grades have **lower rates**.  
- **Default History** (cb_person_default_on_file) has a **strong association** with loan denials.

---

## Results Summary  

### Model Performance Overview  
The project evaluated multiple predictive models to classify loan approvals and estimate default risk.  

| **Model**                | **Accuracy** | **F1 Score** | **Key Insights**                                |  
|--------------------------|-------------|-------------|-----------------------------------------------|  
| **Logistic Regression**  | 80.5%       | 61.4%       | Stable model with moderate performance.        |  
| **K-Nearest Neighbors**  | 89.3%       | 69.2%       | Improved accuracy with optimal `K=9`.          |  
| **Neural Network**       | 90.8%       | 74.9%       | Best performance balancing precision & recall. |  

### Insights  
- **Neural Networks** achieved the best balance between accuracy and recall.  
- The **KNN model** provided strong accuracy but showed sensitivity to data scaling.  
- Logistic Regression delivered interpretable insights but slightly lower performance.  

---

## Key Findings  
1. **Top Influencing Features**:  
   - Loan Amount (`loan_amnt`)  
   - Loan Interest Rate (`loan_int_rate`)  
   - Loan Percent Income (`loan_percent_income`)  
   - Credit Grade (D-G) and Home Ownership Status.  

2. **Applicant Insights**:  
   - Higher-income individuals have lower loan-to-income ratios and approval rates.  
   - Loan defaults are strongly linked to poor credit grades and shorter credit histories.  

3. **Loan Intent**:  
   - Personal loans dominate, but educational loans have slightly lower interest rates.  

---

## Recommendations  
1. **Focus on Key Features**:  
   - Prioritise interest rates and credit grades to identify high-risk applicants.  

2. **Adjust Decision Thresholds**:  
   - Fine-tune loan approval thresholds based on risk tolerance.  

3. **Future Enhancements**:  
   - Include additional features like **debt-to-income ratio** and **geographic data**.  
   - Address class imbalance using techniques like **SMOTE**.  
   - Test ensemble models (e.g., Random Forest, XGBoost) for further improvements.

---

## File Structure  
The project follows a clear and organized folder structure:  
project_folder/
|-- credit_risk_dataset.csv # Raw dataset
|-- final_data.csv # Cleaned dataset
|-- credit_risk_analysis.ipynb # Main notebook
|-- README.md # Project documentation

---

## Future Work  
1. Apply ensemble techniques for better predictive performance (e.g., XGBoost, Random Forest).  
2. Investigate **feature engineering** to include new metrics like debt-to-income ratio.  
3. Address class imbalance with advanced techniques like oversampling (SMOTE).  
4. Deploy the best-performing model into a **production-ready pipeline** for real-world use.

---

## Contact  
**Author**: Mai Trong Nghia Hoang  
For queries or collaboration, please contact: **edward.n.hoang@gmail.com**.  
