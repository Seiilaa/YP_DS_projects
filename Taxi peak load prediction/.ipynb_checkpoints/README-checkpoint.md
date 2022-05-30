# Taxi orders time series prediction

- Analyzed time series data
- Found trends and seasonality in the data that covers a period March 1, 2018 - August 31, 2018
- Engineered features: rolling mean, lag, weekday/month/day of the month
- Built linear regression, random forest regressor and LGBM regressor to predict hourly peak demand.
- Experimented with rolling mean size, maximum lag and model parameters to achieve higher model performance
## Code and resources used

**Python Version:** 3.10.2
**Packages:** pandas, numpy, matplotlib, seaborn, sklearn, statsmodels, lightgbm

## Data description

- taxi.csv
    - datetime — date and time with 10 minutes intervals for a period March 1, 2018 - August 31, 2018
    - num_orders — number of taxi orders received by the taxi operator within this time period.

## Task description

Build an ML model that would predict peak load of the taxi operator in the next hour. The model will be used to call the necessary number of taxi drivers in advance. 

## EDA
-   Calculated rolling mean and added it to the plot. Found a upward trend — number of orders on the selected time period is increasing 
-   Found seasonality on a daily interval. The number of orders reaches it's maximum near midnight and a minimum in the early morning at about 6 AM

## Feature engineering
-   Engineered features:
    -   Month, day of the month and a day of the week
    -   Lag — number of orders in previous hours. These features should be useful to catch patterns in the data on a daily level.
    -   Rolling mean — this feature should be useful to use patterns and find trends on a larger time scale — days and weeks.
## Model building
-   Trained Linear regression, random forest regressor and lgbm regressor. Used time series split for cross validation to avoid data leakage
-   Mean RMSE on the 3 split cross validation:
    -   Linear Regression — 28.67 RMSE
    -   Random Forest Regressor — 29.14 RMSE
    -   LGBM Regressor — 29.61 RMSE

## Testing the models
-   Built a baseline constant model that always predicts the median number of orders. Got 87.152776 RMSE on a test set.
-   Tested the models on a 10% holdout test set
    -   Linear Regression — 46.30 RMSE
    -   Random Forest Regressor — 52.88 RMSE
    -   LGBM Regressor — 55.35 RMSE
    -   Constant median baseline model — 87.15 RMSE

The best result in this project was achieved by the linear regression — most probably it managed to catch the rising trend in the data and used it to to make predictions.

Random Forest and LGBM regressors show nearly similar results though still beating constant model.

## Features and model parameters tuning
Did some experimenting with the rolling mean size and max lag along with parameter tuning (for LGBM model)

All changes were first tested using 3 splits cross validation, next best sets of parameters were tested on a 10% holdout set.
-   Linear regression — 23.89 RMSE on a train set and 43.34 RMSE on a test set
-   LGBM regressor — 24.5 RMSE of a train set and 49.86 RMSE on a test set

By adjusting the rolling mean size and maximum time lag I have managed to improve Linear regression models RMSE by 3 — from ~46.3 to ~43.3 which is a significant improvement.

LGBM regression might not be the best suit for this kind of task as the training dataset is relatively small. Still some parameters and features tuning significantly improved the model performance — RMSE decreased from 55.35 to 49.85 which is a big improvement.