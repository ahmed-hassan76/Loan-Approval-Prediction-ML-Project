# Loan Approval Prediction using Machine Learning  
A complete end-to-end machine learning project that predicts whether a loan application will be approved based on applicant financial and demographic attributes.

---

## 📌 Project Overview  
This project applies supervised machine learning techniques to predict **Loan Approval** using a structured dataset of 20,000 applicants.  
The workflow includes:

- Data Cleaning & Preparation  
- Exploratory Data Analysis (EDA)  
- Feature Engineering  
- Handling Class Imbalance (SMOTE)  
- Model Building (Decision Tree & Random Forest)  
- Model Evaluation & Comparison  
- Final Model Selection  
- Visualization of Decision Tree Structure  

---

## 📂 Dataset Description  
The dataset contains 20,000 rows and 18 features.

### **Key Columns:**
| Feature | Description |
|--------|-------------|
| ApplicationNumber | Unique identifier |
| Age | Applicant’s age |
| AnnualIncome | Yearly income |
| MonthlyIncome | Monthly income |
| CreditScore | Applicant credit score |
| LoanAmount | Amount requested |
| LoanDuration | Duration in months |
| EmploymentStatus | Job category |
| EducationLevel | Highest degree |
| MaritalStatus | Single/Married/Divorced/Widowed |
| NumberOfDependents | Number of dependents |
| HomeOwnershipStatus | Mortgage / Own / Rent / Other |
| BankruptcyHistory | 0 = No, 1 = Yes |
| LoanPurpose | Debt Consolidation / Home Improvement / Personal / Vehicle / Education |
| PreviousLoanDefaults | 0/1 indicator |
| MonthlyLoanPayment | Expected monthly payment |
| JobTenure | Years at current job |
| LoanApproved (Target) | Yes / No (mapped to 1/0) |

---

## 🧹 Data Cleaning  
- Converted monetary strings (e.g., `$26,992.00`) to numeric float types.  
- Standardized categorical labels (capitalization, whitespace).  
- Filled missing values appropriately (median for skewed numeric features).  
- Removed impossible values (e.g., age < 18 or > 100, negative incomes).  
- Ensured no target leakage — target column removed from features before training.

---

## 🛠 Feature Engineering  
Added the following feature:

### **Monthly_Debt_To_Income_Ratio**

---


This provides a normalized measure of payment burden.

---

## 📊 Exploratory Data Analysis (EDA)

### **Key EDA Questions Answered**
- Approval rates by education level  
- Quartile analysis for approved applicants' income  
- Relationship between age and credit score (scatter + best-fit line)  
- Distribution analysis of Monthly Income (normal vs skewed)  

Each visualization included a justification (“Why this chart?”).

---

## ⚖ Handling Class Imbalance  
Loan approval classes were imbalanced:

- **Not Approved:** 76.1%  
- **Approved:** 23.9%  

Used **SMOTE** only on the training set:

---

## 🤖 Model Training
1️⃣ Decision Tree

max_depth = 5

class_weight = None (because SMOTE already balanced classes)

Accuracy: 84.3%
Recall (Approved): 0.85
F1-score (Approved): 0.72

2️⃣ Random Forest

200 trees

max_depth = None

class_weight = None

Accuracy: 88.9%
Recall (Approved): 0.79
F1-score (Approved): 0.77

---

## 📈 Model Comparison
| Metric              | Decision Tree | Random Forest |
| ------------------- | ------------- | ------------- |
| Accuracy            | 0.843         | **0.889**     |
| Recall (Approved)   | **0.85**      | 0.79          |
| F1-score (Approved) | 0.72          | **0.77**      |
| Stability           | Low           | **High**      |
| Overfitting Risk    | High          | **Low**       |

✔ Chosen Model: Random Forest

Because it:

Achieves higher accuracy

Has better F1 score for the minority class

Generalizes better

Is more stable because it aggregates 200 trees

---

## 🌳 Decision Tree Visualization

Generated using:
plt.figure(figsize=(22,12))
plot_tree(model, feature_names=X.columns, filled=True, rounded=True, max_depth=3)
plt.show()

---

## 🛠 Technologies Used

Python

Pandas

NumPy

Matplotlib

Seaborn

Scikit-learn

imbalanced-learn (SMOTE)

Jupyter Notebook

---

## 👤 Author
Ahmed Hassan


