# Project Overview

In this project, you will continue to work with the [Bank Marketing dataset](https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/bankmarketing_train.csv). 

You will use Azure to configure a cloud-based machine learning production model, deploy it, and consume it. You will also create, publish, and consume a pipeline. 

In the end, you will demonstrate all of your work by creating a README file and a screencast video.

## Project main steps

Authentication

Automated ML Experiment

Deploy the best model

Enable logging

Swagger Documentation

Consume model endpoints

Create and publish a pipeline

Documentation

![image](https://user-images.githubusercontent.com/68102477/123021493-8a9fd900-d417-11eb-8834-101b2e1f0266.png)

## Project submissions
At the end of the project, you will submit a README file that describes the main components of the project and a screencast that shows the entire process of the working ML application.


## Project Setup


### Step 1: Authentication
NOTE: If you are using your own Azure account, please complete this step. If you are using the lab Udacity provided to you, you can skip this step since you are not authorized to create a security principal. You will NOT be graded on this item and skipping this step will NOT affect other steps in the project.

In this step, you will need to install the Azure Machine Learning Extension which allows you to interact with Azure Machine Learning Studio, part of the az command. After having the Azure machine Learning Extension, you will create a Service Principal account and associate it with your specific workspace. You will also be instructed to take screenshots to document your work.

![image](https://user-images.githubusercontent.com/68102477/123021667-d9e60980-d417-11eb-8a58-d01dd794f7e3.png)


### Step 2: Automated ML Experiment

At this point, security is enabled and authentication is completed. In this step, you will create an experiment using Automated ML, configure a compute cluster, and use that cluster to run the experiment.

Note: Be careful with your configuration if you use the lab provided to you. Your experiment will timeout after a certain amount of time! All your work saved locally in the lab will be lost once it times out. Always SAVE your work in Github!!!

You will use the same Bankmarketing dataset with course 1.

Copy the link to a new browser window to download the data:
https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/bankmarketing_train.csv

Upload the bankmarketing_train.csv to Azure Machine Learning Studio so that it can be used when training the model.

Create and run Auto ML Experiment
Please complete the following:

Note: the goal of these steps is not to create a great model but to provide you a model so you can deploy it and consume it. So don't be too harsh on yourself in creating a highly accurate model.

![image](https://user-images.githubusercontent.com/68102477/123021986-6690c780-d418-11eb-91bb-19851be7bbcd.png)

### Step 3: Deploy the Best Model

After the experiment run completes, a summary of all the models and their metrics are shown, including explanations. The Best Model will be shown in the Details tab. In the Models tab, it will come up first (at the top). Make sure you select the best model for deployment.

Deploying the Best Model will allow to interact with the HTTP API service and interact with the model by sending data over POST requests.

### Step 4: Enable Application Insights
Now that the Best Model is deployed, enable Application Insights and retrieve logs. Although this is configurable at deploy time with a check-box, it is useful to be able to run code that will enable it for you.

### Step 5: Swagger Documentation
In this step, you will consume the deployed model using Swagger.

Azure provides a Swagger JSON file for deployed models. Head to the Endpoints section, and find your deployed model there, it should be the first one on the list.

A few things you need to pay attention to:

swagger.sh will download the latest Swagger container, and it will run it on port 80. If you don't have permissions for port 80 on your computer, update the script to a higher number (above 9000 is a good idea).

serve.py will start a Python server on port 8000. This script needs to be right next to the downloaded swagger.json file. NOTE: this will not work if swagger.json is not on the same directory.

### Step 6: Consume Model Endpoints
Once the model is deployed, use the endpoint.py script provided to interact with the trained model. In this step, you need to run the script, modifying both the scoring_uri and the key to match the key for your service and the URI that was generated after deployment.

Hint: This URI can be found in the Details tab, above the Swagger URI.

### Step 7: Create, Publish and Consume a Pipeline
For this part of the project, you will use the Jupyter Notebook provided in the starter files. You must make sure to update the notebook to have the same keys, URI, dataset, cluster, and model names already created. The notebook has several notes that look similar to this:

NOTE: update these to match your existing experiment name
experiment_name = 'ml-experiment-1'
This is an indication to make updates or change the code on your own.

### Step 8: Documentation
Screencast
In this project, you need to record a screencast that shows the entire process of the working ML application. The screencast should meet the following criteria:





