# Optimizing an ML Pipeline in Azure

## Overview

This project is the first in the Udacity Azure ML Nanodegree program. In this project, students must build and optimize an Azure ML pipeline using the Python SDK and the Scikit-learn package. After these steps, the model is compared to an Azure AutoML run. The picture depicted below shows the approach followed in this project.

![Diagram of the project](https://github.com/michelmf/azure-ml/blob/main/Optimizing%20an%20ML%20Pipeline%20in%20Azure/diagram.PNG)

There are 4 files in this repository related to the experiments:

* train.py : Script that contains the preprocessing steps of the dataset and triggers the training of a logistic regression model through CLI
* experiment-notebook.ipynb: Jupyter notebook used to create both models, containing all the steps of this project
* best-hyperdrive-model.joblib: Best L2-regularization logistic regression  
* best-automl-model.joblib: Best model obtained by the AutoML tool (for instance, it was an XGBoost Classifier)

## Summary

The dataset [Bank Marketing Data Set](https://archive.ics.uci.edu/ml/datasets/bank+marketing) is related to direct marketing campaigns (phone calls) of a Portuguese banking institution. The classification goal is to predict if the client will subscribe to a term deposit. The dataset has 21 features (numerical and categorical), and it has 32950 examples. For more information, check the link to the UCI repository.

In this project, no exploratory analyses are done, as the focus is on the utilization of the azure ml studio tools and modules.

## Scikit-learn Pipeline
**Explain the pipeline architecture, including data, hyperparameter tuning, and classification algorithm.**

**What are the benefits of the parameter sampler you chose?**

**What are the benefits of the early stopping policy you chose?**

## AutoML
The AutoML tool helps data scientists 

## Pipeline comparison
**Compare the two models and their performance. What are the differences in accuracy? In architecture? If there was a difference, why do you think there was one?**

## Future work
**What are some areas of improvement for future experiments? Why might these improvements help the model?**

## Proof of cluster clean up
**If you did not delete your compute cluster in the code, please complete this section. Otherwise, delete this section.**
**Image of cluster marked for deletion**
