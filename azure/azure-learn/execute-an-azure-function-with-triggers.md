# Execute an Azure Function with triggers



## Introduction

Completed100 XP

* 2 minutes

Imagine a scenario where a busy hair salon has a recurring problem: their customers commonly miss their appointments. The appointments are reserved time slots. If a customer misses an appointment, the salon loses money. To fix this problem, the salon reaches out to you, a software developer. To improve the situation, you decide to send reminder text messages. These could be sent as soon as the appointment is scheduled or changed, and each morning, you'll send a text message to every customer with an appointment that day.

You need to create a service that can be easily scheduled, updated and scaled. You decide to solve this problem using an Azure Functions app. You already know how to implement the logic to send a text message. Now you need to learn how to send the message at a specific time or when a specific event occurs. Luckily, Azure Functions app supports a feature called _triggers_. Triggers are used to determine how an Azure Function is executed.

### Learning objectives <a id="learning-objectives"></a>

In this module, you will:

* Determine which trigger works best for your business needs.
* Create a timer trigger to invoke a function on a consistent schedule.
* Create an HTTP trigger to invoke a function when an HTTP request is received.
* Create a blob trigger to invoke a function when a blob is created or updated in Azure Storage.

## Determine the best trigger for your Azure function

Completed100 XP

* 4 minutes

An Azure Functions app doesn't do work until something tells it to execute. For example, we could create an Azure Function to send out a reminder text message to our customers before an appointment. If we don't tell the function when it should run, our customers will never receive a message.

Here, you'll examine triggers at a high level and explore the most common types of triggers.

### What is a trigger? <a id="what-is-a-trigger"></a>

A trigger is an object that defines how an Azure Function is invoked. For example, if you want a function to execute every 10 minutes, you could use a timer trigger.

Every function must have exactly one trigger associated with it. If you want to execute a piece of logic that runs under multiple conditions, you need to create multiple functions that share the same core function code.

In this module, we're going to focus on the **timer**, **HTTP**, and **blob** trigger types.

### Types of triggers <a id="types-of-triggers"></a>

Azure Functions support a wide range of trigger types. Here are some of the most common types:

| TYPES OF TRIGGERS |  |
| :--- | :--- |
| Type | Purpose |
| **Timer** | Execute a function at a set interval. |
| **HTTP** | Execute a function when an HTTP request is received. |
| **Blob** | Execute a function when a file is uploaded or updated in Azure Blob storage. |
| **Queue** | Execute a function when a message is added to an Azure Storage queue. |
| **Azure Cosmos DB** | Execute a function when a document changes in a collection. |
| **Event Hub** | Execute a function when an event hub receives a new event. |

### What is a binding? <a id="what-is-a-binding"></a>

A binding is a connection to data within your function. Bindings are optional and come in the form of input and output bindings. An input binding is the data that your function receives. An output binding is the data that your function sends.

Unlike a trigger, a function can have multiple input and output bindings.

In the next exercise, we'll run a function on a schedule using a Timer trigger.  


## Run an Azure Function on a schedule

Completed100 XP

* 10 minutes

It's common to execute a piece of logic at a set interval. Imagine you're a blog owner and you notice that your subscribers aren't reading your most recent posts. You decide that the best action is to send an email once a week to remind them to check your blog. You implement this logic using an Azure function app with a _timer trigger_ to invoke your function weekly.

### What is a timer trigger? <a id="what-is-a-timer-trigger"></a>

A timer trigger is a trigger that executes a function at a consistent interval. To create a timer trigger, you need to supply two pieces of information.

1. A _Timestamp parameter name_, which is simply an identifier to access the trigger in code.
2. A _Schedule_, which is a CRON expression that sets the interval for the timer.

### What is a CRON expression? <a id="what-is-a-cron-expression"></a>

A _CRON expression_ is a string that consists of six fields that represent a set of times.

The order of the six fields in Azure is: `{second} {minute} {hour} {day} {month} {day of the week}`.

For example, a CRON expression to create a trigger that executes every five minutes looks like:logCopy

```text
0 */5 * * * *
```

At first, this string may look confusing. We'll come back and break down these concepts when we have a deeper look at CRON expressions.

To build a CRON expression, you need to have a basic understanding of some of the special characters.

| TABLE 1 |  |  |
| :--- | :--- | :--- |
| Special character | Meaning | Example |
| \* | Selects every value in a field | An asterisk "\*" in the day of the week field means _every_ day. |
| , | Separates items in a list | A comma "1,3" in the day of the week field means just Mondays \(day 1\) and Wednesdays \(day 3\). |
| - | Specifies a range | A hyphen "10-12" in the hour field means a range that includes the hours 10, 11, and 12. |
| / | Specifies an increment | A slash "\*/10" in the minutes field means an increment of every 10 minutes. |

Now we'll go back to the original CRON expression example. Let’s try to understand it better by breaking it down field by field.logCopy

```text
0 */5 * * * *
```

The **first field** represents seconds. This field supports the values 0-59. Because the field contains a zero, it selects the first possible value, which is one second.

The **second field** represents minutes. The value "\*/5" contains two special characters. First, the asterisk \(\*\) means "select every value within the field." Because this field represents minutes, the possible values are 0-59. The second special character is the slash \(/\), which represents an increment. When you combine these characters together, it means for all values 0-59, select every fifth value. An easier way to say that is simply "every five minutes."

The **remaining four fields** represent the hour, day, month, and weekday of the week. An asterisk for these fields means to select every possible value. In this example, we select "every hour of every day of every month."

When you put all the fields together, the expression is read as "on the first second, of every fifth minute of every hour, of every day, of every month".

### How to create a timer trigger <a id="how-to-create-a-timer-trigger"></a>

You can create a timer trigger in the Azure portal. In your Azure function app, select **timer trigger** from the list of trigger templates. Enter the logic that you want to execute. Supply a **Timestamp parameter name** and the **CRON expression**.

In this module, we'll focus on creating triggers in the portal but you can also create triggers programmatically using Core Tools, Visual Studio or Visual Studio Code.

A timer trigger invokes an Azure function app on a consistent schedule. To define the schedule for a timer trigger, we build a CRON expression, which is a string that represents a set of times.



## Exercise - Create a timer trigger

600 XP

* 15 minutes

This module requires a sandbox to complete. You have used 2 of 10 sandboxes for today. More sandboxes will be available tomorrow.

Activate sandboxChoose your development languageC\#PowerShell

In this unit, we create an Azure function app that's invoked every 20 seconds using a timer trigger.

### Create an Azure function app <a id="create-an-azure-function-app"></a>

Let’s start by creating an Azure Function app in the portal.

1. Sign in to the [Azure portal](https://portal.azure.com/learn.docs.microsoft.com) using the same account you activated the sandbox with.
2. On the Azure portal menu or from the **Home** page, select **Create a resource**.

   ![Screenshot of Azure portal menu and Create a resource option.](https://docs.microsoft.com/en-us/learn/modules/execute-azure-function-with-triggers/media/4-create-a-resource.png)

3. Select **Compute**, and then select **Function App**. You can also optionally use the search bar to locate and create the new resource. The **Create Function App** pane appears.

   ![Screenshot of the Azure portal showing the Create a resource pane with the Function App highlighted.](https://docs.microsoft.com/en-us/learn/modules/execute-azure-function-with-triggers/media/4-click-function-app.png)

4. On the **Basics** tab, enter the values for each setting.

   | TABLE 1 |  |
   | :--- | :--- |
   | Setting | Value |
   | **Project Details** |  |
   | Subscription | Select the Azure subscription you'd like to use for this exercise |
   | Resource Group | Create a new resource group called **mslearn-autoscale** |
   | **Instance Details** |  |
   | Function App name | _&lt;your-webapp-name&gt;_ |
   | Publish | Code |
   | Runtime stack | .NET |
   | Version | 3.1 |
   | Region | select a location close to you |

5. Select **Next : Hosting**. Enter the values for each setting.

   | TABLE 2 |  |
   | :--- | :--- |
   | Setting | Value |
   | **Storage** |  |
   | Storage account | You can change the name if you like. It will default to a variation of the App name. |
   | **Operating system** |  |
   | Operating System | Windows |
   | **Plan** |  |
   | Plan type | Consumption \(Serverless\). When using the Consumption Plan type, you're charged for each execution of your function, and resources are automatically allocated based on your app workload. |

6. Select **Review + create**, and then select **Create**. After the function app is deployed, select **Go to resource**.

### Create a timer-triggered function <a id="create-a-timer-triggered-function"></a>

Now we're going to create a timer trigger inside our function.

1. In the menu pane for your Function App, select **Functions**, and then select the Add \(**+**\) button. This action starts the function creation process.
2. In the list of quick start templates, select **Timer trigger**, and then select **Add** at the bottom of the pane. The **TimerTrigger1** pane appears.

### Configure the timer trigger <a id="configure-the-timer-trigger"></a>

We have an Azure function app with logic to print a message to the log window. We're going to set the schedule of the timer to execute every 20 seconds.

1. From the menu pane, select **Integration**. The **Integration** page appears.
2. In the **Trigger** box, select the **Trigger \(myTimer\)** link. The **Edit Trigger** pane appears.
3. Enter the following value into the **Schedule** box.logCopy

   ```text
   */20 * * * * *
   ```

4. Select **Save**.

### Test the timer <a id="test-the-timer"></a>

Now that we've configured the timer, it will invoke the function on the interval we defined.

1. Select **TimerTrigger1**.

    Note

   **TimerTrigger1** is a default name. It's automatically selected when you create the trigger.

2. In the left menu pane, under **Developer**, select **Code + Test**. The **Code + Test** pane appears.
3. Select **Test/Run**. From the right-hand pane, select **Run**. The **Logs** pane appears at the bottom of the page.
4. Observe new messages arrive every 20 seconds in the log window.
5. To stop the function from running, select **Stop**.
6. To disable the function, in the left menu pane, select **Overview**, and then select **Disable**.

