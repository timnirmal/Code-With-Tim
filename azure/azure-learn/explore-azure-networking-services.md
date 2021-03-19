# Explore Azure networking services



## Introduction

100 XP

* 2 minutes

Suppose your company, Tailwind Traders, has migrated some applications to the cloud and is architecting new ones. The servers that host Tailwind Traders' customer and product data are based in Silicon Valley. Your company also has several branch offices located in different geographic regions. As part of your migration strategy, your company needs to determine the correct approach to configure its network infrastructure.

![Tailwind Traders company logo.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/shared/media/tailwind-traders-logo.png)

To help save costs, you convince your team to move your website and several of your other networked resources to the cloud. With that in mind, you'll need to provide secure access to private company data for each of its branch locations. You want to know how Azure can help you manage your network more effectively. As it turns out, managing networks on Azure isn't entirely different from managing on-premises networks.

In this module, you'll learn about the different Azure networking options and the scenarios in which each is appropriate.

### Learning objectives <a id="learning-objectives"></a>

After completing this module, you'll be able to:

* Describe the core networking resources that are available in Azure.
* Describe the benefits and usage of Azure Virtual Network, Azure VPN Gateway, and Azure ExpressRoute.

### Prerequisites <a id="prerequisites"></a>

* You should be familiar with basic network concepts and terminology.
* Familiarity with cloud computing is helpful but isn't necessary.

## Azure Virtual Network fundamentals

100 XP

* 8 minutes

Tailwind Traders has an on-premises datacenter that you plan to keep, but you want to use Azure to offload peak traffic by using virtual machines \(VMs\) hosted in Azure. You want to keep your existing IP addressing scheme and network appliances while ensuring that any data transfer is secure.

Using Azure Virtual Network for your virtual networking can help you reach your goals.

### What is Azure virtual networking? <a id="what-is-azure-virtual-networking"></a>

_Azure virtual networks_ enable Azure resources, such as VMs, web apps, and databases, to communicate with each other, with users on the internet, and with your on-premises client computers. You can think of an Azure network as a set of resources that links other Azure resources.

Azure virtual networks provide the following key networking capabilities:

* Isolation and segmentation
* Internet communications
* Communicate between Azure resources
* Communicate with on-premises resources
* Route network traffic
* Filter network traffic
* Connect virtual networks

**Network configurations for virtual machines**

#### Isolation and segmentation <a id="isolation-and-segmentation"></a>

Virtual Network allows you to create multiple isolated virtual networks. When you set up a virtual network, you define a private IP address space by using either public or private IP address ranges. You can divide that IP address space into subnets and allocate part of the defined address space to each named subnet.

For name resolution, you can use the name resolution service that's built in to Azure. You also can configure the virtual network to use either an internal or an external DNS server.

#### Internet communications <a id="internet-communications"></a>

A VM in Azure can connect to the internet by default. You can enable incoming connections from the internet by defining a public IP address or a public load balancer. For VM management, you can connect via the Azure CLI, Remote Desktop Protocol, or Secure Shell.

#### Communicate between Azure resources <a id="communicate-between-azure-resources"></a>

You'll want to enable Azure resources to communicate securely with each other. You can do that in one of two ways:

* **Virtual networks**

  Virtual networks can connect not only VMs but other Azure resources, such as the App Service Environment for Power Apps, Azure Kubernetes Service, and Azure virtual machine scale sets.

* **Service endpoints**

  You can use service endpoints to connect to other Azure resource types, such as Azure SQL databases and storage accounts. This approach enables you to link multiple Azure resources to virtual networks to improve security and provide optimal routing between resources.

#### Communicate with on-premises resources <a id="communicate-with-on-premises-resources"></a>

Azure virtual networks enable you to link resources together in your on-premises environment and within your Azure subscription. In effect, you can create a network that spans both your local and cloud environments. There are three mechanisms for you to achieve this connectivity:

* **Point-to-site virtual private networks**

  This approach is like a virtual private network \(VPN\) connection that a computer outside your organization makes back into your corporate network, except that it's working in the opposite direction. In this case, the client computer initiates an encrypted VPN connection to Azure to connect that computer to the Azure virtual network.

* **Site-to-site virtual private networks**

  A site-to-site VPN links your on-premises VPN device or gateway to the Azure VPN gateway in a virtual network. In effect, the devices in Azure can appear as being on the local network. The connection is encrypted and works over the internet.

* **Azure ExpressRoute**

  For environments where you need greater bandwidth and even higher levels of security, Azure ExpressRoute is the best approach. ExpressRoute provides dedicated private connectivity to Azure that doesn't travel over the internet. \(You'll learn more about ExpressRoute in a separate unit later in this module.\)

#### Route network traffic <a id="route-network-traffic"></a>

By default, Azure routes traffic between subnets on any connected virtual networks, on-premises networks, and the internet. You also can control routing and override those settings, as follows:

* **Route tables**

  A route table allows you to define rules about how traffic should be directed. You can create custom route tables that control how packets are routed between subnets.

* **Border Gateway Protocol**

  Border Gateway Protocol \(BGP\) works with Azure VPN gateways or ExpressRoute to propagate on-premises BGP routes to Azure virtual networks.

#### Filter network traffic <a id="filter-network-traffic"></a>

Azure virtual networks enable you to filter traffic between subnets by using the following approaches:

* **Network security groups**

  A network security group is an Azure resource that can contain multiple inbound and outbound security rules. You can define these rules to allow or block traffic, based on factors such as source and destination IP address, port, and protocol.

* **Network virtual appliances**

  A network virtual appliance is a specialized VM that can be compared to a hardened network appliance. A network virtual appliance carries out a particular network function, such as running a firewall or performing wide area network \(WAN\) optimization.

### Connect virtual networks <a id="connect-virtual-networks"></a>

You can link virtual networks together by using virtual network _peering_. Peering enables resources in each virtual network to communicate with each other. These virtual networks can be in separate regions, which allows you to create a global interconnected network through Azure.

UDR is user-defined Routing. UDR is a significant update to Azure’s Virtual Networks as this allows network admins to control the routing tables between subnets within a VNet, as well as between VNets, thereby allowing for greater control over network traffic flow.

[![Illustration of a local or remote gateway in peered virtual network.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/local-or-remote-gateway-in-peered-virual-network.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/local-or-remote-gateway-in-peered-virual-network-expanded.png#lightbox)

