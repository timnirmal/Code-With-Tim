# Explore Azure compute services



## Introduction

* 2 minutes

Imagine that you work as a development lead at Tailwind Traders, a company that specializes in hardware manufacturing. Your management team tells you that the company's website has been having a difficult time keeping up with the application demands. The team wants you to investigate a solution. The front-end web servers are operating near capacity during peak periods of the day, and you need to get a solution in place quickly. But there's a problem. You don't have any free servers to scale out your application.

![Tailwind Traders company logo.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/shared/media/tailwind-traders-logo.png)

You could ask to buy new equipment, but your department's budget is tight. You want to make a good impression with leadership, but you don't know how many servers are necessary for this project, and you don't want to buy more hardware than you need. Even if you were able to procure several servers, you'd need to invest a lot of time to set them up and install software.

Ideally, you'd obtain the resources you need to do the work without too much administration and configure them to do the work. You'd also pay only for the compute resources you need while you're using them.

This scenario is exactly what you can do in Azure. You can create compute resources, configure them to do the work that's needed, and pay for only what you use.

### Learning objectives <a id="learning-objectives"></a>

After completing this module, you'll be able to describe the benefits and usage of:

* Azure Virtual Machines
* Azure App Service
* Azure Container Instances
* Azure Kubernetes Service
* Azure Functions
* Windows Virtual Desktop

### Prerequisites <a id="prerequisites"></a>

* You should be familiar with basic computing concepts and terminology.
* Familiarity with cloud computing is helpful but isn't necessary.

## Overview of Azure compute services

* 4 minutes

Azure compute is an on-demand computing service for running cloud-based applications. It provides computing resources such as disks, processors, memory, networking, and operating systems. The resources are available on-demand and can typically be made available in minutes or even seconds. You pay only for the resources you use, and only for as long as you're using them.

Azure supports a wide range of computing solutions for development and testing, running applications, and extending your datacenter. The service supports Linux, Windows Server, SQL Server, Oracle, IBM, and SAP. Azure also has many services that can run virtual machines \(VMs\). Each service provides different options depending on your requirements. Some of the most prominent services are:

* Azure Virtual Machines
* Azure Container Instances
* Azure App Service
* Azure Functions \(or _serverless computing_\)

![Screenshot of the Azure portal compute services page that includes VMs and containers.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-compute-fundamentals/media/compute-services.png)

### Virtual machines <a id="virtual-machines"></a>

Virtual machines are software emulations of physical computers. They include a virtual processor, memory, storage, and networking resources. VMs host an operating system, and you can install and run software just like a physical computer. When using a remote desktop client, you can use and control the VM as if you were sitting in front of it.

With [Azure Virtual Machines](https://azure.microsoft.com/services/virtual-machines/), you can create and use VMs in the cloud. Virtual Machines provides infrastructure as a service \(IaaS\) and can be used in different ways. When you need total control over an operating system and environment, VMs are an ideal choice. Just like a physical computer, you can customize all the software running on the VM. This ability is helpful when you're running custom software or custom hosting configurations.

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-compute-fundamentals/media/icon-virtual-machine.png)

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-compute-fundamentals/media/icon-scale-sets.png)

### Virtual machine scale sets <a id="virtual-machine-scale-sets"></a>

[Virtual machine scale sets](https://azure.microsoft.com/services/virtual-machine-scale-sets) are an Azure compute resource that you can use to deploy and manage a set of identical VMs. With all VMs configured the same, virtual machine scale sets are designed to support true autoscale. No pre-provisioning of VMs is required. For this reason, it's easier to build large-scale services targeting big compute, big data, and containerized workloads. As demand goes up, more VM instances can be added. As demand goes down, VM instances can be removed. The process can be manual, automated, or a combination of both.

### Containers and Kubernetes <a id="containers-and-kubernetes"></a>

[Container Instances](https://azure.microsoft.com/services/container-instances) and [Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service) are Azure compute resources that you can use to deploy and manage containers. Containers are lightweight, virtualized application environments. They're designed to be quickly created, scaled out, and stopped dynamically. You can run multiple instances of a containerized application on a single host machine.

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-compute-fundamentals/media/icon-container-instance.png)

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-compute-fundamentals/media/icon-app-service.png)

### App Service <a id="app-service"></a>

With [Azure App Service](https://azure.microsoft.com/services/app-service), you can quickly build, deploy, and scale enterprise-grade web, mobile, and API apps running on any platform. You can meet rigorous performance, scalability, security, and compliance requirements while using a fully managed platform to perform infrastructure maintenance. App Service is a platform as a service \(PaaS\) offering.

### Functions <a id="functions"></a>

[Functions](https://azure.microsoft.com/services/functions) are ideal when you're concerned only about the code running your service and not the underlying platform or infrastructure. They're commonly used when you need to perform work in response to an event \(often via a REST request\), timer, or message from another Azure service, and when that work can be completed quickly, within seconds or less.

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-compute-fundamentals/media/icon-functions.png)

## When to use Azure Virtual Machines

* 8 minutes

One possible solution to Tailwind Traders' lack of physical servers is through the use of virtual machines \(VMs\).

With Azure Virtual Machines, you can create and use VMs in the cloud. VMs provide infrastructure as a service \(IaaS\) in the form of a virtualized server and can be used in many ways. Just like a physical computer, you can customize all of the software running on the VM. VMs are an ideal choice when you need:

* Total control over the operating system \(OS\).
* The ability to run custom software.
* To use custom hosting configurations.

An Azure VM gives you the flexibility of virtualization without having to buy and maintain the physical hardware that runs the VM. You still need to configure, update, and maintain the software that runs on the VM.

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-compute-fundamentals/media/azure-vms.png)

You can create and provision a VM in minutes when you select a preconfigured VM image. Selecting an image is one of the most important decisions you'll make when you create a VM. An image is a template used to create a VM. These templates already include an OS and often other software, like development tools or web hosting environments.

#### Examples of when to use VMs <a id="examples-of-when-to-use-vms"></a>

* **During testing and development.** VMs provide a quick and easy way to create different OS and application configurations. Test and development personnel can then easily delete the VMs when they no longer need them.
* **When running applications in the cloud.** The ability to run certain applications in the public cloud as opposed to creating a traditional infrastructure to run them can provide substantial economic benefits. For example, an application might need to handle fluctuations in demand. Shutting down VMs when you don't need them or quickly starting them up to meet a sudden increase in demand means you pay only for the resources you use.
* **When extending your datacenter to the cloud.** An organization can extend the capabilities of its own on-premises network by creating a virtual network in Azure and adding VMs to that virtual network. Applications like SharePoint can then run on an Azure VM instead of running locally. This arrangement makes it easier or less expensive to deploy than in an on-premises environment.
* **During disaster recovery.** As with running certain types of applications in the cloud and extending an on-premises network to the cloud, you can get significant cost savings by using an IaaS-based approach to disaster recovery. If a primary datacenter fails, you can create VMs running on Azure to run your critical applications and then shut them down when the primary datacenter becomes operational again.

### Move to the cloud with VMs <a id="move-to-the-cloud-with-vms"></a>

VMs are also an excellent choice when you move from a physical server to the cloud \(also known as lift and shift\). You can create an image of the physical server and host it within a VM with little or no changes. Just like a physical on-premises server, you must maintain the VM. You update the installed OS and the software it runs.

### Scale VMs in Azure <a id="scale-vms-in-azure"></a>

You can run single VMs for testing, development, or minor tasks. Or you can group VMs together to provide high availability, scalability, and redundancy. No matter what your uptime requirements are, Azure has several features that can meet them. These features include:

* Virtual machine scale sets
* Azure Batch

#### What are virtual machine scale sets? <a id="what-are-virtual-machine-scale-sets"></a>

Virtual machine scale sets let you create and manage a group of identical, load-balanced VMs. Imagine you're running a website that enables scientists to upload astronomy images that need to be processed. If you duplicated the VM, you'd normally need to configure an additional service to route requests between multiple instances of the website. Virtual machine scale sets could do that work for you.

Scale sets allow you to centrally manage, configure, and update a large number of VMs in minutes to provide highly available applications. The number of VM instances can automatically increase or decrease in response to demand or a defined schedule. With virtual machine scale sets, you can build large-scale services for areas such as compute, big data, and container workloads.

#### What is Azure Batch? <a id="what-is-azure-batch"></a>

Azure Batch enables large-scale parallel and high-performance computing \(HPC\) batch jobs with the ability to scale to tens, hundreds, or thousands of VMs.

When you're ready to run a job, Batch does the following:

* Starts a pool of compute VMs for you.
* Installs applications and staging data.
* Runs jobs with as many tasks as you have.
* Identifies failures.
* Requeues work.
* Scales down the pool as work completes.

There might be situations in which you need raw computing power or supercomputer-level compute power. Azure provides these capabilities.  


## When to use Azure Container Instances or Azure Kubernetes Service

* 12 minutes

While virtual machines are an excellent way to reduce costs versus the investments that are necessary for physical hardware, they're still limited to a single operating system per virtual machine. If you want to run multiple instances of an application on a single host machine, containers are an excellent choice.

### What are containers? <a id="what-are-containers"></a>

Containers are a virtualization environment. Much like running multiple virtual machines on a single physical host, you can run multiple containers on a single physical or virtual host. Unlike virtual machines, you don't manage the operating system for a container. Virtual machines appear to be an instance of an operating system that you can connect to and manage, but containers are lightweight and designed to be created, scaled out, and stopped dynamically. While it's possible to create and deploy virtual machines as application demand increases, containers are designed to allow you to respond to changes on demand. With containers, you can quickly restart in case of a crash or hardware interruption. One of the most popular container engines is Docker, which is supported by Azure.

### Compare virtual machines to containers <a id="compare-virtual-machines-to-containers"></a>

The following video highlights several of the important differences between virtual machines and containers.

### Manage containers <a id="manage-containers"></a>

Containers are managed through a container orchestrator, which can start, stop, and scale out application instances as needed. There are two ways to manage both Docker and Microsoft-based containers in Azure: Azure Container Instances and Azure Kubernetes Service \(AKS\).

#### Azure Container Instances <a id="azure-container-instances"></a>

[Azure Container Instances](https://azure.microsoft.com/services/container-instances) offers the fastest and simplest way to run a container in Azure without having to manage any virtual machines or adopt any additional services. It's a platform as a service \(PaaS\) offering that allows you to upload your containers, which it runs for you.

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-compute-fundamentals/media/icon-container-instance.png)

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-compute-fundamentals/media/icon-kubernetes.png)

#### Azure Kubernetes Service <a id="azure-kubernetes-service"></a>

The task of automating, managing, and interacting with a large number of containers is known as orchestration. [Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service) is a complete orchestration service for containers with distributed architectures and large volumes of containers. Orchestration is the task of automating and managing a large number of containers and how they interact.

#### What is Kubernetes? <a id="what-is-kubernetes"></a>

The following video discusses some important details about Kubernetes container orchestration.

### Use containers in your solutions <a id="use-containers-in-your-solutions"></a>

Containers are often used to create solutions by using a _microservice architecture_. This architecture is where you break solutions into smaller, independent pieces. For example, you might split a website into a container hosting your front end, another hosting your back end, and a third for storage. This split allows you to separate portions of your app into logical sections that can be maintained, scaled, or updated independently.

Imagine your website back-end has reached capacity but the front end and storage aren't being stressed. You could:

* Scale the back end separately to improve performance.
* Decide to use a different storage service.
* Replace the storage container without affecting the rest of the application.

#### What is a microservice? <a id="what-is-a-microservice"></a>

The following video discusses some important details about microservices.  
When to use Azure App Service

* 3 minutes

In your research for Tailwind Traders, you've looked at two different ways that you can virtualize your application. Another alternative is to deploy your application's front-end websites to Azure App Service, which makes it easy to respond to application demand.

App Service enables you to build and host web apps, background jobs, mobile back-ends, and RESTful APIs in the programming language of your choice without managing infrastructure. It offers automatic scaling and high availability. App Service supports Windows and Linux and enables automated deployments from GitHub, Azure DevOps, or any Git repo to support a continuous deployment model.

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-compute-fundamentals/media/appservice.png)

This platform as a service \(PaaS\) environment allows you to focus on the website and API logic while Azure handles the infrastructure to run and scale your web applications.

### Azure App Service costs <a id="azure-app-service-costs"></a>

You pay for the Azure compute resources your app uses while it processes requests based on the App Service plan you choose. The App Service plan determines how much hardware is devoted to your host. For example, the plan determines whether it's dedicated or shared hardware and how much memory is reserved for it. There's even a _free_ tier you can use to host small, low-traffic sites.

### Types of app services <a id="types-of-app-services"></a>

With App Service, you can host most common app service styles like:

* Web apps
* API apps
* WebJobs
* Mobile apps

App Service handles most of the infrastructure decisions you deal with in hosting web-accessible apps:

* Deployment and management are integrated into the platform.
* Endpoints can be secured.
* Sites can be scaled quickly to handle high traffic loads.
* The built-in load balancing and traffic manager provide high availability.

All of these app styles are hosted in the same infrastructure and share these benefits. This flexibility makes App Service the ideal choice to host web-oriented applications.

#### Web apps <a id="web-apps"></a>

App Service includes full support for hosting web apps by using ASP.NET, ASP.NET Core, Java, Ruby, Node.js, PHP, or Python. You can choose either Windows or Linux as the host operating system.

#### API apps <a id="api-apps"></a>

Much like hosting a website, you can build REST-based web APIs by using your choice of language and framework. You get full Swagger support and the ability to package and publish your API in Azure Marketplace. The produced apps can be consumed from any HTTP- or HTTPS-based client.

#### WebJobs <a id="webjobs"></a>

You can use the WebJobs feature to run a program \(.exe, Java, PHP, Python, or Node.js\) or script \(.cmd, .bat, PowerShell, or Bash\) in the same context as a web app, API app, or mobile app. They can be scheduled or run by a trigger. WebJobs are often used to run background tasks as part of your application logic.

#### Mobile apps <a id="mobile-apps"></a>

Use the Mobile Apps feature of App Service to quickly build a back end for iOS and Android apps. With just a few clicks in the Azure portal, you can:

* Store mobile app data in a cloud-based SQL database.
* Authenticate customers against common social providers, such as MSA, Google, Twitter, and Facebook.
* Send push notifications.
* Execute custom back-end logic in C\# or Node.js.

On the mobile app side, there's SDK support for native iOS and Android, Xamarin, and React native apps.



## When to use Azure Functions

* 10 minutes

After consulting with several of your fellow developers at Tailwind Traders, you've determined that some of your application logic is event driven. In other words, for a large amount of time, your application is waiting for a particular input before it performs any processing. To reduce your costs, you want to avoid having to pay for the time that your application is waiting for input. With that in mind, you've decided to investigate Azure Functions to see if it can help.

_Serverless_ computing is the abstraction of servers, infrastructure, and operating systems. With serverless computing, Azure takes care of managing the server infrastructure and the allocation and deallocation of resources based on demand. Infrastructure isn't your responsibility. Scaling and performance are handled automatically. You're billed only for the exact resources you use. There's no need to even reserve capacity.

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-compute-fundamentals/media/serverless.png)

Serverless computing includes the abstraction of servers, an event-driven scale, and micro-billing:

* **Abstraction of servers**: Serverless computing abstracts the servers you run on. You never explicitly reserve server instances. The platform manages that for you. Each function execution can run on a different compute instance. This execution context is transparent to the code. With serverless architecture, you deploy your code, which then runs with high availability.
* **Event-driven scale**: Serverless computing is an excellent fit for workloads that respond to incoming events. Events include triggers by:

  * Timers, for example, if a function needs to run every day at 10:00 AM UTC.
  * HTTP, for example, API and webhook scenarios.
  * Queues, for example, with order processing.
  * And much more.

  Instead of writing an entire application, the developer authors a function, which contains both code and metadata about its triggers and bindings. The platform automatically schedules the function to run and scales the number of compute instances based on the rate of incoming events. Triggers define how a function is invoked. Bindings provide a declarative way to connect to services from within the code.

* **Micro-billing**: Traditional computing bills for a block of time like paying a monthly or annual rate for website hosting. This method of billing is convenient but isn't always cost effective. Even if a customer's website gets only one hit a day, they still pay for a full day's worth of availability. With serverless computing, they pay only for the time their code runs. If no active function executions occur, they're not charged. For example, if the code runs once a day for two minutes, they're charged for one execution and two minutes of computing time.

**Serverless computing in Azure**

Azure has two implementations of serverless compute:

* **Azure Functions**: Functions can execute code in almost any modern language.
* **Azure Logic Apps**: Logic apps are designed in a web-based designer and can execute logic triggered by Azure services without writing any code.

### Azure Functions <a id="azure-functions"></a>

When you're concerned only about the code running your service, and not the underlying platform or infrastructure, using Azure Functions is ideal. Functions are commonly used when you need to perform work in response to an event \(often via a REST request\), timer, or message from another Azure service, and when that work can be completed quickly, within seconds or less.

Functions scale automatically based on demand, so they're a solid choice when demand is variable. For example, you might receive messages from an IoT solution that's used to monitor a fleet of delivery vehicles. You'll likely have more data arriving during business hours.

Using a virtual machine-based approach, you'd incur costs even when the virtual machine is idle. With functions, Azure runs your code when it's triggered and automatically deallocates resources when the function is finished. In this model, you're only charged for the CPU time used while your function runs.

Functions can be either stateless or stateful. When they're stateless \(the default\), they behave as if they're restarted every time they respond to an event. When they're stateful \(called Durable Functions\), a context is passed through the function to track prior activity.

Functions are a key component of serverless computing. They're also a general compute platform for running any type of code. If the needs of the developer's app change, you can deploy the project in an environment that isn't serverless. This flexibility allows you to manage scaling, run on virtual networks, and even completely isolate the functions.

### Azure Logic Apps <a id="azure-logic-apps"></a>

Logic apps are similar to functions. Both enable you to trigger logic based on an event. Where functions execute code, logic apps execute _workflows_ that are designed to automate business scenarios and are built from predefined logic blocks.

Every Azure logic app workflow starts with a trigger, which fires when a specific event happens or when newly available data meets specific criteria. Many triggers include basic scheduling capabilities, so developers can specify how regularly their workloads will run. Each time the trigger fires, the Logic Apps engine creates a logic app instance that runs the actions in the workflow. These actions can also include data conversions and flow controls, such as conditional statements, switch statements, loops, and branching.

You create logic app workflows by using a visual designer on the Azure portal or in Visual Studio. The workflows are persisted as a JSON file with a known workflow schema.

Azure provides more than 200 different connectors and processing blocks to interact with different services. These resources include the most popular enterprise apps. You can also build custom connectors and workflow steps if the service you need to interact with isn't covered. You then use the visual designer to link connectors and blocks together. You pass data through the workflow to do custom processing, often all without writing any code.

As an example, let's say a ticket arrives in Zendesk. You could:

* Detect the intent of the message with cognitive services.
* Create an item in SharePoint to track the issue.
* Add the customer to your Dynamics 365 CRM system if they aren't already in your database.
* Send a follow-up email to acknowledge their request.

All of those actions could be designed in a visual designer, which makes it easy to see the logic flow. For this reason, it's ideal for a business analyst role.

### Functions vs. Logic Apps <a id="functions-vs-logic-apps"></a>

Functions and Logic Apps can both create complex orchestrations. An orchestration is a collection of functions or steps that are executed to accomplish a complex task.

* With Functions, you write code to complete each step.
* With Logic Apps, you use a GUI to define the actions and how they relate to one another.

You can mix and match services when you build an orchestration, calling functions from logic apps and calling logic apps from functions. Here are some common differences between the two.

| FUNCTIONS VS. LOGIC APPS |  |  |
| :--- | :--- | :--- |
|  | Functions | Logic Apps |
| State | Normally stateless, but Durable Functions provide state. | Stateful. |
| Development | Code-first \(imperative\). | Designer-first \(declarative\). |
| Connectivity | About a dozen built-in binding types. Write code for custom bindings. | Large collection of connectors. Enterprise Integration Pack for B2B scenarios. Build custom connectors. |
| Actions | Each activity is an Azure function. Write code for activity functions. | Large collection of ready-made actions. |
| Monitoring | Azure Application Insights. | Azure portal, Log Analytics. |
| Management | REST API, Visual Studio. | Azure portal, REST API, PowerShell, Visual Studio. |
| Execution context | Can run locally or in the cloud. | Runs only in the cloud. |

## When to use Windows Virtual Desktop

* 9 minutes

In addition to the challenges that Tailwind Traders has been facing with application scale, your manager has asked you to put together a new development team of remote workers.

This task would normally require setting up several new computers with all of the requisite development tools for your new team. Then you would need to ship them to the respective developers across the country. The time to procure, set up, and ship each of these computers would be costly. Also, all of your new developers have their own computing devices that are running a mixture of Windows, Android, and macOS operating systems.

You want to find a way to expedite the deployment process for your remote workers. You also want to keep your management costs to a minimum. With that in mind, you want to see how Windows Virtual Desktop can help your organization.

### What is Windows Virtual Desktop? <a id="what-is-windows-virtual-desktop"></a>

Windows Virtual Desktop on Azure is a desktop and application virtualization service that runs on the cloud. It enables your users to use a cloud-hosted version of Windows from any location. Windows Virtual Desktop works across devices like Windows, Mac, iOS, Android, and Linux. It works with apps that you can use to access remote desktops and apps. You can also use most modern browsers to access Windows Virtual Desktop-hosted experiences.

The following video gives you an overview of Windows Virtual Desktop.

### Why should you use Windows Virtual Desktop? <a id="why-should-you-use-windows-virtual-desktop"></a>

#### Provide the best user experience <a id="provide-the-best-user-experience"></a>

Users have the freedom to connect to Windows Virtual Desktop with any device over the internet. They use a Windows Virtual Desktop client to connect to their published Windows desktop and applications. This client could either be a native application on the device or the Windows Virtual Desktop HTML5 web client.

You can make sure your session host virtual machines \(VMs\) run near apps and services that connect to your datacenter or the cloud. This way your users stay productive and don't encounter long load times.

User sign-in to Windows Virtual Desktop is fast because user profiles are containerized by using FSLogix. At sign-in, the user profile container is dynamically attached to the computing environment. The user profile is immediately available and appears in the system exactly like a native user profile.

You can provide individual ownership through personal \(persistent\) desktops. For example, you might want to provide personal remote desktops for members of an engineering team. Then they can add or remove programs without impacting other users on that remote desktop.

#### Enhance security <a id="enhance-security"></a>

Windows Virtual Desktop provides centralized security management for users' desktops with Azure Active Directory \(Azure AD\). You can enable multifactor authentication to secure user sign-ins. You can also secure access to data by assigning granular role-based access controls \(RBACs\) to users.

With Windows Virtual Desktop, the data and apps are separated from the local hardware. Windows Virtual Desktop runs them instead on a remote server. The risk of confidential data being left on a personal device is reduced.

User sessions are isolated in both single and multi-session environments.

Windows Virtual Desktop also improves security by using reverse connect technology. This connection type is more secure than the Remote Desktop Protocol. We don't open inbound ports to the session host VMs.

### What are some key features of Windows Virtual Desktop? <a id="what-are-some-key-features-of-windows-virtual-desktop"></a>

#### Simplified management <a id="simplified-management"></a>

Windows Virtual Desktop is an Azure service, so it will be familiar to Azure administrators. You use Azure AD and RBACs to manage access to resources. With Azure, you also get tools to automate VM deployments, manage VM updates, and provide disaster recovery. As with other Azure services, Windows Virtual Desktop uses Azure Monitor for monitoring and alerts. This standardization lets admins identify issues through a single interface.

#### Performance management <a id="performance-management"></a>

Windows Virtual Desktop gives you options to load balance users on your VM host pools. _Host pools_ are collections of VMs with the same configuration assigned to multiple users. For the best performance, you can configure load balancing to occur as users sign in \(breadth mode\). With breadth mode, users are sequentially allocated across the host pool for your workload. To save costs, you can configure your VMs for depth mode load balancing where users are fully allocated on one VM before moving to the next. Windows Virtual Desktop provides tools to automatically provision additional VMs when incoming demand exceeds a specified threshold.

#### Multi-session Windows 10 deployment <a id="multi-session-windows-10-deployment"></a>

Windows Virtual Desktop lets you use Windows 10 Enterprise multi-session, the only Windows client-based operating system that enables multiple concurrent users on a single VM. Windows Virtual Desktop also provides a more consistent experience with broader application support compared to Windows Server-based operating systems.

### How can you reduce costs with Windows Virtual Desktop? <a id="how-can-you-reduce-costs-with-windows-virtual-desktop"></a>

#### Bring your own licenses <a id="bring-your-own-licenses"></a>

Windows Virtual Desktop is available to you at no additional cost if you have an eligible Microsoft 365 license. Just pay for the Azure resources used by Windows Virtual Desktop.

* Bring your eligible Windows or Microsoft 365 license to get Windows 10 Enterprise and Windows 7 Enterprise desktops and apps at no additional cost.
* If you're an eligible Microsoft Remote Desktop Services Client Access License customer, Windows Server Remote Desktop Services desktops and apps are available at no additional cost.

#### Save on compute costs <a id="save-on-compute-costs"></a>

Buy one-year or three-year Azure Reserved Virtual Machine Instances to save you up to 72 percent versus pay-as-you-go pricing. You can pay for a reservation up front or monthly. Reservations provide a billing discount and don't affect the runtime state of your resources.



## Summary

* 1 minute

In this module, you learned how you can help Tailwind Traders resolve its application demand challenges through the use of Azure virtualization services like Azure Virtual Machines, Azure Container Instances, and Azure Kubernetes Service. You also learned how you can use:

* Azure App Service to create your website front-ends.
* Azure Functions to create event-driven application logic that only runs when you need it.
* Windows Virtual Desktop to quickly provide a customized operating system and software environment for your remote workers.

### Learn more <a id="learn-more"></a>

* [Azure compute](https://azure.microsoft.com/product-categories/compute)
* [Virtual Machines documentation](https://docs.microsoft.com/en-us/azure/virtual-machines/)
* [Windows virtual machines in Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/)
* [Linux virtual machines in Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/)
* [Azure App Service documentation](https://docs.microsoft.com/en-us/azure/app-service/)
* [Azure Container Instances](https://azure.microsoft.com/services/container-instances)
* [Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service)
* [Azure Functions documentation](https://docs.microsoft.com/en-us/azure/azure-functions/)
* [Windows Virtual Desktop documentation](https://docs.microsoft.com/en-us/azure/virtual-desktop/)

