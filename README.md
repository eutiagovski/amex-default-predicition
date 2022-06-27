# Amex Default Pedictions Challange

## Resume
### Propouse
According to Federal Reserve Economic Data, credit card delinquency rates have been increasing since 2016 (sharp decrease in Q1 2020 is due to COVID relief measures).
![image](https://user-images.githubusercontent.com/74082359/175775880-9e445da1-2670-4e66-9f2e-250c0dd80bb4.png)

The bank performs a charge-off on delinquent credit cards and eats the losses. If only there was a way to predict which customers had the highest probability of defaulting so it may be prevented…

The objective of this competition is to predict the probability that a customer does not pay back their credit card balance amount in the future based on their monthly customer profile. The target binary variable is calculated by observing 18 months performance window after the latest credit card statement, and if the customer does not pay due amount in 120 days after their latest statement date it is considered a default event. 

### Datasets
The datasets was provided by the host of the competition, and can be downloaded from https://www.kaggle.com/competitions/amex-default-prediction/data.

The dataset contains aggregated profile features for each customer at each statement date. Features are anonymized and normalized, and fall into the following general categories

### Task
The task is to predict, for each customer_ID, the probability of a future payment default.
Target: Did the customer default? (Yes=1/Positive, No=0/Negative)


## Exploratory Data Analysis
More detais of this step can be found at: https://github.com/eutiagovski/amex-default-predicition/blob/main/data-exploring/Amex_Default_Data_Exploring.ipynb

Distribution of target classes is highly imbalanced, non-defaults far outnumber defaults. This is common in these datasets since most people pay credit cards on time (assuming there isn’t an economic crisis).
![image](https://user-images.githubusercontent.com/74082359/175775987-a2dd7449-0592-417e-8dac-4320bb2de0c6.png)



## Data Pre Processing
More details of this step can be found at: https://github.com/eutiagovski/amex-default-predicition/blob/main/data-preprocess/Amex_Default_Data_PreProcess.ipynb



## Modeling
More details of this step can be found at: https://github.com/eutiagovski/amex-default-predicition/blob/main/model-selection/Amex_Default_Model_Selection.ipynb

### Metrics
The metrics i'm using for this competitions is ofical metric, available in https://www.kaggle.com/competitions/amex-default-prediction/overview/evaluation

### Comparison
First i start modeling with 3 differents ML models that i use the most:

-Voting Classifier had an accuracy of 65%

-AnomalyDetector had an accuracy of 43%

-AutoML had an accuracy of 83%

The result of AutoML follows below, and although the best result is Ensemble, I choose to use the algorithm xgboost, which I am already used to working:

![image](https://user-images.githubusercontent.com/74082359/175653368-076aed0d-2d2b-4f70-a395-7878226e11ea.png)

Learning Curves
![image](https://user-images.githubusercontent.com/74082359/175931729-4b30e851-2333-499c-8da2-eec32b8cf732.png)

Top features
![image](https://user-images.githubusercontent.com/74082359/175931253-53ed94c8-a8c7-4e53-805d-b911b91dcf02.png)

Confusion Matrix
![image](https://user-images.githubusercontent.com/74082359/175931302-c581a9bd-609c-42e7-bd4a-252d26d9cef0.png)

Calibration
![image](https://user-images.githubusercontent.com/74082359/175931510-f6c5c7de-bc38-49ef-83f6-8cfa1a09a329.png)


## Predicting
More details of this step can be found at: https://github.com/eutiagovski/amex-default-predicition/blob/main/final-model/Amex_Default_Final_Model.ipynb

Until now, the best model is AutoML with XGBoost and hyperparams i am tunning. This model has an accuracy of 78.1%, wich leaves me at 1314°.

The leaderboard of this competition can be found at: https://www.kaggle.com/competitions/amex-default-prediction/leaderboard#


## THANK YOU!
The challenge of this competition was to work with the massive volume of data that was provided. There were more than 50gb of data, divided into more than 900k rows and more than 1k columns. To accomplish this, it took a lot of time researching different attempts and methods for loading the data.

Right now I'm tunning my best model hyperparams to increase my score in this competition.

I thank you fr reading and support so far. Fell free to leave any comments or suggestions on this project.

