# Operationalizing Machine Learning

## 1. Overview

After finishing the training of a mchine learning model, now it is time to put it into production! In this second project of the azure machine learning nanodegree, we must 
use Azure to configure a cloud-based machine learning production model, deploy it, and consume it using an AutoML model trained using the same procedure in the [first project](https://github.com/michelmf/azure-ml/tree/main/Optimizing%20an%20ML%20Pipeline%20in%20Azure). Also, we will create, publish, and consume a pipeline. 

## 2. Summary

In this project, we have to deal with the following steps:

* Authentication

* Automated ML Experiment

* Deploy the best model

* Enable logging

* Swagger Documentation

* Consume model endpoints

* Create and publish a pipeline

## 2. Architectural Diagram
TODO: Provide an architectual diagram of the project and give an introduction of each step. An architectural diagram is an image that helps visualize the flow of operations from start to finish. In this case, it has to be related to the completed project, with its various stages that are critical to the overall flow. For example, one stage for managing models could be "using Automated ML to determine the best model".

## 3. Key Steps

### 3.1 Authorization

* Install *az* and enable it in the terminal
* *az login* has succeeded
* Install the Azure Machine Learning Extension
* Create the Service Principal and allow it access the machine learning studio workspace
* Take a screenshot showing that a *"Service Principal"* has been created
* *az ml workspace share* completed without errors
* Tae a screenshot showing that the az ml workspace share command has been run successfully, with no errors or tracebacks

Print Screens from the process:

![Create the service principal (sp) and allow the access to your specific workspace](https://github.com/michelmf/azure-ml/blob/main/Operationalizing%20Machine%20Learning/sp.PNG)

![Take a screeshot showing that the *az ml workspace share* command has been run successfully, with no errors or tracebacks](https://github.com/michelmf/azure-ml/blob/main/Operationalizing%20Machine%20Learning/role.PNG)

### 3.2 Automated ML

* Create a new Automated ML run
* Upload the Bankmarketing dataset
* Create a new Automated ML experiment
* Run the experiment and get the best model


![Select and upload the bankmarketing dataset](https://github.com/michelmf/azure-ml/blob/main/Operationalizing%20Machine%20Learning/dataset.PNG)

![Take a screenshot showing that the experiment is shown as completed](https://github.com/michelmf/azure-ml/blob/main/Operationalizing%20Machine%20Learning/sp.PNG)

![Take a screenshot of the best model after the experiment completes](https://github.com/michelmf/azure-ml/blob/main/Operationalizing%20Machine%20Learning/sp.PNG)

Screen Recording
TODO Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

Standout Suggestions
TODO (Optional): This is where you can provide information about any standout suggestions that you have attempted.
