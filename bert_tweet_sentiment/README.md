# Classify a tweet as toxic or not
- In this project I learned how to do text classification using pretrained BERT model
- Using the embeddings I trained and compared Logistic regression, Random forest classifier and XGBoost models
- The models did the binary classification. The target is whether a tweet is toxic or not (1, 0)
- I used F1 score to measure the model performance due to class disbalance
- Compared the models performance

## Data

- "text" — contains the original text of the tweet
- "toxic" — a target variable. 0 — not toxic, 1 — toxic

## Code and resources used
Python Version: 3.10.2\
Packages: *pandas, numpy, tensorflow, transformers, pytorch, sklearn, xgboost*\
Resources: [DistilBERT](https://huggingface.co/docs/transformers/model_doc/distilbert)

## Data exploration
- All texts are written in English
- Class imbalance detected in data. Targeted tweets are found to only take up ~10% of the data.

## Data preprocessing
- Data tokenization using pretrained weights of a distilbert model
- Used truncation for the vectors that contain 512+ tokens
- Padded all objects to the 512 length
- In batches of 100 created embeddings

## Model training and comparison
- Split the data using 70/30 ratio to train and validation sets
- Trained logistic regression, Random forest classifier and XGBoost models without parameter tuning due to the high duration of training
- Compared the results
- Did 80/20 split, trained new models and repeat the model comparison

## Results

In this project I used pretratrained distilbert to get the embeddings.\
This allowed me to turn thousands of tweets of various length into vectors that could be used for the classification task.

The distilbert model is relatively light (it still took quite a while to create embeddings) but has a limit of 512 tokens in one vector.\
For this reason I decided to truncate ~2% of tweets that had more then 512 tokens. If there were less tokens, I padded them.

Next, I experimented with train/test sets ratio. More training data (80%) led to higher F1 score.

I trained and compared three models: Logistic regression, Random Forest and XGBoost.

Logistic regression easily beat other models showing 0.75-0.76 F1 score.\
Relatively good results were achieved with XGBoost. — ~0.67 F1 score\
I believe that by tuning the parameters the results could be improved and it could compare to the Logistic Regression.

But even if the results are equal, Logistic regression will show faster performance by taking only about a minute to train.\
It is 10 times less compared to XGBoost or Random Forest.