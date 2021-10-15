# Operationalizing Machine Learning in Azure

## Table of Contents
   * [Overview](#overview)
   * [Architectural Diagram](#architectural-diagram)
   * [Key Steps](#key-steps)
       * [Step 1: Authentication](#step-1-authentication)
       * [Step 2: Automated ML Experiment](#step-2-automated-ml-experiment)
       * [Step 3: Deploy the best model](#step-3-deploy-the-best-model)
       * [Step 4: Enable logging](#step-4-enable-logging)
       * [Step 5: Swagger Documentation](#step-5-swagger-documentation)
       * [Step 6: Consume model endpoints](#step-6-consume-model-endpoints)
       * [Step 7: Create and publish a pipeline](#step-7-create-and-publish-a-pipeline)
   * [Screen Recording](#screen-recording)
   * [Future work](#Future-work)
   * [Proof of Cluster Clean Up](#Proof-of-Cluster-Clean-Up)

## Overview
This project enables operationalizing a ML model in Azure as a part of Udacity Nanodegree course. In the previous project we learnt about optimizing the ML model in Azure

## Architectural Diagram
## Key Steps
1. **Authentication** : Skipping this step as it will NOT affect other steps in the project and we will be using the workspace provided by Udacity.
2. **Automated ML Experiment** : In this step, security is enabled and authentication is completed. In this step, we create an experiment using Automated ML, configure a compute cluster, and use that cluster to run the experiment
3. **Deploy the best model** : After the experiment run completes, a summary of all the models and their metrics are shown, including explanations. Deploying the Best Model will allow to interact with the HTTP API service and interact with the model by sending data over POST requests.
4. **Enable logging** : Now that the Best Model is deployed, enable Application Insights and retrieve logs. Although this is configurable at deploy time with a check-box, it is useful to be able to run code that will enable it for you.
5. **Swagger Documentation** : In this step, deployed model is consumed using Swagger.
6. **Consume model endpoints** : Once the model is deployed, use the endpoint.py script provided to interact with the trained model. In this step, you need to run the script, modifying both the scoring_uri and the key to match the key for your service and the URI that was generated after deployment.
7. **Create and publish a pipeline** : In this step, workflow is automated by creating a pipeline with the Python SDK.


### Step 1: Authentication
The udacity lab was used, hence this step was skipped as it was mentioned that it will NOT affect other steps in the project and we will be using the workspace provided by Udacity.

### Step 2: Automated ML Experiment
   **Uploading the Dataset**
      ![image](https://user-images.githubusercontent.com/38326274/137475242-15fa77f9-1b0b-45da-8d24-0daf261105f8.png)
   
   **Dataset uploaded**
      ![image](https://user-images.githubusercontent.com/38326274/137475376-d28c282d-aec6-4c83-bd5b-f95727c1bd1c.png)
   
   **Selecting the dataset**
      ![image](https://user-images.githubusercontent.com/38326274/137475496-35d9302a-b771-4bef-b579-3b65418d8e24.png)
   
   **Selecting the compute cluster** [Standard DS12 v2 cluster is chosen]
      ![image](https://user-images.githubusercontent.com/38326274/137475795-f31166a7-9f8b-40e4-9eb4-77b23744b3a7.png)
   
   **Run configuration** [Chose AUC weighted as we know that the dataset has class imbalance]
      ![image](https://user-images.githubusercontent.com/38326274/137476184-196809b0-0813-4bcd-857f-e0c49c6f3a28.png)
   
   **Additional Configurations**
      ![image](https://user-images.githubusercontent.com/38326274/137476496-4ae85f6e-a489-43bb-9a03-4aec1598067f.png)
   
   **Run the experiment**
      ![image](https://user-images.githubusercontent.com/38326274/137476624-edc1484a-10bb-477c-819f-e21cb0231795.png)


### Step 3: Deploy the best model


### Step 4: Enable logging


### Step 5: Swagger Documentation


### Step 6: Consume model endpoints


#### (Optional) Benchmark

### Step 7: Create and publish a pipeline


## Screen Recording
[Youtube Link]()

## Future work
