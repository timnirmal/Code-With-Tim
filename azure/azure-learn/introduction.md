# Introduction

## What is cloud computing?

It's the delivery of computing services over the internet, which is otherwise known as the cloud. These services include servers, storage, databases, networking, software, analytics, and intelligence. Cloud computing offers faster innovation, flexible resources, and economies of scale.

### Why is cloud computing typically cheaper to use? <a id="why-is-cloud-computing-typically-cheaper-to-use"></a>

Cloud computing is the delivery of computing services over the internet by using a pay-as-you-go pricing model. You typically pay only for the cloud services you use, which helps you:

* Lower your operating costs.
* Run your infrastructure more efficiently.
* Scale as your business needs change.

To put it another way, cloud computing is a way to rent compute power and storage from someone else's datacenter. You can treat cloud resources like you would your resources in your own datacenter. When you're done using them, you give them back. You're billed only for what you use.

### Why should I move to the cloud? <a id="why-should-i-move-to-the-cloud"></a>

The cloud helps you move faster and innovate in ways that were once nearly impossible.

In our ever-changing digital world, two trends emerge:

* Teams deliver new features to their users at record speeds.
* Users expect an increasingly rich and immersive experience with their devices and with software.

Software releases were once scheduled in terms of months or even years. Today, teams release features in smaller batches that are often scheduled in days or weeks. Some teams even deliver software updates continuously--sometimes with multiple releases within the same day.

Think of all the ways you interact with devices that you couldn't do a few years ago. Many devices can recognize your face and respond to voice commands. Augmented reality changes the way you interact with the physical world. Household appliances are even beginning to act intelligently. These technologies are only a few examples, and many of them are powered by the cloud.

To power your services and deliver innovative and novel user experiences more quickly, the cloud provides on-demand access to:

* A nearly limitless pool of raw compute, storage, and networking components.
* Speech recognition and other cognitive services that help make your application stand out from the crowd.
* Analytics services that deliver telemetry data from your software and devices.

### What are some cloud computing advantages? <a id="what-are-some-cloud-computing-advantages"></a>

There are several benefits that a cloud environment has over a physical environment. For example, cloud-based applications employ a myriad of related strategies:

* **Reliability**: Depending on the service-level agreement that you choose, your cloud-based applications can provide a continuous user experience with no apparent downtime even when things go wrong.
* **Scalability**: Applications in the cloud can be scaled in two ways, while taking advantage of autoscaling:
  * _Vertically_: Computing capacity can be increased by adding RAM or CPUs to a virtual machine.
  * _Horizontally_: Computing capacity can be increased by adding instances of a resource, such as adding more virtual machines to your configuration.
* **Elasticity**: Cloud-based applications can be configured to always have the resources they need.
* **Agility**: Cloud-based resources can be deployed and configured quickly as your application requirements change.
* **Geo-distribution**: Applications and data can be deployed to regional datacenters around the globe, so your customers always have the best performance in their region.
* **Disaster recovery**: By taking advantage of cloud-based backup services, data replication, and geo-distribution, you can deploy your applications with the confidence that comes from knowing that your data is safe in the event that disaster should occur.

### What are cloud service models? <a id="what-are-cloud-service-models"></a>

Cloud computing falls into one of the following computing models. If you've been around cloud computing for a while, you've probably seen the terms infrastructure as a service \(IaaS\), platform as a service \(PaaS\), and software as a service \(SaaS\) for the different cloud service models. These models define the different level of shared responsibility that a cloud provider and cloud tenant are responsible for.

| Computing model | Description |
| :--- | :--- |
| **IaaS** | This cloud service model is the closest to managing physical servers. A cloud provider keeps the hardware up to date, but operating system maintenance and network configuration is left to the cloud tenant. For example, Azure virtual machines are fully operational virtual compute devices running in Microsoft's datacenters. An advantage of this cloud service model is rapid deployment of new compute devices. Setting up a new virtual machine is considerably faster than procuring, installing, and configuring a physical server. |
| **PaaS** | This cloud service model is a managed hosting environment. The cloud provider manages the virtual machines and networking resources, and the cloud tenant deploys their applications into the managed hosting environment. For example, Azure App Services provides a managed hosting environment where developers can upload their web applications without having to deal with the physical hardware and software requirements. |
| **SaaS** | In this cloud service model, the cloud provider manages all aspects of the application environment, such as virtual machines, networking resources, data storage, and applications. The cloud tenant only needs to provide their data to the application managed by the cloud provider. For example, Office 365 provides a fully working version of Office that runs in the cloud. All that you need to do is create your content, and Office 365 takes care of everything else. |

The following illustration demonstrates the services that might run in each of the cloud service models.

![](../../.gitbook/assets/image%20%283%29.png)

The following chart illustrates the various levels of responsibility between a cloud provider and a cloud tenant.

![](../../.gitbook/assets/image%20%284%29.png)

### What is serverless computing? <a id="what-is-serverless-computing"></a>

Overlapping with PaaS, serverless computing enables developers to build applications faster by eliminating the need for them to manage infrastructure. With serverless applications, the cloud service provider automatically provisions, scales, and manages the infrastructure required to run the code. Serverless architectures are highly scalable and event-driven. They use resources only when a specific function or trigger occurs.

In understanding the definition of serverless computing, it's important to note that servers are still running the code. The serverless name comes from the fact that the tasks associated with infrastructure provisioning and management are invisible to the developer. This approach enables developers to increase their focus on the business logic and deliver more value to the core of the business. Serverless computing helps teams increase their productivity and bring products to market faster. It allows organizations to better optimize resources and stay focused on innovation.

### What are public, private, and hybrid clouds? <a id="what-are-public-private-and-hybrid-clouds"></a>

There are three deployment models for cloud computing: _public cloud_, _private cloud_, and _hybrid cloud_. Each deployment model has different aspects that you should consider as you migrate to the cloud.

| WHAT ARE PUBLIC, PRIVATE, AND HYBRID CLOUDS? |  |
| :--- | :--- |
| Deployment model | Description |
| **Public cloud** | Services are offered over the public internet and available to anyone who wants to purchase them. Cloud resources like servers and storage are owned and operated by a third-party cloud service provider and delivered over the internet. |
| **Private cloud** | Computing resources are used exclusively by users from one business or organization. A private cloud can be physically located at your organization's on-site datacenter. It also can be hosted by a third-party service provider. |
| **Hybrid cloud** | This computing environment combines a public cloud and a private cloud by allowing data and applications to be shared between them. |

The following image illustrates several of the cloud computing concepts that are presented in this unit. In this example, several factors are demonstrated when you're considering where to deploy a database server in a hybrid cloud environment. As your resources move from on-premises to off-premises, your costs are reduced, and your administration requirements decrease.

![Illustration showing the cloud computing continuum.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/intro-to-azure-fundamentals/media/cloud-computing-continuum.png)

## What is Azure

Azure is a continually expanding set of cloud services that help your organization meet your current and future business challenges. Azure gives you the freedom to build, manage, and deploy applications on a massive global network using your favorite tools and frameworks.

### What does Azure offer? <a id="what-does-azure-offer"></a>

With help from Azure, you have everything you need to build your next great solution. The following table lists several of the benefits that Azure provides, so you can easily invent with purpose.

**Be ready for the future:** Continuous innovation from Microsoft supports your development today and your product visions for tomorrow.

![Image that shows a launching rocket ship to represent the future.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/intro-to-azure-fundamentals/media/future.png)

![Image that shows three slider bars to represent choice in your usage needs.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/intro-to-azure-fundamentals/media/build.png)

**Build on your terms:** You have choices. With a commitment to open source, and support for all languages and frameworks, build how you want and deploy where you want to.

**Operate hybrid seamlessly:** On-premises, in the cloud, and at the edge--we'll meet you where you are. Integrate and manage your environments with tools and services designed for a hybrid cloud solution.

![Image that shows a brick building datacenter next to a cloud datacenter to represent both datacenters working together.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/intro-to-azure-fundamentals/media/hybrid.png)

![Image that shows a shield over a cloud to represent cloud security.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/intro-to-azure-fundamentals/media/trust.png)

**Trust your cloud:** Get security from the ground up, backed by a team of experts, and proactive compliance trusted by enterprises, governments, and startups.

### What can I do with Azure? <a id="what-can-i-do-with-azure"></a>

Azure provides more than 100 services that enable you to do everything from running your existing applications on virtual machines to exploring new software paradigms, such as intelligent bots and mixed reality.

Many teams start exploring the cloud by moving their existing applications to virtual machines that run in Azure. Migrating your existing apps to virtual machines is a good start, but the cloud is much more than a different place to run your virtual machines.

For example, Azure provides AI and machine-learning services that can naturally communicate with your users through vision, hearing, and speech. It also provides storage solutions that dynamically grow to accommodate massive amounts of data. Azure services enable solutions that aren't feasible without the power of the cloud.

### How does Azure work? <a id="how-does-azure-work"></a>

### What is the Azure portal? <a id="what-is-the-azure-portal"></a>

The Azure portal is a web-based, unified console that provides an alternative to command-line tools. With the Azure portal, you can manage your Azure subscription by using a graphical user interface. You can:

* Build, manage, and monitor everything from simple web apps to complex cloud deployments.
* Create custom dashboards for an organized view of resources.
* Configure accessibility options for an optimal experience.

The Azure portal is designed for resiliency and continuous availability. It maintains a presence in every Azure datacenter. This configuration makes the Azure portal resilient to individual datacenter failures and avoids network slowdowns by being close to users. The Azure portal updates continuously and requires no downtime for maintenance activities.

[![Screenshot that shows the Azure portal.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/intro-to-azure-fundamentals/media/azure-portal.png)](https://docs.microsoft.com/en-us/learn/azure-fundamentals/intro-to-azure-fundamentals/media/azure-portal.png#lightbox)

### What is Azure Marketplace? <a id="what-is-azure-marketplace"></a>

[Azure Marketplace](https://azuremarketplace.microsoft.com/) helps connect users with Microsoft partners, independent software vendors, and startups that are offering their solutions and services, which are optimized to run on Azure. Azure Marketplace customers can find, try, purchase, and provision applications and services from hundreds of leading service providers. All solutions and services are certified to run on Azure.

[![Screenshot that shows Azure Marketplace.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/intro-to-azure-fundamentals/media/marketplace.png)](https://docs.microsoft.com/en-us/learn/azure-fundamentals/intro-to-azure-fundamentals/media/marketplace.png#lightbox)

The solution catalog spans several industry categories such as open-source container platforms, virtual machine images, databases, application build and deployment software, developer tools, threat detection, and blockchain. Using Azure Marketplace, you can provision end-to-end solutions quickly and reliably, hosted in your own Azure environment. At the time of writing, there are more than 8,000 listings.

Azure Marketplace is designed for IT pros and cloud developers interested in commercial and IT software. Microsoft partners also use it as a launch point for all joint go-to-market activities.

## Tour of Azure services

### Azure services <a id="azure-services"></a>

Here's a big-picture view of the available services and features in Azure.

[![Diagram showing overall view of popular Azure services with sections for security and management, platform services, hybrid cloud, and infrastructure services.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/intro-to-azure-fundamentals/media/azure-services.png)](https://docs.microsoft.com/en-us/learn/azure-fundamentals/intro-to-azure-fundamentals/media/azure-services.png#lightbox)

Let's take a closer look at the most commonly used categories:

* Compute
* Networking
* Storage
* Mobile
* Databases
* Web
* Internet of Things \(IoT\)
* Big data
* AI
* DevOps

#### Compute <a id="compute"></a>

Compute services are often one of the primary reasons why companies move to the Azure platform. Azure provides a range of options for hosting applications and services. Here are some examples of compute services in Azure.

| TABLE 1 |  |
| :--- | :--- |
| Service name | Service function |
| Azure Virtual Machines | Windows or Linux virtual machines \(VMs\) hosted in Azure. |
| Azure Virtual Machine Scale Sets | Scaling for Windows or Linux VMs hosted in Azure. |
| Azure Kubernetes Service | Cluster management for VMs that run containerized services. |
| Azure Service Fabric | Distributed systems platform that runs in Azure or on-premises. |
| Azure Batch | Managed service for parallel and high-performance computing applications. |
| Azure Container Instances | Containerized apps run on Azure without provisioning servers or VMs. |
| Azure Functions | An event-driven, serverless compute service. |

#### Networking <a id="networking"></a>

Linking compute resources and providing access to applications is the key function of Azure networking. Networking functionality in Azure includes a range of options to connect the outside world to services and features in the global Azure datacenters.

Here are some examples of networking services in Azure.

| TABLE 2 |  |
| :--- | :--- |
| Service name | Service function |
| Azure Virtual Network | Connects VMs to incoming virtual private network \(VPN\) connections. |
| Azure Load Balancer | Balances inbound and outbound connections to applications or service endpoints. |
| Azure Application Gateway | Optimizes app server farm delivery while increasing application security. |
| Azure VPN Gateway | Accesses Azure Virtual Networks through high-performance VPN gateways. |
| Azure DNS | Provides ultra-fast DNS responses and ultra-high domain availability. |
| Azure Content Delivery Network | Delivers high-bandwidth content to customers globally. |
| Azure DDoS Protection | Protects Azure-hosted applications from distributed denial of service \(DDOS\) attacks. |
| Azure Traffic Manager | Distributes network traffic across Azure regions worldwide. |
| Azure ExpressRoute | Connects to Azure over high-bandwidth dedicated secure connections. |
| Azure Network Watcher | Monitors and diagnoses network issues by using scenario-based analysis. |
| Azure Firewall | Implements high-security, high-availability firewall with unlimited scalability. |
| Azure Virtual WAN | Creates a unified wide area network \(WAN\) that connects local and remote sites. |

#### Storage <a id="storage"></a>

Azure provides four main types of storage services.

| TABLE 3 |  |
| :--- | :--- |
| Service name | Service function |
| Azure Blob storage | Storage service for very large objects, such as video files or bitmaps. |
| Azure File storage | File shares that can be accessed and managed like a file server. |
| Azure Queue storage | A data store for queuing and reliably delivering messages between applications. |
| Azure Table storage | Table storage is a service that stores non-relational structured data \(also known as structured NoSQL data\) in the cloud, providing a key/attribute store with a schemaless design.. |

These services all share several common characteristics:

* **Durable** and highly available with redundancy and replication.
* **Secure** through automatic encryption and role-based access control.
* **Scalable** with virtually unlimited storage.
* **Managed**, handling maintenance and any critical problems for you.
* **Accessible** from anywhere in the world over HTTP or HTTPS.

#### Mobile <a id="mobile"></a>

With Azure, developers can create mobile back-end services for iOS, Android, and Windows apps quickly and easily. Features that used to take time and increase project risks, such as adding corporate sign-in and then connecting to on-premises resources such as SAP, Oracle, SQL Server, and SharePoint, are now simple to include.

Other features of this service include:

* Offline data synchronization.
* Connectivity to on-premises data.
* Broadcasting push notifications.
* Autoscaling to match business needs.

#### Databases <a id="databases"></a>

Azure provides multiple database services to store a wide variety of data types and volumes. And with global connectivity, this data is available to users instantly.

| TABLE 4 |  |
| :--- | :--- |
| Service name | Service function |
| Azure Cosmos DB | Globally distributed database that supports NoSQL options. |
| Azure SQL Database | Fully managed relational database with auto-scale, integral intelligence, and robust security. |
| Azure Database for MySQL | Fully managed and scalable MySQL relational database with high availability and security. |
| Azure Database for PostgreSQL | Fully managed and scalable PostgreSQL relational database with high availability and security. |
| SQL Server on Azure Virtual Machines | Service that hosts enterprise SQL Server apps in the cloud. |
| Azure Synapse Analytics | Fully managed data warehouse with integral security at every level of scale at no extra cost. |
| Azure Database Migration Service | Service that migrates databases to the cloud with no application code changes. |
| Azure Cache for Redis | Fully managed service caches frequently used and static data to reduce data and application latency. |
| Azure Database for MariaDB | Fully managed and scalable MariaDB relational database with high availability and security. |

#### Web <a id="web"></a>

Having a great web experience is critical in today's business world. Azure includes first-class support to build and host web apps and HTTP-based web services. The following Azure services are focused on web hosting.

| TABLE 5 |  |
| :--- | :--- |
| Service name | Description |
| Azure App Service | Quickly create powerful cloud web-based apps. |
| Azure Notification Hubs | Send push notifications to any platform from any back end. |
| Azure API Management | Publish APIs to developers, partners, and employees securely and at scale. |
| Azure Cognitive Search | Deploy this fully managed search as a service. |
| Web Apps feature of Azure App Service | Create and deploy mission-critical web apps at scale. |
| Azure SignalR Service | Add real-time web functionalities easily. |

#### IoT <a id="iot"></a>

People are able to access more information than ever before. Personal digital assistants led to smartphones, and now there are smart watches, smart thermostats, and even smart refrigerators. Personal computers used to be the norm. Now the internet allows any item that's online-capable to access valuable information. This ability for devices to garner and then relay information for data analysis is referred to as IoT.

Many services can assist and drive end-to-end solutions for IoT on Azure.

| TABLE 6 |  |
| :--- | :--- |
| Service name | Description |
| IoT Central | Fully managed global IoT software as a service \(SaaS\) solution that makes it easy to connect, monitor, and manage IoT assets at scale. |
| Azure IoT Hub | Messaging hub that provides secure communications between and monitoring of millions of IoT devices. |
| IoT Edge | Fully managed service that allows data analysis models to be pushed directly onto IoT devices, which allows them to react quickly to state changes without needing to consult cloud-based AI models. |

#### Big data <a id="big-data"></a>

Data comes in all formats and sizes. When we talk about big data, we're referring to _large_ volumes of data. Data from weather systems, communications systems, genomic research, imaging platforms, and many other scenarios generate hundreds of gigabytes of data. This amount of data makes it hard to analyze and make decisions. It's often so large that traditional forms of processing and analysis are no longer appropriate.

Open-source cluster technologies have been developed to deal with these large data sets. Azure supports a broad range of technologies and services to provide big data and analytic solutions.

| TABLE 7 |  |
| :--- | :--- |
| Service name | Description |
| Azure Synapse Analytics | Run analytics at a massive scale by using a cloud-based enterprise data warehouse that takes advantage of massively parallel processing to run complex queries quickly across petabytes of data. |
| Azure HDInsight | Process massive amounts of data with managed clusters of Hadoop clusters in the cloud. |
| Azure Databricks | Integrate this collaborative Apache Spark-based analytics service with other big data services in Azure. |

#### AI <a id="ai"></a>

AI, in the context of cloud computing, is based around a broad range of services, the core of which is machine learning. Machine learning is a data science technique that allows computers to use existing data to forecast future behaviors, outcomes, and trends. Using machine learning, computers learn without being explicitly programmed.

Forecasts or predictions from machine learning can make apps and devices smarter. For example, when you shop online, machine learning helps recommend other products you might like based on what you've purchased. Or when your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud. And when your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.

Here are some of the most common AI and machine learning service types in Azure.

| TABLE 8 |  |
| :--- | :--- |
| Service name | Description |
| Azure Machine Learning Service | Cloud-based environment you can use to develop, train, test, deploy, manage, and track machine learning models. It can auto-generate a model and auto-tune it for you. It will let you start training on your local machine, and then scale out to the cloud. |
| Azure ML Studio | Collaborative visual workspace where you can build, test, and deploy machine learning solutions by using prebuilt machine learning algorithms and data-handling modules. |

A closely related set of products are the _cognitive services_. You can use these prebuilt APIs in your applications to solve complex problems.

| TABLE 9 |  |
| :--- | :--- |
| Service name | Description |
| Vision | Use image-processing algorithms to smartly identify, caption, index, and moderate your pictures and videos. |
| Speech | Convert spoken audio into text, use voice for verification, or add speaker recognition to your app. |
| Knowledge mapping | Map complex information and data to solve tasks such as intelligent recommendations and semantic search. |
| Bing Search | Add Bing Search APIs to your apps and harness the ability to comb billions of webpages, images, videos, and news with a single API call. |
| Natural Language processing | Allow your apps to process natural language with prebuilt scripts, evaluate sentiment, and learn how to recognize what users want. |

#### DevOps <a id="devops"></a>

DevOps brings together people, processes, and technology by automating software delivery to provide continuous value to your users. With Azure DevOps, you can create _build_ and _release_ pipelines that provide continuous integration, delivery, and deployment for your applications. You can integrate repositories and application tests, perform application monitoring, and work with build artifacts. You can also work with and backlog items for tracking, automate infrastructure deployment, and integrate a range of third-party tools and services such as Jenkins and Chef. All of these functions and many more are closely integrated with Azure to allow for consistent, repeatable deployments for your applications to provide streamlined build and release processes.

| TABLE 10 |  |
| :--- | :--- |
| Service name | Description |
| Azure DevOps | Use development collaboration tools such as high-performance pipelines, free private Git repositories, configurable Kanban boards, and extensive automated and cloud-based load testing. Formerly known as Visual Studio Team Services. |
| Azure DevTest Labs | Quickly create on-demand Windows and Linux environments to test or demo applications directly from deployment pipelines. |

## Get started with Azure accounts

* 2 minutes

To create and use Azure services, you need an Azure subscription. When you're completing Learn modules, most of the time a temporary subscription is created for you, which runs in an environment called the Learn sandbox. When you're working with your own applications and business needs, you need to create an Azure account, and a subscription will be created for you. After you've created an Azure account, you're free to create additional subscriptions. For example, your company might use a single Azure account for your business and separate subscriptions for development, marketing, and sales departments. After you've created an Azure subscription, you can start creating Azure resources within each subscription.

[![Illustration showing the different levels of account scope.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/intro-to-azure-fundamentals/media/scope-levels.png)](https://docs.microsoft.com/en-us/learn/azure-fundamentals/intro-to-azure-fundamentals/media/scope-levels-expanded.png#lightbox)

If you're new to Azure, you can sign up for a free account on the Azure website to start exploring at no cost to you. When you're ready, you can choose to upgrade your free account. You can create a new subscription that enables you to start paying for Azure services you need to use that are beyond the limits of a free account.

### Create an Azure account <a id="create-an-azure-account"></a>

You can purchase Azure access directly from Microsoft by signing up on the [Azure website](https://azure.microsoft.com/) or through a Microsoft representative. You can also purchase Azure access through a Microsoft partner. Cloud Solution Provider partners offer a range of complete managed-cloud solutions for Azure.

For more information on how to create an Azure account, see the [Create an Azure account](https://docs.microsoft.com/en-us/learn/modules/create-an-azure-account/) learning module.

### What is the Azure free account? <a id="what-is-the-azure-free-account"></a>

The Azure free account includes:

* Free access to popular Azure products for 12 months.
* A credit to spend for the first 30 days.
* Access to more than 25 products that are always free.

The Azure free account is an excellent way for new users to get started and explore. To sign up, you need a phone number, a credit card, and a Microsoft or GitHub account. The credit card information is used for identity verification only. You won't be charged for any services until you upgrade to a paid subscription.

### What is the Learn sandbox? <a id="what-is-the-learn-sandbox"></a>

Many of the Learn exercises use a technology called the sandbox, which creates a temporary subscription that's added to your Azure account. This temporary subscription allows you to create Azure resources for the duration of a Learn module. Learn automatically cleans up the temporary resources for you after you've completed the module.

When you're completing a Learn module, you're welcome to use your personal subscription to complete the exercises in a module. The sandbox is the preferred method to use though, because it allows you to create and test Azure resources at no cost to you.

## Case study introduction

* 2 minutes

Throughout the Azure Fundamentals learning paths, we'll work with [Tailwind Traders](https://www.tailwindtraders.com/), a fictitious home improvement retailer. It operates retail hardware stores across the globe and online.

![A screenshot of the Tailwind Traders website. You can upload a photo to the smart shopping feature or browse recommended products.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/intro-to-azure-fundamentals/media/tailwind-traders-web-top.png)

Tailwind Traders currently manages an on-premises datacenter that hosts the company's retail website. The datacenter also stores all of the data and streaming video for its applications. The IT department is currently responsible for all of the management tasks for its computing hardware and software. For example, let's suppose that you work as an IT specialist for the company's IT department. Your IT team handles the procurement process to buy new hardware, installs and configures software, and deploys everything throughout the datacenter.

These management responsibilities create some obstacles for delivering your applications to your users in a timely fashion. As an IT pro, you realize it would be advantageous to have servers, storage, databases, and other services immediately available when you develop and deploy applications. You want to easily start a new server or add services to your solutions.

In the other units of this learning module, you've learned about some of the cloud-based services that Tailwind Traders can use to address its technology challenges. With that in mind, the services that are available through Azure can help Tailwind Traders conduct its business more efficiently.

As you complete the various modules in the Azure Fundamentals learning paths, we'll analyze the challenges that Tailwind Traders is facing. You'll see how you can use Azure services to address each of the issues as they arise. After you've completed each of the modules, the knowledge that you gained from resolving the hypothetical challenges that the fictional Tailwind Traders company encountered should benefit you in your real-world environments.

## Summary

* 1 minute

In this module, you learned how to:

* Describe the basic concepts of cloud computing.
* Determine whether Azure is the right solution for your business needs.
* Differentiate between the different methods of creating an Azure subscription.

### Learn more <a id="learn-more"></a>

* [Azure free account FAQ](https://azure.microsoft.com/free/free-account-faq/)
* [Create an Azure account](https://docs.microsoft.com/en-us/learn/modules/create-an-azure-account/)
* [Align requirements with cloud types and service models in Azure](https://docs.microsoft.com/en-us/learn/modules/align-requirements-in-azure/)
* [What is infrastructure as a service \(IaaS\)?](https://azure.microsoft.com/overview/what-is-iaas/)
* [What is platform as a service \(PaaS\)?](https://azure.microsoft.com/overview/what-is-paas/)
* [What is software as a service \(SaaS\)?](https://azure.microsoft.com/overview/what-is-saas/)
* [Serverless computing](https://azure.microsoft.com/overview/serverless-computing/)

