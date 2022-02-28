# Report: Predicting Loan Risk with Logistic Regression

## Overview

The objective of this project is to build a model that predicts with reasonable accuracy loan defaults and can be deployed to flag loans that are "high-risk".

The historical dataset used to build this predictive model contains information on more than 77 thousand loans. Dependent variables include:

* Loan size
* Interest rate
* Borrower income
* Debt to income ratio
* Number of accounts
* Derogatory marks
* Total debt

The target of this predictive model is loan status, a binary label (i.e. healthy loan or high-risk loan). The original dataset is an unbalanced one with just 3% of loans defaulting. There are 75,036 loans classified as healthy and just 2,500 classified as high-risk.

This model was created using the following steps of the machine learning process.

* Split the data: The data are split into a training set that is used to fit the model and a testing set that is used to evaluate the accuracy of the model for out-of-sample observations. This is necessary to check for overfitting, a case in which the model performs well for training data but does not generalize this performance.

* Oversample the data: When the training dataset has imbalanced classes, it can produce a model that predicts the majority well but performs poorly predicting the minority class. In these cases oversampling or generating synthetic observations of the minority class will usually improve the efficacy of the predictive model.

* Fit a logistic regression model: Logistic Regression was chosen as a reliable solution for the problem of binary classification. The logistic regression model was fit with the resampled training data.

* Make predictions: The testing dataset was used to make predictions that can be compared with label data to determine accuracy.

* Evaluate the model: A confusion matrix and classification report are used to calculate the performance metrics of the model. Accuracy is the percentage of predictions that were classified correctly. Precision is the percentage of positives that were true positives. And recall is the percent of a given class that was correctly predicted by the model.

The techniques deployed include:
* LogisticRegression: Logistic Regression is a simple but powerful classifier purported to be used in 60% of classification problems. This project uses the Logistic Regression function from the SKLearn library.

* Resampling: The RandomOverSampler function from the imbalanced-learn library was used to solve the problem of imbalanced classes in the original dataset. The function over-samples the minority class by picking samples at random with replacement.

## Results

* Machine Learning Model 1:
  * Accurancy: 95%
  * Precision: 99%
  * Recall: 99%

* Machine Learning Model 2:
  * Accurancy: 99%
  * Precision: 99%
  * Recall: 99%

## Summary

Model 1 does reasonably well predicting both labels (healthy loans and high-risk loans) with 95% accuracy. It is considerably weaker flagging the minority class though. With a precision of 85%, about 15% of predicted high-risk loans are not actually high-risk loans. Recall for high-risk loans is 91%, meaning 91% of the actual high-risk loans are correctly identified by the model.

Model 2 (trained on rebalanced data) does considerably better identifying high-risk loans with recall improving from 91% to 99%. Precision actually declines for high-risk loans, but that is an expected trade-off for higher recall as the number of false positives ticked up.

I recommend using model 2 because the objective is to predict loan defaults and the second model performs better for high-risk loans, the minority class. It is more important to flag the rare but important case of a high-risk loan than predict healthy loans (the typical case).