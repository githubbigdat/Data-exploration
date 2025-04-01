# LendingClub Loan Default Prediction

## Introduction
This project analyzes the LendingClub dataset to understand the features associated with loan defaults. The analysis involves data cleaning, visualization, feature engineering, and model selection to improve the predictive power of machine learning models. Among the various models tested, the **random forest model** performed the best.

The report also highlights the most important features for predicting loan defaults, identified using the **permutation importance algorithm**. These insights are valuable for feature selection and model optimization.

## Data Exploration
The LendingClub dataset contains **226,067 observations** and **31 variables** (both numeric and categorical). The following variables were selected for feature engineering and forecasting:

- **Loan amount (loan_amnt)**: The approved loan amount.
- **Interest rate (int_rate)**: The loan's interest rate (percentage).
- **Annual income (annual_inc)**: Borrower's reported annual income.
- **Total mortgage payment (total_pymnt)**: Total amount paid on the loan.
- **Mortgage installment (installment)**: Monthly required payment (principal + interest).
- **Total paid in interest rates (total_rec_int)**: Total interest paid on the loan.
- **Last payment amount (last_pymnt_amnt)**: Amount of the most recent loan payment.

## Data Cleaning
To ensure accurate predictions, the dataset was cleaned using the following steps:
1. **Removing variables with more than 10 missing observations** to eliminate irrelevant or biased data.
2. **Dropping only the missing observations** for variables with fewer than 10 missing values to retain as much data as possible.

## Data Visualization
The exploratory analysis revealed that:
- Loan amounts tend to increase with **higher credit grades**.
- Interest rates are higher for **lower credit grades**, indicating higher risk.

## Feature Engineering
To enhance predictive power, new features were created, including:
- **Loan_dummy**: A binary variable representing loan status (1 = charged off, 0 = otherwise).
- **Other transformations** to standardize features and improve model performance.

## Model Selection
Several machine learning models were trained and evaluated using **5-fold cross-validation** and the **Area Under the Receiver Operating Characteristic Curve (AUC-ROC)** metric:

| Model                           | AUC-ROC Score |
|---------------------------------|--------------|
| Logistic Regression             | 0.74         |
| Classification Tree             | 0.79         |
| Classification Tree (Cross-Val) | 0.81         |
| **Random Forest**               | **0.93**     |

### **Model Evaluation**
#### 1. Logistic Regression
- Achieved an **AUC-ROC of 0.74**.
- Model performance was only slightly better than random guessing.

#### 2. Classification Tree
- Performed better than logistic regression (**AUC-ROC of 0.79**).
- More effective at distinguishing between positive and negative loan statuses.

#### 3. Classification Tree with Cross-Validation
- Cross-validation improved performance to **AUC-ROC 0.81**.
- Helped reduce overfitting and improve generalization.

#### 4. Random Forest
- **Best model with an AUC-ROC of 0.93**.
- Outperformed all other models in predictive power.
- Effective at handling categorical and continuous data without extensive preprocessing.

## Feature Importance Analysis
Using the **permutation importance algorithm**, the most influential features for predicting loan default were:
1. **Interest Rate (int_rate)**
2. **Total Mortgage Payment (total_pymnt)**
3. **Installment Amount (installment)**

## Conclusion
- **Random Forest is the best-performing model** for predicting loan defaults.
- The **interest rate, total payments, and installment amount** are the most important predictors.
- Data cleaning and feature engineering significantly improved model performance.

These insights are valuable for lenders to assess loan risks more accurately and improve lending decisions.

## Repository Structure
```
├── data/                 # Raw and cleaned datasets
├── notebooks/            # Jupyter Notebooks for data analysis and modeling
├── models/               # Trained machine learning models
├── reports/              # Analysis reports and visualization results
├── README.md             # Project overview
```

## How to Use
1. Clone the repository:
   ```sh
   git clone https://github.com/yourusername/LendingClub-Loan-Prediction.git
   ```
2. Navigate to the project directory:
   ```sh
   cd LendingClub-Loan-Prediction
   ```
3. Install dependencies:
   ```sh
   pip install -r requirements.txt
   ```
4. Run the Jupyter Notebook for analysis:
   ```sh
   jupyter notebook
   ```

## Future Work
- Improve feature selection using advanced techniques.
- Test deep learning models for better accuracy.
- Deploy the model as an API for real-time loan risk assessment.

## Contributors
- Sujata Sarkar (https://github.com/Sujata Sarkar)

## License
This project is licensed under the MIT License.

