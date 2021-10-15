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

   **Run Complete** [The best model is the voting ensemble model with weighted AUC as ~0.948]
      ![image](https://user-images.githubusercontent.com/38326274/137478957-59add80a-7152-4736-8ffb-f593e8c4dc52.png)

   **Best model**
      
      - *Model Name and type*
      ![image](https://user-images.githubusercontent.com/38326274/137479333-64d47c75-680f-45bd-9f6a-e321df796eb1.png)
      
      - *Metric group 1 for best model*
      ![image](https://user-images.githubusercontent.com/38326274/137479437-fd1f4bec-6d26-4f9c-a049-0777a9103dbc.png)

      - *Metric group 2 for best model*
      ![image](https://user-images.githubusercontent.com/38326274/137479654-70a7079c-3608-4fd7-9c6b-b869202fafb5.png)

      - *Metric group 3 for best model*
      ![image](https://user-images.githubusercontent.com/38326274/137479754-6f6764b2-f18c-4b5d-b3be-8a2c56bc9022.png)


### Step 3: Deploy the best model

    - **Selecting the best model**
    ![image](https://user-images.githubusercontent.com/38326274/137480275-5bb97e78-f74a-4b31-9d9d-28aee41c9082.png)

    - **Clicking on Deploy** [Deployed on Azure contianer Instance withauthentication ON]
    ![image](https://user-images.githubusercontent.com/38326274/137480332-120e33b1-570f-4c0e-9d81-43dfcab76453.png)

    - **Enter the relevant parameters and click on deploy**
    ![image](https://user-images.githubusercontent.com/38326274/137480446-685f61b8-fe95-42fd-960d-ab31fc5f9a42.png)

    - **Deployment successful**
    ![image](https://user-images.githubusercontent.com/38326274/137482366-f3304e35-0aa0-4de8-ba38-6e184c4f9e59.png)

    - **Deployment State**
    ![image](https://user-images.githubusercontent.com/38326274/137482512-ea49f047-3599-4907-8990-9b653546aae0.png)

    
### Step 4: Enable logging


### Step 5: Swagger Documentation


### Step 6: Consume model endpoints


#### (Optional) Benchmark

### Step 7: Create and publish a pipeline


## Screen Recording
[Youtube Link]()

## Future work
