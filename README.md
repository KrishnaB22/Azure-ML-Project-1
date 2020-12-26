# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Summary
The provided dataset is a Bank Marketing dataset. We have to predict whether a client subscribed a term deposit or not. <br>
We were provided with a custom coded model-a sci-kit learn Logistic Regression.<br>
At first, the hyperparameters are tuned using the tool Hyperdrive. We save the best model obtained through this.<br>
Next, using Automated Machine Learning(AutoML) an optimal model is determined. We then compare both the results and find out which method gives better results.<br> 
The best model was AutoML which gave an accuracy of 91.5%.

## Scikit-learn Pipeline
The train.py file is used as script. Then the Bank Marketing dataset is loaded using the URL provided. 
The dataset is split into train(90%) and test(10%) data. 
After that, the Logistic Regression Model was used for training the dataset based on hyperparameters such as 'Inverse of Regularization Strength' and 'Maximum number of iterations to converge'.<br>

The early stopping policy used is Bandit Policy<br>
Bandit Policy is based on slack factor/slack amount and evaluation interval.<br>
This policy will terminate runs whose primary metric is not within the specified slac factor/slack amount.<br>
By using this policy we could improve the computational efficiency.<br>
