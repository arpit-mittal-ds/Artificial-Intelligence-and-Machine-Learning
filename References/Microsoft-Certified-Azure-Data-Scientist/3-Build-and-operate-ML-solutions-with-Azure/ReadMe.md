# Notes [Build and operate ML solutions with Azure](https://docs.microsoft.com/en-us/learn/paths/build-ai-solutions-with-azure-ml-service/)

## [AZURE ML EXERCISES](https://microsoftlearning.github.io/mslearn-dp100/)

# INTRODUCTION TO AZURE ML 

Azure ML is a platform for operating machine learning workloads in the **cloud**.

## WORKSPACES

![image](https://user-images.githubusercontent.com/68102477/123052923-b25a6580-d446-11eb-9867-13698270b56b.png)

**The Azure resources created alongside a workspace include:**

A storage account - used to store files used by the workspace as well as data for experiments and model training.

An Application Insights instance, used to monitor predictive services in the workspace.

An Azure Key Vault instance, used to manage secrets such as authentication keys and credentials used by the workspace.

A container registry, created as-needed to manage containers for deployed models.

[Azure Machine Learning Exercises](https://microsoftlearning.github.io/mslearn-dp100/)

## AZURE ML TOOLS AND INTERFACES tools and interfaces

### 1. Azure [ML Studio](https://ml.azure.com/)

Azure ML studio is a web-based tool for managing an Azure ML Workspacce. 

It enables you to create, manage, and view all of the assets in your workspace and provides the following **graphical tools**:

**Designer:**  A drag and drop interface for "no code" machine learning model development.

**Auto ML:** A wizard interface that enables you to train a model using a combination of algorithms and data preprocessing techniques to find the best model for your data.

### 2. The Azure Machine Learning SDK

While **graphical interfaces like Azure ML studio** make it easy to create and manage machine learning assets, it is often advantageous to use a **code-based approach** to managing resources. 

**By writing scripts to create and manage resources, we can:**

Run ML Operations from our preferred development environment.

Automate asset creation and configuration to make it repeatable.

Ensure consistency for resources that must be replicated in multiple environments (for example, development, test, and production)

Incorporate machine learning asset configuration into developer operations (DevOps) workflows, such as continuous integration / continuous deployment (CI/CD) pipelines.


### 3. Compute Instance

Azure Machine Learning includes the ability to create Compute Instances in a workspace to provide a development environment that is managed with all of the other assets in the workspace.

# TRAIN AN ML MODEL

Use a ScriptRunConfig to run a model training script as an Azure Machine Learning experiment.

Create reusable, parameterized training scripts.

Register trained models.

**Prerequisites**

Experience of training machine learning models using Python frameworks such as scikit-learn

## 1. Run a training script

We can use a **ScriptRunConfig** to run a script-based experiment that trains a machine learning model.

### Writing a script to train a model

When using an experiment to train a model, your script should save the trained model in the outputs folder. For example, the following script trains a model using Scikit-Learn, and saves it in the outputs folder using the joblib package:


from azureml.core import Run
import pandas as pd
import numpy as np
import joblib
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression

**Get the experiment run context**

run = Run.get_context()

**Prepare the dataset**

diabetes = pd.read_csv('data.csv')
X, y = diabetes[['Feature1','Feature2','Feature3']].values, diabetes['Label'].values
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.30)

**Train a logistic regression model**
reg = 0.1
model = LogisticRegression(C=1/reg, solver="liblinear").fit(X_train, y_train)

**calculate accuracy**

y_hat = model.predict(X_test)
acc = np.average(y_hat == y_test)
run.log('Accuracy', np.float(acc))

**Save the trained model**

os.makedirs('outputs', exist_ok=True)
joblib.dump(value=model, filename='outputs/model.pkl')

run.complete()

To prepare for an experiment that trains a model, a script like this is created and saved in a folder. For example, you could save this script as training_script.py in a folder named training_folder. Since the script includes code to load training data from data.csv, this file should also be saved in the folder.

### Running the script as an experiment

To run the script, create a ScriptRunConfig that references the folder and script file. You generally also need to define a Python (Conda) environment that includes any packages required by the script. In this example, the script uses Scikit-Learn so you must create an environment that includes that. The script also uses Azure Machine Learning to log metrics, so you need to remember to include the azureml-defaults package in the environment.

from azureml.core import Experiment, ScriptRunConfig, Environment
from azureml.core.conda_dependencies import CondaDependencies

**Create a Python environment for the experiment**

sklearn_env = Environment("sklearn-env")

**Ensure the required packages are installed**

packages = CondaDependencies.create(conda_packages=['scikit-learn','pip'],
                                    pip_packages=['azureml-defaults'])
sklearn_env.python.conda_dependencies = packages

**Create a script config**

script_config = ScriptRunConfig(source_directory='training_folder',
                                script='training.py',
                                environment=sklearn_env) 

**Submit the experiment**

experiment = Experiment(workspace=ws, name='training-experiment')
run = experiment.submit(config=script_config)
run.wait_for_completion()

### Using script parameters

### Passing arguments to an experiment script

# WORKING WITH DATA

Data is a fundamental element in any machine learning workload.

In this module,  will learn how to create and manage datastores and datasets in an Azure Machine Learning workspace,

and how to use them in model training experiments.

Types of Datastore
Azure Machine Learning supports the creation of datastores for multiple kinds of Azure data source, including:

Azure Storage (blob and file containers)
Azure Data Lake stores
Azure SQL Database
Azure Databricks file system (DBFS)







