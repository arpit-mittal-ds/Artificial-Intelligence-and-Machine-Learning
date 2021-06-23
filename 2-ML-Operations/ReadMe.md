# Notes

**1. DEPLOY A MODEL**

**2. CONSUME ENDPOINTS**

**3. PIPELINE AUTOMATION**

# DEPLOY A MODEL

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


# CONSUME ENDPOINTS

This is the lesson about Consuming Endpoints. These endpoints allow other services to interact with deployed models. And in this lesson, you will learn all the key facts about interacting with them.

There are some interesting details you need to be aware of when trying to use HTTP and you will go through each of these:

**Swagger** (A tool that eases the documentation efforts of HTTP APIs)

**Consuming deployed services**

**Benchmarking** (being able to create a baseline of acceptable performance so that it can be compared to day-to-day behavior)



### Swagger Documentation

Swagger is a tool that helps build, document, and consume RESTful (A style for building HTTP endpoints that emphasizes separation of concerns) web services like the ones you are deploying in Azure ML Studio. It further explains what types of HTTP requests that an API can consume, like POST and GET.

Azure provides a swagger.json that is used to create a web site that documents the HTTP endpoint for a deployed model.

![image](https://user-images.githubusercontent.com/68102477/123007946-62a37c00-d3fd-11eb-8e9f-6d04f5dd006b.png)

Further reading
[The Swagger homepage](https://swagger.io/tools/swagger-ui/) has in-depth examples and usage to dig further into other details.

### Steps

1. Ensure that Docker is installed on your computer.

Azure provides a Swagger JSON file for deployed models. Head to the Endpoints section, and find your deployed model there.

Click on the name of the model, and details will open that contains a Swagger URI section. Download the file locally to your computer and put it in the same directory with serve.py and swagger.sh.

2. Run two scripts:

serve.py will start a Python server on port 8000. This script needs to be right next to the downloaded swagger.json file. NOTE: this will not work if swagger.json is not on the same directory.

swagger.sh which will download the latest Swagger container, and it will run it on port 80. If you don't have permissions for port 80 on your computer, update the script to a higher number (above 9000 is a good idea).

3. Open the browser and go to http://localhost:8000 where serve.py should list the contents of the directory. swagger.json must show. If it doesn't, it needs to be downloaded from the deployed model endpoint.

![image](https://user-images.githubusercontent.com/68102477/123009570-4a812c00-d400-11eb-9d08-370f98c9bba7.png)


4. Go to http://localhost/ which should have Swagger running from the container (as defined in swagger.sh). If you changed the port number, use that new port number to reach the local Swagger service (for example, http://localhost:9000 if port 9000 is used).

![image](https://user-images.githubusercontent.com/68102477/123009592-5371fd80-d400-11eb-9db5-a3fa0b784c79.png)


5. On the top bar, where petsore.swagger.io shows, change it to http://localhost:8000/swagger.json, then hit the Explore button. It should now display the contents of the API for the model

Look around at the different HTTP requests that are supported for your model, including the example.

![image](https://user-images.githubusercontent.com/68102477/123009621-5ec52900-d400-11eb-88d2-9992a4c1da3e.png)

### Consume Deployed Service

You can consume a deployed service via an HTTP API. An HTTP API is a URL that is exposed over the network so that interaction with a trained model can happen via HTTP requests.

Users can initiate an input request, usually via an HTTP POST request. HTTP POST is a request method that is used to submit data. The HTTP GET is another commonly used request method. HTTP GET is used to retrieve information from a URL. The allowed requests methods and the different URLs exposed by Azure create a bi-directional flow of information.

The APIs exposed by Azure ML will use JSON (JavaScript Object Notation) to accept data and submit responses. It served as a bridge language among different environments.

New terms
JSON: JavaScript Object Notation, also referred to as a "bridge language" used to make communication possible between two groups who do not share a native dialect
GET request method: GET is a request method supported by HTTP. This method should only be used to retrieve data from a web server
POST request method: POST is a request method supported by HTTP. This method requests that a web server accepts the data enclosed in the body of the request message
Further reading
The "[How to consume a web service](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-consume-web-service)" Azure documentation has good examples of further interactions with an endpoint.

### Steps:

1. In Azure ML Studio, head over to the "Endpoints" section and find a previously deployed model. The compute type should be ACI (Azure Container Instance).

![image](https://user-images.githubusercontent.com/68102477/123012878-6982bc80-d406-11eb-965f-5b06ccea9916.png)

2. In the "Consume" tab, of the endpoint, a "Basic consumption info" will show the endpoint URL and the authentication types. Take note of the URL and the "Primary Key" authentication type.

![image](https://user-images.githubusercontent.com/68102477/123012902-77d0d880-d406-11eb-8d5e-cb5db85c991b.png)

3. Using the provided endpoint.py replace the scoring_uri and key to match the REST endpoint and primary key respectively. The script issues a POST request to the deployed model and gets a JSON response that gets printed to the terminal.

Running it should produce similar results to this:

$  python endpoint.py
{"result": [2553]}
A data.json file will appear after you run endpoint.py

Note: the instructor used a different target column in the demo other than cnt. So the result displayed in the demo would be different from yours if you use cnt as the target column. Your display should be similar to {"result": [2553]}


### Creating a Benchmark

A benchmark is used to create a baseline or acceptable performance measure. Benchmarking HTTP APIs is used to find the average response time for a deployed model.

One of the most significant metrics is the response time since Azure will timeout if the response times are longer than sixty seconds.

Apache Benchmark is an easy and popular tool for benchmarking HTTP services. You will learn about it on the next page.


**Response Time:** The time in seconds (or milliseconds) that service takes to produce a response

**Timeout:** When a request is sent, this is an error when the server cannot produce a response in a given amount of time


The documentation website for the [Apache Benchmark Tool](https://httpd.apache.org/docs/2.4/programs/ab.html) goes deep into all the options needed to benchmark almost any URL.

### Steps:

Make sure you have the Apache Benchmark command-line tool installed and available in your path:

$ which ab
/usr/bin/ab
$ ab --help
Usage: ab [options] [http[s]://]hostname[:port]/path
Options are:
...

2. Run the endpoint.py. Just like before, it is important to use the right URI and Key to communicate with the deployed endpoint. A data.json should be present. This is required for the next step where the JSON file is used to HTTP POST to the endpoint.
In the provided started code, there is a benchmark.sh script with a call to ab similar to this:
 ab -n 10 -v 4 -p data.json -T 'application/json' -H 'Authorization: Bearer Agbasf3asdIygqpjasdfasdfVevsnPzCC' http://8asdf0dfd665-1f3-49c8-a953-b81234dsdg1g2917.eastus.azurecontainer.io/score
Once you verify the file exists locally, run the benchmark.sh script. A highly verbose output should appear similar to this:

$ bash benchmark.sh
 This is ApacheBench, Version 2.3 <$Revision: 1843412 $>
 Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
 Licensed to The Apache Software Foundation, http://www.apache.org/

 Benchmarking 8530a665-66f3-49c8-a953-b82a2d312917.eastus.azurecontainer.io (be patient)...INFO: POST header ==
 ---
 POST /score HTTP/1.0
 Content-length: 812
 Content-type: application/json
 Authorization: Bearer Agb3D23IygqpjVet4z8Y5oYGEvsnPzCC
 Host: 8530a665-66f3-49c8-a953-b82a2d312917.eastus.azurecontainer.io
 User-Agent: ApacheBench/2.3
 Accept: */*


 ---
 LOG: header received:
 HTTP/1.0 200 OK
 Content-Length: 33
 Content-Type: application/json
 Date: Thu, 30 Jul 2020 12:33:34 GMT
 Server: nginx/1.10.3 (Ubuntu)
 X-Ms-Request-Id: babfc511-a0f0-4ecb-a243-b3010a76b8b9
 X-Ms-Run-Function-Failed: False

 "{"forecast": [985.0001475440272], "index": [{"date": 1356998400000, "_automl_dummy_grain_col": "_automl_dummy_grain_col"}]}"
 LOG: Response code = 200
 LOG: header received:
 HTTP/1.0 200 OK
 Content-Length: 33
 Content-Type: application/json
 Date: Thu, 30 Jul 2020 12:33:34 GMT
 Server: nginx/1.10.3 (Ubuntu)
 X-Ms-Request-Id: b48dd8da-0b4e-44fd-a1e5-04043bfa77f1
 X-Ms-Run-Function-Failed: False

"{"forecast": [985.0001475440272], "index": [{"date": 1356998400000, "_automl_dummy_grain_col": "_automl_dummy_grain_col"}]}"
 LOG: Response code = 200
 ..done
 
 ### Curating Data Input
 
There are some key items to ensure when sending data to a deployed endpoint. You need to make sure that the keys and values are following the constraints. For example, if one field is repeated, this could potentially cause an error response, or if the format needs a date and time as a string, rather than an integer.

Remember, using values that the service doesn't expect would produce an error response.

**Summary**

In this lesson, we went through a critical step after deploying a model: consuming information from it.

This lesson covered a lot of material related to a deployed model: starting with Swagger to better understand the API, to consume a deployed service, and all the way to create a baseline for finding potential problems.

**Further reading**
[Chapter 4 of Python For DevOps](https://www.oreilly.com/library/view/python-for-devops/9781492057680/) covers benchmarking and other useful Linux utilities that can be useful


# PIPELINE AUTOMATION

In this lesson, we will go into more detail about automation. Automation is a core pillar of DevOps applicable to Machine Learning operations.

A good feature of Azure is Pipelines, and these are closely related to automation. Some key factors covered about pipelines are:

Creating a pipeline (include batch inference pipeline)

Publishing a pipeline

Interacting with a pipeline via an HTTP API endpoint

["What are Machine Learning Pipelines](https://docs.microsoft.com/en-us/azure/machine-learning/concept-ml-pipelines)" has good information about Pipelines and how they related to Machine Learning.

### Create a Pipeline

The most common SDK class is the Pipeline class. You will use this when creating a Pipeline. Pipelines can take configuration and different steps, like AutoML for example.

Different steps can have different arguments and parameters. Parameters are just like variables in a Python script.

There are areas you can play with when creating a pipeline and we covered two:

Use pipeline parameters
Recurring Scheduled Pipelines
Batch Inference Pipelines
Create a Pipeline
This is the most common Python SDK class you will see when dealing with Pipelines. Aside from accepting a workspace and allowing multiple steps to be passed in, it uses a description that is useful to identify it later.

from azureml.pipeline.core import Pipeline

pipeline = Pipeline(
    description="pipeline_with_automlstep",
    workspace=ws, 
    steps=[automl_step])
Using Pipeline Parameters
Pipeline parameters are also available as a class. You configure this class with the various different parameters needed so that they can later be used.

In this example, the avg_rate_param is used in the arguments attribute of the PythonScriptStep.

from azureml.pipeline.steps import PythonScriptStep
from azureml.pipeline.core import PipelineParameter

avg_rate_param = PipelineParameter(name="avg_rate", default_value=0.5)
train_step = PythonScriptStep(script_name="train.py",
                              arguments=["--input", avg_rate_param],
                              target=compute_target,
                              source_directory=project_folder)
Scheduling a recurring Pipeline
To schedule a Pipeline, you must use the ScheduleRecurrence class which has the information necessary to set the interval.

Once that has been created, it has to be passed into the create() method of the Schedule class as a recurrence value.

from azureml.pipeline.core.schedule import ScheduleRecurrence, Schedule

hourly = ScheduleRecurrence(frequency="Hourly", interval=4)
pipeline_schedule = Schedule.create(ws, name="RecurringSchedule", 
                            description="Trains model every few hours",
                            pipeline_id=pipeline_id, 
                            experiment_name="Recurring_Pipeline_name", 
                            recurrence=hourly)
Batch Inference Pipeline
One of the core responsibilities of a batch inference pipeline is to run in parallel. For this to happen, you must use the ParallelRunConfig class which helps define the configuration needed to run in parallel.

Some important aspects of this are the script that will do the work (entry_script), how many failures it should tolerate (error_threshold), and the number of nodes/batches needed to run (mini_batch_size, 5 in this example).

from azureml.pipeline.steps import ParallelRunConfig

parallel_run_config = ParallelRunConfig(
    source_directory='scripts',
    entry_script="scoring.py",
    mini_batch_size="5",
    error_threshold=4,
    output_action="append_row",
    environment=batch_env,
    compute_target=aml_target,
    node_count=5)

parallelrun_step = ParallelRunStep(
    name="batch-score",
    parallel_run_config=parallel_run_config,
    inputs=[batch_data_set.as_named_input('batch_data')],
    output=output_dir,
    arguments=[],
    allow_reuse=True
)

### create the pipeline

pipeline = Pipeline(workspace=ws, steps=[parallerun_step])


Batch inference: The process of doing predictions using parallelism. In a pipeline, it will usually be on a recurring schedule

Recurring schedule: A way to schedule pipelines to run at a given interval

Pipeline parameters: Like variables in a Python script, these can be passed into a script argument

[The Batch inference announcement](https://techcommunity.microsoft.com/t5/azure-ai/batch-inference-in-azure-machine-learning/ba-p/1417010) from Microsoft has very good insight as to what can these types of Pipelines do.

### Steps:

1. Open up the Jupyter Notebook and make sure you replace all of the URIs, Keys, and experiment names to match your own. Anywhere noted, ensure that the right components are replaced as shown in the next screenshot.

![image](https://user-images.githubusercontent.com/68102477/123014097-d5febb00-d408-11eb-8099-8b6af04b7cbc.png)


Run the Jupyter Notebook all the way up until the Examine Results section. In the end, the pipeline should be available in Azure ML Studio in the Pipelines section.

![image](https://user-images.githubusercontent.com/68102477/123014134-e57e0400-d408-11eb-88f5-231585838990.png)

3. Clicking on the Pipeline should take you to the experiment that demonstrates the graph using the Bikesharing Dataset and the Auto ML Model.

4. (Optional) You can keep running through the cells in the Examine Results section to retrieve metrics and the best model

### Publish a Pipeline

Publishing a pipeline is the process of making a pipeline publicly available. You can publish pipelines in Azure Machine Learning Studio, but you can also do this with the Python SDK.

When a Pipeline is published, a public HTTP endpoint becomes available, allowing other services, including external ones, to interact with an Azure Pipeline.

Automation with pipelines
Pipelines are all about Automation. Automation connects different services and actions together to be part of a new workflow that wasn’t possible before.

There are some good examples of how different services can communicate to the pipeline endpoint to enable automation.

A hosted project using version control: when a new change gets merged, a trigger is created to send an HTTP request to the endpoint and train the model.

A newer dataset gets uploaded to a storage system that triggers an HTTP request to the endpoint to re-train the model.

Several teams that want to use AutoML with datasets that are hosted externally can configure the external cloud provider to trigger an HTTP request when a new dataset gets saved.

A CI /CD platform like Jenkins, with a job that submits an HTTP request to Azure when it completes without error.


**HTTP Trigger:** With configuration, a service can create an HTTP request based on certain conditions

**Publishing a Pipeline:** Allowing external access to a Pipeline over an HTTP endpoint

**Further reading**

The Azure documentation on [how to create and run ML Pipelines](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-create-your-first-pipeline) is a good introduction to Pipelines in general, but also on publishing them.


### Consume Pipeline Endpoint (API)

Pipeline endpoints can be consumed via HTTP, but it is also possible to do so via the Python SDK. Since there are different ways to interact with published Pipelines, this makes the whole pipeline environment very flexible.

It is key to find and use the correct HTTP endpoint to interact with a published pipeline. Sending a request over HTTP to a pipeline endpoint will require authentication in the request headers. We will talk more about it later.

New terms
Pipeline endpoint: The URL of the published Pipeline
HTTP Headers: Part of the HTTP specification, where a request can attach extra information, like authentication
Further reading
The documentation on the [Pipeline Endpoint class](https://docs.microsoft.com/en-us/python/api/azureml-pipeline-core/azureml.pipeline.core.pipeline_endpoint.pipelineendpoint?view=azure-ml-py) has some good information about methods that allow interacting with a pipeline.

### Exercise Publish and Consume a Pipeline:

**Part 1: Publish a Pipeline**

ML Studio
In Azure ML Studio, under the Pipelines section, you will get to a list of all the pipelines available. Click on a Run ID that has a status of Completed.

![image](https://user-images.githubusercontent.com/68102477/123016104-3d1e6e80-d40d-11eb-99e0-46ef7529c17b.png)

Click on the Publish button so that the overlay menu shows up, and fill it with something descriptive. You can either re-use an endpoint, or create a new one.

![image](https://user-images.githubusercontent.com/68102477/123016133-44457c80-d40d-11eb-8fb6-5b0716db76d9.png)

**Python SDK**

Create experiment and pipeline_run
The experiment and run_id of that experiment are crucial. Update the experiment name, project_folder:

# NOTE: update these to match your existing experiment name and a previous experiment
experiment_name = 'ml-bike-experiment-1'
project_folder = './pipeline-bike-project'

experiment = Experiment(ws, experiment_name)
And for the run_id:

from azureml.pipeline.core import PipelineRun

run_id = "78e729c3-4746-fffff-aaaaa-abe970f4966f"
pipeline_run = PipelineRun(experiment, run_id)

Find the Run ID in the Pipelines section in Azure ML Studio

Once the pipeline_run object is created, you can publish the pipeline
published_pipeline = pipeline_run.publish_pipeline(
    name="Bikesharing Train", description="Training bikesharing pipeline", version="1.0")
Part 2: Consume a pipeline endpoint
Once the pipeline is published, you can authenticate:
from azureml.core.authentication import InteractiveLoginAuthentication

interactive_auth = InteractiveLoginAuthentication()
auth_header = interactive_auth.get_authentication_header()
The published pipeline will be used to retrieve the endpoint. This endpoint is the URI that the SDK will use to communicate with it over HTTP. The relevant code that uses the endpoint to make the HTTP request looks like this:
import requests

rest_endpoint = published_pipeline.endpoint
response = requests.post(rest_endpoint, 
                         headers=auth_header, 
                         json={"ExperimentName": "pipeline-bike-rest-endpoint"}
                        )

Once the Jupyter Notebook completes all of its steps, the Pipeline will be triggered and available in Azure ML Studio.

![image](https://user-images.githubusercontent.com/68102477/123016248-87075480-d40d-11eb-8a74-9869c18cc763.png)

**Summary - This lesson covered a few key aspects of Machine Learning Pipelines:**

Creating a Machine Learning Pipeline using Python SDK

Publish a pipeline using both ML Studio and Python SDK

Consume a published pipeline using Python SDK

All of these concepts are a solid foundation to start exploring pipelines more and taking advantage of their flexibility.













































