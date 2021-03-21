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

## Azure Virtual Network settings

100 XP

* 7 minutes

You can create and configure Azure Virtual Network instances from the Azure portal, Azure PowerShell on your local computer, or Azure Cloud Shell.

#### Create a virtual network <a id="create-a-virtual-network"></a>

When you create an Azure virtual network, you configure a number of basic settings. You'll have the option to configure advanced settings, such as multiple subnets, distributed denial of service \(DDoS\) protection, and service endpoints.

![Screenshot of the Azure portal showing an example of the Create virtual network pane fields.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/create-virtual-network.png)

You'll configure the following settings for a basic virtual network:

* **Network name**

  The network name must be unique in your subscription, but it doesn't need to be globally unique. Make the name a descriptive one that's easy to remember and identified from other virtual networks.

* **Address space**

  When you set up a virtual network, you define the internal address space in Classless Interdomain Routing \(CIDR\) format. This address space needs to be unique within your subscription and any other networks that you connect to.

  Let's assume you choose an address space of 10.0.0.0/24 for your first virtual network. The addresses defined in this address space range from 10.0.0.1 to 10.0.0.254. You then create a second virtual network and choose an address space of 10.0.0.0/8. The addresses in this address space range from 10.0.0.1 to 10.255.255.254. Some of the addresses overlap and can't be used for the two virtual networks.

  But you can use 10.0.0.0/16, with addresses that range from 10.0.0.1 to 10.0.255.254, and 10.1.0.0/16, with addresses that range from 10.1.0.1 to 10.1.255.254. You can assign these address spaces to your virtual networks because there's no address overlap.

  Note

  You can add address spaces after you create the virtual network.

* **Subscription**

  This option only applies if you have multiple subscriptions to choose from.

* **Resource group**

  Like any other Azure resource, a virtual network needs to exist in a resource group. You can either select an existing resource group or create a new one.

* **Location**

  Select the location where you want the virtual network to exist.

* **Subnet**

  Within each virtual network address range, you can create one or more subnets that partition the virtual network's address space. Routing between subnets will then depend on the default traffic routes. You also can define custom routes. Alternatively, you can define one subnet that encompasses all the virtual networks' address ranges.

  Note

  Subnet names must begin with a letter or number and end with a letter, number, or underscore. They may contain only letters, numbers, underscores, periods, or hyphens.

* **DDoS protection**

  You can select either Basic or Standard DDoS protection. Standard DDoS protection is a premium service. For more information on Standard DDoS protection, see [Azure DDoS protection Standard overview](https://docs.microsoft.com/en-us/azure/virtual-network/ddos-protection-overview).

* **Service endpoints**

  Here, you enable service endpoints. Then you select from the list which Azure service endpoints you want to enable. Options include Azure Cosmos DB, Azure Service Bus, Azure Key Vault, and so on.

After you've configured these settings, select **Create**.

#### Define additional settings <a id="define-additional-settings"></a>

After you create a virtual network, you can then define further settings. These include:

* **Network security group**

  Network security groups have security rules that enable you to filter the type of network traffic that can flow in and out of virtual network subnets and network interfaces. You create the network security group separately. Then you associate it with the virtual network.

* **Route table**

  Azure automatically creates a route table for each subnet within an Azure virtual network and adds system default routes to the table. You can add custom route tables to modify traffic between virtual networks.

You can also amend the service endpoints.

![Screenshot of the Azure portal showing an example pane for editing virtual network settings.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/virtual-network-additional-settings.png)

#### Configure virtual networks <a id="configure-virtual-networks"></a>

After you've created a virtual network, you can change any further settings on the **Virtual network** pane in the Azure portal. Alternatively, you can use PowerShell commands or commands in Cloud Shell to make changes.

![Screenshot of the Azure portal showing an example pane for configuring a virtual network.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/configure-virtual-network.png)

You can then review and change settings in further subpanes. These settings include:

* **Address spaces**: You can add additional address spaces to the initial definition.
* **Connected devices**: Use the virtual network to connect machines.
* **Subnets**: You can add additional subnets.
* **Peerings**: Link virtual networks in peering arrangements.

You can also monitor and troubleshoot virtual networks. Or, you can create an automation script to generate the current virtual network.

Virtual networks are powerful and highly configurable mechanisms for connecting entities in Azure. You can connect Azure resources to one another or to resources you have on-premises. You can isolate, filter, and route your network traffic. Azure allows you to increase security where you feel you need it.

## Azure VPN Gateway fundamentals

100 XP

* 10 minutes

A virtual private network \(VPN\) is a type of private interconnected network. VPNs use an encrypted tunnel within another network. They're typically deployed to connect two or more trusted private networks to one another over an untrusted network \(typically the public internet\). Traffic is encrypted while traveling over the untrusted network to prevent eavesdropping or other attacks.

For our Tailwind Traders scenario, VPNs can enable branch offices to share sensitive information between locations. For example, let's say that your offices on the East Coast region of North America need to access your company's private customer data, which is stored on servers that are physically located in a West Coast region. A VPN that connects your East Coast offices to your West Coast servers allows your company to securely access your private customer data.

### VPN gateways <a id="vpn-gateways"></a>

A VPN gateway is a type of virtual network gateway. Azure VPN Gateway instances are deployed in Azure Virtual Network instances and enable the following connectivity:

* Connect on-premises datacenters to virtual networks through a _site-to-site_ connection.
* Connect individual devices to virtual networks through a _point-to-site_ connection.
* Connect virtual networks to other virtual networks through a _network-to-network_ connection.

[![Visualization of a VPN connection to Azure](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/vpngateway-site-to-site-connection-diagram.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/vpngateway-site-to-site-connection-diagram-expanded.png#lightbox)

All transferred data is encrypted in a private tunnel as it crosses the internet. You can deploy only one VPN gateway in each virtual network, but you can use one gateway to connect to multiple locations, which includes other virtual networks or on-premises datacenters.

When you deploy a VPN gateway, you specify the VPN type: either _policy-based_ or _route-based_. The main difference between these two types of VPNs is how traffic to be encrypted is specified. In Azure, both types of VPN gateways use a pre-shared key as the only method of authentication. Both types also rely on Internet Key Exchange \(IKE\) in either version 1 or version 2 and Internet Protocol Security \(IPSec\). IKE is used to set up a security association \(an agreement of the encryption\) between two endpoints. This association is then passed to the IPSec suite, which encrypts and decrypts data packets encapsulated in the VPN tunnel.

#### Policy-based VPNs <a id="policy-based-vpns"></a>

Policy-based VPN gateways specify statically the IP address of packets that should be encrypted through each tunnel. This type of device evaluates every data packet against those sets of IP addresses to choose the tunnel where that packet is going to be sent through.

Key features of policy-based VPN gateways in Azure include:

* Support for IKEv1 only.
* Use of _static routing_, where combinations of address prefixes from both networks control how traffic is encrypted and decrypted through the VPN tunnel. The source and destination of the tunneled networks are declared in the policy and don't need to be declared in routing tables.
* Policy-based VPNs must be used in specific scenarios that require them, such as for compatibility with legacy on-premises VPN devices.

#### Route-based VPNs <a id="route-based-vpns"></a>

If defining which IP addresses are behind each tunnel is too cumbersome, route-based gateways can be used. With route-based gateways, IPSec tunnels are modeled as a network interface or virtual tunnel interface. IP routing \(either static routes or dynamic routing protocols\) decides which one of these tunnel interfaces to use when sending each packet. Route-based VPNs are the preferred connection method for on-premises devices. They're more resilient to topology changes such as the creation of new subnets.

Use a route-based VPN gateway if you need any of the following types of connectivity:

* Connections between virtual networks
* Point-to-site connections
* Multisite connections
* Coexistence with an Azure ExpressRoute gateway

Key features of route-based VPN gateways in Azure include:

* Supports IKEv2
* Uses any-to-any \(wildcard\) traffic selectors
* Can use _dynamic routing protocols_, where routing/forwarding tables direct traffic to different IPSec tunnels

  In this case, the source and destination networks aren't statically defined as they are in policy-based VPNs or even in route-based VPNs with static routing. Instead, data packets are encrypted based on network routing tables that are created dynamically using routing protocols such as Border Gateway Protocol \(BGP\).

### VPN gateway sizes <a id="vpn-gateway-sizes"></a>

The capabilities of your VPN gateway are determined by the SKU or size that you deploy. This table shows the main capabilities of each available SKU.

| VPN GATEWAY SIZES |  |  |  |
| :--- | :--- | :--- | :--- |
| SKU | Site-to-site/Network-to-network tunnels | Aggregate throughput benchmark | Border Gateway Protocol support |
| Basic \[See Note\] | Maximum: 10 | 100 Mbps | Not supported |
| VpnGw1/Az | Maximum: 30 | 650 Mbps | Supported |
| VpnGw2/Az | Maximum: 30 | 1 Gbps | Supported |
| VpnGw3/Az | Maximum: 30 | 1.25 Gbps | Supported |

Note

A Basic VPN gateway should only be used for Dev/Test workloads. In addition, it's unsupported to migrate from Basic to the VpnGW1/2/3/Az SKUs at a later time without having to remove the gateway and redeploy.

### Deploy VPN gateways <a id="deploy-vpn-gateways"></a>

Before you can deploy a VPN gateway, you'll need some Azure and on-premises resources.

#### Required Azure resources <a id="required-azure-resources"></a>

You'll need these Azure resources before you can deploy an operational VPN gateway:

* **Virtual network**. Deploy a virtual network with enough address space for the additional subnet that you'll need for the VPN gateway. The address space for this virtual network must not overlap with the on-premises network that you'll be connecting to. You can deploy only one VPN gateway within a virtual network.
* **GatewaySubnet**. Deploy a subnet called `GatewaySubnet` for the VPN gateway. Use at least a **/27** address mask to make sure you have enough IP addresses in the subnet for future growth. You can't use this subnet for any other services.
* **Public IP address**. Create a Basic-SKU dynamic public IP address if you're using a non-zone-aware gateway. This address provides a public-routable IP address as the target for your on-premises VPN device. This IP address is dynamic, but it won't change unless you delete and re-create the VPN gateway.
* **Local network gateway**. Create a local network gateway to define the on-premises network's configuration, such as where the VPN gateway will connect and what it will connect to. This configuration includes the on-premises VPN device's public IPv4 address and the on-premises routable networks. This information is used by the VPN gateway to route packets that are destined for on-premises networks through the IPSec tunnel.
* **Virtual network gateway**. Create the virtual network gateway to route traffic between the virtual network and the on-premises datacenter or other virtual networks. The virtual network gateway can be either a VPN or ExpressRoute gateway, but this unit only deals with VPN virtual network gateways. \(You'll learn more about ExpressRoute in a separate unit later in this module.\)
* **Connection**. Create a connection resource to create a logical connection between the VPN gateway and the local network gateway.

  * The connection is made to the on-premises VPN device's IPv4 address as defined by the local network gateway.
  * The connection is made from the virtual network gateway and its associated public IP address.

  You can create multiple connections.

The following diagram shows this combination of resources and their relationships to help you better understand what's required to deploy a VPN gateway.

[![Visualization of resource requirements for a VPN gateway.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/resource-requirements-for-vpn-gateway.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/resource-requirements-for-vpn-gateway-expanded.png#lightbox)

#### Required on-premises resources <a id="required-on-premises-resources"></a>

To connect your datacenter to a VPN gateway, you'll need these on-premises resources:

* A VPN device that supports policy-based or route-based VPN gateways
* A public-facing \(internet-routable\) IPv4 address

### High-availability scenarios <a id="high-availability-scenarios"></a>

There are several ways to ensure you have a fault-tolerant configuration.

#### Active/standby <a id="activestandby"></a>

By default, VPN gateways are deployed as two instances in an active/standby configuration, even if you only see one VPN gateway resource in Azure. When planned maintenance or unplanned disruption affects the active instance, the standby instance automatically assumes responsibility for connections without any user intervention. Connections are interrupted during this failover, but they're typically restored within a few seconds for planned maintenance and within 90 seconds for unplanned disruptions.

[![Visualization of active/standby virtual network gateway.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/active-standby.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/active-standby-expanded.png#lightbox)

#### Active/active <a id="activeactive"></a>

With the introduction of support for the BGP routing protocol, you can also deploy VPN gateways in an active/active configuration. In this configuration, you assign a unique public IP address to each instance. You then create separate tunnels from the on-premises device to each IP address. You can extend the high availability by deploying an additional VPN device on-premises.

[![Visualization of active/active virtual network gateway.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/dual-redundancy.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/dual-redundancy-expanded.png#lightbox)

#### ExpressRoute failover <a id="expressroute-failover"></a>

Another high-availability option is to configure a VPN gateway as a secure failover path for ExpressRoute connections. ExpressRoute circuits have resiliency built in. But they aren't immune to physical problems that affect the cables delivering connectivity or outages that affect the complete ExpressRoute location. In high-availability scenarios, where there's risk associated with an outage of an ExpressRoute circuit, you can also provision a VPN gateway that uses the internet as an alternative method of connectivity. In this way, you can ensure there's always a connection to the virtual networks.

#### Zone-redundant gateways <a id="zone-redundant-gateways"></a>

In regions that support availability zones, VPN gateways and ExpressRoute gateways can be deployed in a zone-redundant configuration. This configuration brings resiliency, scalability, and higher availability to virtual network gateways. Deploying gateways in Azure availability zones physically and logically separates gateways within a region while protecting your on-premises network connectivity to Azure from zone-level failures. These gateways require different gateway SKUs and use Standard public IP addresses instead of Basic public IP addresses.

## Azure ExpressRoute fundamentals

100 XP

* 5 minutes

ExpressRoute lets you extend your on-premises networks into the Microsoft cloud over a private connection with the help of a connectivity provider. With ExpressRoute, you can establish connections to Microsoft cloud services, such as Microsoft Azure and Microsoft 365.

Connectivity can be from an any-to-any \(IP VPN\) network, a point-to-point Ethernet network, or a virtual cross-connection through a connectivity provider at a colocation facility. ExpressRoute connections don't go over the public Internet. This allows ExpressRoute connections to offer more reliability, faster speeds, consistent latencies, and higher security than typical connections over the Internet. For information on how to connect your network to Microsoft using ExpressRoute, see ExpressRoute connectivity models.

[![Visualization that shows a high-level overview of the Azure ExpressRoute service.](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/azure-expressroute-overview.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/azure-expressroute-overview-expanded.png#lightbox)

As part of your work for Tailwind Traders, you should understand what Azure ExpressRoute is and how it integrates with on-premises and Azure networks. In this unit, you'll learn about the benefits that ExpressRoute provides compared to other site-to-site connectivity options. As a result, you'll learn whether ExpressRoute can provide your company with the best possible network performance.

Throughout this unit, we'll focus on two different layers of the Open Systems Interconnection \(OSI\) model:

* **Layer 2 \(L2\)**: This layer is the Data Link Layer, which provides node-to-node communication between two nodes on the same network.
* **Layer 3 \(L3\)**: This layer is the Network Layer, which provides addressing and routing between nodes on a multi-node network.

### Features and benefits of ExpressRoute <a id="features-and-benefits-of-expressroute"></a>

There are several benefits to using ExpressRoute as the connection service between Azure and on-premises networks.

* Layer 3 connectivity between your on-premises network and the Microsoft Cloud through a connectivity provider. Connectivity can be from an any-to-any \(IPVPN\) network, a point-to-point Ethernet connection, or through a virtual cross-connection via an Ethernet exchange.
* Connectivity to Microsoft cloud services across all regions in the geopolitical region.
* Global connectivity to Microsoft services across all regions with the ExpressRoute premium add-on.
* Dynamic routing between your network and Microsoft via BGP.
* Built-in redundancy in every peering location for higher reliability.
* Connection uptime SLA.
* QoS support for Skype for Business.

#### Layer 3 connectivity <a id="layer-3-connectivity"></a>

ExpressRoute provides Layer 3 \(address-level\) connectivity between your on-premises network and the Microsoft cloud through connectivity partners. These connections can be from a point-to-point or any-to-any network. They can also be virtual cross-connections through an exchange.

#### Built-in redundancy <a id="built-in-redundancy"></a>

Each connectivity provider uses redundant devices to ensure that connections established with Microsoft are highly available. You can configure multiple circuits to complement this feature. All redundant connections are configured with Layer 3 connectivity to meet service-level agreements.

#### Connectivity to Microsoft cloud services <a id="connectivity-to-microsoft-cloud-services"></a>

ExpressRoute enables direct access to the following services in all regions:

* Microsoft Office 365
* Microsoft Dynamics 365
* Azure compute services, such as Azure Virtual Machines
* Azure cloud services, such as Azure Cosmos DB and Azure Storage

Office 365 was created to be accessed securely and reliably via the internet. For this reason, we recommend the use of ExpressRoute for specific scenarios. The "Learn more" section at the end of this module includes a link about using ExpressRoute to access Office 365.

#### Across on-premises connectivity with ExpressRoute Global Reach <a id="across-on-premises-connectivity-with-expressroute-global-reach"></a>

You can enable ExpressRoute Global Reach to exchange data across your on-premises sites by connecting your ExpressRoute circuits. For example, assume that you have a private datacenter in California connected to ExpressRoute in Silicon Valley. You have another private datacenter in Texas connected to ExpressRoute in Dallas. With ExpressRoute Global Reach, you can connect your private datacenters through two ExpressRoute circuits. Your cross-datacenter traffic will travel through the Microsoft network.

#### Dynamic routing <a id="dynamic-routing"></a>

ExpressRoute uses the Border Gateway Protocol \(BGP\) routing protocol. BGP is used to exchange routes between on-premises networks and resources running in Azure. This protocol enables dynamic routing between your on-premises network and services running in the Microsoft cloud.

### ExpressRoute connectivity models <a id="expressroute-connectivity-models"></a>

ExpressRoute supports three models that you can use to connect your on-premises network to the Microsoft cloud:

* CloudExchange colocation
* Point-to-point Ethernet connection
* Any-to-any connection

[![Azure connectivity models](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/azure-connectivity-models.png)](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/azure-connectivity-models-expanded.png#lightbox)

#### Colocation at a cloud exchange <a id="colocation-at-a-cloud-exchange"></a>

Colocated providers can normally offer both Layer 2 and Layer 3 connections between your infrastructure, which might be located in the colocation facility, and the Microsoft cloud. For example, if your datacenter is colocated at a cloud exchange such as an ISP, you can request a virtual cross-connection to the Microsoft cloud.

#### Point-to-point Ethernet connection <a id="point-to-point-ethernet-connection"></a>

Point-to-point connections provide Layer 2 and Layer 3 connectivity between your on-premises site and Azure. You can connect your offices or datacenters to Azure by using the point-to-point links. For example, if you have an on-premises datacenter, you can use a point-to-point Ethernet link to connect to Microsoft.

#### Any-to-any networks <a id="any-to-any-networks"></a>

With any-to-any connectivity, you can integrate your wide area network \(WAN\) with Azure by providing connections to your offices and datacenters. Azure integrates with your WAN connection to provide a connection like you would have between your datacenter and any branch offices.

With any-to-any connections, all WAN providers offer Layer 3 connectivity. For example, if you already use Multiprotocol Label Switching to connect to your branch offices or other sites in your organization, an ExpressRoute connection to Microsoft behaves like any other location on your private WAN.

### Security considerations <a id="security-considerations"></a>

With ExpressRoute, your data doesn't travel over the public internet, so it's not exposed to the potential risks associated with internet communications. ExpressRoute is a private connection from your on-premises infrastructure to your Azure infrastructure. Even if you have an ExpressRoute connection, DNS queries, certificate revocation list checking, and Azure Content Delivery Network requests are still sent over the public internet.

## Summary

100 XP

* 2 minutes

In this module, you used the Tailwind Traders scenario to learn about the core networking resources that are available in Azure. You learned about the benefits and usage of Azure Virtual Network, Azure VPN Gateway, and Azure ExpressRoute.

You can now apply this information to help your business use Azure's networking resources to configure its network infrastructure.

### Learn more <a id="learn-more"></a>

* [Azure networking services overview](https://docs.microsoft.com/en-us/azure/networking/networking-overview)
* [Virtual Network documentation](https://docs.microsoft.com/en-us/azure/virtual-network/)
* [ExpressRoute overview](https://docs.microsoft.com/en-us/azure/expressroute/)
* [ExpressRoute FAQ](https://docs.microsoft.com/en-us/azure/expressroute/expressroute-faqs)
* [Learning Path: Architect network infrastructure in Azure](https://docs.microsoft.com/en-us/learn/paths/architect-network-infrastructure/)
* [Module: Connect your on-premises network to the Microsoft global network by using ExpressRoute](https://docs.microsoft.com/en-us/learn/modules/connect-on-premises-network-with-expressroute/)
* [Virtual network peering](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview)

### Azure Fundamentals learning path <a id="azure-fundamentals-learning-path"></a>

This module is part of the [Azure Fundamentals part 2: Describe core Azure services](https://docs.microsoft.com/en-us/learn/paths/az-900-describe-core-azure-services/) learning path, which is one of six learning paths for Azure Fundamentals.

Here are the learning paths in this series:

* [Azure Fundamentals part 1: Describe core Azure concepts](https://docs.microsoft.com/en-us/learn/paths/az-900-describe-cloud-concepts/)
* [Azure Fundamentals part 2: Describe core Azure services](https://docs.microsoft.com/en-us/learn/paths/az-900-describe-core-azure-services/)
* [Azure Fundamentals part 3: Describe core solutions and management tools on Azure](https://docs.microsoft.com/en-us/learn/paths/az-900-describe-core-solutions-management-tools-azure/)
* [Azure Fundamentals part 4: Describe general security and network security features](https://docs.microsoft.com/en-us/learn/paths/az-900-describe-general-security-network-security-features/)
* [Azure Fundamentals part 5: Describe identity, governance, privacy, and compliance features](https://docs.microsoft.com/en-us/learn/paths/az-900-describe-identity-governance-privacy-compliance-features/)
* [Azure Fundamentals part 6: Describe Azure cost management and service level agreements](https://docs.microsoft.com/en-us/learn/paths/az-900-describe-azure-cost-management-service-level-agreements/)

