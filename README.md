# Your Project Title Here

*TODO:* Write an overview to your project.

## Architectural Diagram
*TODO*: Provide an architectual diagram of the project and give an introduction of each step. An architectural diagram is an image that helps visualize the flow of operations from start to finish. In this case, it has to be related to the completed project, with its various stages that are critical to the overall flow. For example, one stage for managing models could be "using Automated ML to determine the best model". 

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


## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.

