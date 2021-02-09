# Optimizing an ML Pipeline in Azure

## 1. Overview

This project is the first in the Udacity Azure ML Nanodegree program. In this project, students must build and optimize an Azure ML pipeline using the Python SDK and the Scikit-learn package. After these steps, the model is compared to an Azure AutoML run. The picture depicted below shows the approach followed in this project.

![Diagram of the project](https://github.com/michelmf/azure-ml/blob/main/Optimizing%20an%20ML%20Pipeline%20in%20Azure/diagram.PNG)

There are 4 files in this repository related to the experiments:

* train.py : Script that contains the preprocessing steps of the dataset and triggers the training of a logistic regression model through CLI
* experiment-notebook.ipynb: Jupyter notebook used to create both models, containing all the steps of this project
* best-hyperdrive-model.joblib: Best L2-regularization logistic regression  
* best-automl-model.joblib: Best model obtained by the AutoML tool (for instance, it was an XGBoost Classifier)

## 2. Summary

The dataset [Bank Marketing Data Set](https://archive.ics.uci.edu/ml/datasets/bank+marketing) is related to direct marketing campaigns (phone calls) of a Portuguese banking institution. The classification goal is to predict if the client will subscribe to a term deposit. The dataset has 21 features (numerical and categorical), it has 32950 examples, and the classes are high imbalanced (~89% not subcribed clients vs ~11% subscribed clients). For more information, check the link to the UCI repository. 

In this project, no exploratory analyses are done, as the focus is on the utilization of the azure ml studio tools and modules. Moreover, no balancing techniques are explored.

## 3. Scikit-learn Pipeline


**Explain the pipeline architecture, including data, hyperparameter tuning, and classification algorithm.**

**What are the benefits of the parameter sampler you chose?**

**What are the benefits of the early stopping policy you chose?**

## 4. AutoML

The AutoML tool helps data scientists to automate the creation of many different algorithms in a few steps, speeding up the search of better models to fit data. Here, 45 different models were tested on different combinations of features selection methods and machine learning algorithms. One interesting AutoML feature is the automatic run of *Data guardrails*, which helps on the identification of potential issues with data, such as imbalanced classes, High cardinality feature handling, and [more](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-configure-auto-features).

In order to obtain the best result, a 5-fold cross-validation was performed, and the winning model was the Voting Ensemble with Sparse Normalizer feature selection (the ensemble is a XGBoost algorithm).

## 5. Pipeline comparison

By the results of each model, we have:

* Logistic Regression with L2-Regularization - 
* VotingEnsemble - 

By the performances of each model on the test set, it is clear that there is no real or practical difference between both models if they were used in real life. Having said that, we can state that the logistic regression model is a better choice over the xgboost, as it is simpler, more interpretable, faster to train, and faster to predict.

## 6. Future work

AutoML is here to help data scientists to be more productive. However, it should be used with parsimony. The use of AutoML does not guarantee a higher performance when compared to single models, such as a simple logistic regression. In this project, it is clear that sophisticated models (or ensemble of models) do not perform better than simpler ones, and in these cases, we should consider a business-centered approach, such as:

* better feature engineering of the variables
* Try different categorization of data
* Group variables, according to the business experience

Besides that, there are some aspects we can improve, like:

* exploration of class balancing techniques (oversampling of the minority class, subsampling of majority class, synthesis of new data, etc.)
* Different categorical encodings
* Utilization of appropriate metrics if the classes are imbalanced
