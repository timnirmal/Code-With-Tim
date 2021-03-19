# Explore Azure Storage services



## Introduction

100 XP

* 2 minutes

Suppose your company, Tailwind Traders, has a number of product brochures, datasheets, product images, and other files that are related to marketing, sales, and support. In the past, your company has been hosting these files on standalone web servers in your datacenter.

Your company is now in the process of migrating its applications to the cloud, and your development team is currently architecting new applications. Your Chief Technology Officer \(CTO\) wants to migrate all of your marketing, sales, and support files to the cloud in order to take advantage of geographic distribution of your files. This move also reduces the number of physical servers that your company maintains in your datacenter. As part of your migration strategy, you need to determine the correct approach for your cloud-based storage infrastructure.

![Tailwind Traders company logo.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/shared/media/tailwind-traders-logo.png)

In this module, you'll learn about the different Azure storage options and the scenarios in which each is appropriate.

 Note

Azure storage isn't the same as Azure database services.

### Learning objectives <a id="learning-objectives"></a>

After completing this module, you'll be able to describe the benefits and usage of:

* Azure Blob Storage
* Azure Disk Storage
* Azure Files Storage
* Azure Blob Access tiers

### Prerequisites <a id="prerequisites"></a>

* You should be familiar with basic computing concepts and terminology

## Azure Storage account fundamentals

100 XP

* 4 minutes

The Chief Technology Officer \(CTO\) for your company, Tailwind Traders, has tasked your team with migrating all of your files to the cloud. Your team has chosen [Azure Storage](https://azure.microsoft.com/product-categories/storage), which is a service that you can use to store files, messages, tables, and other types of information. Clients such as websites, mobile apps, desktop applications, and many other types of custom solutions can read data from and write data to Azure Storage. Azure Storage is also used by infrastructure as a service virtual machines, and platform as a service cloud services.

The following video introduces the different services that should be available with Azure Storage.

To begin using Azure Storage, you first create an Azure Storage account to store your data objects. You can create an Azure Storage account by using the Azure portal, PowerShell, or the Azure CLI.

[![Screenshot of creating a storage account.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-storage-fundamentals/media/create-storage-account.png)](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-storage-fundamentals/media/create-storage-account-expanded.png#lightbox)

Your storage account will contain all of your Azure Storage data objects, such as blobs, files, and disks.

 Note

Azure VMs use Azure Disk Storage to store virtual disks. However, you can't use Azure Disk Storage to store a disk outside of a virtual machine.

![Diagram of hierarchy of a storage account.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-storage-fundamentals/media/account-container-blob.png)

A storage account provides a unique namespace for your Azure Storage data, that's accessible from anywhere in the world over HTTP or HTTPS. Data in this account is secure, highly available, durable, and massively scalable.

For more information, see [Create a storage account](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-create).  


## Disk storage fundamentals

100 XP

* 4 minutes

Disk Storage provides disks for Azure virtual machines. Applications and other services can access and use these disks as needed, similar to how they would in on-premises scenarios. Disk Storage allows data to be persistently stored and accessed from an attached virtual hard disk.

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-storage-fundamentals/media/icon-azure-standard-storage.png)

Disks come in many different sizes and performance levels, from solid-state drives \(SSDs\) to traditional spinning hard disk drives \(HDDs\), with varying performance tiers. You can use standard SSD and HDD disks for less critical workloads, premium SSD disks for mission-critical production applications, and ultra disks for data-intensive workloads such as SAP HANA, top tier databases, and transaction-heavy workloads. Azure has consistently delivered enterprise-grade durability for infrastructure as a service \(Iaas\) disks, with an industry-leading ZERO% annualized failure rate.

The following illustration shows an Azure virtual machine that uses separate disks to store different data.

![Diagram of two disks inside a virtual machine. One stores the operating system and one stores data.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-storage-fundamentals/media/azure-disks.png)

## Azure Blob storage fundamentals

100 XP

* 4 minutes

Azure Blob Storage is an object storage solution for the cloud. It can store massive amounts of data, such as text or binary data. Azure Blob Storage is unstructured, meaning that there are no restrictions on the kinds of data it can hold. Blob Storage can manage thousands of simultaneous uploads, massive amounts of video data, constantly growing log files, and can be reached from anywhere with an internet connection.

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-storage-fundamentals/media/icon-azure-blob-storage.png)

Blobs aren't limited to common file formats. A blob could contain gigabytes of binary data streamed from a scientific instrument, an encrypted message for another application, or data in a custom format for an app you're developing. One advantage of blob storage over disk storage is that it does not require developers to think about or manage disks; data is uploaded as blobs, and Azure takes care of the physical storage needs.

Blob Storage is ideal for:

* Serving images or documents directly to a browser.
* Storing files for distributed access.
* Streaming video and audio.
* Storing data for backup and restore, disaster recovery, and archiving.
* Storing data for analysis by an on-premises or Azure-hosted service.
* Storing up to 8 TB of data for virtual machines.

You store blobs in containers, which helps you organize your blobs depending on your business needs.

The following diagram illustrates how you might use Azure accounts, containers, and blobs.

![Diagram of hierarchy of a storage account.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-storage-fundamentals/media/account-container-blob.png)

## Azure Files fundamentals

100 XP

* 4 minutes

Azure Files offers fully managed file shares in the cloud that are accessible via the industry standard Server Message Block and Network File System \(preview\) protocols. Azure file shares can be mounted concurrently by cloud or on-premises deployments of Windows, Linux, and macOS. Applications running in Azure virtual machines or cloud services can mount a file storage share to access file data, just as a desktop application would mount a typical SMB share. Any number of Azure virtual machines or roles can mount and access the file storage share simultaneously. Typical usage scenarios would be to share files anywhere in the world, diagnostic data, or application data sharing.

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-storage-fundamentals/media/icon-azure-files.png)

Use Azure Files for the following situations:

* Many on-premises applications use file shares. Azure Files makes it easier to migrate those applications that share data to Azure. If you mount the Azure file share to the same drive letter that the on-premises application uses, the part of your application that accesses the file share should work with minimal, if any, changes.
* Store configuration files on a file share and access them from multiple VMs. Tools and utilities used by multiple developers in a group can be stored on a file share, ensuring that everybody can find them, and that they use the same version.
* Write data to a file share, and process or analyze the data later. For example, you might want to do this with diagnostic logs, metrics, and crash dumps.

The following illustration shows Azure Files being used to share data between two geographical locations. Azure Files ensures the data is encrypted at rest, and the SMB protocol ensures the data is encrypted in transit.

![Diagram that shows the file sharing capabilities of Azure Files between a Western US Azure file share and a European Azure file share, each with their own SMB users.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-storage-fundamentals/media/azure-files.png)

One thing that distinguishes Azure Files from files on a corporate file share is that you can access the files from anywhere in the world, by using a URL that points to the file. You can also use Shared Access Signature \(SAS\) tokens to allow access to a private asset for a specific amount of time.

Here's an example of a service SAS URI, showing the resource URI and the SAS token:

[![Screenshot of components of a service SAS URI.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-storage-fundamentals/media/sas-storage-uri.png)](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-storage-fundamentals/media/sas-storage-uri.png#lightbox)



## Understanding Blob access tiers

100 XP

* 4 minutes

Data stored in the cloud can grow at an exponential pace. To manage costs for your expanding storage needs, it's helpful to organize your data based on attributes like frequency of access and planned retention period. Data stored in the cloud can be different based on how it's generated, processed, and accessed over its lifetime. Some data is actively accessed and modified throughout its lifetime. Some data is accessed frequently early in its lifetime, with access dropping drastically as the data ages. Some data remains idle in the cloud and is rarely, if ever, accessed after it's stored. To accommodate these different access needs, Azure provides several _access tiers_, which you can use to balance your storage costs with your access needs.

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-storage-fundamentals/media/icon-storage-tiers.png)

Azure Storage offers different access tiers for your blob storage, helping you store object data in the most cost-effective manner. The available access tiers include:

* **Hot access tier**: Optimized for storing data that is accessed frequently \(for example, images for your website\).
* **Cool access tier**: Optimized for data that is infrequently accessed and stored for at least 30 days \(for example, invoices for your customers\).
* **Archive access tier**: Appropriate for data that is rarely accessed and stored for at least 180 days, with flexible latency requirements \(for example, long-term backups\).

The following considerations apply to the different access tiers:

* Only the hot and cool access tiers can be set at the account level. The archive access tier isn't available at the account level.
* Hot, cool, and archive tiers can be set at the blob level, during upload or after upload.
* Data in the cool access tier can tolerate slightly lower availability, but still requires high durability, retrieval latency, and throughput characteristics similar to hot data. For cool data, a slightly lower availability service-level agreement \(SLA\) and higher access costs compared to hot data are acceptable trade-offs for lower storage costs.
* Archive storage stores data offline and offers the lowest storage costs, but also the highest costs to rehydrate and access data.

The following illustration demonstrates choosing between the hot and cool access tiers on a general purpose storage account.

[![Screenshot of specifying the Azure access tier.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-storage-fundamentals/media/account-tier.png)](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-storage-fundamentals/media/account-tier.png#lightbox)

