
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

## Step 2: Model Training and Deployment

**Train a model using Automated ML**

The automl.ipynb file contains a starter code to help you train a model using Automated ML. The file contains some TODOs that you need to finish.

**Train a model with HyperDrive**

The hyperparameter_tuning.ipynb file contains some starter codes to help you train a model and perform hyperparameter tuning using HyperDrive.

The type of model you use is not important. You can use ML models through Scikit-learn or Deep Learning models like ANNs and CNNs through Keras, TensorFlow, or PyTorch for this part of the project.

**Model Deployment**

After you have trained your models. You will have to deploy your best model as a webservice and test the model endpoint

## Step 3: Complete the README

## Step 4: Standout suggestions

If you've been having a good time with this project and want to take it further, here are some suggestions for a whole bunch of additional things you can do with it. If you want the additional practice or want to turn this project into a nice portfolio piece, we recommend taking a shot at these

![image](https://user-images.githubusercontent.com/68102477/123070525-30bf0380-d457-11eb-97c1-69497758bdad.png)

## Step 5: Create a [Screencast](https://en.wikipedia.org/wiki/Screencast)

In this project, you need to record a screencast that shows the entire process of the working ML application. The screencast should meet the following criteria:

![image](https://user-images.githubusercontent.com/68102477/123070704-53511c80-d457-11eb-9638-09799cff9b22.png)

![image](https://user-images.githubusercontent.com/68102477/123070847-7976bc80-d457-11eb-9292-3d7dd2273266.png)






