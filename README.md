# Amex Default Pedictions Challange

## Resume

This is my resolution fot the challange propouse in: https://www.kaggle.com/competitions/amex-default-prediction

### Propouse
According to Federal Reserve Economic Data, credit card delinquency rates have been increasing since 2016 (sharp decrease in Q1 2020 is due to COVID relief measures).
![image](https://user-images.githubusercontent.com/74082359/175775880-9e445da1-2670-4e66-9f2e-250c0dd80bb4.png)

The bank performs a charge-off on delinquent credit cards and eats the losses. If only there was a way to predict which customers had the highest probability of defaulting so it may be prevented…

The objective of this competition is to predict the probability that a customer does not pay back their credit card balance amount in the future based on their monthly customer profile. The target binary variable is calculated by observing 18 months performance window after the latest credit card statement, and if the customer does not pay due amount in 120 days after their latest statement date it is considered a default event. 

### Datasets
The datasets was provided by the host of the competition, and can be downloaded from https://www.kaggle.com/competitions/amex-default-prediction/data.

It contains aggregated profile features for each customer at each statement date. Features are anonymized and normalized, and fall into the following general categories

### Task
The task is to predict, for each customer_ID, the probability of a future payment default.
Target: Did the customer default? (Yes=1/Positive, No=0/Negative)


## Exploratory Data Analysis

We will start by looking for the distribution of target. As we can see,  classes are not highly imbalanced. Non-defaults is not too far outnumber defaults. This is not common in these datasets since most people pay credit cards on time (assuming there isn’t an economic crisis).
![image](https://user-images.githubusercontent.com/74082359/175775987-a2dd7449-0592-417e-8dac-4320bb2de0c6.png)

In this scenario, we have expenses, payments, balance, risk and delinquency variables distributed in numerical and categorical variables.

In this step, we will be looking for patterns, correlations between variables, the amount of missing variables and putting together some theories.

One theory is that the date column is perhaps the most important of all. This is because we have more than one row for each customer_ID, and this leads us to calculate the difference between dates for the same id, and then get a variety of information, such as, the difference in days between each statement, the number of rows each id has related.

And finally we'll be looking for the correlation between these values and the final target variable.

More detais of this step can be found at: https://github.com/eutiagovski/amex-default-predicition/blob/main/data-exploring/Amex_Default_Data_Exploring.ipynb

## Data Pre Processing

In order to reduce even more the size of the datasets, we'll be encoding the customer_id and numericals columns.

In this step, we'll be applying what we've learn in previous section.

To facilitate validation of the initial model, we will be splitting the data into equal parts and training each chunk on a different model and comparing their results.

More details of this step can be found at: https://github.com/eutiagovski/amex-default-predicition/blob/main/data-preprocess/Amex_Default_Data_PreProcess.ipynb

## Modeling

### Metrics
The metrics i'm using for this competitions is ofical metric, available in https://www.kaggle.com/competitions/amex-default-prediction/overview/evaluation

### Comparison
First we start modeling with 3 differents ML Classifier models that we use the most.
We will be using a mandatory binary for this task as it will be prevented default or non-default targets.

![image](https://user-images.githubusercontent.com/74082359/175933565-2499cb66-4d4a-4bdd-964d-fe0756bd8423.png)

The result of AutoML follows below, and although the best result is Ensemble, I choose to use the algorithm xgboost, which I am already used to working:

![image](https://user-images.githubusercontent.com/74082359/175653368-076aed0d-2d2b-4f70-a395-7878226e11ea.png)


Learning Curves

What follows below shows us that the selected model had a high ability to adapt to the data with not too much iterations. We can use this information, and set set that point to save resources. 

![image](https://user-images.githubusercontent.com/74082359/175931729-4b30e851-2333-499c-8da2-eec32b8cf732.png)

Top features

Since we've made features engine, we can perform a validation of the best attributes in search of those that offer the best modeling conditions we need for optimization.

As we can see, the calculated variables had great importance in the model learning context.

![image](https://user-images.githubusercontent.com/74082359/175931253-53ed94c8-a8c7-4e53-805d-b911b91dcf02.png)


Confusion Matrix

The Confusion Matrix is calculated by the Rank search function. It displays the distribution of records in terms of their current classes and their predicted classes. This indicates the quality of the current model. 

The matrix brings us an interesting conclusion: it is easier for our model to predict a non-default target. So we will be treating this information in the future

![image](https://user-images.githubusercontent.com/74082359/175942441-f82c3f28-9598-4cf3-831a-943a2e00df0b.png)

Calibration

Finally, our final optimized model has a calibration curve that closely approximates the ideal model, indicating that the model is perfectly fitted.

![image](https://user-images.githubusercontent.com/74082359/175931510-f6c5c7de-bc38-49ef-83f6-8cfa1a09a329.png)


And now we are able to make the first predicts!

More details of this step can be found at: https://github.com/eutiagovski/amex-default-predicition/blob/main/model-selection/Amex_Default_Model_Selection.ipynb


## Predicting

Until now, the best model is AutoML with XGBoost and hyperparams i am tunning. This model has an accuracy of 78.1%, wich leaves me at 1314°.

The leaderboard of this competition can be found at: https://www.kaggle.com/competitions/amex-default-prediction/leaderboard?search=eutiagovski

More details of this step can be found at: https://github.com/eutiagovski/amex-default-predicition/blob/main/final-model/Amex_Default_Final_Model.ipynb

## THANK YOU!
The challenge of this competition was to work with the massive volume of data that was provided. There were more than 50gb of data, divided into more than 900k rows and more than 1k columns. To accomplish this, it took a lot of time researching different attempts and methods for loading the data.

Right now I'm tunning my best model hyperparams to increase my score in this competition.

I thank you fr reading and support so far. Fell free to leave any comments or suggestions on this project.

