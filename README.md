# HomeLoanDefaultManagementRisk

- An existential problem for any Loan providers today is to find out the Loan applicants who are very likely to repay the loan. This way companies can avoid losses and incur huge profits.

# Problem statement:
- Building a model to predict how capable each applicant is of repaying a loan, so that sanctioning loan only for the applicants who are likely to repay the loan.

# Data Description and Overview:
- The data is provided by Home Credit, a service dedicated to provided lines of credit (loans) to the unbanked population.

- There are 7 different sources of data:

- application_train/application_test: The main training data with information about each loan application at Home Credit. Every loan has its own row and is identified by the feature SK_ID_CURR. The training application data comes with the TARGET indicating 0: the loan was repaid or 1: the loan was not repaid. Here we will use only the Training data.
- bureau: In this dataset it consists of data concerning client’s previous credits from other financial institutions. Each previous credit has its own row in bureau, but one loan in the application data can have multiple previous credits.
- bureau_balance: It consists of monthly data about the previous credits in bureau. Each row is one month of a previous credit, and a single previous credit can have multiple rows, one for each month of the credit length.
- previous_application:The data of previous applications for loans at Home Credit of clients who have loans in the application data. Each current loan in the application data can have multiple previous loans. Each previous application has one row and is identified by the feature SK_ID_PREV.
- POS_CASH_BALANCE: It consists of monthly data about previous point of sale or cash loans clients have had with Home Credit. Each row is one month of a previous point of sale or cash loan, and a single previous loan can have many rows.
- credit_card_balance:The monthly data about previous credit cards clients have had with Home Credit. Each row is one month of a credit card balance, and a single credit card can have many rows.
- installments_payment:The data of payment history for previous loans at Home Credit. There is one row for every made payment and one row for every missed payment.

We can see that the data can be divided into three categories:
- Applicant-level data which contains information about the applicant, such as education, number of family members, car owned, etc.
- Bureau-level data which provides historical transactional information and credit balance information.
- Other data, including external data from other data sources such as credit scores from other platforms, etc.


![home](https://user-images.githubusercontent.com/101788326/186601675-5bc3d64e-80ed-4884-b624-e71375736055.png)

# EDA and Insights:

![target](https://user-images.githubusercontent.com/101788326/186606923-39751d22-dfc4-4e8e-986f-6333ed46df76.jpg)


- No. of defaulters: 24825
- No. of non-defaulters: 282686
- Percentage of defaulters: 8.072881945686495
- It’s an imbalance Dataset. (Defaulter : Non-Defaulter = 8 : 92 = 2 : 23)  Percentage of applicants approved previously but are defaulter in current loan: 7.588655443691958.
- Percentage of applicants refused previously but are non-defaulter in current loan: 88.00358612820408.
-  Most applications are approved. Cancelled and Refused are almost on the same level.

# Merging and Data Preprocessing

- Merging is done based on logics and merged on unique IDs.
- Used Pipelines like Simple Imputation, Column Transformer.
- Balancing the target variable using SMOTE.

# Model Building and Evaluation

- Different Algorithms are used like Logistic Regression, RandomForest,XGBoost where RandomForest gave a recall score of 97.4% and AUC – ROC curve measurement is performed for classification at various threshold settings where RandomFprest outperformed with 100%.

