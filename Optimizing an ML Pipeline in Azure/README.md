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

The dataset [Bank Marketing Data Set](https://archive.ics.uci.edu/ml/datasets/bank+marketing) is related to direct marketing campaigns (phone calls) of a Portuguese banking institution. The classification goal is to predict if the client will subscribe to a term deposit. The dataset has 21 features (numerical and categorical), it has 32950 examples, and the classes are highly imbalanced (~89% not subcribed clients vs ~11% subscribed clients). For more information, check the link to the UCI repository. 

In this project, no exploratory analyses are done, as the focus is on the utilization of the azure ml studio tools and modules. Moreover, no class balancing techniques are explored.

## 3. Scikit-learn Pipeline

### 3.1 Data preparation

The first model is created using the Scikit-Learn module. The following steps are performed in order to get data ready to be used by the model:

1. The dataset is downloaded from the source, and then, stored in azure as a Tabular Dataset

2. After that, a function called *clean_data* is called from the *train.py* script. This functions preprocess data and returns two dataframes, one with the features and the other with the labels associated to each example. The preprocessing step is described later

3. The next step in pipeline is the split of examples into disjoint sets: the training set, and test set.

4. The logistic regression model is trained using the Scikit-Learn implementation of the algorithm on the training set

5. Here, the hyperdrive come in: it is used to search for the best combination of hyperparameters. In the case of this project, the number of maximum iterations of the algorithm, and the regularization strength (--C and --max_iter)

6. The accuracy is checked on the teste set

### 3.2 Hyperdrive and hyperparameter tuning

The hyperdrive package helps us in the hyperparameter tuning task, which leads to the best performance of our model, given the training set. Finding the best combination of these hyperparameters is a consuming task, considering a list of possible combinations of each variable (in our case with only two hyperparameters, a list of *M* C inverse regularization factors and *N* max_iter iterations of the algorithm would lead to *MxN* runs). Not selecting all combinations would decrease the experiments's time, and still lead us to good results. In this case, a *random selection* of parameters would help us to get some results in less time.

Moreover, hyperdrive monitors the runs and their results, using predefined policies that can interrupt an experiment if the criteria is not met. It is useful when a combination of parameters is chosen, however the performance of the model using them is unacceptable and far from the best results so far.

Thus, the following choices regarding hyperdrive were taken:

* Parameter Sampling - Random Parameter sampling, as we can select both continuous and discrete values from a list
* BanditPolicy - Early termination based on some criteria, it stops the run if the performance is far below from the best run

## 4. AutoML

The AutoML tool helps data scientists automate the creation of many different algorithms in a few steps, speeding up the search of better models to fit data. Here, 45 different models were tested on different combinations of features selection methods and machine learning algorithms. One interesting AutoML feature is the automatic run of *Data guardrails*, which helps on the identification of potential issues with data, such as imbalanced classes, High cardinality feature handling, and [more](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-configure-auto-features).

In order to obtain the best result, a 5-fold cross-validation was performed, and the winning model was the Voting Ensemble with Sparse Normalizer feature selection (the ensemble is a XGBoost algorithm).

## 5. Pipeline comparison

By the results of each model, we have:

* Logistic Regression with L2-Regularization - 0.9163
* VotingEnsemble - 0.9212

Given the performances of each model on the test set (~0,0049), it is clear that there is no real or practical difference between both models if they were used in production. Taking these facts into account, we can state that the logistic regression model is a better choice over the xgboost, as it is simpler, more interpretable, faster to train, and faster to predict.

## 6. Future work

AutoML helps data scientists to be more productive. However, it should be used carefully. The use of AutoML does not guarantee a higher performance when compared to single models, such as a simple logistic regression. In this project, it is clear that sophisticated models (or ensemble of models) do not perform better than simpler ones, and in these cases, we should consider a business-centered approach, such as:

* better feature engineering of the variables
* Try different categorization of data
* Group variables, according to the business experience

Besides that, there are some aspects we can improve, like:

* exploration of class balancing techniques (oversampling of the minority class, subsampling of majority class, synthesis of new data, etc.)
* Different categorical encodings
* Utilization of appropriate metrics if the classes are imbalanced
* Increase the range of values for hyperparameter search in logistic regression
* Explore different metrics
