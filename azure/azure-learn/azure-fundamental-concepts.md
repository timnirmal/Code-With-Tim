# Azure Fundamental Concepts

## Describe the benefits of cloud computing

* 5 minutes

### What are some cloud computing advantages? <a id="what-are-some-cloud-computing-advantages"></a>

There are several advantages that a cloud environment has over a physical environment that Tailwind Traders can use following its migration to Azure.

* **High availability**: Depending on the service-level agreement \(SLA\) that you choose, your cloud-based apps can provide a continuous user experience with no apparent downtime, even when things go wrong.
* **Scalability**: Apps in the cloud can scale _vertically_ and _horizontally_:
  * Scale vertically to increase compute capacity by adding RAM or CPUs to a virtual machine.
  * Scaling horizontally increases compute capacity by adding instances of resources, such as adding VMs to the configuration.
* **Elasticity**: You can configure cloud-based apps to take advantage of autoscaling, so your apps always have the resources they need.
* **Agility**: Deploy and configure cloud-based resources quickly as your app requirements change.
* **Geo-distribution**: You can deploy apps and data to regional datacenters around the globe, thereby ensuring that your customers always have the best performance in their region.
* **Disaster recovery**: By taking advantage of cloud-based backup services, data replication, and geo-distribution, you can deploy your apps with the confidence that comes from knowing that your data is safe in the event of disaster.

### Cloud computing is a consumption-based model <a id="cloud-computing-is-a-consumption-based-model"></a>

Cloud service providers operate on a _consumption-based model_, which means that end users only pay for the resources that they use. Whatever they use is what they pay for.

A consumption-based model has many benefits, including:

* No upfront costs.
* No need to purchase and manage costly infrastructure that users might not use to its fullest.
* The ability to pay for additional resources when they are needed.
* The ability to stop paying for resources that are no longer needed.

### Capital expenses vs. operating expenses <a id="capital-expenses-vs-operating-expenses"></a>

There are two different types of expenses that you should consider:

* **Capital Expenditure \(CapEx\)** is the up-front spending of money on physical infrastructure, and then deducting that up-front expense over time. The up-front cost from CapEx has a value that reduces over time.
* **Operational Expenditure \(OpEx\)** is spending money on services or products now, and being billed for them now. You can deduct this expense in the same year you spend it. There is no up-front cost, as you pay for a service or product as you use it.

In other words, when Tailwind Traders owns its infrastructure, it buys equipment that goes onto its balance sheets as assets. Because a capital investment was made, accountants categorize this transaction as a CapEx. Over time, to account for the assets' limited useful lifespan, assets are depreciated or amortized.

Cloud services, on the other hand, are categorized as an OpEx, because of their consumption model. There's no asset for Tailwind Traders to amortize, and its cloud service provider \(Azure\) manages the costs that are associated with the purchase and lifespan of the physical equipment. As a result, OpEx has a direct impact on net profit, taxable income, and the associated expenses on the balance sheet.

To summarize, CapEx requires significant up-front financial costs, as well as ongoing maintenance and support expenditures. By contrast, OpEx is a consumption-based model, so Tailwind Traders is only responsible for the cost of the computing resources that it uses.

## Describe the different categories of cloud services

### What are cloud service models? <a id="what-are-cloud-service-models"></a>

If you've been around cloud computing for a while, you've probably seen the _PaaS_, _IaaS_, and _SaaS_ acronyms for the different _cloud service models_. These models define the different levels of shared responsibility that a cloud provider and cloud tenant are responsible for.

| WHAT ARE CLOUD SERVICE MODELS? |  |  |
| :--- | :--- | :--- |
| Model | Definition | Description |
| **IaaS** | _Infrastructure-as-a-Service_ | This cloud service model is the closest to managing physical servers; a cloud provider will keep the hardware up-to-date, but operating system maintenance and network configuration is up to you as the cloud tenant. For example, Azure virtual machines are fully operational virtual compute devices running in Microsoft datacenters. An advantage of this cloud service model is rapid deployment of new compute devices. Setting up a new virtual machine is considerably faster than procuring, installing, and configuring a physical server. |
| **PaaS** | _Platform-as-a-Service_ | This cloud service model is a managed hosting environment. The cloud provider manages the virtual machines and networking resources, and the cloud tenant deploys their applications into the managed hosting environment. For example, Azure App Services provides a managed hosting environment where developers can upload their web applications, without having to worry about the physical hardware and software requirements. |
| **SaaS** | _Software-as-a-Service_ | In this cloud service model, the cloud provider manages all aspects of the application environment, such as virtual machines, networking resources, data storage, and applications. The cloud tenant only needs to provide their data to the application managed by the cloud provider. For example, Microsoft Office 365 provides a fully working version of Microsoft Office that runs in the cloud. All you need to do is create your content, and Office 365 takes care of everything else. |

The following illustration demonstrates the services that might run in each of the cloud service models.

[![Diagram of services separated by cloud service models.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/fundamental-azure-concepts/media/iaas-paas-saas.png)](https://docs.microsoft.com/en-us/learn/azure-fundamentals/fundamental-azure-concepts/media/iaas-paas-saas-expanded.png#lightbox)

Let's compare the three models in more detail in the following sections.

#### IaaS <a id="iaas"></a>

IaaS is the most flexible category of cloud services. It aims to give you complete control over the hardware that runs your application. Instead of buying hardware, with IaaS, you rent it.

**Advantages**

**No CapEx**. Users have no up-front costs.

**Agility**. Applications can be made accessible quickly, and deprovisioned whenever needed.

**Management**. The shared responsibility model applies; the user manages and maintains the services they have provisioned, and the cloud provider manages and maintains the cloud infrastructure.

**Consumption-based model**. Organizations pay only for what they use and operate under an Operational Expenditure \(OpEx\) model.

**Skills**. No deep technical skills are required to deploy, use, and gain the benefits of a public cloud. Organizations can use the skills and expertise of the cloud provider to ensure workloads are secure, safe, and highly available.

**Cloud benefits**. Organizations can use the skills and expertise of the cloud provider to ensure workloads are made secure and highly available.

**Flexibility**. IaaS is the most flexible cloud service because you have control to configure and manage the hardware running your application.

#### PaaS <a id="paas"></a>

PaaS provides the same benefits and considerations as IaaS, but there are some additional benefits to be aware of.

**Advantages**

**No CapEx**. Users have no up-front costs.

**Agility**. PaaS is more agile than IaaS, and users don't need to configure servers for running applications.

**Consumption-based model**. Users pay only for what they use, and operate under an OpEx model.

**Skills**. No deep technical skills are required to deploy, use, and gain the benefits of PaaS.

**Cloud benefits**. Users can take advantage of the skills and expertise of the cloud provider to ensure that their workloads are made secure and highly available. In addition, users can gain access to more cutting-edge development tools. They can then apply these tools across an application's lifecycle.

**Productivity**. Users can focus on application development only, because the cloud provider handles all platform management. Working with distributed teams as services is easier because the platform is accessed over the internet. You can make the platform available globally more easily.

**Disadvantage**

**Platform limitations**. There can be some limitations to a cloud platform that might affect how an application runs. When you're evaluating which PaaS platform is best suited for a workload, be sure to consider any limitations in this area.

#### SaaS <a id="saas"></a>

SaaS is software that's centrally hosted and managed for you and your users or customers. Usually one version of the application is used for all customers, and it's licensed through a monthly or annual subscription.

SaaS provides the same benefits as IaaS, but again there are some additional benefits to be aware of too.

**Advantages**

**No CapEx**. Users have no up-front costs.

**Agility**. Users can provide staff with access to the latest software quickly and easily.

**Pay-as-you-go pricing model**. Users pay for the software they use on a subscription model, typically monthly or yearly, regardless of how much they use the software.

**Skills**. No deep technical skills are required to deploy, use, and gain the benefits of SaaS.

**Flexibility**. Users can access the same application data from anywhere.

**Disadvantage**

**Software limitations**. There can be some limitations to a software application that might affect how users work. Because you're using as-is software, you don't have direct control of features. When you're evaluating which SaaS platform is best suited for a workload, be sure to consider any business needs and software limitations.

### What is serverless computing? <a id="what-is-serverless-computing"></a>

Like PaaS, _serverless computing_ enables developers to build applications faster by eliminating the need for them to manage infrastructure. With serverless applications, the cloud service provider automatically provisions, scales, and manages the infrastructure required to run the code. Serverless architectures are highly scalable and event-driven, only using resources when a specific function or trigger occurs.

It's important to note that servers are still running the code. The "serverless" name comes from the fact that the tasks associated with infrastructure provisioning and management are invisible to the developer. This approach enables developers to increase their focus on the business logic, and deliver more value to the core of the business. Serverless computing helps teams increase their productivity and bring products to market faster, and it allows organizations to better optimize resources and stay focused on innovation.

## Describe the different types of cloud computing

* 5 minutes

### What are public, private, and hybrid clouds? <a id="what-are-public-private-and-hybrid-clouds"></a>

There are three deployment models for cloud computing: _public cloud_, _private cloud_, and _hybrid cloud_. Each deployment model has different aspects that you should consider as you migrate to the cloud.

| WHAT ARE PUBLIC, PRIVATE, AND HYBRID CLOUDS? |  |
| :--- | :--- |
| Deployment model | Description |
| **Public cloud** | Services are offered over the public internet and available to anyone who wants to purchase them. Cloud resources, such as servers and storage, are owned and operated by a third-party cloud service provider, and delivered over the internet. |
| **Private cloud** | A private cloud consists of computing resources used exclusively by users from one business or organization. A private cloud can be physically located at your organization's on-site \(on-premises\) datacenter, or it can be hosted by a third-party service provider. |
| **Hybrid cloud** | A hybrid cloud is a computing environment that combines a public cloud and a private cloud by allowing data and applications to be shared between them. |

The following image illustrates several of the cloud computing concepts that are presented in this unit. In this example, several factors are demonstrated when you are considering where to deploy a database server in a hybrid cloud environment: as your resources move from on-premises to off-premises, your costs are reduced, and your administration requirements decrease.

![Illustration showing the cloud computing continuum.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/fundamental-azure-concepts/media/cloud-computing-continuum.png)

## Summary

* 2 minutes

In this module, you learned how Tailwind Traders can take advantage of several cloud computing features, which will help the company reduce its overall computing costs. You examined several of the benefits that cloud computing provides, such as high availability, scalability, and geographic distribution. You compared the differences between capital expenses and operating expenses in a cloud computing scenario. Lastly, you learned about the different categories \(IaaS, PaaS, SaaS\) and types \(public, private, and hybrid\) of cloud computing. Armed with this new knowledge, you can help Tailwind Traders migrate successfully to Azure.

### Learn more <a id="learn-more"></a>

* [Discuss Azure fundamental concepts](https://docs.microsoft.com/en-us/learn/modules/fundamental-azure-concepts/)
* [Examples of fiscal outcomes](https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/strategy/business-outcomes/fiscal-outcomes)
* [What is cloud computing? A beginner's guide](https://azure.microsoft.com/overview/what-is-cloud-computing/)
* [What are public, private, and hybrid clouds?](https://azure.microsoft.com/overview/what-are-private-public-hybrid-clouds/)
* [What is a private cloud?](https://azure.microsoft.com/overview/what-is-a-private-cloud/)
* [What is a hybrid cloud?](https://azure.microsoft.com/overview/what-is-hybrid-cloud-computing/)
* [What is a public cloud?](https://azure.microsoft.com/overview/what-is-a-public-cloud/)

