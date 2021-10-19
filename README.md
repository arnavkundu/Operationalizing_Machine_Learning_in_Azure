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
This project enables operationalizing a ML model in Azure as a part of Udacity Nanodegree course. In the previous project we learnt about optimizing the ML model in Azure. the deployement of the model was done using a service in Azure. In this project the model was trained using AutoML feature in Azure that allows running of a significant number of models and then allowing the user to chose the model that needs to be deployed (obviously the best model!). The model is consumed through an endpoint using Swagger.

## Architectural Diagram

![image](https://user-images.githubusercontent.com/38326274/137786806-df9d1c40-4ab4-4a4b-8795-10fe72558eed.png)


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
   
   *Model Name and type*
      ![image](https://user-images.githubusercontent.com/38326274/137479333-64d47c75-680f-45bd-9f6a-e321df796eb1.png)
      
   *Metric group 1 for best model*
      ![image](https://user-images.githubusercontent.com/38326274/137479437-fd1f4bec-6d26-4f9c-a049-0777a9103dbc.png)

   *Metric group 2 for best model*
      ![image](https://user-images.githubusercontent.com/38326274/137479654-70a7079c-3608-4fd7-9c6b-b869202fafb5.png)

   *Metric group 3 for best model*
      ![image](https://user-images.githubusercontent.com/38326274/137479754-6f6764b2-f18c-4b5d-b3be-8a2c56bc9022.png)


### Step 3: Deploy the best model

  **Selecting the best model**
    ![image](https://user-images.githubusercontent.com/38326274/137480275-5bb97e78-f74a-4b31-9d9d-28aee41c9082.png)

  **Clicking on Deploy** [Deployed on Azure contianer Instance withauthentication ON]
    ![image](https://user-images.githubusercontent.com/38326274/137480332-120e33b1-570f-4c0e-9d81-43dfcab76453.png)

  **Enter the relevant parameters and click on deploy**
    ![image](https://user-images.githubusercontent.com/38326274/137480446-685f61b8-fe95-42fd-960d-ab31fc5f9a42.png)

  **Deployment successful**
    ![image](https://user-images.githubusercontent.com/38326274/137482366-f3304e35-0aa0-4de8-ba38-6e184c4f9e59.png)

  **Deployment State**
    ![image](https://user-images.githubusercontent.com/38326274/137482512-ea49f047-3599-4907-8990-9b653546aae0.png)
    ![image](https://user-images.githubusercontent.com/38326274/137482840-0d58d00f-5d64-433a-8700-6065f63f0ada.png)


    
### Step 4: Enable logging

  **Run the logs.py file in Git bash**
  ![image](https://user-images.githubusercontent.com/38326274/137484220-abe01208-580a-48e8-b7a1-37b850cc46ed.png)

  **Once we run the logs.py we enable the Application insight and get the URL**
  ![image](https://user-images.githubusercontent.com/38326274/137485366-ddc6d99e-ddbb-46ed-9ef5-dd1bfea63d85.png)


### Step 5: Swagger Documentation

  **Running the swagger.sh"
  ![image](https://user-images.githubusercontent.com/38326274/137497124-ad63c187-027d-43d6-a936-8f5b18b2d8a8.png)
  
  **opening localhost:9001"
  ![image](https://user-images.githubusercontent.com/38326274/137497240-1682eaf7-6cbe-4494-a4ee-c01177c4f957.png)

  **Pointing to Swagger JSON**
  ![image](https://user-images.githubusercontent.com/38326274/137497742-b5e870e3-7b00-4dcd-afa7-b6406812ba69.png)
  **

### Step 6: Consume model endpoints
  Finally we will test the model endpoint by running the endpoints.py file. The scoring URI and the key needs to be the one which is mentioned in the detail page of the endpoint page in Azure. Once it is run it will look something like:
  
  ![image](https://user-images.githubusercontent.com/38326274/137760452-8fbcc021-0118-46c7-99c9-41da23f78dfa.png)


### Step 7: Create and publish a pipeline
   For this we will use the Jupyter file and run the cells to complete this step.
   
   ML studio showing the scheduled run
   ![image](https://user-images.githubusercontent.com/38326274/137980409-1210ec35-e258-4952-8789-7abc81d1c44a.png)

   Pipeline section of ML Azure Studio
   ![image](https://user-images.githubusercontent.com/38326274/137767728-6711e46f-87a9-4c54-a80e-84b526af3af5.png)
   
   Pipeline Endpoint
   ![image](https://user-images.githubusercontent.com/38326274/137767834-5b5b4c08-a699-4d7f-8d62-fa94c8c9257c.png)

   Published Pipeline Overview with ACTIVE STATUS
   ![image](https://user-images.githubusercontent.com/38326274/137768016-491aa14d-d5d0-4b48-acc1-06e3007d82b6.png)

   Run details Snippets
   ![image](https://user-images.githubusercontent.com/38326274/137768239-f66ba926-c253-4d7c-97fe-ab890d457056.png)


   
## Screen Recording
Link to Screencast(https://github.com/arnavkundu/Operationalizing_Machine_Learning_in_Azure/blob/main/Screencast/ScreenCast.mp4)

## Future work
  In future experiments I would like to explore the following ideas to enable better prediction on the dataset so that we improve on the AUC as well as the accuracy in a holistic way

   - Using techniques like SMOTE to oversample the data making sure that we don't bias the data: Using SMOTE, we will be generating synthetic samples for the minority class and using the k-NN based oversampling, we can create some synthetic data points in the close vicinity of other data points so that we attain a class balance.
   - Using undersampling techniques like NearMiss to reduce the imbalance. This helps in improving the model by removing some sample points from the majority class so as to increase the gaps between 2 classes. Near-neighbour method also takes care of lesser information loss during undersampling.
   - Understanding other metrics to look into the aspect of evaluating the model like Precision/Recall/F1 score and also understand if precision is of more importance or recall (of course getting in touch with business stakeholders to know their focus area) and try to focus our model's development in that direction. This will enable us to be closer to the business case solving hence improving adaptibility by business.

  Another point which I saw during the run was feature engineering, and would like to try out the feature in AzureML as a future Work scope.
