# Model prototype for heavy industry

- Performed data exploration of the gold extraction from gold ore process 
- Analysed and visualized concentration of various metals throught the ore cleaning process.
- Built two separate Random Forest models to predict gold concentration in various stages of the cleaning process. An ensemble of these models can be used as a prototype to create other models on top of.

## Libraries used

- **Python Version:** 3.10.2
- **Packages:** pandas, numpy, matplotlib, sklearn

## Data description

**Technological process**

- Rougher feed - initial raw material
- Rougher additions - flotation reagents: Xanthate, Sulphate, Depressant
- Xanthate ** - xanthate (promoter, or flotation activator);
- Sulphate - sulfate (in this production, sodium sulfide);
- Depressant - depressant (sodium silicate).
- Rougher process - flotation
- Rougher tails
- Float banks - flotation unit
- Cleaner process - cleaning
- Rougher Au - crude gold concentrate
- Final Au - final gold concentrate

**Stage parameters**

- air amount — air volume
- fluid levels - fluid level
- feed size - feed granule size
- feed rate — feed rate

## Task description

Prepare a prototype of a machine learning model that predicts the recovery rate of gold from gold ore.

The project is made for a company that develops solutions for the efficient operation for the gold mining industry.
The end result of the project is development of a prototype model that predicts the recovery factor of gold from gold-bearing ore.
This model will be used to help optimize production and avoid launching enterprises with unprofitable characteristics.

## Process description 

When the mined ore undergoes primary processing, a crushed mixture is obtained. It is sent for flotation (enrichment) and two-stage cleaning. This is how gold ore is recovered from mined ore.

1. **Flotation**

A mixture of gold-bearing ore is fed into the flotation plant. After enrichment, a rough concentrate and “waste tailings” are obtained — product residues with a low concentration of valuable metals.
The stability of this process is affected by the unstable and non-optimal physico-chemical state of the flotation pulp (a mixture of solid particles and liquid).

2. **Cleaning**

The crude concentrate goes through two purifications. The output is the final concentrate and new final tailings.

The Recovery coefficient (the target variable) is calculated using this formula:

Recovery = C*(F-T)/F*(C-T)*100%

C — share of gold in concentrate after flotation/cleaning;
F — share of gold in raw material/concentrate before flotation/cleaning;
T — proportion of gold in waste tailings after flotation/cleaning.

The idea is to have higher concentration of gold in the final concentrate and waste as little gold as possible by leaving it in the tailings (waste).

## Initial exploration

- Found missing values in the dataset, understood the dataset structure.
- Found that training set has features on present in the test set and could be potential target leaks.
- Made sure to recalculate the target variable using available data.

## Data cleaning

Found and dealt with missing values. Checked datasets for correlations and decided to remove some of the features to avoid multicorreality problems training the models on this data.

## EDA

Analyzed in more details gold extraction process, visualised change of different metals concetrations in the ore throught the cleaning and flotation process. In addition to that I included some analysis of the granule sizes and total concentration of different metals in the ore on different stages.

## Model builing

To optimize the models I used sMAPE metric.
As the final results depends on predicting two separate target variables, I trained two separate models two predict recovery coefficients in final concentrate and in the tailings.
I compared Linear regression and Random Forest models with the hyperparameters tuned using gridsearch.
Random Forest showed better performance overall. The feature imporatances test showed that only 9 parameters were actively used by the model to predict the target.

In the end I prepared a prototype of a model to estimate gold recovery coefficient. 
This model consists of two separate Random Forest Regressors. Results of these models are combined using the recovery coefficient formula.
sMAPE of a final model on a test holdout set is: ~9.8 
