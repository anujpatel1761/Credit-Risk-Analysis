# 🏦Credit Risk Analysis with XGBoost💸

<img src="./static/images/Home_page_mobile.png"/>

## What is Credit Risk Analysis?
**Credit Risk Analysis** is an important process that enables lenders, credit rating agencies, and other financial institutions to evaluate the creditworthiness of borrowers and make informed decisions about extending credit. In this project, we use the **XGBoost** algorithm with **RandomizedSearchCV** for hyperparameter tuning to predict whether a borrower is likely to default on a loan or not.

## Dataset
The <a href="./Data/">dataset</a> used in this project contains information about loan applications including:
- **Personal Information**: Gender, Marital Status, Dependents, Education, Self-Employment
- **Financial Metrics**: Applicant Income, Co-Applicant Income, Loan Amount, Loan Amount Term
- **Credit Information**: Credit History
- **Property Details**: Property Area
- **Target Variable**: Loan Status (Approved/Rejected)

## Data Preprocessing Steps
Our preprocessing pipeline includes:
1. **Handling Missing Values**: 
   - Categorical variables filled with mode
   - Numerical variables filled with mean
2. **Feature Engineering**:
   - Created TotalIncome by combining ApplicantIncome and CoapplicantIncome
   - Applied log transformation to LoanAmount and TotalIncome to handle skewness
3. **Categorical Encoding**:
   - Binary mapping for Gender, Married, Education, Self_Employed
   - Label Encoding for Dependents and Property_Area
4. **Feature Selection**:
   - Removed redundant features like Loan_ID
   - Selected the most relevant features for prediction

## Model Building
Our modeling approach includes:
1. **Base Model**: Initial XGBoost classifier with default parameters
2. **Hyperparameter Tuning**:
   - Used RandomizedSearchCV with 5-fold cross-validation
   - Optimized parameters: learning_rate, max_depth, n_estimators, gamma, subsample, colsample_bytree
3. **Final Model Training**: Trained with optimized parameters on preprocessed data
4. **Evaluation**: Assessed model using classification metrics

## Results & Performance
Our XGBoost model achieves:
- **Accuracy**: 85% overall prediction accuracy
- **Precision**: 
  - 91% for rejected loans (Class 0)
  - 83% for approved loans (Class 1)
- **Recall**: 
  - 55% for rejected loans (Class 0)
  - 98% for approved loans (Class 1)
- **Confusion Matrix**:
  ```
  [[21 17]
   [ 2 83]]
  ```
- **AUC Score**: High area under ROC curve indicating good classification performance

## Web Application
We've developed a Flask-based web application that allows users to:
- Input loan applicant details
- Get instant loan approval predictions
- Understand the key factors affecting the decision

<img src="./static/images/Loan Approval.png"/>

## Technical Architecture
- **Backend**: Flask web framework 
- **Database**: SQLite for storing prediction records
- **Model Deployment**: Pickled XGBoost model for real-time inference
- **Frontend**: HTML/CSS for interface design

## Installation Guide:
1. Clone the repository to your local machine:
```
git clone https://github.com/SannketNikam/Credit-Risk-Analysis.git
```

2. Install the dependencies:
```
pip install -r requirements.txt
```

3. Run the application:
```
python app.py
```

4. Access the application in your browser:
```
http://127.0.0.1:8080
```

## Future Improvements
- Implement feature importance visualization
- Add explainability with SHAP values
- Develop a more sophisticated user interface
- Add model monitoring and retraining pipeline
- Explore additional algorithms for comparison

## Conclusion
This project demonstrates the effective use of XGBoost for credit risk analysis, achieving 85% prediction accuracy. The model is particularly strong at identifying good loan candidates while maintaining reasonable precision for rejections. The web application provides a user-friendly interface for lenders to make data-driven decisions on loan approvals.