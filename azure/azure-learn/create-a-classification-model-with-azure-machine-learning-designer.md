# Create a classification model with Azure Machine Learning designer

## Introduction

100 XP

* 2 minutes

_Classification_ is a form of machine learning that is used to predict which category, or _class_, an item belongs to. For example, a health clinic might use the characteristics of a patient \(such as age, weight, blood pressure, and so on\) to predict whether the patient is at risk of diabetes. In this case, the characteristics of the patient are the features, and the label is a classification of either **0** or **1**, representing non-diabetic or diabetic.

![Patients with clinical data, classified as diabetic and non-diabetic](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-classification-model-azure-machine-learning-designer/media/diabetes.png)

Classification is an example of a _supervised_ machine learning technique in which you train a model using data that includes both the features and known values for the label, so that the model learns to _fit_ the feature combinations to the label. Then, after training has been completed, you can use the trained model to predict labels for new items for which the label is unknown.

You can use Microsoft Azure Machine Learning designer to create classification models by using a drag and drop visual interface, without needing to write any code.

In this module, you'll learn how to:

* Use Azure Machine Learning designer to train a classification model.
* Use a classification model for inferencing.
* Deploy a classification model as a service.

To complete this module, you'll need a Microsoft Azure subscription. If you don't already have one, you can sign up for a free trial at [https://azure.microsoft.com](https://azure.microsoft.com/).

## Create an Azure Machine Learning workspace

100 XP

* 5 minutes

Azure Machine Learning is a cloud-based platform for building and operating machine learning solutions in Azure. It includes a wide range of features and capabilities that help data scientists prepare data, train models, publish predictive services, and monitor their usage. One of these features is a visual interface called _designer_, that you can use to train, test, and deploy machine learning models without writing any code.

### Create an Azure Machine Learning workspace <a id="create-an-azure-machine-learning-workspace"></a>

To use Azure Machine Learning, you create a _workspace_ in your Azure subscription. You can then use this workspace to manage data, compute resources, code, models, and other artifacts related to your machine learning workloads.

 Note

This module is one of many that make use of an Azure Machine Learning workspace. If you are completing this module in preparation for the [Azure AI Fundamentals](https://docs.microsoft.com/en-us/learn/certifications/azure-ai-fundamentals) or [Azure Data Scientist](https://docs.microsoft.com/en-us/learn/certifications/azure-data-scientist) certification, consider creating the workspace once and reusing it in other modules. After completing each module, be sure to follow the **Clean Up** instructions at the end of the module to stop compute resources.

If you do not already have one, follow these steps to create a workspace:

1. Sign into the [Azure portal](https://portal.azure.com/) using your Microsoft credentials.
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
4. On the **Overview** page for your workspace, launch Azure Machine Learning Studio \(or open a new browser tab and navigate to [https://ml.azure.com](https://ml.azure.com/)\), and sign into Azure Machine Learning studio using your Microsoft account.
5. In Azure Machine Learning studio, toggle the ☰ icon at the top left to view the various pages in the interface. You can use these pages to manage the resources in your workspace.

You can manage your workspace using the Azure portal, but for data scientists and Machine Learning operations engineers, Azure Machine Learning studio provides a more focused user interface for managing workspace resources.

## Create compute resources

100 XP

* 5 minutes

To train and deploy models using Azure Machine Learning designer, you need compute on which to run the training process, and to test the trained model after deploying it.

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

* 10 minutes

To train a classification model, you need a dataset that includes historical _features_ \(characteristics of the entity for which you want to make a prediction\) and known _label_ values \(the class indicator that you want to train a model to predict\).

### Create a dataset <a id="create-a-dataset"></a>

In Azure Machine Learning, data for model training and other operations is usually encapsulated in an object called a _dataset_.

1. In [Azure Machine Learning studio](https://ml.azure.com/), view the **Datasets** page. Datasets represent specific data files or tables that you plan to work with in Azure ML.
2. Create a dataset from web files, using the following settings:
   * **Basic Info**:
     * **Web URL**: [https://aka.ms/diabetes-data](https://aka.ms/diabetes-data)
     * **Name**: diabetes-data
     * **Dataset type**: Tabular
     * **Description**: Diabetes data
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
3. After the dataset has been created, open it and view the **Explore** page to see a sample of the data. This data represents details from patients who have been tested for diabetes.

### Create a pipeline <a id="create-a-pipeline"></a>

To get started with Azure Machine Learning designer, first you must create a pipeline and add the dataset you want to work with.

1. In [Azure Machine Learning studio](https://ml.azure.com/) for your workspace, view the **Designer** page and select **+** to create a new pipeline.
2. In the **Settings** pane, change the default pipeline name \(**Pipeline-Created-on-**_**date**_\) to **Diabetes Training** \(if the **Settings** pane is not visible, click the **⚙** icon next to the pipeline name at the top\).
3. Note that you need to specify a compute target on which to run the pipeline. In the **Settings** pane, click **Select compute target** and select the **aml-cluster** compute cluster you created previously.
4. On the left side of the designer, expand the **Datasets** section, and drag the **diabetes-data** dataset you created in the previous exercise onto the canvas.
5. Right-click \(Ctrl+click on a Mac\) the **diabetes-data** dataset on the canvas, and on the **Visualize** menu, select **Dataset output**.
6. Review the schema of the data, noting that you can see the distributions of the various columns as histograms.
7. Scroll to the right and select the column heading for the **Diabetic** column, and note that it contains two values **0** and **1**. These values represent the two possible classes for the _label_ that your model will predict, with a value of **0** meaning that the patient does not have diabetes, and a value of **1** meaning that the patient is diabetic.
8. Scroll back to the left and review the other columns, which represent the _features_ that will be used to predict the label. Note that most of these columns are numeric, but each feature is on its own scale. For example, **Age** values range from 21 to 77, while **DiabetesPedigree** values range from 0.078 to 2.3016. When training a machine learning model, it is sometimes possible for larger values to dominate the resulting predictive function, reducing the influence of features that on a smaller scale. Typically, data scientists mitigate this possible bias by _normalizing_ the numeric columns so they're on the similar scales.
9. Close the **diabetes-data result visualization** window so that you can see the dataset on the canvas like this:

![The diabetes-data dataset on the designer canvas](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-classification-model-azure-machine-learning-designer/media/diabetes-data.png)

### Add Transformations <a id="add-transformations"></a>

Before you can train a model, you typically need to apply some preprocessing transformations to the data.

1. In the pane on the left, expand the **Data Transformation** section, which contains a wide range of modules you can use to transform data before model training.
2. Drag a **Normalize Data** module to the canvas, below the **diabetes-data** dataset. Then connect the output from the bottom of the **diabetes-data** dataset to the input at the top of the **Normalize Data** module, like this:

![A pipeline with the diabetes-data dataset connected to a Normalize Data module](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-classification-model-azure-machine-learning-designer/media/dataset-normalize.png)

1. Select the **Normalize Data** module and view its settings, noting that it requires you to specify the transformation method and the columns to be transformed.
2. Set the transformation to **MinMax** and edit the columns to include the following columns by name, as shown in the image:
   * **Pregnancies**
   * **PlasmaGlucose**
   * **DiastolicBloodPressure**
   * **TricepsThickness**
   * **SerumInsulin**
   * **BMI**
   * **DiabetesPedigree**
   * **Age**

![columns selected for normalization](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-classification-model-azure-machine-learning-designer/media/normalize-data.png)

The data transformation is normalizing the numeric columns to put them on the same scale, which should help prevent columns with large values from dominating model training. You'd usually apply a whole bunch of pre-processing transformations like this to prepare your data for training, but we'll keep things simple in this exercise.

### Run the pipeline <a id="run-the-pipeline"></a>

To apply your data transformations, you need to run the pipeline as an experiment.

1. Ensure your pipeline looks similar to this:

![diabetes-data dataset with Normalize Data module](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-classification-model-azure-machine-learning-designer/media/data-prep-pipeline.png)

1. Select **Submit**, and run the pipeline as a new experiment named **mslearn-diabetes-training** on your compute cluster.
2. Wait for the run to finish - this may take a few minutes.

### View the transformed data <a id="view-the-transformed-data"></a>

The dataset is now prepared for model training.

1. Select the completed **Normalize Data** module, and in its **Settings** pane on the right, on the **Outputs + logs** tab, select the **Visualize** icon for the **Transformed dataset**.
2. View the data, noting that the numeric columns you selected have been normalized to a common scale.
3. Close the normalized data result visualization.



## Explore data

100 XP

* 10 minutes

To train a classification model, you need a dataset that includes historical _features_ \(characteristics of the entity for which you want to make a prediction\) and known _label_ values \(the class indicator that you want to train a model to predict\).

### Create a dataset <a id="create-a-dataset"></a>

In Azure Machine Learning, data for model training and other operations is usually encapsulated in an object called a _dataset_.

1. In [Azure Machine Learning studio](https://ml.azure.com/), view the **Datasets** page. Datasets represent specific data files or tables that you plan to work with in Azure ML.
2. Create a dataset from web files, using the following settings:
   * **Basic Info**:
     * **Web URL**: [https://aka.ms/diabetes-data](https://aka.ms/diabetes-data)
     * **Name**: diabetes-data
     * **Dataset type**: Tabular
     * **Description**: Diabetes data
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
3. After the dataset has been created, open it and view the **Explore** page to see a sample of the data. This data represents details from patients who have been tested for diabetes.

### Create a pipeline <a id="create-a-pipeline"></a>

To get started with Azure Machine Learning designer, first you must create a pipeline and add the dataset you want to work with.

1. In [Azure Machine Learning studio](https://ml.azure.com/) for your workspace, view the **Designer** page and select **+** to create a new pipeline.
2. In the **Settings** pane, change the default pipeline name \(**Pipeline-Created-on-**_**date**_\) to **Diabetes Training** \(if the **Settings** pane is not visible, click the **⚙** icon next to the pipeline name at the top\).
3. Note that you need to specify a compute target on which to run the pipeline. In the **Settings** pane, click **Select compute target** and select the **aml-cluster** compute cluster you created previously.
4. On the left side of the designer, expand the **Datasets** section, and drag the **diabetes-data** dataset you created in the previous exercise onto the canvas.
5. Right-click \(Ctrl+click on a Mac\) the **diabetes-data** dataset on the canvas, and on the **Visualize** menu, select **Dataset output**.
6. Review the schema of the data, noting that you can see the distributions of the various columns as histograms.
7. Scroll to the right and select the column heading for the **Diabetic** column, and note that it contains two values **0** and **1**. These values represent the two possible classes for the _label_ that your model will predict, with a value of **0** meaning that the patient does not have diabetes, and a value of **1** meaning that the patient is diabetic.
8. Scroll back to the left and review the other columns, which represent the _features_ that will be used to predict the label. Note that most of these columns are numeric, but each feature is on its own scale. For example, **Age** values range from 21 to 77, while **DiabetesPedigree** values range from 0.078 to 2.3016. When training a machine learning model, it is sometimes possible for larger values to dominate the resulting predictive function, reducing the influence of features that on a smaller scale. Typically, data scientists mitigate this possible bias by _normalizing_ the numeric columns so they're on the similar scales.
9. Close the **diabetes-data result visualization** window so that you can see the dataset on the canvas like this:

![The diabetes-data dataset on the designer canvas](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-classification-model-azure-machine-learning-designer/media/diabetes-data.png)

### Add Transformations <a id="add-transformations"></a>

Before you can train a model, you typically need to apply some preprocessing transformations to the data.

1. In the pane on the left, expand the **Data Transformation** section, which contains a wide range of modules you can use to transform data before model training.
2. Drag a **Normalize Data** module to the canvas, below the **diabetes-data** dataset. Then connect the output from the bottom of the **diabetes-data** dataset to the input at the top of the **Normalize Data** module, like this:

![A pipeline with the diabetes-data dataset connected to a Normalize Data module](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-classification-model-azure-machine-learning-designer/media/dataset-normalize.png)

1. Select the **Normalize Data** module and view its settings, noting that it requires you to specify the transformation method and the columns to be transformed.
2. Set the transformation to **MinMax** and edit the columns to include the following columns by name, as shown in the image:
   * **Pregnancies**
   * **PlasmaGlucose**
   * **DiastolicBloodPressure**
   * **TricepsThickness**
   * **SerumInsulin**
   * **BMI**
   * **DiabetesPedigree**
   * **Age**

![columns selected for normalization](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-classification-model-azure-machine-learning-designer/media/normalize-data.png)

The data transformation is normalizing the numeric columns to put them on the same scale, which should help prevent columns with large values from dominating model training. You'd usually apply a whole bunch of pre-processing transformations like this to prepare your data for training, but we'll keep things simple in this exercise.

### Run the pipeline <a id="run-the-pipeline"></a>

To apply your data transformations, you need to run the pipeline as an experiment.

1. Ensure your pipeline looks similar to this:

![diabetes-data dataset with Normalize Data module](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-classification-model-azure-machine-learning-designer/media/data-prep-pipeline.png)

1. Select **Submit**, and run the pipeline as a new experiment named **mslearn-diabetes-training** on your compute cluster.
2. Wait for the run to finish - this may take a few minutes.

### View the transformed data <a id="view-the-transformed-data"></a>

The dataset is now prepared for model training.

1. Select the completed **Normalize Data** module, and in its **Settings** pane on the right, on the **Outputs + logs** tab, select the **Visualize** icon for the **Transformed dataset**.
2. View the data, noting that the numeric columns you selected have been normalized to a common scale.
3. Close the normalized data result visualization.

## Create and run a training pipeline

100 XP

* 12 minutes

After you've used data transformations to prepare the data, you can use it to train a machine learning model.

### Add training modules <a id="add-training-modules"></a>

It's common practice to train the model using a subset of the data, while holding back some data with which to test the trained model. This enables you to compare the labels that the model predicts with the actual known labels in the original dataset.

In this exercise, you're going to extend the **Diabetes Training** pipeline as shown here:

![split data, then train with logistic regression and score](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-classification-model-azure-machine-learning-designer/media/train-score-pipeline.png)

Follow the steps below, using the image above for reference as you add and configure the required modules.

1. Open the **Diabetes Training** pipeline you created in the previous unit if it's not already open.
2. In the pane on the left, in the **Data Transformations** section, drag a **Split Data** module onto the canvas under the **Normalize Data** module. Then connect the _Transformed Dataset_ \(left\) output of the **Normalize Data** module to the input of the **Split Data** module.
3. Select the **Split Data** module, and configure its settings as follows:
   * **Splitting mode** Split Rows
   * **Fraction of rows in the first output dataset**: 0.7
   * **Random seed**: 123
   * **Stratified split**: False
4. Expand the **Model Training** section in the pane on the left, and drag a **Train Model** module to the canvas, under the **Split Data** module. Then connect the _Result dataset1_ \(left\) output of the **Split Data** module to the _Dataset_ \(right\) input of the **Train Model** module.
5. The model we're training will predict the **Diabetic** value, so select the **Train Model** module and modify its settings to set the **Label column** to **Diabetic** \(matching the case and spelling exactly!\)
6. The **Diabetic** label the model will predict is a class \(0 or 1\), so we need to train the model using a _classification_ algorithm. Specifically, there are two possible classes, so we need a _binary classification_ algorithm. Expand the **Machine Learning Algorithms** section, and under **Classification**, drag a **Two-Class Logistic Regression** module to the canvas, to the left of the **Split Data** module and above the **Train Model** module. Then connect its output to the **Untrained model** \(left\) input of the **Train Model** module.

 Note

There are multiple algorithms you can use to train a classification model. For help choosing one, take a look at the [Machine Learning Algorithm Cheat Sheet for Azure Machine Learning designer](https://aka.ms/mlcheatsheet).

1. To test the trained model, we need to use it to _score_ the validation dataset we held back when we split the original data - in other words, predict labels for the features in the validation dataset. Expand the **Model Scoring & Evaluation** section and drag a **Score Model** module to the canvas, below the **Train Model** module. Then connect the output of the **Train Model** module to the **Trained model** \(left\) input of the **Score Model** module; and connect the **Results dataset2** \(right\) output of the **Split Data** module to the **Dataset** \(right\) input of the **Score Model** module.
2. Ensure your pipeline looks like this:

![split data, then train with logistic regression and score](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-classification-model-azure-machine-learning-designer/media/train-score-pipeline.png)

### Run the training pipeline <a id="run-the-training-pipeline"></a>

Now you're ready to run the training pipeline and train the model.

1. Select **Submit**, and run the pipeline using the existing experiment named **mslearn-diabetes-training**.
2. Wait for the experiment run to finish. This may take 5 minutes or more.
3. When the experiment run has finished, select the **Score Model** module and in the settings pane, on the **Outputs + Logs** tab, under **Data outputs** in the **Scored dataset** section, use the **Visualize** icon to view the results.
4. Scroll to the right, and note that next to the **Diabetic** column \(which contains the known true values of the label\) there is a new column named **Scored Labels**, which contains the predicted label values, and a **Scored Probabilities** columns containing a probability value between 0 and 1. This indicates the probability of a _positive_ prediction, so probabilities greater than 0.5 result in a predicted label of _**1**_ \(diabetic\), while probabilities between 0 and 0.5 result in a predicted label of _**0**_ \(not diabetic\).
5. Close the **Score Model result visualization** window.

The model is predicting values for the **Diabetic** label, but how reliable are its predictions? To assess that, you need to evaluate the model.  


## Evaluate a classification model

100 XP

* 10 minutes

The validation data you held back and used to score the model includes the known values for the label. So to validate the model, you can compare the true values for the label to the label values that were predicted when you scored the validation dataset. Based on this comparison, you can calculate various metrics that describe how well the model performs.

### Add an Evaluate Model module <a id="add-an-evaluate-model-module"></a>

1. Open the **Diabetes Training** pipeline you created in the previous unit if it's not already open.
2. In the pane on the left, in the **Model Scoring & Evaluation** section, drag an **Evaluate Model** module to the canvas, under the **Score Model** module, and connect the output of the **Score Model** module to the **Scored dataset** \(left\) input of the **Evaluate Model** module.
3. Ensure your pipeline looks like this:

![Evaluate Model module added to Score Model module](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-classification-model-azure-machine-learning-designer/media/evaluate-pipeline.png)

1. Select **Submit**, and run the pipeline using the existing experiment named **mslearn-diabetes-training**.
2. Wait for the experiment run to finish.
3. When the experiment run has finished, select the **Evaluate Model** module and in the settings pane, on the **Outputs + Logs** tab, under **Data outputs** in the **Evaluation results** section, use the **Visualize** icon to view the performance metrics. These metrics can help data scientists assess how well the model predicts based on the validation data.
4. View the _confusion matrix_ for the model, which is a tabulation of the predicted and actual value counts for each possible class. For a binary classification model like this one, where you're predicting one of two possible values, the confusion matrix is a 2x2 grid showing the predicted and actual value counts for classes **0** and **1**, similar to this:

![A confusion matrix showing actual and predicted value counts for each class](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-classification-model-azure-machine-learning-designer/media/confusion-matrix.png)

The confusion matrix shows cases where both the predicted and actual values were 1 \(known as _true positives_\) at the top left, and cases where both the predicted and the actual values were 0 \(_true negatives_\) at the bottom right. The other cells show cases where the predicted and actual values differ \(_false positives_ and _false negatives_\). The cells in the matrix are colored so that the more cases represented in the cell, the more intense the color - with the result that you can identify a model that predicts accurately for all classes by looking for a diagonal line of intensely colored cells from the top left to the bottom right \(in other words, the cells where the predicted values match the actual values\). For a multi-class classification model \(where there are more than two possible classes\), the same approach is used to tabulate each possible combination of actual and predicted value counts - so a model with three possible classes would result in a 3x3 matrix with a diagonal line of cells where the predicted and actual labels match.

1. Review the metrics to the left of the confusion matrix, which include:

   * **Accuracy**: The ratio of correct predictions \(true positives + true negatives\) to the total number of predictions. In other words, what proportion of diabetes predictions did the model get right?
   * **Precision**: The fraction of positive cases correctly identified \(the number of true positives divided by the number of true positives plus false positives\). In other words, out of all the patients that the model predicted as having diabetes, how many are actually diabetic?
   * **Recall**: The fraction of the cases classified as positive that are actually positive \(the number of true positives divided by the number of true positives plus false negatives\). In other words, out of all the patients who actually have diabetes, how many did the model identify?
   * **F1 Score**: An overall metric that essentially combines precision and recall.
   * _We'll return to **AUC** later_.

   Of these metric, _accuracy_ is the most intuitive. However, you need to be careful about using simple accuracy as a measurement of how well a model works. Suppose that only 3% of the population is diabetic. You could create a model that always predicts **0** and it would be 97% accurate - just not very useful! For this reason, most data scientists use other metrics like precision and recall to assess classification model performance.

2. Above the list of metrics, note that there's a **Threshold** slider. Remember that what a classification model predicts is the probability for each possible class. In the case of this binary classification model, the predicted probability for a _positive_ \(that is, diabetic\) prediction is a value between 0 and 1. By default, a predicted probability for diabetes above 0.5 results in a class prediction of 1, while a prediction below this threshold means that there's a greater probability of the patient **not** having diabetes \(remember that the probabilities for all classes add up to 1\), so the predicted class would be 0. Try moving the threshold slider and observe the effect on the confusion matrix. If you move it all the way to the left \(0\), the Recall metric becomes 1, and if you move it all the way to the right \(1\), the Recall metric becomes 0.
3. Look above the Threshold slider at the **ROC curve** \(ROC stands for _received operator characteristic_, but most data scientists just call it a ROC curve\). Another term for _recall_ is **True positive rate**, and it has a corresponding metric named **False positive rate**, which measures the number of negative cases incorrectly identified as positive compared the number of actual negative cases. Plotting these metrics against each other for every possible threshold value between 0 and 1 results in a curve. In an ideal model, the curve would go all the way up the left side and across the top, so that it covers the full area of the chart. The larger the _area under the curve_ \(which can be any value from 0 to 1\), the better the model is performing - this is the **AUC** metric listed with the other metrics below. To get an idea of how this area represents the performance of the model, imagine a straight diagonal line from the bottom left to the top right of the ROC chart. This represents the expected performance if you just guessed or flipped a coin for each patient - you could expect to get around half of them right, and half of them wrong, so the area under the diagonal line represents an AUC of 0.5. If the AUC for your model is higher than this for a binary classification model, then the model performs better than a random guess.
4. Close the **Evaluate Model result visualization** window.

The performance of this model isn't all that great, partly because we performed only minimal feature engineering and pre-processing. You could try a different classification algorithm, such as **Two-Class Decision Forest**, and compare the results. You can connect the outputs of the **Split Data** module to multiple **Train Model** and **Score Model** modules, and you can connect a second **Score Model** module to the **Evaluate Model** module to see a side-by-side comparison. The point of the exercise is simply to introduce you to classification and the Azure Machine Learning designer interface, not to train a perfect model!



