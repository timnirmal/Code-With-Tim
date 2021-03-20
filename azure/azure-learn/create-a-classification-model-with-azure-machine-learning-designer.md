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



