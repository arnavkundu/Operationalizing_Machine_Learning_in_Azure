# Operationalizing Machine Learning in Azure

## Table of Contents
   * [Overview](#overview)
   * [Architectural Diagram](#architectural-diagram)
   * [Key Steps](#key-steps)
       * [Step 1: Authentication](#authentication)
       * [Step 2: Automated ML Experiment](#automated-ml-experiment)
       * [Step 3: Deploy the best model](#deploy-the-best-model)
       * [Step 4: Enable logging](#enable-logging)
       * [Step 5: Swagger Documentation](#swagger-documentation)
       * [Step 6: Consume model endpoints](#consume-model-endpoints)
       * [Step 7: Create and publish a pipeline](#create-and-publish-a-pipeline)
   * [Screen Recordin](#screen-recording)
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
### Authentication
The udacity lab was used, hence this step was skipped as it was mentioned that it will NOT affect other steps in the project and we will be using the workspace provided by Udacity.

### Step 1: Automated ML Experiment


### Step 2: Deploy the best model


### Step 3: Enable logging


### Step 4: Swagger Documentation


### Step 5: Consume model endpoints


#### (Optional) Benchmark

### Step 6: Create and publish a pipeline


## Screen Recording
[Youtube Link](https://www.youtube.com/embed/xXjspFEyZnY)
<!--[Subtitles](https://drive.google.com/file/d/1urtaKvpkmQr-1t5N8SGM42FD4NZKKts_/view?usp=sharing)-->

## Future work
