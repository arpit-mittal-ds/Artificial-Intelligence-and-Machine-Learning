# Notes

## Deploy A Model

In this lesson we will talk about model deployments, and what are all the important details you want to be aware of when shipping models into production.

Deploying a model is a crucial step towards a robust workflow. To get a model into production, several things need to take place. We will cover these topics in this lesson.

Enabling Security and Authentication

Configuring Deployment Settings

Deploying a Model

Troubleshooting

Benefits of compute instances


[Chapter 7 of Python For DevOps](https://www.oreilly.com/library/view/python-for-devops/9781492057680/) has an excellent section about logging and troubleshooting.

### Enable Security and Authentication

Authentication is crucial for the continuous flow of operations. Continuous Integration and Delivery system (CI/CD) rely on uninterrupted flows. When authentication is not set properly, it requires human interaction and thus, the flow is interrupted. An ideal scenario is that the system doesn't stop waiting for a user to input a password. So whenever possible, it's good to use authentication with automation.

Authentication types
Key- based
Azure Kubernetes service enabled by default
Azure Container Instances service disabled by default
Token- based
Azure Kubernetes service disabled by default
Not support Azure Container Instances
Interactive
Used by local deployment and experimentation (e.g. using Jupyter notebook)
Service Principal
A “Service Principal” is a user role with controlled permissions to access specific resources. Using a service principal is a great way to allow authentication while reducing the scope of permissions, which enhances security.

New terms
CI/CD: Continuous Integration and Continuous Delivery platform. Jenkins, CircleCI, and [Github Actions](https://github.com/features/actions) are a few examples.
Further reading
Both the Jenkins and Github Actions websites have good information about their CI/CD platforms and why they are compelling the CI/CD platform.



### Configure Deployment Settings

Deployment is about delivering a trained model into production so that it can be consumed by others. Configuring deployment settings means making choices on cluster settings and other types of interaction with a deployment. Having a good grasp on configuring production environments in Azure ML Studio and the Python SDK is the key to get robust deployments.

ACI and AKS
Both ACI and AKS are available in the Azure ML platform as deployment options for models.

ACI is a container offering from Azure, which uses container technology to quickly deploy compute instances. The flexibility of ACI is reduced as to what AKS offers, but it is far simpler to use.

AKS, on the other hand, is a Kubernetes offering. The Kubernetes service is a cluster that can expand and contract given on demand, and it does take more effort than the container instance to configure and setup.

New terms
ACI: Azure Container Instance
AKS: Azure Kubernetes Service
Deployment: A way to deliver work into production
Concurrent Operations: Also referred to as "concurrency", it is the number of operations to run at the same time

### Deploy an Azure Machine Learning model

The primary task as a Machine Learning engineer is to ship models into production. Constant evaluation (A feedback loop that is necessary to detect potential issues) allows identifying potential issues and creating a baseline so that adapting or updating is possible.

Some key steps to deploy a model are:

A previously trained model
Complete the deployment form
Enable authentication
Select or create a new compute cluster

### Part 1: Configure deployment settings

**1. Create a new Automated ML run**

![image](https://user-images.githubusercontent.com/68102477/122902588-f2134580-d391-11eb-8b3d-40638e882a25.png)

**2. Next, make sure you have the dataset uploaded.** 
If you don't, upload and select it. This solution uses the [bike-no.csv](https://raw.githubusercontent.com/Azure/MachineLearningNotebooks/master/how-to-use-azureml/automated-machine-learning/forecasting-bike-share/bike-no.csv) dataset.

![image](https://user-images.githubusercontent.com/68102477/122902704-0d7e5080-d392-11eb-90cb-d995452a70ca.png)

**3. Create and configure your new compute cluster.**

![image](https://user-images.githubusercontent.com/68102477/122902915-3dc5ef00-d392-11eb-9db9-a0cbe2527e62.png)

![image](https://user-images.githubusercontent.com/68102477/122902934-428aa300-d392-11eb-82a2-6ddfd27a673d.png)


4. Once the new compute cluster is successfully created, use this cluster to run the autoML experiment. Make sure you fill the name and target column.

![image](https://user-images.githubusercontent.com/68102477/122902997-52a28280-d392-11eb-94d1-a9a375b30eda.png)

5. You will see the experiment in the experiment section and a new model is created.

![image](https://user-images.githubusercontent.com/68102477/122903042-5d5d1780-d392-11eb-9f48-12a87fe2eef4.png)

### Part 2: Deploy an Azure ML model

Go to the Automated ML section and find the recent experiment with a completed status. Click on it.

![image](https://user-images.githubusercontent.com/68102477/122903160-7c5ba980-d392-11eb-89f6-edfdc741aec1.png)


Go to the "Model" tab and select a model from the list and click it. Above it, a triangle button (or Play button) will show with the "Deploy" word. Click on it.

Then

1) Fill out the form with a meaningful name and description. For Compute Type use Azure Container Instance (ACI)

2) Enable Authentication

3) Do not change anything in the Advanced section.


![image](https://user-images.githubusercontent.com/68102477/122903193-82ea2100-d392-11eb-97ee-e40549323b81.png)

Deployment takes a few seconds. After a successful deployment, a green checkmark will appear on the "Run" tab and the "Deploy status" will show as succeed.
![image](https://user-images.githubusercontent.com/68102477/122903296-9c8b6880-d392-11eb-87e2-c272787fcec1.png)

### Enable Application Insights

In this section, we discussed Application Insights that is a very useful tool to detect anomalies, visualize performance. It can be enabled before or after a deployment. To enable Application Insights after a model is deployed, you can use the below command with the python SDK. In the next section, you will learn how to do it.

### enable application insight
service.update(enable_app_insights=True)
New terms
Logging: Informational output produced by the software, usually in the form of text
Application Insights: A special Azure service which provides key facts about an application
Webservice: One of the most used Python classes from Azure's Python SDK
Further reading
Azure's documentation has a whole section on monitoring and collecting data with [Application Insights](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-enable-app-insights)







## Consume Endpoints 







## Consume Endpoints 





## Pipeline Automation




















































