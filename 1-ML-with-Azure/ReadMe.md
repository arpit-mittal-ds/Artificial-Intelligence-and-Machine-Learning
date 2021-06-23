# Notes

![image](https://user-images.githubusercontent.com/68102477/119915814-a776f700-bfa6-11eb-8d1c-7e3abd6e330b.png)

# LESSON 1 INTRO TO AZURE ML

[Microsoft Documentation: What is automated machine learning?](https://docs.microsoft.com/en-us/azure/machine-learning/concept-automated-ml)

[Auto ML](https://docs.microsoft.com/en-us/learn/modules/use-automated-machine-learning/)

### Why Do Machine Learning in the Cloud?

Although you can certainly do machine learning locally on your own machine, but this will involve limitations imposed by your machine's resources. In contrast, the cloud provides a variety of platform tools that are constantly being developed and improved by some of the best engineers in the world. In the Azure cloud, these include:

Data lakes, which provide essentially infinite storage that is also very secure.

Machine Learning Studio, which makes it easy to build a full, end-to-end ML solution, leveraging great ready-made resources like open datasets.

DevOps build systems, allowing you to integrate DevOps pipelines with your machine learning workflows.

Serverless technology, in which Azure runs the server and handles the provisioning of machine resources for you automatically, allowing you to more easily solve complex orchestration problems.

[What is elastic computing or cloud elasticity?](https://azure.microsoft.com/en-us/overview/what-is-elastic-computing/)

### When and When not to do ML in the Cloud

Most of the time the cloud is your best option for ML. Some reasons to favor cloud computing include:

Data governance. Cloud solutions offer additional security to help prevent problems like data breaches and piracy.

Better ability to leverage new services. A cloud-native approach allows you to leverage new services as they're developed. You're betting on the future, knowing that the cloud platform will get a constant set of new features (in contrast to you needing to build those features yourself).

**Even so, there are a few edge cases in which using the cloud may not be the best route. These include:**

Legal/government requirements. If your company handles sensitive data, such as medical records or government files, it may not be legally possible to move to the cloud.

Legacy applications. If you have a legacy application that is currently working, but that is unlikely to be updated, it may not make sense to take the risk of moving it to the cloud.

Specialized HPC. In some cases, you may already have a specialized and very expensive High Performance Computing (HPC) cluster. In such a case, it may be more cost effective to keep what you have and only use the cloud for some parts of your workflow.

### Additional Resources

[Microsoft Documentation: Comparison between Azure data storage and on-premises storage](https://docs.microsoft.com/en-us/learn/modules/intro-to-data-in-azure/4-comparison-azure-and-on-prem-storage)

## Customers of Machine Learning

Additional Resources
If you'd like to read more about bias and discrimination, you may want to check out:

The blog post, [Tackling Bias in Machine Learning](https://arxiv.org/pdf/1908.09635.pdf), by Suraj Acharya, which includes a description of several techniques that can be used to mitigate bias.

The paper, [A Survey on Bias and Fairness in Machine Learning](https://arxiv.org/pdf/1908.09635.pdf), which includes real-world examples of algorithmic discrimination, as well as an extensive list of different types of bias that can occur.

How can your company perform a [digital transformation?](https://docs.microsoft.com/en-us/learn/modules/enable-digital-transformation/2-what-is-digital-transformation)


# LESSON 2: WORKSPACES AND AZURE-ML STUDIO

The Azure ML Platform. We'll talk about the core features of the Microsoft Azure ML platform and how they enable you to be more productive as a data scientist or machine learning engineer.
Workspaces and Notebooks. Workspaces and notebooks are critical components of Microsoft Azure. We'll learn how these tools enable you to be a more effective data scientist—including the use of Jupyter to build and deploy machine learning models.

### The Azure ML platform is composed of two main components: The Azure Cloud and Azure ML Studio.

**Key features of Azure Cloud include:**

Scalable, on-demand compute instances.

Data storage and connectivity.

**Key features of Azure ML studio include:**

The ability to easily orchestrate machine learning workflows.

Model registration and management (or MLOps). This allows you to register models or track them and control the [lineage](https://en.wikipedia.org/wiki/Data_lineage).

Metrics and monitoring, giving you the ability to look at the compute, the storage, or a training job, and make sure that it's running effectively.

Model deployment; you can create an inference end point and deploy your model so that it runs 24/7 and is elastically scaled to meet demand.

[ Microsoft's official documentation on the Azure ML Plaftorm](https://docs.microsoft.com/en-us/azure/machine-learning/overview-what-is-azure-ml)

### Managing compute resources effectively involves several main components:

Compute instances
A central component of managing compute resources involves the ability to spin up a Virtual Machine (VM), provision the correct resources for that VM, and then launch a notebook—which you can then use to control other components of your project, such as by calling out to a compute cluster.

Compute clusters
A compute cluster is a specialized cluster of Virtual Machines used to train ML models at scale, adjusting elastically to the requirements. Compute clusters can also employ specialized GPU or CPU resources.

Inference clusters
Inference clusters, as the name suggests, are used to establish a production ML endpoint and serve out predictions. Like compute clusters, inference clusters are also groups of Virtual Machines—and like compute clusters, they too can scale up and down in response to demand, thus ensuring that your customers always have a good response time. Inference clusters can be configured to do monitoring and logging, and set up to ensure that the model is running 24/7.

Attached compute
Attached compute, or "unmanaged compute," allows you to do integration with third party services. Those third party services could be anything from your own VM to something like a data bricks cluster that does managed Spark. If you have experience with a tool from, say, a previous job, you can integrate that tool with Azure ML Studio and thus use that pre-existing skill in your pipeline.

Creating a compute instance and then spinning up a notebook is one of the most critical tasks in an Azure ML pipeline, because the notebook is used as an interface for conducting MLOps and controlling the pipeline. For example, the notebook is used to:

Conduct Exploratory Data Analysis (EDA)
Call out to a compute cluster to train models
Call out to an inference cluster to deploy an endpoint

[Explore Azure Machine Learning with Jupyter notebooks](https://docs.microsoft.com/en-us/azure/machine-learning/samples-notebooks)

When choosing the compute resources for your needs, some key factors to consider are GPU vs CPU, cluster size, VM size, and dedicated vs low-priority instances. Let's have a look at the factors involved in each of these choices.

CPU vs GPU
Characteristics of CPUs:

Less expensive
Lower level of concurrency (a CPU isn't designed for parallel computing)
Can be a lot slower in training deep learning models
If time really isn't a critical factor, it could be a good option to save
Characteristics of GPUs

More expensive
Higher level of concurrency (GPUs are designed for parallel computing)
Optimal for deep learning
Used in both inference and training; the power level for these may be different
Cluster Size
The primary consideration with cluster size is response time:

If you have a cluster that starts at zero nodes, that means it will have to spin up a node when it is needed for a task, which could lead to slower response times (but will save on costs).
A larger starting cluster size will result in better responsiveness, but will also be more expensive.
In sum, if you have more time, but less money, you may want to go with a smaller cluster size. Conversely, if you have less time and more money, you may want to go with a larger cluster size.

VM Size
The "size" of a VM can vary in terms of a number of features, including:

RAM
Disk size
Number of cores
Clock speed
Getting a VM with more RAM, larger disk size, a greater number of cores, and higher clock speed, will result in better performance, but will also be more expensive. The choice depends on the training and inference needs of the problem you're trying to solve, as well as your time and budgetary constraints.

Dedicated Instances vs Low-Priority Instances
When an instance is low-priority this means it is interruptible—essentially, Microsoft Azure can take those resources and assign them to another task, thus interrupting a job.
When an instance is dedicated, or non-interruptible, this means that the job will never be terminated without your permission.
This is another consideration of time vs money, since interruptible instances are less expensive than dedicated ones.

The Azure ML Platform. We talked about the core features of the Microsoft Azure ML platform and how they enable us to be more productive as data scientists or machine learning engineers—including how elastic resources give us the power to do ML at scale.
Managing and choosing compute resources. We explored the role of compute instances, compute clusters, inference clusters, and attached compute. We also explored the tradeoffs involved in choosing resources, such as GPU vs CPU, VM size, cluster size, and dedicated vs low-priority instances.
Workspaces and Notebooks. Workspaces and notebooks are critical components of Microsoft Azure. We learned how these tools enable you to be a more effective data scientist—including the use of Jupyter to build and deploy machine learning models.


# LESSON 3 DATASTORES AND DATASETS

Datastores and Datasets. Datastores and Datasets are a critical component of cloud computing. We'll learn how Azure allows you to easily integrate third party datasets and open datasets into our ML pipeline to quickly develop working solutions.

Lesson Outline: Datastores and Datasets
This lesson is all about managing data by using Datastores and Datasets. Here are the main topics we'll cover:

Managing data. We'll talk about some of the MLOps workflows that are enabled by managing data within the Azure ML studio platform.
Working with Datasets. Working with datasets is critical for sharing data and having a high performance pipeline that doesn't require copying the data back and forth.
Dataset monitoring and data drift. If you collect your data, train a model, and then you get some new customers, those new customers may not be the correct target for the model that you created previously—you may need to recreate the model to get a better fit. With Dataset monitoring, you can detect those changes.
Using Datasets in notebooks. We'll cover the workflow for using Datasets in notebook, and we'll show you how you can leverage the open Datasets that are available in Azure.
Dealing with sensitive data. One of the most important topics in ML is how to handle personally identifiable information and protect it using encryption.

The Problem: Managing Data Without the Cloud
To understand why we need Datastores—and cloud-based data storage more generally—it helps to first consider the alternative. If you were trying to handle the data on your own local machine, you would be faced with a number of challenges, including:

Data governance. If you have secret or sensitive data that you need to keep protected, data governance becomes a concern.
Do-It-Yourself (DIY) interface to data storage types. You will have to write a bunch of extra code to connect different storage types (such as SQL or Databricks).
Hardware constraints. Your machine's resources (e.g., CPU, disk IO, storage) are limited.
Third party integration. If you want to use an off-the-shelf, third party tool, this could pose integration problems—and you will have to handle the integration problems on your own.
The Solution: The Azure Cloud and Datastores
Datastores have a number of key properties that address the above challenges:

Easy-to-use interface for many storage types. A Datastore is essentially an abstraction that provides easy methods to interact with many different tools and with many different complex data storage types. This removes the extra work of struggling with third-party integrations and writing do-it-yourself interfaces for different data storage types.
Secure, centralized control of the data. This means you don't need to have separate systems that move your data to different locations—which results in better efficiency. You don't have to copy the data back and forth; instead, your ML projects can simply use copies derived from that centralized data. This centralized control also includes built-in encryption and thus results in better security.

Scalability. Datastores leverage cloud-native elastic storage, meaning that they can scale in response to demand. Obviously, this is something your hard drive cannot do.

### Working with Datasets

A Datastore is an abstraction that gives you an easy way to interact with different data storage types.
A Dataset is a pointer to the location of a data file stored in a Datastore.

### Dataset Monitor and Data Drift

A common problem is that you may train a model on some data and achieve a good fit—but then, over time, new data comes in and the model fits less and less well. This is called data drift. You can use Dataset monitor to address this problem. Essentially, the process is:

Register a baseline Dataset. This would be a Dataset that has a good fit with your model (commonly you would use the Dataset with which you trained the model).
Register a target Dataset. This might be your model input data that you are receiving over time.
Check for a delta. If there's a specified delta (i.e., a given magnitude of difference) between the baseline and target Datasets, the system will trigger an alert (such as an email) and/or some form of automatic, corrective action (such as re-training the model).

## Using Datasets in Notebooks

![image](https://user-images.githubusercontent.com/68102477/123044743-69ea7a00-d43d-11eb-81ea-8c34e582ef5a.png)

Notebooks provide the main control point for interfacing with the Azure ML platform. You can use them to control things like model deployments and distributed training, and they also provide a convenient way to share with other people on your team. In this section, we'll get into how you can use Datasets in your notebooks.

### There are two Dataset types you should take note of:

FileDataset. This is a generic Dataset type. This is useful for things like computer vision or anything where you need to have a lot of flexibility.

TabularDataset. As the name implies, this type is for tabular (i.e., table-based) data. This type allows you to handle formats like JSON, CSV, or Parquet.

As you're getting started using Datasets in Azure notebooks, you may find it very helpful to make use of [Azure Open Datasets.](https://azure.microsoft.com/en-us/services/open-datasets/) 

These are curated, ready-to-use, public Datasets that you can use to get things running and do ML without needing to worry about collecting your own data.

### Dealing with Sensitive Data

The Principle of Least Privilege (PoLP)
In the video, Noah mentioned a fundamental security principle known as the Principle of Least Privilege or PoLP, which says:

We should give users access only to what they need and nothing more.

Essentially, the more privileges a user has, the more potential there is for them to misuse those privileges. By restricting a user's access rights to only those features they need, we can reduce this potential of misuse.

You don't need to have a deep understanding of this principle for this course, but if you're curious to learn more about it, you might enjoy [this article](https://www.us-cert.gov/bsi/articles/knowledge/principles/least-privilege) from the Cybersecurity and Infrastructure Security Agency (CISA) (part of the US Department of Homeland Security). It has a number of examples that are interesting to read and will help make the principle more concrete.

Security Principles and Practices
To keep your data from being compromised, you'll want your system to follow some core security principles and practices. Let's briefly review some of the main ones:

Authentication. This is all about who can log in. You want to restrict access using the PoLP principle, so that people who don't need to log in can't log in.
Authorization. This is all about what a user can access once they have logged in. Again, you want to restrict access using the PoLP to make sure that users are only able to access, for example, the folders that they really need to be able to access. A user can only access what they need to access.
Securing compute targets and data. You want to lock down both physical access to the data storage and also online access (e.g., applying best practices, such as firewall rules, to lock down access to open ports).
Network security. This is all about protecting data from interception. Are you using a VPN to limit access to the network resources? And are you also encrypting the data over the network?
Data encryption. Data encryption itself encompasses both data at rest and in transit. Obviously, you want to use secure protocols to prevent others from accessing the data. But by making sure the data is encrypted at all times, you ensure that even if the data is somehow breached, it still cannot be used.
Azure Encryption Services
To help you ensure your data is secure, Azure has several encryption services that that are deeply integrated with the platform:

Increased control over keys and passwords, making it much easier to implement security best practices as described above.
The ability to create and import encryption keys in minutes, which ensures that you're not having performance bottlenecks by using encryption.
Applications have no direct access to encryption keys. Each service only accesses what it needs, so that If a machine is compromised, this breach won't then open the door to a further attack on your system.


Lesson Outline: Datastores and Datasets
This lesson was all about managing data by using Datastores and Datasets. Here are the main topics we covered:

Managing data. We talked about some of the MLOps workflows that are enabled by managing data within the Azure ML studio platform.
Working with Datasets. Working with datasets is critical for sharing data and having a high performance pipeline that doesn't require copying the data back and forth.
Dataset monitoring and data drift. If you collect your data, train a model, and then you get some new customers, those new customers may not be the correct target for the model that you created previously—you may need to recreate the model to get a better fit. With Dataset monitoring, you can detect those changes.
Using Datasets in notebooks. We covered the workflow for using Datasets in notebook, and we showed you how you can leverage the open Datasets that are available in Azure.
Dealing with sensitive data. One of the most important topics in ML is how to handle personally identifiable information and protect it using encryption.

# LESSON 4 TRAINING MODELS IN AZURE

Managing pipelines. We'll cover how to create a pipeline that you manage yourself using the console, which will alow you to make very small changes that can be run repeatedly.
Hyperparameters in experiments. We'll learn how to use hyperparameters in experiments, including how we can automate the creation of hyperparameters and make very small changes that create huge value in terms of prediction accuracy.

## Lesson Outline: Training models in Azure

This lesson is all about training models. Here's what we'll be covering in this lesson:

Introduction to Designer. First, we'll learn how we can quickly build our models using the no code/low code, drag-and-drop interface of the Designer.

Managing pipelines. We'll cover how to create a pipeline that we manage ourselves using the console, which will allow us to make very small changes that can be run repeatedly. Our goal in managing our pipelines is to do MLOps—that is, to apply a DevOps-based workflow to ML.

Running pipelines. We'll learn how to run pipelines and experiments, as well as how to look at the output and tune our models.

Hyperparameters in experiments. Finally, we'll learn how to use hyperparameters in experiments, including how we can automate the creation of hyperparameters and make very small changes that create huge value in terms of prediction accuracy.
Monitoring models with application insights. Finally, we'll talk about how we can leverage Azure's Application Insights infrastructure to monitor the performance of our models in production.

## Designer

The Designer is a no code/low code interface that allows you to organize resources using a simple drag-and-drop interface. You can use the Designer to build, test, and deploy your ML models. 

![image](https://user-images.githubusercontent.com/68102477/123044917-ab7b2500-d43d-11eb-948d-27e746507ade.png)

The Designer can be used to organize and configure a variety of resources, including:

[Pipelines](https://docs.microsoft.com/en-us/azure/machine-learning/concept-designer#pipeline)
[Datasets](https://docs.microsoft.com/en-us/azure/machine-learning/concept-designer#datasets)
[Compute resources](https://docs.microsoft.com/en-us/azure/machine-learning/concept-designer#compute)
[Registered models](https://docs.microsoft.com/en-us/azure/machine-learning/concept-azure-machine-learning-architecture#models)
[Published pipelines](https://docs.microsoft.com/en-us/azure/machine-learning/concept-designer#publish)
[Real-time endpoints](https://docs.microsoft.com/en-us/azure/machine-learning/concept-designer#deploy)

Note that the Designer has many sample projects, which provide a great way to get started and learn the interface.



## What is Azure Pipelines?
Azure Pipelines is a cloud service that incorporates the DevOps approach of Continuous Integration (CI) and Continuous Delivery (CD) to automate your ML workflow. With Azure Pipelines, you can:

Automatically build and test your code project
Share your project with others
Ways to Run Pipelines
There are several different tools you can use to control a pipeline in Azure:

You can use the Designer to set up your pipeline using a low code/no code, drag-and-drops interface.
You can use the console to go through and adjust an existing pipeline.
You can use the Azure ML SDK to programmatically control your pipeline with Python.
You can use a notebook to spin up a pipeline, configure it, and rerun it whenever needed.

![image](https://user-images.githubusercontent.com/68102477/123048537-d9626880-d441-11eb-8575-509b84e6ee21.png)

## An AzureML pipeline has several main components:

![image](https://user-images.githubusercontent.com/68102477/123048594-e8e1b180-d441-11eb-8fcb-67b955c8d564.png)

**Data preparation** 
This involves steps like importing, validating, cleaning, wrangling (or "munging"), transforming, normalizing, and staging your data. This step tends to be a large proportion of the work in most ML projects.

**Training configuration**
A typical training configuration includes steps like parameterization, file paths, logging, and reporting.

**Training validation**
Training validation involves repeatedly running through your experiment, picking different hardware, compute resources, doing distributed computing, and also monitoring your progress.

**Model deployment**
The final step is to deploy the model. This typically involves actions like versioning, scaling, provisioning, and configuring access control.
The Azure Machine Learning Workspace

A lot of the complicated inner workings of a pipeline are automated for you behind the scenes by the Azure Machine Learning Workspace. You can see this in the diagram below:

![image](https://user-images.githubusercontent.com/68102477/122871030-cbddad80-d371-11eb-835b-40707d5acbb7.png)


You don't need to understand or remember all of the details shown here, but one key idea to understand is that this system supports an MLOps approach by providing a traceable data lineage—meaning, you have visibility into the process that the data has undergone, including the origin of the data and the root cause of any errors that arise.

## Hyperparameters in Experiments

Key Tasks for Using Hyperparameters in Experiments
Using hyperparameters in experiments involves the following key tasks:

Define the parameter search space.
Optimize a chosen metric.
Specify termination—meaning, define the criteria that say when the process should be terminated.
Allocate resources, such as selecting the compute clusters you'll use.
Launch an experiment using an Azure pipeline.
Visualize the results to see what you actually created.
On the next page, we'll get some hands-on practice with this process, including how to choose runs that have the best hyperparameter tuning.

### Monitoring Models with Application Insights

Once you have deployed an ML model, you need to monitor the model's performance—which you can do using Microsoft Azure's Application Insights. Application Insights is an Application Performance Management (APM) service that is available as a feature of Azure Monitor.

Metrics for Monitoring Models
There are a variety of metrics you can use when monitoring your ML models with Application Insights. Some examples are:

Request rate. The request rate allows you to figure out how many times your model is being called. If it's being called quite frequently, you may want to have a larger cluster.
Response time. For example, if your application is getting very long response times and it's doing computer vision, you might need to switch to a GPU inference end point.
Failure rate. If your application is failing more than it should (e.g., it has a 20% failure rate) this is something that you may be able to address with an infrastructure change or by using a different model.
Exceptions. You may train a new mode and put it into production, but then find it doesn't fit with the data structure of what your request is expecting—a situation like this will generate an exception, which you can then address.

Lesson Outline: Training models in Azure
This lesson was all about training models. Here's what we covered in this lesson:

Introduction to Designer. First, we learned how we can quickly build our models using the no code/low code, drag-and-drop interface of the Designer.
Managing pipelines. We covered how to create a pipeline that we manage ourselves using the console, which allows us to make very small changes that can be run repeatedly. We saw that our goal in managing our pipelines is to do MLOps—that is, to apply a DevOps-based workflow to ML.
Running pipelines. We learned how to run pipelines and experiments, as well as how to look at the output and tune our models.
Hyperparameters in experiments. Finally, we learned how to use hyperparameters in experiments, including how we can automate the creation of hyperparameters and make very small changes that create huge value in terms of prediction accuracy.
Monitoring models with application insights. Finally, we talked about how we can leverage Azure's Application Insights infrastructure to monitor the performance of our models in production.

# LESSON 5 AZURE ML SDK

Creating pipelines. We'll talk about how the Azure ML SDK allows us to programmatically create pipelines. By automating the creation of pipelines, we can create more pipelines; also, our pipeline creation becomes a a repeatable process that other members of our team can follow.
Managing experiments. We'll learn how to use the SDK to manage experiments programmatically with Python, allowing us to easily rerun our processes using Python scripts.

Lesson Outline: Azure ML SDK
This lesson is all about the Azure ML SDK—and in particular, how to use the SDK to programmatically control and automate our machine learning pipelines. Here are the main topics:

Managing data with the SDK. We'll get into how to manage our cloud resources with the SDK, including how to do monitoring and logging.
Creating pipelines. We'll talk about how the Azure ML SDK allows us to programmatically explore, create, and manage pipelines. By automating the creation of pipelines, we can create much larger numbers of pipelines; also, our pipeline creation becomes a a repeatable process that other members of our team can follow.
Managing experiments. We'll learn how to use the SDK to manage experiments programmatically with Python, allowing us to easily rerun our processes using Python scripts.

The Azure ML SDK
This lesson is all about the Azure ML Software Development Kit (SDK). The SDK is especially useful to us because it essentially connects two other incredibly useful tools:

The Azure ML platform, which gives us the ability to easily automate our machine learning pipelines.
The Python ecosystem, which has a rich open source library and allows you to greatly customize your applications.
The SDK allows you to combine the automation of the Azure ML platform with the customizability of the Python ecosystem to greatly increase the effectiveness, efficiency, and flexibility of your ML applications. Because the SDK is Python-based, it allows us to tap into a rich ecosystem and build a huge variety of tools, from web applications to command-line tools.

Azure ML Key Capabilities
Dataset lifecycle. You can use the SDK to manage your dataset lifecycle. This includes organizing, monitoring, and logging your ML experiments and resources.
Train models. The SDK can be used to train a model, either locally or with cloud resources (e.g., to do GPU-accelerated model training).
AutoML. Using the SDK, you can leverage the power of the cloud platform to automatically iterate through algorithms and hyper parameter tunings to find the best model for running predictions.
Web services. Finally, you can deploy your web service easily by converting your trained model into a RESTful service that can be consumed by any application.
Azure ML Modes
Stable. The stable mode uses an established version to ensure you have a stable environment that you can count on. This is recommended for most use cases.
Experimental. If you're an early adopter, you can use experimental mode, which is for advanced users who want to try out new features as they become available and are comfortable tolerating some potential bugs.

[Azure ML SDK documentation](https://docs.microsoft.com/en-us/python/api/overview/azure/ml/?view=azure-ml-py)

[Install the Azure Machine Learning SDK for Python](https://docs.microsoft.com/en-us/python/api/overview/azure/ml/install?view=azure-ml-py)

### Managing Data with the SDK

The Azure ML SDK allows you to automate your machine learning pipeline, and a key part of this automation is using the SDK to manage data. As we've mentioned, the data preparation step in an ML pipeline often makes up a large proportion (not uncommonly about 80%) of the work, so automating the management of this part of the pipeline can make it dramatically more efficient.

Note: Earlier we mentioned that a dataset can reference data in a Datastore. In addition, a dataset object can also reference a dataset using public web URLs. We'll see an example of this in the following video.


Interfacing with Datasets
You can interface with Datasets via the API. How you do so depends in part on the type of Dataset you are using. If you recall from an earlier lesson, there are two Dataset types:

FileDataset. This is a generic Dataset type. This is useful for things like computer vision or anything where you need to have a lot of flexibility.
TabularDataset. As the name implies, this type is for tabular (i.e., table-based) data. This type allows you to handle formats like JSON, CSV, or Parquet.
We'll get some practice managing Datasets in an exercise shortly, but to get an initial idea of how this might work, here's an example of a typical piece of code for interfacing with a FileDataset:

from azureml.core.dataset import Dataset

url_paths = [
            'http://yann.lecun.com/exdb/mnist/train-images-idx3-ubyte.gz',
            'http://yann.lecun.com/exdb/mnist/train-labels-idx1-ubyte.gz',
            'http://yann.lecun.com/exdb/mnist/t10k-images-idx3-ubyte.gz',
            'http://yann.lecun.com/exdb/mnist/t10k-labels-idx1-ubyte.gz'
            ]

dataset = Dataset.File.from_files(path=url_paths)
This small block of Python allows us to simplify this part of the process considerably via the straightforward act of placing all the URL paths in a list and assigning them to a single variable.

Then, by instantiating the dataset object, we have the power to manipulate the data using built-in methods that come with the API. For example we may want to load the data into a Pandas DataFrame, which we can easily do using the to_pandas_dataframe method:

 df = dataset.to_pandas_dataframe()
 
 ### Using the SDK in Azure Cloud Shell (Optional)
As we saw in the previous exercise, one of the most common ways to use the SDK is via a Jupyter notebook. Another approach that can also be quite useful is to use the SDK via the Azure Cloud Shell.

As a developer, you may want to explore SDK functionality in a Command-Line Interface where you can try out commands in the interactive prompt. By using IPython in the Azure Cloud Shell, you can easily experiment with different SDK features. An approach that some developers use is to play with a feature initially in the Cloud Shell, and then later implement it in a Jupyter Notebook.

Using the SDK in the Cloud Shell is optional for this course. If you'd like to explore it, we'll walk through the basic setup on this page. If you prefer not to explore it at this time, you can simply skip the remainder of this page and come back to it another time.

Enable Cloud Shell
The first time you use the Cloud Shell in your Azure account, you'll need to enable it. To do so, click on the shell icon:

The cloud shell icon.
Then click on Bash > Create storage. Once the process has completed, you should see the Command-Line Interface for Cloud Shell.

Create a Virtual Environment and Install IPython
Once you have the Cloud Shell running, the first thing you'll want to do is create a virtual environment for the SDK. You can do that using venv as follows:

python -m venv ~/.azure-ml-sdk
Then activate the virtual environment and install IPython:

source ~/.azure-ml-sdk/bin/activate && pip install ipython
Import the SDK
Now you're ready to import and access the SDK from the Cloud Shell, as demonstrated in the video below.

### Creating a Pipeline with the SDK

We've seen previously how to set up a pipeline use the Designer—now we'll see how to do it programmatically using the SDK. Specifically, we'll look here at some example code for the data preparation, training configuration, and training validation steps of the pipeline.

You can find the code examples we went over below, for your reference. On the next page, we'll go through an exercise so you can get some hands-on practice.

Data Preparation
ws = Workspace.from_config() 
blob_store = Datastore(ws, "workspaceblobstore")
compute_target = ws.compute_targets["STANDARD_NC6"]
experiment = Experiment(ws, 'MyExperiment') 

input_data = Dataset.File.from_files(
    DataPath(datastore, '20newsgroups/20news.pkl'))
    
Training Configuration
output_data = PipelineData("output_data", datastore=blob_store)

input_named = input_data.as_named_input('input')

steps = [ PythonScriptStep(
    script_name="train.py",
    arguments=["--input", input_named.as_download(),
        "--output", output_data],
    inputs=[input_data],
    outputs=[output_data],
    compute_target=compute_target,
    source_directory="myfolder"
) ]

pipeline = Pipeline(workspace=ws, steps=steps)
Training Validation

pipeline_run = experiment.submit(pipeline)
pipeline_run.wait_for_completion()

### Managing Experiments with the SDK

Earlier, you learned how to use the Designer to view the results of your previous runs. If we manage our experiments with the SDK, then we can also access this same data—but in a way that gives us greater control and increased functionality. This involves two main tasks: Listing past experiments and submitting new experiments.

1. Listing Past Experiments
To do this, we need to pass in a workspace object, and then list the collection of trials. This will give us data very similar to the list we've accessed previously using the Designer. Here's the example code we looked at:

from azureml.core.experiment import Experiment

**First, we pass in the workspace object `ws` to the `list` method and it returns a Python list of `Experiment` objects. **

list_experiments = Experiment.list(ws)

**If we print the contents of the variable, we can see the list of all the experiments that have been run in that workspace.**

print(list_experiments)
[Experiment(Name: dataset_profile,
 Workspace: Azure-ML-Workspace), Experiment(Name: binary-classification,
 Workspace: Azure-ML-Workspace), Experiment(Name: regression,
 Workspace: Azure-ML-Workspace), Experiment(Name: sfautoml]

2. Submitting New Experiments
To submit a new experiment (such as if we wanted to try a different model type or a different algorithm), we would again pass in a workspace object and then submit the experiment. Here's the example code:

from azureml.core.experiment import Experiment

experiment = Experiment(ws, "automl_test_experiment")
run = experiment.submit(config=automl_config, show_output=True)


### Edge Cases: SDK Versioning

One potential issue or "gotcha" that can come up when you're using tools like Jupyter Notebooks or the Azure Cloud Shell is that you may not really know what versions your code is using. Things may run fine for a while and then suddenly stop working because of an issue with the version of one of the libraries being used by your code.

One way you can address this problem is by pinning your dependencies so that your code always uses a specific known version. For example:

Jupyter notebooks can do this by using a pip package that has a specific version
Azure Cloud Shell can do this by using a requirements file
For example, here's what that might look like in a requirements.txt file for a Python project:

Flask==1.0.2
pandas==0.24.2
scikit-learn==0.20.3
pylint
The first three packages are specifically pinned to a version number. The last package, pylint, isn't.

Lesson Outline: Azure ML SDK
This lesson was all about the Azure ML SDK—and in particular, how to use the SDK to programmatically control and automate our machine learning pipelines. Here are the main topics we covered:

Managing data with the SDK. We got into how to manage our cloud resources with the SDK, including how to do monitoring and logging.
Creating pipelines. We talked about how the Azure ML SDK allows us to programmatically explore, create, and manage pipelines. By automating the creation of pipelines, we can create much larger numbers of pipelines; also, our pipeline creation becomes a a repeatable process that other members of our team can follow.
Managing experiments. We learned how to use the SDK to manage experiments programmatically with Python, allowing us to easily rerun our processes using Python scripts.



## Lesson 6: Automated Machine Learning and Hyperparameter Tuning
Automated ML and SDK. We'll discuss how we can use the Azure ML SDK to do Automated ML and create models more quickly and accurately.
Model Interpretation. We'll explore how model interpretation allows us to build solutions using Automated ML that we (and others) can more easily interpret, making visible the core features that are driving the model.

### Lesson Outline: AutoML and Hyperparameter Tuning
In this lesson, we'll see how we can use Automated ML and Hyperparameter tuning to dramatically speed up the development of our models. Here's what we'll be covering:

Automated ML and SDK. We'll discuss how we can use the Azure ML SDK with AutoML to operationalize and automate model creation—allowing you to create models more quickly and accurately.
Model Interpretation. We'll explore how model interpretation allows us to build solutions using AutoML that we (and others) can more easily interpret, making visible the core features that are driving the model.
Exporting Models with ONNX. ONNX is a portability platform for models that was created by Microsoft and that allows you to convert models from one framework to another, or even to deploy models to a device (such as an iOS or Android mobile device).

