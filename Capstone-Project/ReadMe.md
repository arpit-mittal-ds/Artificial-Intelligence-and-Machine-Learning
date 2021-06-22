
 create two models: one using Automated ML (denoted as AutoML from now on) and one customized model whose hyperparameters are tuned using HyperDrive. You will then compare the performance of both the models and deploy the best performing model.

This project will demonstrate your ability to use an external dataset in your workspace, train a model using the different tools available in the AzureML framework as well as your ability to deploy the model as a web service.

How it works
You will be using both the hyperdrive and automl API from azureml to build this project. You can choose the model you want to train, and the data you want to use. However, the data you use needs to be external and not available in the Azure's ecosystem. For instance, you can use the Heart Failure Prediction dataset from Kaggle to build a classification model.

Project Workflow
To complete this project, you will have to perform these overall tasks, in the order given below:

![image](https://user-images.githubusercontent.com/68102477/122845741-b0f64380-d347-11eb-9f41-e71d302d5112.png)


After you have deployed the model and tested the web service, you will need to submit a README file with details about the data, the model, its performance, and how you deployed it.

### Useful Links

[Automated ML Overview](https://docs.microsoft.com/en-us/azure/machine-learning/concept-automated-ml?view=azure-ml-py)
[HyperDrive Overview](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-tune-hyperparameters?view=azure-ml-py)
[Deploy and Consume your model](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-consume-web-service?view=azure-ml-py#call-the-service-python)
[Hyperparameter tuning for ML models example](https://github.com/microsoft/MLHyperparameterTuning)

## Step 1: Project Setup
By the end of this task, you should have your workspace set up and your data accessible in your workspace.

https://github.com/udacity/nd00333-capstone/tree/master/starter_file

