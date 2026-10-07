# 🏦 Loan Approval Prediction

A machine learning classification project that predicts whether a loan application is likely to be approved based on applicant and loan-related information.

The project includes data analysis, preprocessing, model comparison, evaluation, model persistence, and a Streamlit web application for making predictions.

## 🚀 Live Demo

The Streamlit deployment link will be added here after deployment.

## 📌 Project Overview

The goal of this project is to build a binary classification model that predicts:

- `Y` → Loan Approved
- `N` → Loan Rejected

The model takes applicant information such as income, credit history, education, property area, and loan amount as input and returns the predicted loan decision along with approval probability.

## 📊 Dataset

The dataset contains **381 records and 14 columns**.

Important features include:

- Gender
- Married
- Dependents
- Education
- Self Employed
- Applicant Income
- Coapplicant Income
- Loan Amount
- Loan Amount Term
- Credit History
- Property Area

Target variable:

- `Loan_Status`

The columns `Unnamed: 0` and `Loan_ID` were removed because they do not provide useful predictive information.

## 🔍 Exploratory Data Analysis

The project includes analysis of:

- Missing values
- Duplicate records
- Numerical feature distributions
- Loan approval distribution
- Credit history vs loan approval
- Education vs loan approval
- Applicant income vs loan approval
- Loan amount vs loan approval
- Property area vs loan approval

One of the strongest relationships observed was between **Credit History and Loan Status**.

Applicants with good credit history had a much higher approval rate than applicants without good credit history.

## 🧹 Data Preprocessing

The following preprocessing steps were performed:

- Removed unnecessary columns
- Checked duplicate records
- Handled missing numerical values using median imputation
- Handled missing categorical values using most-frequent imputation
- Encoded categorical features using One-Hot Encoding
- Standardized numerical features using StandardScaler
- Used a train-test split with stratification

```python
train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42,
    stratify=y
)
```

## 🤖 Models Compared

Three classification algorithms were evaluated:

1. Logistic Regression
2. Decision Tree
3. Random Forest
#### Cross-Validation Results
Model	                       CV Accuracy
Logistic Regression	           83.99%
Random Forest	               81.62%
Decision Tree	               77.68%

Based on the cross-validation results and overall evaluation, Logistic Regression was selected as the final model.

### 📈 Final Model Performance

The final Logistic Regression model achieved:

Test Accuracy: 85.71%

Confusion Matrix:

[[11 11]
 [ 0 55]]

Classification Report:

              precision    recall    f1-score

N                1.00       0.50       0.67
Y                0.83       1.00       0.91

accuracy                              0.86

The model achieved 100% recall for approved loans (Y) on the test set.

### 💾 Model Persistence

The trained model was saved using Joblib:

joblib.dump(final_model, "loan_approval_model.pkl")

The saved model is loaded by the Streamlit application to make predictions without retraining the model.

### 🌐 Streamlit Application

The project includes an interactive Streamlit interface where users can enter:

Gender
Marital status
Number of dependents
Education
Self-employment status
Applicant income
Coapplicant income
Loan amount
Loan term
Credit history
Property area

The application returns:

Loan approval/rejection
Approval probability
Rejection probability

### 🖥️ Run Locally
1. Clone the repository
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd LoanPricePrediction


2. Create a virtual environment
Windows:
py -3.13 -m venv .venv


3. Activate the environment
.venv\Scripts\activate


4. Install dependencies
python -m pip install -r requirements.txt


5. Run the Streamlit application
streamlit run main.py

The application will open in your browser.


### 📁 Project Structure
LoanPricePrediction/
│
├── loan_data_1.csv
├── loan_approval_model.pkl
├── main.ipynb
├── main.py
├── requirements.txt
├── README.md
└── .gitignore


### 🛠️ Technologies Used
Python
Pandas
NumPy
Scikit-learn
Joblib
Streamlit
Jupyter Notebook
Git & GitHub


### 🔮 Future Improvements

Possible improvements include:

Hyperparameter tuning
Better handling of class imbalance
Additional feature engineering
Model explainability
Interactive probability visualization
Deployment monitoring
Experiment tracking
Improved UI/UX