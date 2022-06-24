# Amex Default Pedictions Challange

## Resume
### Propouse
The objective of this competition is to predict the probability that a customer does not pay back their credit card balance amount in the future based on their monthly customer profile. The target binary variable is calculated by observing 18 months performance window after the latest credit card statement, and if the customer does not pay due amount in 120 days after their latest statement date it is considered a default event. 

### Datasets
The datasets was provided by the host of the competition, and can be downloaded from https://www.kaggle.com/competitions/amex-default-prediction/data.

The dataset contains aggregated profile features for each customer at each statement date. Features are anonymized and normalized, and fall into the following general categories

### Task
The task is to predict, for each customer_ID, the probability of a future payment default (target = 1).

## Data Exploring

## Data Pre Processing
More details of this step can be found at: https://github.com/eutiagovski/amex-default-predicition/blob/main/data-preprocess/Amex_Default_Data_PreProcess.ipynb

## Model Selection
### Files
More details of this step can be found at: https://github.com/eutiagovski/amex-default-predicition/blob/main/model-selection/Amex_Default_Model_Selection.ipynb

### Metrics
The metrics i'm using for this competitions is ofical metric, available in https://www.kaggle.com/competitions/amex-default-prediction/overview/evaluation

### Model Comparison
First i start modeling with 3 differents ML models that i use the most:

-Voting Classifier had an accuracy of 65%

-AnomalyDetector had an accuracy of 43%

-AutoML had an accuracy of 83%

The result of AutoML follows below, and although the best result is Ensemble, I choose to use the algorithm xgboost, which I am already used to working:

![image](https://user-images.githubusercontent.com/74082359/175653368-076aed0d-2d2b-4f70-a395-7878226e11ea.png)

## Final Model
More details of this step can be found at: https://github.com/eutiagovski/amex-default-predicition/blob/main/final-model/Amex_Default_Final_Model.ipynb

Until now, the best model is AutoML with XGBoost and hyperparams tunning.

### Final Predictions
Until now, the best model is AutoML with XGBoost and hyperparams i am tunning. This model has an accuracy of 78.1%, wich leaves me at 1314°.

The leaderboard of this competition can be found at: https://www.kaggle.com/competitions/amex-default-prediction/leaderboard#

## THANK YOU!
The challenge of this competition was to work with the massive volume of data that was provided. There were more than 50gb of data, divided into more than 900k rows and more than 1k columns. To accomplish this, it took a lot of time researching different attempts and methods for loading the data.

Right now I'm tunning my best model hyperparams to increase my score in this competition.

