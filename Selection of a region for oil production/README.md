# Selection of a region for oil production

* Explored 3 oil producing regions 
* Predicted the best oil fields in these regions using linear regression
*  Evaluated possible profits and risks of developing these fields using the Bootstrap technique

## Code and resources used

**Python Version:** 3.7  
**Packages:** pandas, numpy, matplotlib, sklearn, seaborn  

## Data description

Data about the regions is located in the datasets below:

* geo_data_0.csv
* geo_data_1.csv
* geo_data_2.csv

* id — unique id number of an oilfield
* f0, f1, f2 — the features of the oilfields
* product — amount of oil in the oilfield (thousand barrels)

## Task description

- Only linear regression is suitable for training the model (other models are considered to be not predictable enough).
- During the exploration of the region, 500 fields are explored, from which, using machine learning, the best 200 are selected for development.
- The budget for the development of wells in the region is 10 billion rubles.
- One barrel of raw materials brings 450 rubles of income. The income from each unit of the product is 450 thousand rubles, since the volume is indicated in thousands of barrels.
- The data is synthetic: details of contracts and characteristics of the oil fields are not disclosed.

## Data cleaning
For each region I made sure that the data is ready for analysis and model building.
*	Checked datasets for missing values
*	Checked for the anomalies such as negative values where they certainly shouldn't be,  outliers, etc.
*	Made sure that the data types are suitable for further analysis

## EDA
I looked at the distributions of the data, correlation between features.  
*	Studied correlations between all features, built heatmap plots to visualize it
*	Studied distributions of the numeric features (all three regions only had numeric features). Built histograms

## Model building
Using linear regression predicted the oil amount in all three regions. Afterwards I compared both the models using RMSE metric and by calculating the real amount of oil in the locations selected by the models. 
*	Dedicated 25% of each regions' dataset to the test set
*	Trained linear regression models
*	Combined all models results in one table and compared their performance

## Profit calculation
Using the task description I estimated how much oil each location should contain in order to cover the development costs. Next I calculated the mean profits of each region's best 200 locations.

*	Each oil location should have at least 111.115 thousands of barrels to make development profitable
*	Mean oil amount across all locations in the region is lower than 111.115. This means that we can't just select random locations hoping that on average they are profitable. In this case we should be very peaky about the locations we select for development.	

## Risks calculation
To estimate the risks associated with each region's development I estimated the confidence intervals using bootstrap technique. 

*	Take all locations of the region
*	Randomly take out a subsample of the size of 500 units from all locations. After I take a location, I shuffle it back into the dataset, so that I have a chance to take it into my subsample again.
*	Using a pre-trained model, predict the amount of product in each location.
*	Select the top 200 locations according to the model prediction
*	Look at the real amount of product in the selected locations and calculate the profit that the company would have received if it had carried out work here
*	Save the result, put it on the histogram.
*	Repeat steps above 1000 times for each region.

## Results
All of the results are combined in one table. Only one of the regions can be reliably developed as it has < 1% risk of not being profitable and it has the biggest predicted amount of oil, thus the highest potential profit.