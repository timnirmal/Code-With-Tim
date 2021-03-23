# Create a Clustering Model with Azure Machine Learning designer

## Introduction

100 XP

* 2 minutes

_Clustering_ is a form of machine learning that is used to group similar items into clusters based on their features. For example, a researcher might take measurements of penguins, and group them based on similarities in their proportions.

![Penguins clustered into groups](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-clustering-model-azure-machine-learning-designer/media/penguins.png)

Clustering is an example of _unsupervised_ machine learning, in which you train a model to separate items into clusters based purely on their characteristics, or _features_. There is no previously known cluster value \(or _label_\) from which to train the model.

You can use Microsoft Azure Machine Learning designer to create clustering models by using a drag and drop visual interface, without needing to write any code.

In this module, you'll learn how to:

* Use Azure Machine Learning designer to train a clustering model.
* Use a clustering model for inferencing.
* Deploy a clustering model as a service.

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

* 8 minutes

To train a clustering model, you need a dataset that includes multiple observations of the items you want to cluster, including numeric features that can be used to determine similarities between individual cases that will help separate them into clusters.

### Create a dataset <a id="create-a-dataset"></a>

In Azure Machine Learning, data for model training and other operations is usually encapsulated in an object called a _dataset_. In this module, you'll use a dataset that includes observations of three species of penguin.

1. In [Azure Machine Learning studio](https://ml.azure.com/), view the **Datasets** page. Datasets represent specific data files or tables that you plan to work with in Azure ML.
2. Create a dataset from web files, using the following settings:
   * **Basic Info**:
     * **Web URL**: [https://aka.ms/penguin-data](https://aka.ms/penguin-data)
     * **Name**: penguin-data
     * **Dataset type**: Tabular
     * **Description**: Penguin data
   * **Settings and preview**:
     * **File format**: Delimited
     * **Delimiter**: Comma
     * **Encoding**: UTF-8
     * **Column headers**: Use headers from the first file
     * **Skip rows**: None
   * **Schema**:
     * Include all columns other than **Path**
     * Review the automatically detected types
   * **Confirm details**:
     * Do not profile the dataset after creation
3. After the dataset has been created, open it and view the **Explore** page to see a sample of the data. This data represents measurements of the culmen \(bill\) length and depth, flipper length, and body mass for multiple observations of penguins. There are three species of penguin represented in the dataset: _Amelie_, _Gentoo_, and _Chinstrap_.

 Note

The penguins dataset used in the this exercise is a subset of data collected and made available by [Dr. Kristen Gorman](https://www.uaf.edu/cfos/people/faculty/detail/kristen-gorman.php) and the [Palmer Station, Antarctica LTER](https://pal.lternet.edu/), a member of the [Long Term Ecological Research Network](https://lternet.edu/).

### Create a pipeline <a id="create-a-pipeline"></a>

To get started with Azure machine Learning designer, first you must create a pipeline and add the dataset you want to work with.

1. In [Azure Machine Learning studio](https://ml.azure.com/) for your workspace, view the **Designer** page and create a new pipeline.
2. In the **Settings** pane, change the default pipeline name \(**Pipeline-Created-on-**_**date**_\) to **Train Penguin Clustering** \(if the **Settings** pane is not visible, click the **⚙** icon next to the pipeline name at the top\).
3. Note that you need to specify a compute target on which to run the pipeline. In the **Settings** pane, click **Select compute target** and select the compute cluster you created previously.
4. In the pane on the left side of the designer, expand the **Datasets** section, and drag the **penguin-data** dataset you created in the previous exercise onto the canvas.
5. Right-click \(Ctrl+click on a Mac\) the **penguin-data** dataset on the canvas, and on the **Visualize** menu, select **Dataset output**.
6. Review the schema of the data, noting that you can see the distributions of the various columns as histograms. Then select the **CulmenLength** column. The dataset should look similar to this:

![The penguin-data dataset connected to the Select Columns in Dataset module](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-clustering-model-azure-machine-learning-designer/media/penguin-visualization.png)

1. Note the following characteristics of the dataset:
   * The dataset includes the following columns:
     * **CulmenLength**: Length of the penguin's bill in millimeters.
     * **CulmenDepth**: Depth of the penguin's bill in millimeters.
     * **FlipperLength**: Length of the penguin's flipper in millimeters.
     * **BodyMass**: Weight of the penguin in grams.
     * **Species**: Species indicator \(0:"Amelie", 1:"Gentoo", 2:"Chinstrap"\)
   * There are two missing values in the **CulmenLength** column \(the **CulmenDepth**, **FlipperLength**, and **BodyMass** columns also have two missing values\).
   * The measurement values are in different scales \(from tens of millimeters to thousands of grams\).
2. Close the dataset visualization so you can see the dataset on the pipeline canvas.

### Apply transformations <a id="apply-transformations"></a>

To cluster the penguin observations, we're going to use only the measurements; so we'll discard the species column. We also need to remove rows where values are missing, and normalize the numeric measurement values so they're on a similar scale.

1. In the pane on the left, expand the **Data Transformation** section, which contains a wide range of modules you can use to transform data before model training.
2. To cluster the penguin observations, we're going to use only the measurements - we'll ignore the species column. So, drag a **Select Columns in Dataset** module to the canvas, below the **penguin-data** module and connect the output at the bottom of the **penguin-data** module to the input at the top of the **Select Columns in Dataset** module, like this:

![The penguin-data dataset connected to the Select Columns in Dataset module](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-clustering-model-azure-machine-learning-designer/media/dataset-select-columns.png)

1. Select the **Select Columns in Dataset** module, and in its **Settings** pane on the right, select **Edit column**. Then in the **Select columns** window, select **By name** and use the **+** links to select the column names **CulmenLength**, **CulmenDepth**, **FlipperLength**, and **BodyMass**; like this:

![include column names CulmenLength, CulmenDepth, FlipperLength, and BodyMass](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-clustering-model-azure-machine-learning-designer/media/select-columns.png)

1. Save the **Select Columns in a Dataset** module settings to return to the designer canvas.
2. Drag a **Clean Missing Data** module to the canvas, below the **Select columns in a dataset** module and connect them like this:

![Connect the output of the Select Columns in Dataset module to the input of the Clean Missing Data module](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-clustering-model-azure-machine-learning-designer/media/clean-missing-data.png)

1. Select the **Clean Missing Data** module, and in the settings pane on the right, click **Edit column**. Then in the **Select columns** window, select **With rules** and include **All columns**; like this:

![Use the With rules option to Select all columns](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-clustering-model-azure-machine-learning-designer/media/normalize-columns.png)

1. With the **Clean Missing Data** module still selected, in the settings pane, set the following configuration settings:
   * **Minimum missing value ratio**: 0.0
   * **Maximum missing value ratio**: 1.0
   * **Cleaning mode**: Remove entire row
2. Drag a **Normalize Data** module to the canvas, below the **Clean Missing Data** module. Then connect the left-most output from the **Clean Missing Data** module to the input of the **Normalize Data** module.

![Connect the output of the Clean Missing Data module to the input of the Normalize Data module](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-clustering-model-azure-machine-learning-designer/media/dataset-normalize.png)

1. Select the **Normalize Data** module, and in its **Settings** pane on the right, set the **Transformation method** to **MinMax** and select **Edit column**. Then in the **Select columns** window, select **With rules** and include **All columns**; like this:

![Use the With rules option to Select all columns](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-clustering-model-azure-machine-learning-designer/media/normalize-columns.png)

1. Save the **Normalize Data** module settings to return to the designer canvas.

### Run the pipeline <a id="run-the-pipeline"></a>

To apply your data transformations, you need to run the pipeline as an experiment.

1. Ensure your pipeline looks similar to this:

![The penguin-data dataset, a Select Columns in Dataset module, a Clean Missing Data module, and a Normalize Data module](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-clustering-model-azure-machine-learning-designer/media/data-preparation.png)

1. Select **Submit**, and run the pipeline as a new experiment named **mslearn-penguin-training** on your compute cluster.
2. Wait for the run to finish. This may take 5 minutes or more. When the run has completed, the modules should look like this:

![Select Columns in Dataset and Normalize Data modules with a &quot;Completed&quot; state](https://docs.microsoft.com/en-us/learn/wwl-data-ai/create-clustering-model-azure-machine-learning-designer/media/normalize-complete.png)

### View the transformed data <a id="view-the-transformed-data"></a>

The dataset is now prepared for model training.

1. Select the completed **Normalize Data** module, and in its **Settings** pane on the right, on the **Outputs + logs** tab, select the **Visualize** icon for the **Transformed dataset**.
2. View the data, noting that the **Species** column has been removed, there are no missing values, and the values for all four features have been normalized to a common scale.
3. Close the normalized data result visualization.

Now that you have selected and prepared the features you want to use from the dataset, you're ready to use them to train a clustering model.  




