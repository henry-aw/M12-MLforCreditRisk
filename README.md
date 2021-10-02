# Module 12 Report: Evaluating ML Models for Identifying Borrower Creditworthiness

## Overview of the Analysis

Credit risk poses a classification problem that's inherently imbalanced. This is because healthy loans easily outnumber risky loans. In this project, I used various techniques to train and evaluate models with imbalanced classes. I used a dataset of historical lending activity from a peer-to-peer lending services company to build a model that can identify the creditworthiness of borrowers.

To start off, I read in a CSV file containing historical lending data to a DataFrame, then chose to focus on the data specifically pertaining to loan status (whether the loan was healthy or at high risk of defaulting) as a target variable for my predictions. Then, I split up the data into training and testing datasets and used the training datasets to fit a logistic regression model. The predicitons made by this model were saved to the testing data labels to create a new dataset. I then evelauated the model's performance by calculating the accuracy score, generating a confusion matrix, and printing a classification report. 

Based on the performance of this model, which reflected a small number of high-risk loan labels, there was reason to speculate whether a model that used resampled data would perform better. Thus, I resampled the training data and reevaluated the model. More specifically, I used the RandomOverSampler module from the imbalanced-learn library to resample the data, and used the LogisticRegression classifier and the resampled data to fit the model and make predicitions. I reevaluated the model's performance by, once again, calculating the accuracy score, generating a confusion matrix, and printing the clssification report. 

## Results

* Machine Learning Model 1:
  * The logistic regression model predicted the healthy loans (represented by O's in the loan status data column) nearly perfectly, which was indicated by the precision, recall and f1 values in the evaluation report being a perfect "1.00" or close enough to 1.00 for us to consider it perfect. The model also performed well in predicting the high-risk loans (represented by the 1's in the loan status data column), with an f1 score of 0.88, though not as well as it did for predicting the healthy loans.

* Machine Learning Model 2:
  * The logistic regression model fit with oversampled data predicted both the healthy loan ('0') and the high-risk loan ('1') almost perfectly: healthy loans were predicted with an f1 score of 1.00 (the same as before) and the high-risk loans were predicted with an f1 score of 0.91 (up from 0.88), healthy loans were predicted with a precision of 1.00 (the same as before) and high-risk with a precision of 0.84 (down from 0.85), and both had a recall score of 0.99 (the same as before for healthy loans and up from 0.91 for high-risk loans).
