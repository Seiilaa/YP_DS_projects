# Telecom customer churn prediction

- Analyzed customers behavior, checked numerical and categorical features distributions
- Built logistic regression, random forest and CatBoostClassifier models to predict customer churn
- Tested and compared the models

## Code and resources used

**Python Version:** 3.10.2\
**Packages:** pandas, numpy, scipy, matplotlib, seaborn, sklearn, statsmodels, catboost

## Data description

The operator provides two main types of services:

1. Fixed telephone connection.
2. Internet. The connection can be of two types: via a telephone line DSL or fiber optic cable.

Clients can pay for services every month or sign a contract for 1-2 years. Various payment methods and the possibility of receiving an electronic check are available.

- `contract.csv` — contract info;
- `personal.csv` — clients personal data;
- `internet.csv` — info about internet services;
- `phone.csv` — info about phone services.

## Task description

Build an ML model that would predict customer churn of a Telecom company. This model will be used to preemptively contact leaving customers and offer them promo codes or similar offers to increase their lifetime.

## Data cleaning
-   Found and processed missing values in the categorical variables
-   Checked data for duplicates
-   Changed data types to prepare data for model training
-   Extracted target variable from one of the features

## EDA
Studied categorical and numeric data, visualized distributions and correlations.
-   Categorical data:
    -   Studied distributions. Built piecharts
    -   Checked features influences on the target variable 
-   Numeric data
    -   Studied distributions with histograms
    -   Compared payments made by different categories of customers based on their payment plans
    -   Analyzed correlations, built scatterplots
-   Time trends
    -   Analyzed dynamics of the arrival and churn of the customers

## Data preparation
Removed useless features such as customer id, applied one hot encoding to the categorical features. Extracted 20% of the data as a holdout test set. Scaled numeric features with standard scaler so that the models give similar weights to all features.

## Model building
I used the ROC AUC metric to measure the quality of the models and compare them. ROC AUC was calculated based on the mean result of 4 split cross validation training.
-   Logistic regression
    - Train set: 0.8427 ROC AUC
    - Test set: 0.8432 ROC AUC
-   Random forest regressor
    - Test set: 0.846 ROC AUC
-   CatBoostClassifier
    - No parameter tuning — 0.8195 test set ROC AUC
    - Grid search parameters — 0.8396 test set ROC AUC
    - Less important features excluded — 0.8355 ROC AUC
## Models combining
I combined the best models into small ensembles to increase quality.
-   Logistic regression + Random Forest + Catboost gave 0.8477 ROC AUC on a test set
-   Logistic regression + Random Forest gave 0.8470 ROC AUC on a test set.

In the end all models gave an approximate result of 0.83 - 0.85 ROC AUC
When combining the best models into an ensemble, they give slightly better results.
