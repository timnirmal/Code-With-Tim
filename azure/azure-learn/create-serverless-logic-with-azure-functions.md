# Create serverless logic with Azure Functions

## Introduction

100 XP

* 3 minutes

Imagine you work for an escalator company that has invested in IoT technology to monitor its product in the field. You oversee the processing of temperature sensor data from the drive gears of the escalators. You monitor the temperature data and add a data flag to indicate when the gears are too hot. In downstream systems, this data helps determine when maintenance is required.

Your company receives sensor data from several locations and from different escalator models. The data arrives in different formats, including batch file uploads, scheduled database pulls, messages on a queue, and incoming data from an event hub. You want to develop a reusable service that can process your temperature data from all these sources.

When designing a service such as this with traditional enterprise architecture strategies, you would need to consider server infrastructure and maintenance up front: scope out necessary hardware, plan to install it, coordinate with IT to manage it, and so on. An alternative to all that work is **serverless computing**. With serverless computing, your cloud provider manages the provisioning and maintenance of the infrastructure letting you focus completely on building the app logic. Azure Functions is a key component of the serverless computing offering from Azure and enables you to run pieces of code or _functions_, written in the programming language of your choice, in the cloud.

### Learning objectives <a id="learning-objectives"></a>

In this module, you will:

* Decide if serverless computing is right for your business need.
* Create an Azure function app in the Azure portal.
* Execute a function using triggers.
* Monitor and test your Azure function from the Azure portal.

## Decide if serverless computing is right for your business needs

100 XP

* 5 minutes

To help decide whether serverless computing is right for you, let's first learn what serverless is all about.

### What is serverless compute? <a id="what-is-serverless-compute"></a>

[Serverless compute](https://azure.microsoft.com/solutions/serverless/) can be thought of as a function as a service \(FaaS\), or a microservice that is hosted on a cloud platform. Your business logic runs as functions and you don't have to manually provision or scale infrastructure. The cloud provider manages infrastructure. Your app is automatically scaled out or down depending on load. Azure has several ways to build this sort of architecture. The two most common approaches are Azure Logic Apps and Azure Functions, which we focus on in this module.

### What is Azure Functions? <a id="what-is-azure-functions"></a>

Azure Functions is a serverless application platform. It allows developers to host business logic that can be executed without provisioning infrastructure. Functions provides intrinsic scalability and you are charged only for the resources used. You can write your function code in the language of your choice, including C\#, F\#, JavaScript, Python, and PowerShell Core. Support for package managers like NuGet and NPM is also included, so you can use popular libraries in your business logic.

### Benefits of a serverless compute solution <a id="benefits-of-a-serverless-compute-solution"></a>

Serverless compute is a great option for hosting business logic code in the cloud. With serverless offerings such as Azure Functions, you can write your business logic in the language of your choice. You get automatic scaling, you have no servers to manage, and you are charged based on what is used — not on reserved time. Here are some additional characteristics of a serverless solution for you to consider.

#### Avoids over-allocation of infrastructure <a id="avoids-over-allocation-of-infrastructure"></a>

Suppose you've provisioned VM servers and configured them with enough resources to handle your peak load times. When the load is light, you are potentially paying for infrastructure you're not using. Serverless computing helps solve the allocation problem by scaling up or down automatically, and you're only billed when your function is processing work.

#### Stateless logic <a id="stateless-logic"></a>

Stateless functions are great candidates for serverless compute; function instances are created and destroyed on demand. If state is required, it can be stored in an associated storage service.

#### Event driven <a id="event-driven"></a>

Functions are _event driven_. This means they run only in response to an event \(called a "trigger"\), such as receiving an HTTP request, or a message being added to a queue. You configure a trigger as part of the function definition. This approach simplifies your code by allowing you to declare where the data comes from \(trigger/input binding\) and where it goes \(output binding\). You don't need to write code to watch queues, blobs, hubs, etc. You can focus purely on the business logic.

#### Functions can be used in traditional compute environments <a id="functions-can-be-used-in-traditional-compute-environments"></a>

Functions are a key component of serverless computing, but they are also a general compute platform for executing any type of code. Should the needs of your app change, you can take your project and deploy it in a non-serverless environment, which gives you the flexibility to manage scaling, run on virtual networks, and even completely isolate your functions.

### Drawbacks of a serverless compute solution <a id="drawbacks-of-a-serverless-compute-solution"></a>

Serverless compute will not always be the appropriate solution to hosting your business logic. Here are a few characteristics of functions that may affect your decision to host your services in serverless compute.

#### Execution time <a id="execution-time"></a>

By default, functions have a timeout of 5 minutes. This timeout is configurable to a maximum of 10 minutes. If your function requires more than 10 minutes to execute, you can host it on a VM. Additionally, if your service is initiated through an HTTP request and you expect that value as an HTTP response, the timeout is further restricted to 2.5 minutes. Finally, there's also an option called [**Durable Functions**](https://docs.microsoft.com/en-us/azure/azure-functions/durable) that allows you to orchestrate the executions of multiple functions without any timeout.

#### Execution frequency <a id="execution-frequency"></a>

The second characteristic is execution frequency. If you expect your function to be executed continuously by multiple clients, it would be prudent to estimate the usage and calculate the cost of using functions accordingly. It might be cheaper to host your service on a VM.

While scaling, only one function app instance can be created every 10 seconds, for up to 200 total instances. Keep in mind, each instance can service multiple concurrent executions, so there is no set limit on how much traffic a single instance can handle. Different types of triggers have different scaling requirements, so research your choice of trigger and investigate its limits.



## Exercise - Create a function app in the Azure portal

600 XP

* 5 minutes

Microsoft Learn needs your permission to create Azure resources.

For more information, please check the [troubleshooting guidance page](https://docs.microsoft.com/en-us/learn/support/troubleshooting).

[Review permissions](https://login.microsoftonline.com/redeem?rd=https%3a%2f%2finvitations.microsoft.com%2fredeem%2f%3ftenant%3d604c1504-c6a3-4080-81aa-b33091104187%26user%3df2e4c65b-3506-453f-a082-35c36ddf2286%26ticket%3drctHaoe7wJRFQhcp%252fP%252bKJpWn0tcBSiTtXsoK%252bSpMwUU%253d%26ver%3d2.0)Choose your development languageJavaScriptPowerShell

You are now ready to start implementing the temperature service. In the previous unit, you determined that a serverless solution would best fit your needs. Let's start by creating a function app to hold our Azure Function.

### What is a function app? <a id="what-is-a-function-app"></a>

Functions are hosted in an execution context called a **function app**. You define function apps to logically group and structure your functions and a compute resource in Azure. In our escalator example, you would create a function app to host the escalator drive gear temperature service. There are a few decisions that need to be made to create the function app; you need to choose a service plan and select a compatible storage account.

#### Choose a service plan <a id="choose-a-service-plan"></a>

Function apps may use one of two types of service plans. The first service plan is the **Consumption service plan**. The plan that you choose when using the Azure serverless application platform. The Consumption service plan provides automatic scaling and bills you when your functions are running. The Consumption plan comes with a configurable timeout period for the execution of a function. By default, it is 5 minutes, but may be configured to have a timeout as long as 10 minutes.

The second plan is called the **Azure App Service plan**. The plan allows you to avoid timeout periods by having your function run continuously on a VM that you define. When using an App Service plan, you are responsible for managing the app resources the function runs on, so this is technically not a serverless plan. However, it may be a better choice if your functions are used continuously or if your functions require more processing power or execution time than the Consumption plan can provide.

#### Storage account requirements <a id="storage-account-requirements"></a>

When you create a function app, it must be linked to a storage account. You can select an existing account or create a new one. The function app uses this storage account for internal operations such as logging function executions and managing execution triggers. On the Consumption service plan, this is also where the function code and configuration file are stored.

### Create a function app <a id="create-a-function-app"></a>

Let's create a function app in the Azure portal.

1. Sign into the [Azure portal ](https://portal.azure.com/learn.docs.microsoft.com) using the same account you activated for the sandbox.
2. Select **Create a resource**.

    Important

   We are currently working to update our sandbox to support the new workflow for creating an Azure Function in the portal. The instructions will be updated when that is available. Until then, you can use the version of the create experience that matches the current instructions by clicking the notification bar labeled **Looking for the classic Function App create experience?** at the top of the **Function App** page. This experience can also be reached by choosing the **Function App \(Classic\)** option from the Azure Marketplace.

   ![Screenshot of the Azure portal menu open showing the Create a resource choice.](https://docs.microsoft.com/en-us/learn/modules/create-serverless-logic-with-azure-functions/media/3-create-function-app-1.png)

3. In the left menu pane, select **Compute**, and then select **Function App**. The **Create Function App** page appears.
4. On the **Basics** tab, enter the following values for each setting.

   | TABLE 1 |  |
   | :--- | :--- |
   | Setting | Value |
   | **Project Details** |  |
   | Subscription | Concierge Subscription |
   | Resource Group | **\[sandbox resource group name\]** |
   | **Instance Details** |  |
   | Function App name | Enter a globally unique app name. The function app name will serve as the base URL of your service. For example, you can name it **escalator-functions-xxxxxxx**, where the x's can be replaced with your initials and your birth year. If this isn't globally unique, you can try any other combination. Valid characters are a-z, 0-9 and - |
   | Publish | Code |
   | Runtime stack | Node.js \(which is the language in which we implement the function examples in this exercise\). |
   | Version | _default_ |
   | Region | Select a geographical location close to you. In a production system, you would want to select a location near your customers or consumers of the function. |

5. Select **Review + create**, and then select **Create**. Deployment will take a few minutes. You'll receive a notification when deployment is completed.

### Verify your Azure function app <a id="verify-your-azure-function-app"></a>

1. When deployment completes, select **Go to resource**. Your Function App page appears.
2. In the **Essentials** section, select the **URL** link to open it in a browser. A default web page appears that indicates your Function App is up and running.

## Run your code on-demand with Azure Functions

Completed100 XP

* 10 minutes

Now that we have a function app created, let's look at how to build, configure, and execute a function.

#### Triggers <a id="triggers"></a>

Functions are event driven, which means they run in response to an event.

The type of event that starts the function is called a **trigger**. You must configure a function with exactly one trigger.

Azure supports triggers for the following services.

| TRIGGERS |  |
| :--- | :--- |
| Service | Trigger description |
| Blob storage | Starts a function when a new or updated blob is detected. |
| Azure Cosmos DB | Start a function when inserts and updates are detected. |
| Event Grid | Starts a function when an event is received from Event Grid. |
| HTTP | Starts a function with an HTTP request. |
| Microsoft Graph Events | Starts a function in response to an incoming webhook from the Microsoft Graph. Each instance of this trigger can react to one Microsoft Graph resource type. |
| Queue storage | Starts a function when a new item is received on a queue. The queue message is provided as input to the function. |
| Service Bus | Starts a function in response to messages from a Service Bus queue. |
| Timer | Starts a function on a schedule. |

#### Bindings <a id="bindings"></a>

Bindings are a declarative way to connect data and services to your function. Bindings know how to talk to different services, which means you don't have to write code in your function to connect to data sources and manage connections. The platform takes care of that complexity for you as part of the binding code. Each binding has a direction - your code reads data from _input_ bindings, and writes data to _output_ bindings. Each function can have zero or more bindings to manage the input and output data processed by the function.

A trigger is a special type of input binding that has the additional capability of initiating execution.

Azure provides a [large number of bindings](https://docs.microsoft.com/en-us/azure/azure-functions/functions-triggers-bindings#supported-bindings) to connect to different storage and messaging services.

#### Define a sample binding <a id="define-a-sample-binding"></a>

Let's look at an example of configuring a function with an input binding \(trigger\) and an output binding. Let's say we want to write a new row to Azure Table storage whenever a new message appears in Azure Queue storage. This scenario can be implemented using an Azure Queue storage _trigger_ and an Azure Table storage _output binding_.

The following snippet is the _function.json_ file for this scenario.JSONCopy

```text
{
  "bindings": [
    {
      "name": "order",
      "type": "queueTrigger",
      "direction": "in",
      "queueName": "myqueue-items",
      "connection": "MY_STORAGE_ACCT_APP_SETTING"
    },
    {
      "name": "$return",
      "type": "table",
      "direction": "out",
      "tableName": "outTable",
      "connection": "MY_TABLE_STORAGE_ACCT_APP_SETTING"
    }
  ]
}
```

Our JSON configuration specifies that our function will be triggered when a message is added to a queue named **myqueue-items**. The return value of our function is then written to the **outTable** table in Azure Table storage. For PowerShell functions, output bindings are explicitly written to with the `Push-OutputBinding` cmdlet.

This example is a simple illustration about how we configure bindings for a function. We could change the output to be an email using a SendGrid binding, or put an event onto a Service Bus to notify some other component in our architecture, or even have multiple output bindings to push data to various services.

 Tip

To view and edit the contents of _function.json_ in the Azure portal, select the **Advanced** editor option on the **Integrate** tab of your function.

### Create a function in the Azure portal <a id="create-a-function-in-the-azure-portal"></a>

Azure provides several pre-made function templates for common scenarios:

* Quickstart
* Custom functions

#### Quickstart templates <a id="quickstart-templates"></a>

When adding your first function, you are presented with the Quickstart screen where you can choose the trigger for your function. Based on your selections, Azure will generate the function code and configuration with some sample code provided to display the input data received in the log.

#### Custom function templates <a id="custom-function-templates"></a>

Selecting Quickstart templates provides easy access to the most common scenarios. However, Azure provides over 30 additional templates you can start with. These can be selected from the template list screen when creating subsequent functions, or you can select them by using the **Custom function** option on the Quickstart screen.

### Navigate to your function and files <a id="navigate-to-your-function-and-files"></a>

When you create a function from a template, several files are created. For example, if you opted to use the Webhook + API Quickstart using JavaScript, the files generated would be a configuration file, **function.json**, and a source code file, **index.js**. The functions you create in a function app appear under the **Functions** menu item in the function app portal.

When you select a function in your function app, a code editor opens and displays the code for your function, as shown in the following screenshot.

![Screenshot of the Azure portal showing the function editor pane, including the expanded View files menu, with the selected &quot;HttpTriggerJS1&quot; function in our app service navigation and the View files menu highlighted.](https://docs.microsoft.com/en-gb/learn/modules/create-serverless-logic-with-azure-functions/media/4-file-navigation.png)

As you can see, there's a flyout menu on the right that includes a tab to **View files**. Selecting this tab shows the file structure that makes up your function.

### Test your Azure function <a id="test-your-azure-function"></a>

After you've created a function, you'll want to test it. There are a couple of approaches:

* Manual execution
* Testing from within the Azure portal itself.

#### Manual execution <a id="manual-execution"></a>

You can start a function by manually triggering the configured trigger. For instance, if you are using an HTTP trigger, you can use a tool, such as Postman or cURL, to initiate an HTTP request to your function endpoint URL, which is available from the HTTP trigger definition \(**Get function URL**\).

#### Test in the Azure portal <a id="test-in-the-azure-portal"></a>

The portal also provides a convenient way to test your functions. On the right side of the code window, there is a tabbed flyout menu. This menu contains a **Test** item. Expanding the menu, and selecting this tab provides another way to execute your function, and view the result. When you select **Run** in this test window, the results appear in the output window, along with a status code.

### Monitoring dashboard <a id="monitoring-dashboard"></a>

The ability to monitor your functions is critical during development and in production. The Azure portal provides a monitoring dashboard if you turn on the Application Insights integration. In the function app nav menu, after you expand the function node, you'll see a **Monitor** menu item. This monitor dashboard provides a quick way to view the history of function executions, and displays the timestamp, result code, duration, and operation ID populated by Application Insights.

![Screenshot of the Azure portal showing an HTTP function Monitor pane with several function results and their corresponding HTTP status codes, with the Module menu item of the function highlighted.](https://docs.microsoft.com/en-gb/learn/modules/create-serverless-logic-with-azure-functions/media/4-monitor-function.png)

### Streaming log window <a id="streaming-log-window"></a>

You're also able to add logging statements to your function for debugging in the Azure portal. The called methods for each language are passed a "logging" object, which may be used to log information to the log window located in a tabbed flyout menu located at the bottom of the code window.

The following JavaScript code snippet shows how to log a message using the `context.log` method \(the `context` object is passed to the handler\).JavaScriptCopy

```text
context.log('Enter your logging statement here');
```

We could do the same thing in C\# using the `log.Info` method. In this case, the `log` object is passed to the C\# method processing the function.C\#Copy

```text
log.Info("Enter your logging statement here");
```

In PowerShell, use `Write-Host` to write to the log:PowerShellCopy

```text
Write-Host "Enter your logging statement here"
```

#### Errors and warnings window <a id="errors-and-warnings-window"></a>

You can locate the errors and warnings window tab in the same flyout menu as the log window. This window shows compilation errors and warnings within your code.



