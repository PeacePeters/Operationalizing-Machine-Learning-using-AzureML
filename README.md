# Operationalizing Mahine Learning using Azure

In this project, we work with the [Bank Marketing dataset](https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/bankmarketing_train.csv) which is related to direct marketing campaigns of a Portuguese banking sector. Here the project's goal is to use both Azure ML Studio and the Python SDK to configure a cloud-based machine learning production model, deploy it, and consume it using HTTP API. It also innvolves creating, publishing, and interacting with a pipeline.

## Architectural Diagram

This is the project workflow diagram that starts with autenticating with Azure ML services and ends with documentation of the entire working ML application process.
<p align="center">
<img src="https://user-images.githubusercontent.com/68206315/104122429-3a3f2e00-5345-11eb-9075-f059ef41021d.png">
</p>

![Architecture](./images/104122429-3a3f2e00-5345-11eb-9075-f059ef41021d.png)

Here are the major steps in this project:

1. Authentication
2. Automated ML Experiment
3. Deploy the best model
4. Enable logging
5. Swagger Documentation
6. Consume model endpoints
7. Create and publish a pipeline

## Autentication

Authentication is crucial for the continuous flow of operations particularly in Continuous Integration and Delivery system (CI/CD), which rely on uninterrupted flows. When authentication is not set properly, it requires human interaction and thus, the flow is interrupted. So, it's always a good practice to use autentication with automation. In Azure ML workspaces, there are a few different ways to autenticate. These include Token-based, Key-based, and Interactive Autentication.

## Automated ML Experiment

Automated ML involves the application of DevOps principles to machine learning, in order to automate all aspects of the process. For example, we can automate feature engineering, hyperparameter selection, model training, and tuning. With AutoML, hundreds of models can be created in a day with better model accuracy and deployment is faster. The automl feature of Azure was used to detect the best algorithm for the Bank Marketing dataset.

## Deploy the best model

Deployment is about delivering a trained model into production so that it can be consumed by others. Configuring deployment settings means making choices on cluster settings and other types of interaction with a deployment. In Azure ML platorm, Python SDK & Azure ML Studio are the different ways to deploy a model, and the deployment options available are Azure Container Instance (ACI) & Azure Kubernetes Service (AKS).

## Enable logging
Logging is the core pillar of DevOps/MLOps. It is important because it is at the forefront of discovering irregularities in services and most problem in general. Enabling logging in Cloud services like Azure provides you with information about how the whole service is behaving. This can be done using Application Insights which is modifiable with Azure SDK after a model has been deployed.

## Swagger Documentation

Swagger is a tool that helps build, document, and consume RESTful web services (HTTP APIs). It is offered by Azure as a swagger.json file that is used to create a web site that documents the HTTP endpoint for a deployed model. It also explains what types of HTTP requests that an API can consume, like POST and GET. Swagger documentation provides us with the information to interact with the deployed service. By using this documentation, you can verify the inputs and outputs of an API, share knowledge, and achieve more efficiency.

## Consume model endpoints

A deployed service can be consumed through an HTTP API. An HTTP API is a URL that is exposed over the network so that interaction with a trained model can happen via HTTP requests. For most common workflows, users can initiate an input request, usually via an HTTP POST request. HTTP POST is a request method that is used to submit data. The HTTP GET is another commonly used request method. HTTP GET is used to retrieve information from a URL. The APIs exposed by Azure ML will use JSON (JavaScript Object Notation) to accept data and submit responses. It served as a bridge language among different environments. The allowed requests methods and the different URLs exposed by Azure create a bi-directional flow of information and the APIs use JSON to accept data and submit responses.

## Create and publish a pipeline

Pipelines are very useful and are a foundation of automation and operations in general. Being able to create a Pipeline allows for easier interaction with model deployments. Azure pipeline is a cloud service that can be used to automatically build and test code project and make it avaible. Publishing a pipeline is the process of making a pipeline publicly available, and that can be done using both Azure Machine Learning Studio and Python SDK. Published pipelines allow external services to interact with them so that they can do work more efficiently. When a Pipeline is published, a public HTTP endpoint becomes available, allowing other services, including external ones, to interact with an Azure Pipeline. The main components of AzureML Pipeline include Data Preparation, Training Configuration & Validation, and Model Deployment.


## Key Steps

1. Ensures dataset is uploaded and available in the registered dataset dashboard

<p align="center">
<img src="https://user-images.githubusercontent.com/68206315/104123777-68287080-534d-11eb-88e5-aa1598fa991c.png">
</p>

2. Create an Automated ML experiment and wait for the run to be completed. Here Automl detected Voting Ensemble as the best algorithm for the Bank Marketing dataset.

<p align="center">
<img src="https://user-images.githubusercontent.com/68206315/104123799-7ffff480-534d-11eb-8c76-698b7df9c5fb.png">
</p>

3. Deploy the best model using Azure Container Instance (ACI) deployment option and enable authentication

<p align="center">
<img src="https://user-images.githubusercontent.com/68206315/104123895-ef75e400-534d-11eb-836f-7a70154ec3f2.png">
</p>

4. Enable Applications Insights using Python SDK by running the logs.py script

<p align="center">
<img src="https://user-images.githubusercontent.com/68206315/104123991-79be4800-534e-11eb-97de-8ab4f805b00b.png">
</p>

5. Enable logging to review important log information about service when consuming the model

<p align="center">
<img src="https://user-images.githubusercontent.com/68206315/104124004-8e9adb80-534e-11eb-9816-fbc0be616aa2.png">
</p>

6. Run swagger.sh and serve.py scripts to get docker running locally and serving swagger in order to interact with the deployed model Documentation. Here is the Swager UI showing the HTTP API methods and responses for the model

<p align="center">
<img src="https://user-images.githubusercontent.com/68206315/104124169-927b2d80-534f-11eb-83ca-e5f6155b0728.png">
</p>

<p align="center">
<img src="https://user-images.githubusercontent.com/68206315/104124083-fbae7100-534e-11eb-9d1d-53e409368f52.png">
</p>

7. Consume the model by running endpoint.py script which has been updated with the endpoint URL and Primary key authentication type. This produces a JSON output from the model

<p align="center">
<img src="https://user-images.githubusercontent.com/68206315/104124251-146b5680-5350-11eb-9b40-0876f1bebc88.png">
</p>

8. Benchmarking HTTP APIs is used to find the average response time for a deployed model. Here Apache Benchmark runs against HTTP API using authentication keys to retrieve performance results.

<p align="center">
<img src="https://user-images.githubusercontent.com/68206315/104127123-a1b6a700-5360-11eb-9309-ab10ee3382ce.png">
</p>

9. Run the Jupyter Notebook to create the pipeline and ensure the process is completed

<p align="center">
<img src="https://user-images.githubusercontent.com/68206315/104124702-817feb80-5352-11eb-8ef8-07c2661c06ad.png">
</p>

<p align="center">
<img src="https://user-images.githubusercontent.com/68206315/104124799-fd7a3380-5352-11eb-8517-3386bb2bac40.png">
</p>

10. The Bankmarketing dataset with the AutoML module

<p align="center">
<img src="https://user-images.githubusercontent.com/68206315/104124577-e71fa800-5351-11eb-87d4-8a55eb6eb744.png">
</p>

11. The “Published Pipeline overview” showing a REST endpoint and a status of ACTIVE

<p align="center">
<img src="https://user-images.githubusercontent.com/68206315/104124567-dcfda980-5351-11eb-8fe0-24a9ba792e51.png">
</p>

12. Consume and publish the API using Azure SDK

<p align="center">
<img src="https://user-images.githubusercontent.com/68206315/104125304-20f2ad80-5356-11eb-95f2-0e3b8c0e51d7.png">
</p>

13. Here is ML studio showing the scheduled run

<p align="center">
<img src="https://user-images.githubusercontent.com/68206315/104125597-22bd7080-5358-11eb-89bb-479d571e408c.png">
</p>

14. Status of RunDetails Widget

<p align="center">
<img src="https://user-images.githubusercontent.com/68206315/104124973-35ce4180-5354-11eb-9358-a1c39d2778f6.png">
</p>

## Future work

1. Solving the dataset imbalance will improve the accuracy of the model.

2. Increasing the number of cross validation can help in achieving better accuracy.

3. A better performing model can be detected by the AutoML feature if the duration of the exit criterion is increased.
