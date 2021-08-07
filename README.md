# Operationalizing Machine Learning

The running project code is in the file operationalizing_ml.ipynb which is based on the starter code file starter_files/aml-pipelines-with-automated-machine-learning-step.ipynb
This project comprises of operationalizing Machine Learning in Microsoft Azure.
A classification model is trained and deployed. The deployed model endpoint URI can later be used to make predictions
A pipeline is also created, published and consumed. The published pipeline endpoint URI can later be used to initiate a new run.

## Architectural Diagram
![image](https://user-images.githubusercontent.com/17679107/128580722-fe579b49-1fbb-4416-bcac-cdd357cb0942.png)

## Suggestions for improvement
1. Consider implementing one or more stand out suggestions
2. Research and use balanced data to improve the outcome of the predictions
3. Version the pipelines. This would allow development of new models while customers continue to use the existing version

## Key Steps
## Step 2: Automated ML Experiment
This step allows a model to be trained across different algorithms/parameters and highlights the best model
1. An Azure ML Dataset is created and registered if it does not already exist from the URL for Marketing Bank data.

![image](https://user-images.githubusercontent.com/17679107/128581444-5b38a755-b62a-411a-8a31-b2d18c7464ef.png)

2. A Compute cluster is created if it does not already exist
3. An AtoML configuration is specified with key information such as the best metric to use, the column label, etc.
4. A run is then submitted to train the model. Once the experiment/run is completed, the best model is identified.

![image](https://user-images.githubusercontent.com/17679107/128581670-9ea69c86-5994-435e-8dd4-fada48bf36c0.png)
![image](https://user-images.githubusercontent.com/17679107/128581678-737b45b4-c08d-4273-9438-c17aef46914d.png)
![image](https://user-images.githubusercontent.com/17679107/128584944-13b9800a-534d-4b5f-9ce4-e3107953b6b8.png)

## Step 3: Deploy the best model
In this step, we use the Azure ML Studio U/I to deploy the best model. We use ACI (Azure Container Instance) with authentication enabled.

## Step 4. Enable logging
Logging helps troubleshoot and understanding the workflow. It also helps with quantifying performance at various stages of the execution. The WebServcie is used to enable/disable Application Insights.

![image](https://user-images.githubusercontent.com/17679107/128584962-10ebb48e-dcce-460c-a2df-a0c6e1814db0.png)

Sample output of the logs that are available once application insight is enabled.

![image](https://user-images.githubusercontent.com/17679107/128584977-07130de5-cbb1-4ab1-ae97-871fe17ebcf7.png)



## Step 5. Swagger Doc
Once a model is published, Azure ML exposes a swagger.json file. This can be consumed by Swagger and helps with the documentation of the methods that are exposed together with the JSON payloads for input/output. This makes it much easier to start consuming the endpoint.

![image](https://user-images.githubusercontent.com/17679107/128585201-c30da670-2dfd-4198-b78c-af8c0af81f7a.png)
![image](https://user-images.githubusercontent.com/17679107/128585210-7c62272d-7e88-4e33-8b1f-cf5998eba113.png)
![image](https://user-images.githubusercontent.com/17679107/128585220-f21e45ae-1fd2-4d66-aefb-ed2734af325b.png)
![image](https://user-images.githubusercontent.com/17679107/128585235-bf724759-b982-476f-9c6f-e686f609b3d7.png)


## Step 6. Consume model endpoints
The model endpoint is consumed by making a REST API call to the scoring URI. If authentication is enabled, the key must also be provide. The output of such a model invocation is displayed below.

![image](https://user-images.githubusercontent.com/17679107/128585397-1b0ed104-df8d-4101-94b6-7d28dd4ef334.png)



## Step 7. Create and publish pipeline
1. A pipeline is created when it is "run in the context of an experiment. The pipeline can also be visualized in the Pipelines section of Azure ML Studio

![image](https://user-images.githubusercontent.com/17679107/128585471-e8f37b05-b641-43d0-9f00-e2eee0412377.png)

2. Once a pipeline is published, a pipeline endpoint is generated and may be accessed from Azure ML Studio under the 'Pipeline Endpoint' tab

![image](https://user-images.githubusercontent.com/17679107/128585479-18af2d38-f5b4-4158-9b8e-f74899f8ab81.png)

3. Review of the pipeline from Azure ML studio showing the bank marketing dataset and the AutoML module

![image](https://user-images.githubusercontent.com/17679107/128585585-813d1250-08ff-447f-b964-4412041bbf33.png)

4. Once published, the Pipeline Details tab will show the published pipeline status (Active in this case) and also the pipeline REST endpoint that can be called to "run" the pipeline.

![image](https://user-images.githubusercontent.com/17679107/128585501-d1cca096-e3ca-4adf-83d5-08a9c1f6a34d.png)

5. The RunDetails widget asynchronously displays the run details in the Notebook as the pipeline run progresses.

![image](https://user-images.githubusercontent.com/17679107/128585661-f524f924-e6f1-4129-9e79-3586013ecf4c.png)

6. A pipeline run stats (Scheduled, Completed, etc.) can be reviewed in Azure ML Studio in the Pipelines section

![image](https://user-images.githubusercontent.com/17679107/128585674-8a9a075b-59d7-4db3-8cff-f948926f3c83.png)



## Screen Recording
[Project Screencast](https://drive.google.com/file/d/1ATN5RPttjm1xlc9htaBOFCGPFaAHfoE8/view?usp=sharing)
## 

