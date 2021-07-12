# Operationalizing Machine Learning

*TODO:* Write an overview to your project.

## Architectural Diagram (reference to Lessen 1 Intro to Azure ML)
![image](https://user-images.githubusercontent.com/35376272/125314000-a72e8300-e2ea-11eb-84ef-5599e52953d1.png)

## Key Steps
Step 1: Authentication
I am using the lab Udacity, so I skip this step since I am not authorized to create a security principal. 
Step 2: Automated ML Experiment
I first Create a new ML run

![Capture_mlrun](https://user-images.githubusercontent.com/35376272/125310154-30dc5180-e2e7-11eb-94f0-994ac265d07c.PNG)

I selected the bankmarketing dataset, which I think it was previously registered.

![Capture_dataset](https://user-images.githubusercontent.com/35376272/125310491-7ac53780-e2e7-11eb-870d-9517ef309b85.PNG)

I configure the new compute cluster follow the project requirements (Standard_DS12_v2) and select 1 as minimum nodes.
And run the experiment using classification, I have checked the "explain best model", I have modified the exit critiria from 6 hours to 1 hour. I have checked the concurrency to make sure it is 5. Once the experiment is finished, it is shown as below:

![Capture_completerun](https://user-images.githubusercontent.com/35376272/125312445-1dca8100-e2e9-11eb-89f6-cc557b014994.PNG)

And the information of the best model can be found. It is votingEnsemble with accuracy of 0.91775.
![Capture_bestmodel](https://user-images.githubusercontent.com/35376272/125312626-4eaab600-e2e9-11eb-81d1-cda0d3e45de4.PNG)
![Capture_bestmodel_detail](https://user-images.githubusercontent.com/35376272/125312647-52d6d380-e2e9-11eb-9dc1-3e78a9e968b9.PNG)
![runwithbestmodel](https://user-images.githubusercontent.com/35376272/125313010-ac3f0280-e2e9-11eb-8a39-0fa927f95cbe.PNG)

Step 3: Deploy the Best Model. Select the run of the best model, (which is Run 106 here) deploy the model and select the "enable authentication". Make sure that deploy the model using ACI. All of these selections are done in the configuration panel.
![Capture_deployenableauthentication](https://user-images.githubusercontent.com/35376272/125313103-c4af1d00-e2e9-11eb-8751-22867f206aae.PNG)

Step 4: Enable Application Insights
Now that the Best Model is deployed, enable Application Insights and retrieve logs. Although I found it is very convienent to configure it at deploy time with a check-box, but we are requested to run code that will enable it as part of the project. I run the log.py and enable application insigts by code "service.update(enable_app_insights=True)".
I found that the deplyment is not very stable , since the status kept changing from "healthy" to "transitioning" after I run the log.py. Not sure the reason behind it.

![Capture_loginfo](https://user-images.githubusercontent.com/35376272/125315167-b104b600-e2eb-11eb-8ee0-a4d3a8d28aec.PNG)

![Capture_applicationinsight](https://user-images.githubusercontent.com/35376272/125315124-a8ac7b00-e2eb-11eb-891c-756327c4992d.PNG)

Step 5: Swagger Documentation
In this step, I will consume the deployed model using Swagger. First I need to download the a Swagger JSON file for deployed models provided by Azure. And make sure  the file is located in the same folder as serve.py and swagger.sh. I have ran into "It works" empty webpage problem, it turns out I need to change the port number to 9000 in swagger.sh. It very important to do so docker run -p 9000:8080 swaggerapi/swagger-ui
![Capture_swaggermymodel](https://user-images.githubusercontent.com/35376272/125317838-27a2b300-e2ee-11eb-9a51-20bcad6b428d.PNG)
![Capture_swaggerrun](https://user-images.githubusercontent.com/35376272/125317856-2bced080-e2ee-11eb-8b31-348dd6d6b024.PNG)
![Capture_post](https://user-images.githubusercontent.com/35376272/125317862-2d989400-e2ee-11eb-954b-9e01af1e9390.PNG)
![Capture_swaggerget](https://user-images.githubusercontent.com/35376272/125317875-2ffaee00-e2ee-11eb-938a-1f847aa385e6.PNG)

Step 6: Consume Model Endpoints
Once the model is deployed, I run the endpoint.py script provided to interact with the trained model.I need to modify both the scoring_uri and the key in the script.
I have some issue here: I kept having 502 error
![image](https://user-images.githubusercontent.com/35376272/125324778-13ae7f80-e2f5-11eb-97b6-663e1502d5e5.png)
maybe anyone can give me a hint here.

Step 7: Create, Publish and Consume a Pipeline
I uploaded the aml-pipelines-with-automated-machine-learning-step Jupyter Notebook to Azure mlStudio, then all the parameters are updated accordingly.
![image](https://user-images.githubusercontent.com/35376272/125335291-3f376700-e301-11eb-9630-03fe33a3341e.png)


## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.

