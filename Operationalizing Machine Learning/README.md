# Operationalizing Machine Learning

## 1. Overview

After finishing the training of a mchine learning model, now it is time to put it into production! In this second project of the azure machine learning nanodegree, we must 
use Azure to configure a cloud-based machine learning production model, deploy it, and consume it using an AutoML model. Also, we will create, publish, and consume a pipeline. 

## 2. Summary

In this project, we have to deal with the following steps:

* Authentication
* Automated ML Experiment
* Deployment of the best model
* Application Logging
* Swagger Documentation
* Consume model endpoints
* Create and publish a pipeline

These steps will be described in the following sections.

## 3. Architectural Diagram

![Flow of the project](https://github.com/michelmf/azure-ml/blob/main/Operationalizing%20Machine%20Learning/overview.png)

## 4. Key Steps

### 4.1 Authentication and Authorization

Before deploying any artifact to production, we must take care of the security of our systems. Unauthorized access to a production model could . Another important aspect of Authentication is the CI/CD flow, as Continuous Integration and Continuous Delivery (CI/CD) relies on automated tasks, human intervention is needed when these steps are not configured properly. In Azure, we can use a Service Principal to help us in both scenarios. A Service Principal is a user role with controlled permissions to access specific resources. Using a service principal is a great way to allow authentication while reducing the scope of permissions, which enhances security.

Below, the steps needed to properly configure the authentication/authorization step to access the Azure ML Studio environment:

* Install *az* and enable it in the terminal
* *az login* has succeeded
* Install the Azure Machine Learning Extension
* Create the Service Principal and allow it access the machine learning studio workspace

After that, some actions were taken as proof of the steps above:

* Take a screenshot showing that a "Service Principal" has been created
* *az ml workspace share* completed without errors
* Take a screenshot showing that the az ml workspace share command has been run successfully, with no errors or tracebacks

Screenshots of the CLI:

![Create the service principal (sp) and allow the access to your specific workspace](https://github.com/michelmf/azure-ml/blob/main/Operationalizing%20Machine%20Learning/sp.PNG)

![Take a screeshot showing that the *az ml workspace share* command has been run successfully, with no errors or tracebacks](https://github.com/michelmf/azure-ml/blob/main/Operationalizing%20Machine%20Learning/role.PNG)

### 4.2 Automated ML

After configuring the Authorization to the ML environment, we use the Azure AutoML to train a model using the same dataset as the [first project](https://github.com/michelmf/azure-ml/tree/main/Optimizing%20an%20ML%20Pipeline%20in%20Azure). These steps were done:

* Upload the Bankmarketing dataset
* Create a new Automated ML run
* Create a new Automated ML experiment
* Run the experiment and get the best model

As a proof of completion, the screenshots below show that the tasks were done successfully.

![Select and upload the bankmarketing dataset](https://github.com/michelmf/azure-ml/blob/main/Operationalizing%20Machine%20Learning/figures/dataset_image.png)

![Take a screenshot showing that the experiment is shown as completed](https://github.com/michelmf/azure-ml/blob/main/Operationalizing%20Machine%20Learning/figures/experiment.png)

![Take a screenshot of the experiment's settings](https://github.com/michelmf/azure-ml/blob/main/Operationalizing%20Machine%20Learning/figures/settings.png)

![Take a screenshot of the best model after the experiment completes](https://github.com/michelmf/azure-ml/blob/main/Operationalizing%20Machine%20Learning/figures/model.png)

Screen Recording
TODO Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

Standout Suggestions
TODO (Optional): This is where you can provide information about any standout suggestions that you have attempted.
