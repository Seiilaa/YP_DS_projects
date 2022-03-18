# Demand for airline flights analysis

* Analyzed flight data within Russia in 2018 
* For the first time used plotly library to create interactive charts

## Code and resources used

**Python Version:** 3.10.2
**Packages:** pandas, plotly

## Data description

- query_1.csv
    - model — airplane model
    - flights_amount — number of flights completed by each airplane model in September 2018
- query_3.csv
    - city — destination city;
    - average_flights — mean number of flights to the city per day in September 2018

## Task description

- Select top 10 cities by the number of arriving flights
- Understand what aircraft models are used by the airplane companies in Russia
- Find the most popular city by the number of arriving flights. Compare it to other cities

## Data cleaning
-	Made sure that there are no missing values
-	Made sure that there are no duplicates
-	Checked for anomalies and outliers in the data.

## EDA
-	Found that the aircraft models can be divided into two camps by the number of flights they did
-	One camp contains Airbus and Boeing aircrafts with only 5% of all daily flights each.
-	The other camp is represented by Bombardier, Cessna and Suchoi aircrafts each accounting for ~27% of daily races.
-	The maximum number of daily flights is ~130 while the median is only 3. Turns out that the top city by the number of arriving flights is Moscow accounting for 23.4% of all daily races in Russia.
-	All findings are accompanied by interactive plotly charts which I found to be pretty handy!