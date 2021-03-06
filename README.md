# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.<br>

## Summary
The provided dataset is a Bank Marketing dataset. We have to predict whether a client subscribed a term deposit or not. <br>
We were provided with a custom coded model-a sci-kit learn Logistic Regression.<br>
At first, the hyperparameters are tuned using the tool Hyperdrive. We save the best model obtained through this.<br>
Next, using Automated Machine Learning(AutoML) an optimal model is determined. We then compare both the results and find out which method gives better results.<br> 
The best model was AutoML which gave an accuracy of 91.5%.<br><br>
<img src ='screenshots/block_diagram.png'><br><br>

## Scikit-learn Pipeline
The train.py file is used as script. Then the Bank Marketing dataset is loaded using the URL provided.<br>
The dataset is split into train(90%) and test(10%) data.<br>
After that, the Logistic Regression Model was used for training the dataset based on hyperparameters such as 'Inverse of Regularization Strength' and 'Maximum number of iterations to converge'.<br>
<br>
The sampling method used is RandomSampling. It supports both discrete and continuous values. It supports early termination of low-performance runs. In Random Sampling, the values are selected randomly from a defined search space.<br>
<br>
The early stopping policy used is Bandit Policy<br>
Bandit Policy is based on slack factor/slack amount and evaluation interval.<br>
This policy will terminate runs whose primary metric is not within the specified slac factor/slack amount.<br>
By using this policy we could improve the computational efficiency.<br>
The best model obtained is saved.<br>
<br>
The acccuracy obtained in hyperdrive model is 91.1%.<br>
<br>

<img src ='screenshots/hyperdrive accuracy.png'><br><br>

## Auto-ML

Automated Machine Learning, often referred to as AutoML is the process of automating the entire Machine Learning pipeline.<br>
The AutoMLConfig class is used specify paramters such as <i>experiment_timeout_minutes, task,primary_metric, training_data, label_column_name, n_cross_validations</i>.<br>
Automated machine learning supports ensemble models, which are enabled by default. Ensemble learning improves machine learning results and predictive performance by combining multiple models as opposed to using single models.<br>
The best model obtained through AutoML is VotingEnsemble. Voting Ensemble predicts based on the weighted average of predicted class probabilities (for classification tasks) or predicted regression targets (for regression tasks).<br>
The value of AUC weighted was 0.94779, recall_score_macro was 0.7689, precision_score_macro was 0.797713. The value of hyperparamaters for VotingEnsemble were max_iter = 1000, n_jobs =1, power_t = 0.222222, tol=0.0001.<br>
It had an accuracy of 91.5%.<br><br>

Classification report<br><br>
<img src ='screenshots/automl classification.png'><br><br>

## Pipeline Comparison
The accuracy obatined through hyperdrive run is 91.1%. Whereas, the accuracy obtained through AutoML 91.5%.<br>
In hyperdrive, we chose a model, here in this case Logistic Regression. We were only able to tune the hyperparameters with different values.<br>
Whereas, in case of AutoML, different models were used. As of result of this, we were able to choose the best performing model instead of sticking to just one type.<br><br>

## Future work
Deprecate SKLearn estimator type function in the favour of ScriptRunConfig.<br>
We could improve the Parameter sampler, so that more values of hyperparameters could be included.<br>
We could try using other Early Termination policy, or optimize the current one to get better results.<br><br>

## Proof of Cluster Cleanup

<img src ='screenshots/cluster cleanup.png'><br><br>
