# Describe core Azure architectural components

## Overview of Azure subscriptions, management groups, resources, and regions

* 2 minutes

As part of your research for Tailwind Traders, you need to learn the organizing structure for resources in Azure, which has four levels: management groups, subscriptions, resource groups, and resources.

The following image shows the top-down hierarchy of organization for these levels.

[![Screenshot of the hierarchy for objects in Azure.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/hierarchy.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/hierarchy-expanded.png#lightbox)

Having seen the top-down hierarchy of organization, let's describe each of those levels from the bottom up:

* **Resources**: Resources are instances of services that you create, like virtual machines, storage, or SQL databases.
* **Resource groups**: Resources are combined into resource groups, which act as a logical container into which Azure resources like web apps, databases, and storage accounts are deployed and managed.
* **Subscriptions**: A subscription groups together user accounts and the resources that have been created by those user accounts. For each subscription, there are limits or quotas on the amount of resources that you can create and use. Organizations can use subscriptions to manage costs and the resources that are created by users, teams, or projects.
* **Management groups**: These groups help you manage access, policy, and compliance for multiple subscriptions. All subscriptions in a management group automatically inherit the conditions applied to the management group.

You'll examine each of these four organizational levels in the next few units.

## Azure subscriptions and management groups

* 6 minutes

As Tailwind Traders gets started with Azure, one of your first steps will be to create at least one Azure subscription. You'll use it to create your cloud-based resources in Azure.

Note

An Azure resource is a manageable item that's available through Azure. Virtual machines \(VMs\), storage accounts, web apps, databases, and virtual networks are all examples of resources.

### Azure subscriptions <a id="azure-subscriptions"></a>

Using Azure requires an Azure subscription. A subscription provides you with authenticated and authorized access to Azure products and services. It also allows you to provision resources. An Azure subscription is a logical unit of Azure services that links to an Azure account, which is an identity in Azure Active Directory \(Azure AD\) or in a directory that Azure AD trusts.

[![Diagram showing Azure subscriptions using authentication and authorization to access Azure accounts.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/subscriptions.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/subscriptions-expanded.png#lightbox)

An account can have one subscription or multiple subscriptions that have different billing models and to which you apply different access-management policies. You can use Azure subscriptions to define boundaries around Azure products, services, and resources. There are two types of subscription boundaries that you can use:

* **Billing boundary**: This subscription type determines how an Azure account is billed for using Azure. You can create multiple subscriptions for different types of billing requirements. Azure generates separate billing reports and invoices for each subscription so that you can organize and manage costs.
* **Access control boundary**: Azure applies access-management policies at the subscription level, and you can create separate subscriptions to reflect different organizational structures. An example is that within a business, you have different departments to which you apply distinct Azure subscription policies. This billing model allows you to manage and control access to the resources that users provision with specific subscriptions.

#### Create additional Azure subscriptions <a id="create-additional-azure-subscriptions"></a>

You might want to create additional subscriptions for resource or billing management purposes. For example, you might choose to create additional subscriptions to separate:

* **Environments:** When managing your resources, you can choose to create subscriptions to set up separate environments for development and testing, security, or to isolate data for compliance reasons. This design is particularly useful because resource access control occurs at the subscription level.
* **Organizational structures:** You can create subscriptions to reflect different organizational structures. For example, you could limit a team to lower-cost resources, while allowing the IT department a full range. This design allows you to manage and control access to the resources that users provision within each subscription.
* **Billing:** You might want to also create additional subscriptions for billing purposes. Because costs are first aggregated at the subscription level, you might want to create subscriptions to manage and track costs based on your needs. For instance, you might want to create one subscription for your production workloads and another subscription for your development and testing workloads.

You might also need additional subscriptions because of:

* **Subscription limits:** Subscriptions are bound to some hard limitations. For example, the maximum number of Azure ExpressRoute circuits per subscription is 10. Those limits should be considered as you create subscriptions on your account. If there's a need to go over those limits in particular scenarios, you might need additional subscriptions.

#### Customize billing to meet your needs <a id="customize-billing-to-meet-your-needs"></a>

If you have multiple subscriptions, you can organize them into invoice sections. Each invoice section is a line item on the invoice that shows the charges incurred that month. For example, you might need a single invoice for your organization but want to organize charges by department, team, or project.

Depending on your needs, you can set up multiple invoices within the same billing account. To do this, create additional billing profiles. Each billing profile has its own monthly invoice and payment method.

The following diagram shows an overview of how billing is structured. If you've previously signed up for Azure or if your organization has an Enterprise Agreement, your billing might be set up differently.

[![Flowchart-style diagram showing an example of setting up a billing structure where different groups like marketing or development have their own Azure subscription that rolls up into a larger company-paid Azure billing account.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/billing-structure-overview.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/billing-structure-overview-expanded.png#lightbox)

### Azure management groups <a id="azure-management-groups"></a>

If your organization has many subscriptions, you might need a way to efficiently manage access, policies, and compliance for those subscriptions. Azure management groups provide a level of scope above subscriptions. You organize subscriptions into containers called management groups and apply your governance conditions to the management groups. All subscriptions within a management group automatically inherit the conditions applied to the management group. Management groups give you enterprise-grade management at a large scale no matter what type of subscriptions you might have. All subscriptions within a single management group must trust the same Azure AD tenant.

For example, you can apply policies to a management group that limits the regions available for VM creation. This policy would be applied to all management groups, subscriptions, and resources under that management group by only allowing VMs to be created in that region.

#### Hierarchy of management groups and subscriptions <a id="hierarchy-of-management-groups-and-subscriptions"></a>

You can build a flexible structure of management groups and subscriptions to organize your resources into a hierarchy for unified policy and access management. The following diagram shows an example of creating a hierarchy for governance by using management groups.

[![Diagram showing an example of a management group hierarchy tree.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/management-groups-and-subscriptions.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/management-groups-and-subscriptions-expanded.png#lightbox)

You can create a hierarchy that applies a policy. For example, you could limit VM locations to the US West Region in a group called Production. This policy will inherit onto all the Enterprise Agreement subscriptions that are descendants of that management group and will apply to all VMs under those subscriptions. This security policy can't be altered by the resource or subscription owner, which allows for improved governance.

Another scenario where you would use management groups is to provide user access to multiple subscriptions. By moving multiple subscriptions under that management group, you can create one role-based access control \(RBAC\) assignment on the management group, which will inherit that access to all the subscriptions. One assignment on the management group can enable users to have access to everything they need instead of scripting RBAC over different subscriptions.

#### Important facts about management groups <a id="important-facts-about-management-groups"></a>

* 10,000 management groups can be supported in a single directory.
* A management group tree can support up to six levels of depth. This limit doesn't include the root level or the subscription level.
* Each management group and subscription can support only one parent.
* Each management group can have many children.
* All subscriptions and management groups are within a single hierarchy in each directory.

## Azure resources and Azure Resource Manager

* 4 minutes

After you've created a subscription for Tailwind Traders, you're ready to start creating resources and storing them in resource groups. With that in mind, it's important to define those terms:

* **Resource**: A manageable item that's available through Azure. Virtual machines \(VMs\), storage accounts, web apps, databases, and virtual networks are examples of resources.
* **Resource group**: A container that holds related resources for an Azure solution. The resource group includes resources that you want to manage as a group. You decide which resources belong in a resource group based on what makes the most sense for your organization.

### Azure resource groups <a id="azure-resource-groups"></a>

Resource groups are a fundamental element of the Azure platform. A resource group is a logical container for resources deployed on Azure. These resources are anything you create in an Azure subscription like VMs, Azure Application Gateway instances, and Azure Cosmos DB instances. All resources must be in a resource group, and a resource can only be a member of a single resource group. Many resources can be moved between resource groups with some services having specific limitations or requirements to move. Resource groups can't be nested. Before any resource can be provisioned, you need a resource group for it to be placed in.

#### Logical grouping <a id="logical-grouping"></a>

Resource groups exist to help manage and organize your Azure resources. By placing resources of similar usage, type, or location in a resource group, you can provide order and organization to resources you create in Azure. Logical grouping is the aspect that you're most interested in here, because there's a lot of disorder among our resources.

![Conceptual image showing a resource group box with a function, VM, database, and app included.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/resource-group.png)

#### Life cycle <a id="life-cycle"></a>

If you delete a resource group, all resources contained within it are also deleted. Organizing resources by life cycle can be useful in nonproduction environments, where you might try an experiment and then dispose of it. Resource groups make it easy to remove a set of resources all at once.

#### Authorization <a id="authorization"></a>

Resource groups are also a scope for applying role-based access control \(RBAC\) permissions. By applying RBAC permissions to a resource group, you can ease administration and limit access to allow only what's needed.

### Azure Resource Manager <a id="azure-resource-manager"></a>

Azure Resource Manager is the deployment and management service for Azure. It provides a management layer that enables you to create, update, and delete resources in your Azure account. You use management features like access control, locks, and tags to secure and organize your resources after deployment.

When a user sends a request from any of the Azure tools, APIs, or SDKs, Resource Manager receives the request. It authenticates and authorizes the request. Resource Manager sends the request to the Azure service, which takes the requested action. Because all requests are handled through the same API, you see consistent results and capabilities in all the different tools.

The following image shows the role Resource Manager plays in handling Azure requests.

[![Diagram showing a Resource Manager request model.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/consistent-management-layer.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/consistent-management-layer-expanded.png#lightbox)

All capabilities that are available in the Azure portal are also available through PowerShell, the Azure CLI, REST APIs, and client SDKs. Functionality initially released through APIs will be represented in the portal within 180 days of initial release.

#### The benefits of using Resource Manager <a id="the-benefits-of-using-resource-manager"></a>

With Resource Manager, you can:

* Manage your infrastructure through declarative templates rather than scripts. A Resource Manager template is a JSON file that defines what you want to deploy to Azure.
* Deploy, manage, and monitor all the resources for your solution as a group, rather than handling these resources individually.
* Redeploy your solution throughout the development life cycle and have confidence your resources are deployed in a consistent state.
* Define the dependencies between resources so they're deployed in the correct order.
* Apply access control to all services because RBAC is natively integrated into the management platform.
* Apply tags to resources to logically organize all the resources in your subscription.
* Clarify your organization's billing by viewing costs for a group of resources that share the same tag.

## Azure regions and availability zones

* 7 minutes

In the previous unit, you learned about Azure resources and resource groups. Resources are created in regions, which are different geographical locations around the globe that contain Azure datacenters.

Azure is made up of datacenters located around the globe. When you use a service or create a resource such as a SQL database or virtual machine \(VM\), you're using physical equipment in one or more of these locations. These specific datacenters aren't exposed to users directly. Instead, Azure organizes them into regions. As you'll see later in this unit, some of these regions offer availability zones, which are different Azure datacenters within that region.

### Azure regions <a id="azure-regions"></a>

A _region_ is a geographical area on the planet that contains at least one but potentially multiple datacenters that are nearby and networked together with a low-latency network. Azure intelligently assigns and controls the resources within each region to ensure workloads are appropriately balanced.

When you deploy a resource in Azure, you'll often need to choose the region where you want your resource deployed.

Important

Some services or VM features are only available in certain regions, such as specific VM sizes or storage types. There are also some global Azure services that don't require you to select a particular region, such as Azure Active Directory, Azure Traffic Manager, and Azure DNS.

A few examples of regions are West US, Canada Central, West Europe, Australia East, and Japan West. Here's a view of all the available regions as of June 2020.

[![Global map of available Azure regions as of June 2020.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/regions-small.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/regions-expanded.png#lightbox)

#### Why are regions important? <a id="why-are-regions-important"></a>

Azure has more global regions than any other cloud provider. These regions give you the flexibility to bring applications closer to your users no matter where they are. Global regions provide better scalability and redundancy. They also preserve data residency for your services.

#### Special Azure regions <a id="special-azure-regions"></a>

Azure has specialized regions that you might want to use when you build out your applications for compliance or legal purposes. A few examples include:

* **US DoD Central, US Gov Virginia, US Gov Iowa and more:** These regions are physical and logical network-isolated instances of Azure for U.S. government agencies and partners. These datacenters are operated by screened U.S. personnel and include additional compliance certifications.
* **China East, China North, and more:** These regions are available through a unique partnership between Microsoft and 21Vianet, whereby Microsoft doesn't directly maintain the datacenters.

Regions are what you use to identify the location for your resources. There are two other terms you should also be aware of: _geographies_ and _availability zones_.

### Azure availability zones <a id="azure-availability-zones"></a>

You want to ensure your services and data are redundant so you can protect your information in case of failure. When you host your infrastructure, setting up your own redundancy requires that you create duplicate hardware environments. Azure can help make your app highly available through availability zones.

#### What is an availability zone? <a id="what-is-an-availability-zone"></a>

Availability zones are physically separate datacenters within an Azure region. Each availability zone is made up of one or more datacenters equipped with independent power, cooling, and networking. An availability zone is set up to be an _isolation boundary_. If one zone goes down, the other continues working. Availability zones are connected through high-speed, private fiber-optic networks.

[![Diagram showing three datacenters connected within a single Azure region to represent an availability zone.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/availability-zones.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/availability-zones-expanded.png#lightbox)

#### Supported regions <a id="supported-regions"></a>

Not every region has support for availability zones. For an updated list, see [Regions that support availability zones in Azure](https://docs.microsoft.com/en-us/azure/availability-zones/az-region).

#### Use availability zones in your apps <a id="use-availability-zones-in-your-apps"></a>

You can use availability zones to run mission-critical applications and build high-availability into your application architecture by co-locating your compute, storage, networking, and data resources within a zone and replicating in other zones. Keep in mind that there could be a cost to duplicating your services and transferring data between zones.

Availability zones are primarily for VMs, managed disks, load balancers, and SQL databases. Azure services that support availability zones fall into two categories:

* **Zonal services**: You pin the resource to a specific zone \(for example, VMs, managed disks, IP addresses\).
* **Zone-redundant services**: The platform replicates automatically across zones \(for example, zone-redundant storage, SQL Database\).

Check the documentation to determine which elements of your architecture you can associate with an availability zone.

### Azure region pairs <a id="azure-region-pairs"></a>

Availability zones are created by using one or more datacenters. There's a minimum of three zones within a single region. It's possible that a large disaster could cause an outage big enough to affect even two datacenters. That's why Azure also creates _region pairs_.

#### What is a region pair? <a id="what-is-a-region-pair"></a>

Each Azure region is always paired with another region within the same geography \(such as US, Europe, or Asia\) at least 300 miles away. This approach allows for the replication of resources \(such as VM storage\) across a geography that helps reduce the likelihood of interruptions because of events such as natural disasters, civil unrest, power outages, or physical network outages that affect both regions at once. If a region in a pair was affected by a natural disaster, for instance, services would automatically failover to the other region in its region pair.

Examples of region pairs in Azure are West US paired with East US and SouthEast Asia paired with East Asia.

[![Diagram showing the relationship between geography, region pair, region, and datacenter. The geography box contains two region pairs. Each region pair contains two Azure regions. Each region contains three availability zones.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/region-pairs.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/region-pairs-expanded.png#lightbox)

Because the pair of regions is directly connected and far enough apart to be isolated from regional disasters, you can use them to provide reliable services and data redundancy. Some services offer automatic geo-redundant storage by using region pairs.

Additional advantages of region pairs:

* If an extensive Azure outage occurs, one region out of every pair is prioritized to make sure at least one is restored as quickly as possible for applications hosted in that region pair.
* Planned Azure updates are rolled out to paired regions one region at a time to minimize downtime and risk of application outage.
* Data continues to reside within the same geography as its pair \(except for Brazil South\) for tax- and law-enforcement jurisdiction purposes.

Having a broadly distributed set of datacenters allows Azure to provide a high guarantee of availability.

## Summary

* 2 minutes

In this module, you learned the concepts and terminology for several of the core Azure architecture components. Now you have the basic level of understanding for Azure architecture that you'll need to make Tailwind Traders successful as it migrates to the cloud.

You learned how to describe the benefits and usage of:

* Azure subscriptions and management groups.
* Azure resources, resource groups, and Azure Resource Manager.
* Azure regions, region pairs, and availability zones.

### Learn more <a id="learn-more"></a>

* [Build a cloud governance strategy on Azure](https://docs.microsoft.com/en-us/learn/modules/build-cloud-governance-strategy-azure/)
* [Azure Resource Manager template documentation](https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/)
* [Describe core Azure architectural components](https://docs.microsoft.com/en-us/learn/modules/azure-architecture-fundamentals/)
* [Control and organize Azure resources with Azure Resource Manager](https://docs.microsoft.com/en-us/learn/modules/control-and-organize-with-azure-resource-manager/)
* [Examine Azure subscriptions](https://docs.microsoft.com/en-us/learn/modules/examine-azure-subscriptions/)
* [Regions and availability zones in Azure](https://docs.microsoft.com/en-us/azure/availability-zones/az-overview)
* [What are Azure management groups?](https://docs.microsoft.com/en-us/azure/governance/management-groups/overview)

### Azure Fundamentals learning path <a id="azure-fundamentals-learning-path"></a>

This module is part of the [Azure Fundamentals part 1: Describe core Azure concepts](https://docs.microsoft.com/en-us/learn/paths/az-900-describe-cloud-concepts/) learning path, which is one of six learning paths for Azure Fundamentals.

Here are the learning paths in this series:

* [Azure Fundamentals part 1: Describe core Azure concepts](https://docs.microsoft.com/en-us/learn/paths/az-900-describe-cloud-concepts/)
* [Azure Fundamentals part 2: Describe core Azure services](https://docs.microsoft.com/en-us/learn/paths/az-900-describe-core-azure-services/)
* [Azure Fundamentals part 3: Describe core solutions and management tools on Azure](https://docs.microsoft.com/en-us/learn/paths/az-900-describe-core-solutions-management-tools-azure/)
* [Azure Fundamentals part 4: Describe general security and network security features](https://docs.microsoft.com/en-us/learn/paths/az-900-describe-general-security-network-security-features/)
* [Azure Fundamentals part 5: Describe identity, governance, privacy, and compliance features](https://docs.microsoft.com/en-us/learn/paths/az-900-describe-identity-governance-privacy-compliance-features/)
* [Azure Fundamentals part 6: Describe Azure cost management and service level agreements](https://docs.microsoft.com/en-us/learn/paths/az-900-describe-azure-cost-management-service-level-agreements/)

## Exercise - Create a website hosted in Azure

* 7 minutes

This module requires a sandbox to complete. You have used 1 of 10 sandboxes for today. More sandboxes will be available tomorrow.

Activate sandbox

As a developer for Tailwind Traders, you likely have expertise creating applications. As you migrate to Azure, many of the steps that you'll follow to set up a website in the cloud will parallel the steps that you followed when you created websites in your company's datacenter. For example, you need to choose where you'll create your website, and then allocate the necessary resources. In Azure, the physical hardware is managed for you, so your tasks are to choose where your website will be located and which resources to provide.

In this exercise, you'll create an Azure App Service instance to host a WordPress website.

### Azure terminology and concepts <a id="azure-terminology-and-concepts"></a>

Before you get started, let's review and discuss some basic terms and concepts that you'll need to know when you create your website.

#### What is App Service? <a id="what-is-app-service"></a>

App Service is an HTTP-based service that enables you to build and host many types of web-based solutions without managing infrastructure. For example, you can host web apps, mobile back ends, and RESTful APIs in several supported programming languages. Applications developed in .NET, .NET Core, Java, Ruby, Node.js, PHP, or Python can run in and scale with ease on both Windows- and Linux-based environments.

For this exercise, we want to create a website in less than the time it takes to eat lunch. So, we're not going to write any code. Instead, you'll deploy a predefined application from Azure Marketplace.

#### What is Azure Marketplace? <a id="what-is-azure-marketplace"></a>

Azure Marketplace is an online store that hosts applications that are certified and optimized to run in Azure. Many types of applications are available, ranging from AI and machine learning to web applications. As you'll see in a couple of minutes, deployments from the store are done via the Azure portal by using a wizard-style user interface. This user interface makes evaluating different solutions easy.

We're going to use one of the WordPress application options from Azure Marketplace for our website.

#### Create resources in Azure <a id="create-resources-in-azure"></a>

Typically, the first thing we'd do is to create a _resource group_ to hold all the things that we need to create. The resource group allows us to administer all the services, disks, network interfaces, and other elements that potentially make up our solution as a unit. We can use the Azure portal to create and manage our solution's resource groups. Keep in mind that you can also manage resources via a command line by using the Azure CLI. The Azure CLI is a useful option if you need to automate the process in the future.

In the free Azure sandbox environment, you'll use the pre-created resource group **\[sandbox resource group name\]**, and you don't need to do this step.

#### Choose a location <a id="choose-a-location"></a>

The free sandbox allows you to create resources in a subset of the Azure global regions. Select a region from this list when you create resources:

* westus2
* southcentralus
* centralus
* eastus
* westeurope
* southeastasia
* japaneast
* brazilsouth
* australiasoutheast
* centralindia

### Create a WordPress website <a id="create-a-wordpress-website"></a>

1. If you haven't done so already, verify that you've activated the sandbox.

   Activating the sandbox allocates the subscription and resource group you'll use in this exercise. This step is required for any Microsoft Learn exercises that use a sandbox.

2. Sign in to the [Azure portal](https://portal.azure.com/learn.docs.microsoft.com) by using the same account you used to activate the sandbox.
3. On the top left of the Azure portal panel, select **Create a resource**.

   [![Screenshot of the Azure portal showing the left pane with Create a resource option highlighted.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/create-resource.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/create-resource-expanded.png#lightbox)

   This option takes you to **Azure Marketplace**.

   [![Screenshot of the Azure portal showing Azure Marketplace categories in a left column and popular options in a right column.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/azure-marketplace.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/azure-marketplace-expanded.png#lightbox)

4. Azure Marketplace has many services, solutions, and resources available for you to use. We know that we want to install WordPress, so we can do a quick search for it. In the **Search the Marketplace** box with the listed application options, enter **WordPress**. Select the default **WordPress** option from the list of options available.

   [![Screenshot of the Azure portal showing search results for the term WordPress with the WordPress option highlighted.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/search-select-wordpress.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/search-select-wordpress-expanded.png#lightbox)

5. In the panel that appears, you'll typically find more information about the item you're about to install, such as the publisher, a brief description of the resource, and links to more information. Make sure to review this information. Select **Create** to begin the process to create a WordPress app. The **WordPress/Create** panel appears.

   [![Screenshot of the Azure portal showing WordPress resource type summary.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/create-site.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/create-site-expanded.png#lightbox)

6. Several options appear to configure your deployment. Enter the following values for each setting.

   | TABLE 1 |  |
   | :--- | :--- |
   | Setting | Value |
   | App name | Choose a unique value for the app name. It will form part of a fully qualified domain name \(FQDN\). |
   | Subscription | Make sure **Concierge Subscription** is selected. |
   | Resource Group | Select the **Use existing** option, and then select the **\[sandbox resource group name\]** resource group from the dropdown. |
   | Database Provider | From the dropdown, select **MySQL in App**. |
   | App Service plan/Location | You'll change the App Service plan in the next step. |
   | Application Insights | Leave at the default configuration. |

   Your configuration should look like this example.

   ![Screenshot of the Azure portal showing the new WordPress app service configured as instructed.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/config-info-create.png)

   Note

   If you still see a section called **Database**, make sure you selected the correct **Database Provider** described in the preceding configuration.

7. Now let's configure the App Service plan to use a specific pricing tier. The App Service plan specifies the compute resources and location for the web app. Select **App Service plan/Location**. The **App Service plan** panel appears.

   ![Screenshot of the Azure portal showing WordPress App Service creation with App Service plan/Location button highlighted.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/config-app-service-plan.png)

8. Select **Create new**. The **New App Service Plan** panel appears.

   [![Screenshot of the Azure portal showing the App Service plan pane with the Create new button highlighted.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/new-app-service-plan.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/new-app-service-plan-expanded.png#lightbox)

9. Enter the following values for each setting.

   | TABLE 2 |  |
   | :--- | :--- |
   | Setting | Value |
   | App Service plan | Choose a unique name for the new app service plan. |
   | Location | Select **Central US** to make sure we choose a region that allows the service plan you'll choose. Normally, you'll select the region that's closest to your customers while offering the services you need. |
   | Pricing tier | Select this option to see the performance and feature options of the various types of app service plans. The **Spec Picker** panel appears. |

   [![Screenshot of the Azure portal showing New App Service plan configuration with the Pricing tier button highlighted.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/new-service-plan-config.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/new-service-plan-config-expanded.png#lightbox)

10. The **Spec Picker** enables us to select a new pricing tier for our application. The panel opens to the **Production** tab, with the S1 pricing tier selected. Select a new pricing tier from the **Dev / Test** tab for our website.
11. Select the **Dev / Test** tab, then select the **F1** pricing tier, and then select **Apply**.

    [![Screenshot of the Azure portal showing the App Service plan Spec Picker pane with the Dev / Test section selected and the free F1 tier and the Apply button highlighted.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/select-pricing-tier.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/select-pricing-tier-expanded.png#lightbox)

12. Back on the **New App Service Plan** pane, select **OK** to create the new plan.
13. Finally, select **Create** to start the deployment of your new site.

    Note

    If you encounter an issue when you create the resources, verify you've selected the **F1** pricing tier in the new App Service plan. Using the F1 pricing tier is a requirement of the sandbox system when you create this WordPress site.

### Verify your website is running <a id="verify-your-website-is-running"></a>

The deployment of the new website can take a few minutes to complete. You're welcome to explore the portal further on your own.

We can track the progress of the deployment at any time.

1. Select the **Notifications** bell icon at the top of the portal. If your browser window width is smaller, it might be shown when you select the ellipsis \(**...**\) icon in the upper-right corner.

   [![Screenshot of the Azure portal showing the top-right menu with the Notifications bell button highlighted.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/notification-bell.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/notification-bell-expanded.png#lightbox)

2. Select **Deployment in progress** to see the details about all the resources that are created.

   [![Screenshot of the Azure portal showing deployment notification in the Notifications list.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/notification-bell-info.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/notification-bell-info-expanded.png#lightbox)

   Notice how resources are listed as they're created and the status changes to a green check mark as each component in the deployment completes.

   [![Screenshot of the Azure portal showing details of the deployment notification stating, &quot;Your deployment is underway.&quot;](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/deployment-progress.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/deployment-progress-expanded.png#lightbox)

3. After the deployment status message changes to **Your deployment is complete**, you'll notice the status in the **Notifications** dialog box changes to **Deployment succeeded**. Select **Go to resource** to go to the App Service overview.

   [![Screenshot of the Azure portal showing deployment notification stating, &quot;Deployment succeeded.&quot;](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/deployment-complete.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/deployment-complete-expanded.png#lightbox)

4. Find the **URL** in the **Overview** section.

   [![Screenshot of the Azure portal showing App Service Overview pane with URL location highlighted.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/website-url.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/website-url-expanded.png#lightbox)

5. Copy the **URL** information by selecting the **Copy to clipboard** icon at the end of URL.
6. Open a new tab in your browser, paste this URL, and press Enter to browse to your new WordPress site. You can now configure your WordPress site, and add content.

   ![Screenshot showing preconfigured WordPress website waiting on language/location selection.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-architecture-fundamentals/media/configure-wordpress.png)

