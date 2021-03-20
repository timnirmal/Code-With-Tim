# Use automated machine learning in Azure Machine Learning

## Introduction

100 XP

* 1 minute

_Machine Learning_ is the foundation for most artificial intelligence solutions, and the creation of an intelligent solution often begins with the use of machine learning to train a predictive model using historic data that you have collected.

_Azure Machine Learning_ is a cloud service that you can use to train and manage machine learning models.

In this module, you'll learn how to:

* Identify different kinds of machine learning model.
* Use the automated machine learning capability of Azure Machine Learning to train and deploy a predictive model.

To complete this module, you'll need a Microsoft Azure subscription. If you don't already have one, you can sign up for a free trial at [https://azure.microsoft.com](https://azure.microsoft.com/).

## What is machine learning?

100 XP

* 5 minutes

Machine learning is a technique that uses mathematics and statistics to create a model that can predict unknown values.

![Adventure Works cycle rental location, on a cloudy day in January](https://docs.microsoft.com/en-us/learn/wwl-data-ai/use-automated-machine-learning/media/adventureworks.png)

For example, suppose _Adventure Works Cycles_ is a business that rents cycles in a city. The business could use historic data to train a model that predicts daily rental demand in order to make sure sufficient staff and cycles are available.

To do this, Adventure Works could create a machine learning model that takes information about a specific day \(the day of week, the anticipated weather conditions, and so on\) as an input, and predicts the expected number of rentals as an output.

Mathematically, you can think of machine learning as a way of defining a function \(let's call it _**f**_\) that operates on one or more _features_ of something \(which we'll call _**x**_\) to calculate a predicted _label_ \(_**y**_\) - like this:

_**f\(x\) = y**_

In this bicycle rental example, the details about a given day \(day of the week, weather, and so on\) are the _features_ \(_**x**_\), the number of rentals for that day is the _label_ \(_**y**_\), and the function \(_**f**_\) that calculates the number of rentals based on the information about the day is encapsulated in a machine learning model.

The specific operation that the _**f**_ function performs on _x_ to calculate _y_ depends on a number of factors, including the type of model you're trying to create and the specific algorithm used to train the model. Additionally in most cases, the data used to train the machine learning model requires some pre-processing before model training can be performed.

The following video discusses the various kinds of machine learning model you can create, and the process generally followed to train and use them.

### Azure Machine Learning <a id="azure-machine-learning"></a>

Training and deploying an effective machine learning model involves a lot of work, much of it time-consuming and resource-intensive. Azure Machine Learning is a cloud-based service that helps simplify some of the tasks and reduce the time it takes to prepare data, train a model, and deploy a predictive service. In the rest of this unit, you'll explore Azure Machine Learning, and in particular its _automated machine learning_ capability.  


## Create an Azure Machine Learning workspace

100 XP

* 5 minutes

Data scientists expend a lot of effort exploring and pre-processing data, and trying various types of model-training algorithms to produce accurate models, which is time consuming, and often makes inefficient use of expensive compute hardware.

Azure Machine Learning is a cloud-based platform for building and operating machine learning solutions in Azure. It includes a wide range of features and capabilities that help data scientists prepare data, train models, publish predictive services, and monitor their usage. Most importantly, it helps data scientists increase their efficiency by automating many of the time-consuming tasks associated with training models; and it enables them to use cloud-based compute resources that scale effectively to handle large volumes of data while incurring costs only when actually used.

### Create an Azure Machine Learning workspace <a id="create-an-azure-machine-learning-workspace"></a>

To use Azure Machine Learning, you create a _workspace_ in your Azure subscription. You can then use this workspace to manage data, compute resources, code, models, and other artifacts related to your machine learning workloads.

 Note

This module is one of many that make use of an Azure Machine Learning workspace, including the other modules in the [Create no-code predictive models with Azure Machine Learning](https://docs.microsoft.com/en-us/learn/paths/create-no-code-predictive-models-azure-machine-learning/) learning path. If you are using your own Azure subscription, consider creating the workspace once and reusing it in other modules. After completing each module, be sure to follow the **Clean Up** instructions at the end of the module to stop compute resources.

If you don't already have one, follow these steps to create a workspace:

1. Sign into the [Azure portal](https://portal.azure.com/) using the Microsoft credentials associated with your Azure subscription.
2. Select **＋Create a resource**, search for _Machine Learning_, and create a new **Machine Learning** resource the following settings:
   * **Subscription**: _Your Azure subscription_
   * **Resource group**: _Create or select a resource group_
   * **Workspace name**: _Enter a unique name for your workspace_
   * **Region**: _Select the geographical region closest to you_
   * **Storage account**: _Note the default new storage account that will be created for your workspace_
   * **Key vault**: _Note the default new key vault that will be created for your workspace_
   * **Application insights**: _Note the default new application insights resource that will be created for your workspace_
   * **Container registry**: None \(_one will be created automatically the first time you deploy a model to a container_\)
3. Wait for your workspace to be created \(it can take a few minutes\). Then go to it in the portal.
4. On the **Overview** page for your workspace, launch Azure Machine Learning studio \(or open a new browser tab and navigate to [https://ml.azure.com](https://ml.azure.com/)\), and sign into Azure Machine Learning studio using your Microsoft account. If prompted, select your Azure directory and subscription, and your Azure Machine Learning workspace.
5. In Azure Machine Learning studio, toggle the ☰ icon at the top left to view the various pages in the interface. You can use these pages to manage the resources in your workspace.

You can manage your workspace using the Azure portal, but for data scientists and Machine Learning operations engineers, Azure Machine Learning studio provides a more focused user interface for managing workspace resources.

## Create compute resources

100 XP

* 3 minutes

After you have created an Azure Machine Learning workspace, you can use it to manage the various assets and resources you need to create machine learning solutions. At its core, Azure Machine Learning is a platform for training and managing machine learning models, for which you need compute on which to run the training process.

### Create compute targets <a id="create-compute-targets"></a>

Compute targets are cloud-based resources on which you can run model training and data exploration processes.

1. In [Azure Machine Learning studio](https://ml.azure.com/), view the **Compute** page \(under **Manage**\). This is where you manage the compute targets for your data science activities. There are four kinds of compute resource you can create:
   * **Compute Instances**: Development workstations that data scientists can use to work with data and models.
   * **Compute Clusters**: Scalable clusters of virtual machines for on-demand processing of experiment code.
   * **Inference Clusters**: Deployment targets for predictive services that use your trained models.
   * **Attached Compute**: Links to existing Azure compute resources, such as Virtual Machines or Azure Databricks clusters.
2. On the **Compute Instances** tab, add a new compute instance with the following settings. You'll use this as a workstation from which to test your model:
   * **Virtual Machine type**: CPU
   * **Virtual Machine size**: Standard\_DS11\_v2 \(Choose **Select from all options** to search for and select this machine size\)
   * **Compute name**: _enter a unique name_
   * **Enable SSH access**: Unselected
3. While the compute instance is being created, switch to the **Compute Clusters** tab, and add a new compute cluster with the following settings. You'll use this to train a machine learning model:
   * **Virtual Machine priority**: Dedicated
   * **Virtual Machine type**: CPU
   * **Virtual Machine size**: Standard\_DS11\_v2 \(Choose **Select from all options** to search for and select this machine size\)
   * **Compute name**: _enter a unique name_
   * **Minimum number of nodes**: 0
   * **Maximum number of nodes**: 2
   * **Idle seconds before scale down**: 120
   * **Enable SSH access**: Unselected

 Note

If you decide not to complete this module, be sure to stop your compute instance to avoid incurring unnecessary charges to your Azure subscription.

The compute targets will take some time to be created. You can move onto the next unit while you wait.



## Explore data

100 XP

* 3 minutes

Machine learning models must be trained with existing data. In this case, you'll use a dataset of historical bicycle rental details to train a model that predicts the number of bicycle rentals that should be expected on a given day, based on seasonal and meteorological features.

### Create a dataset <a id="create-a-dataset"></a>

In Azure Machine Learning, data for model training and other operations is usually encapsulated in an object called a _dataset_.

1. View the comma-separated data at [https://aka.ms/bike-rentals](https://aka.ms/bike-rentals) in your web browser. Then save this as a local file named **daily-bike-share.csv** \(it doesn't matter where you save it\).
2. In [Azure Machine Learning studio](https://ml.azure.com/), view the **Datasets** page. Datasets represent specific data files or tables that you plan to work with in Azure ML.
3. Create a new dataset from local files, using the following settings:
   * **Basic Info**:
     * **Name**: bike-rentals
     * **Dataset type**: Tabular
     * **Description**: Bicycle rental data
   * **Datastore and file selection**:
     * **Select or create a datastore**: Currently selected datastore
     * **Select files for your dataset**: Browse to the **daily-bike-share.csv** file you downloaded.
     * **Upload path**: _Leave the default selection_
     * **Skip data validation**: Not selected
   * **Settings and preview**:
     * **File format**: Delimited
     * **Delimiter**: Comma
     * **Encoding**: UTF-8
     * **Column headers**: Use headers from first file
     * **Skip rows**: None
   * **Schema**:
     * Include all columns other than **Path**
     * Review the automatically detected types
   * **Confirm details**:
     * Do not profile the dataset after creation
4. After the dataset has been created, open it and view the **Explore** page to see a sample of the data. This data contains historical features and labels for bike rentals.

> **Citation**: _This data is derived from_ [_Capital Bikeshare_](https://www.capitalbikeshare.com/system-data) _and is used in accordance with the published data_ [_license agreement_](https://www.capitalbikeshare.com/data-license-agreement)_._

\_\_

## Train a machine learning model

100 XP

* 15 minutes

Azure Machine Learning includes an _automated machine learning_ capability that leverages the scalability of cloud compute to automatically try multiple pre-processing techniques and model-training algorithms in parallel to find the best performing supervised machine learning model for your data.

 Note

The automated machine learning capability in Azure Machine Learning supports _supervised_ machine learning models - in other words, models for which the training data includes known label values. You can use automated machine learning to train models for:

* **Classification** \(predicting categories or _classes_\)
* **Regression** \(predicting numeric values\)
* **Time series forecasting** \(regression with a time-series element, enabling you to predict numeric values at a future point in time\)

### Run an automated machine learning experiment <a id="run-an-automated-machine-learning-experiment"></a>

In Azure Machine Learning, operations that you run are called _experiments_. Follow the steps below to run an experiment that uses automated machine learning to train a regression model that predicts bicycle rentals.

1. In [Azure Machine Learning studio](https://ml.azure.com/), view the **Automated ML** page \(under **Author**\).
2. Create a new Automated ML run with the following settings:
   * **Select dataset**:
     * **Dataset**: bike-rentals
   * **Configure run**:
     * **New experiment name**: mslearn-bike-rental
     * **Target column**: rentals \(_this is the label the model will be trained to predict\)_
     * **Training compute target**: _the compute cluster you created previously_
   * **Task type and settings**:
     * **Task type**: Regression _\(the model will predict a numeric value\)_
     * **Additional configuration settings:**
       * **Primary metric**: Select **Normalized root mean squared error** _\(more about this metric later!\)_
       * **Explain best model**: Selected - _this option causes automated machine learning to calculate feature importance for the best model; making it possible to determine the influence of each feature on the predicted label._
       * **Blocked algorithms**: _Block **all** other than **RandomForest** and **LightGBM** - normally you'd want to try as many as possible, but doing so can take a long time!_
       * **Exit criterion**:
         * **Training job time \(hours\)**: 0.25 - _this causes the experiment to end after a maximum of 15 minutes._
         * **Metric score threshold**: 0.08 - _this causes the experiment to end if a model achieves a normalized root mean squared error metric score of 0.08 or less._
     * **Featurization settings:**
       * **Enable featurization**: Selected - _this causes Azure Machine Learning to automatically preprocess the features before training._
3. When you finish submitting the automated ML run details, it will start automatically. Wait for the run status to change from _Preparing_ to _Running_.
4. When the run status changes to _Running_, view the **Models** tab and observe as each possible combination of training algorithm and pre-processing steps is tried and the performance of the resulting model is evaluated. The page will automatically refresh periodically, but you can also select **↻ Refresh**. It may take ten minutes or so before models start to appear, as the cluster nodes need to be initialized before training can begin.
5. Wait for the experiment to finish. It may take a while - now might be a good time for a coffee break!

### Review the best model <a id="review-the-best-model"></a>

After the experiment has finished; you can review the best performing model that was generated \(note that in this case, we used exit criteria to stop the experiment - so the "best" model found by the experiment may not be the best possible model, just the best one found within the time allowed for this exercise!\).

1. On the **Details** tab of the automated machine learning run, note the best model summary.
2. Select the **Algorithm name** for the best model to view its details.

   The best model is identified based on the evaluation metric you specified \(_Normalized root mean squared error_\). To calculate this metric, the training process used some of the data to train the model, and applied a technique called _cross-validation_ to iteratively test the trained model with data it wasn't trained with and compare the predicted value with the actual known value. The difference between the predicted and actual value \(known as the _residuals_\) indicates the amount of _error_ in the model, and this particular performance metric is calculated by squaring the errors across all of the test cases, finding the mean of these squares, and then taking the square root. What all of this means is that smaller this value is, the more accurately the model is predicting.

3. Next to the _Normalized root mean squared error_ value, select **View all other metrics** to see values of other possible evaluation metrics for a regression model.
4. Select the **Metrics** tab and select the **residuals** and **predicted\_true** charts if they are not already selected. Then review the charts, which show the performance of the model by comparing the predicted values against the true values, and by showing the _residuals_ \(differences between predicted and actual values\) as a histogram.

   The **Predicted vs. True** chart should show a diagonal trend in which the predicted value correlates closely to the true value. A dotted line shows how a perfect model should perform, and the closer the line for your model's average predicted value is to this, the better its performance. A histogram below the line chart shows the distribution of true values.

   ![Predicted vs True chart](https://docs.microsoft.com/en-us/learn/wwl-data-ai/use-automated-machine-learning/media/predicted-vs-true.png)

   The **Residual Histogram** shows the frequency of residual value ranges. Residuals represent variance between predicted and true values that can't be explained by the model - in other words, errors; so what you should hope to see is that the most frequently occurring residual values are clustered around 0 \(in other words, most of the errors are small\), with fewer errors at the extreme ends of the scale.

   ![Residuals histogram](https://docs.microsoft.com/en-us/learn/wwl-data-ai/use-automated-machine-learning/media/residual-histogram.png)

5. Select the **Explanations** tab. Click on the arrows &gt;&gt; next to **Explanation ID** to expand the explanations list. Select an explanation ID, select **View previous dashboard experience** on the right-hand side. Then select **Global Importance**. This chart shows how much each feature in the dataset influences the label prediction, like this:

   ![Feature importance](https://docs.microsoft.com/en-us/learn/wwl-data-ai/use-automated-machine-learning/media/feature-importance.png)



## Deploy a model as a service

100 XP

* 10 minutes

After you've used automated machine learning to train some models, you can deploy the best performing model as a service for client applications to use.

### Deploy a predictive service <a id="deploy-a-predictive-service"></a>

In Azure Machine Learning, you can deploy a service as an Azure Container Instances \(ACI\) or to an Azure Kubernetes Service \(AKS\) cluster. For production scenarios, an AKS deployment is recommended, for which you must create an _inference cluster_ compute target. In this exercise, you'll use an ACI service, which is a suitable deployment target for testing, and does not require you to create an inference cluster.

1. In [Azure Machine Learning studio](https://ml.azure.com/), on the **Automated ML** page, select the run for your automated machine learning experiment and view the **Details** tab.
2. Select the algorithm name for the best model. Then, on the **Model** tab, use the **Deploy** button to deploy the model with the following settings:
   * **Name**: predict-rentals
   * **Description**: Predict cycle rentals
   * **Compute type**: ACI
   * **Enable authentication**: Selected
3. Wait for the deployment to start - this may take a few seconds. Then, in the **Model summary** section, observe the **Deploy status** for the **predict-rentals** service, which should be **Running**. Wait for this status to change to **Successful**. You may need to select **↻ Refresh** periodically.
4. In Azure Machine Learning studio, view the **Endpoints** page and select the **predict-rentals** real-time endpoint. Then select the **Consume** tab and note the following information there. You need this information to connect to your deployed service from a client application.
   * The REST endpoint for your service
   * the Primary Key for your service
5. Note that you can use the ⧉ link next to these values to copy them to the clipboard.

### Test the deployed service <a id="test-the-deployed-service"></a>

Now that you've deployed a service, you can test it using some simple code.

1. With the **Consume** page for the **predict-rentals** service page open in your browser, open a new browser tab and open a second instance of [Azure Machine Learning studio](https://ml.azure.com/). Then in the new tab, view the **Notebooks** page \(under **Author**\).
2. In the **Notebooks** page, under **My files**, use the **🗋** button to create a new file with the following settings:
   * **File location**: Users/_your user name_
   * **File name**: Test-Bikes
   * **File type**: Notebook
   * **Overwrite if already exists**: Selected
3. When the new notebook has been created, ensure that the compute instance you created previously is selected in the **Compute** box, and that it has a status of **Running**.
4. Use the **≪** button to collapse the file explorer pane and give you more room to focus on the **Test-Bikes.ipynb** notebook tab.
5. In the rectangular cell that has been created in the notebook, paste the following code:PythonCopy

   ```text
   endpoint = 'YOUR_ENDPOINT' #Replace with your endpoint
   key = 'YOUR_KEY' #Replace with your key

   import json
   import requests

   #An array of features based on five-day weather forecast
   x = [[1,1,2022,1,0,6,0,2,0.344167,0.363625,0.805833,0.160446],
       [2,1,2022,1,0,0,0,2,0.363478,0.353739,0.696087,0.248539],
       [3,1,2022,1,0,1,1,1,0.196364,0.189405,0.437273,0.248309],
       [4,1,2022,1,0,2,1,1,0.2,0.212122,0.590435,0.160296],
       [5,1,2022,1,0,3,1,1,0.226957,0.22927,0.436957,0.1869]]

   #Convert the array to JSON format
   input_json = json.dumps({"data": x})

   #Set the content type and authentication for the request
   headers = {"Content-Type":"application/json",
           "Authorization":"Bearer " + key}

   #Send the request
   response = requests.post(endpoint, input_json, headers=headers)

   #If we got a valid response, display the predictions
   if response.status_code == 200:
       y = json.loads(response.json())
       print("Predictions:")
       for i in range(len(x)):
           print (" Day: {}. Predicted rentals: {}".format(i+1, max(0, round(y["result"][i]))))
   else:
       print(response)
   ```

    Note

   Don't worry too much about the details of the code. It just defines features for a five day period using hypothetical weather forecast data, and uses the **predict-rentals** service you created to predict cycle rentals for those five days.

6. Switch to the browser tab containing the **Consume** page for the **predict-rentals** service, and copy the REST endpoint for your service. The switch back to the tab containing the notebook and paste the key into the code, replacing YOUR\_ENDPOINT.
7. Switch to the browser tab containing the **Consume** page for the **predict-rentals** service, and copy the Primary Key for your service. The switch back to the tab containing the notebook and paste the key into the code, replacing YOUR\_KEY.
8. Save the notebook, Then use the **▷** button next to the cell to run the code.
9. Verify that predicted number of rentals for each day in the five day period are returned.



## Summary

100 XP

* 1 minute

In this module, you explored machine learning and learned how to use the automated machine learning capability of Azure Machine Learning to train and deploy a predictive model.

### Clean-up <a id="clean-up"></a>

The web service you created is hosted in an _Azure Container Instance_. If you don't intend to experiment with it further, you should delete the endpoint to avoid accruing unnecessary Azure usage. You should also stop the training cluster and compute instance resources until you need them again.

1. In [Azure Machine Learning studio](https://ml.azure.com/), on the **Endpoints** tab, select the **predict-rentals** endpoint. Then select **Delete** \(🗑\) and confirm that you want to delete the endpoint.
2. On the **Compute** page, on the **Compute Instances** tab, select your compute instance and then select **Stop**.

If you have finished exploring Azure Machine Learning, you can delete the resource group containing your Azure Machine Learning workspace:

1. In the [Azure portal](https://portal.azure.com/), in the **Resource groups** page, open the resource group you specified when creating your Azure Machine Learning workspace.
2. Click **Delete resource group**, type the resource group name to confirm you want to delete it, and select **Delete**.



