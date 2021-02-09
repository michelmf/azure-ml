https://www.drivendata.org/competitions/44/dengai-predicting-disease-spread/page/82/

Problem description
Your goal is to predict the total_cases label for each (city, year, weekofyear) in the test set. There are two cities, San Juan and Iquitos, with test data for each city spanning 5 and 3 years respectively. You will make one submission that contains predictions for both cities. The data for each city have been concatenated along with a city column indicating the source: sj for San Juan and iq for Iquitos. The test set is a pure future hold-out, meaning the test data are sequential and non-overlapping with any of the training data. Throughout, missing values have been filled as NaNs.

Project Overview
This project gives you the opportunity to use the knowledge you have obtained from this Nanodegree to solve an interesting problem. In this project, you will create two models: one using Automated ML (denoted as AutoML from now on) and one customized model whose hyperparameters are tuned using HyperDrive. You will then compare the performance of both the models and deploy the best performing model.

This project will demonstrate your ability to use an external dataset in your workspace, train a model using the different tools available in the AzureML framework as well as your ability to deploy the model as a web service.

How it works
You will be using both the hyperdrive and automl API from azureml to build this project. You can choose the model you want to train, and the data you want to use. However, the data you use needs to be external and not available in the Azure's ecosystem. For instance, you can use the Heart Failure Prediction dataset from Kaggle to build a classification model.

Project Workflow
To complete this project, you will have to perform these overall tasks, in the order given below:


We will go over these tasks in more detail in the later pages. After you have deployed the model and tested the web service, you will need to submit a README file with details about the data, the model, its performance, and how you deployed it. Finally, make sure that you check the project rubrics to make sure that your project has all the requirements the reviewer will be looking for in your submission.


