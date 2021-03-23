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



