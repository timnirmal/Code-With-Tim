# Explore Azure database and analytics services  Introduction



## Introduction

* 2 minutes

Due to a growing number of acquisitions over the last decade, Tailwind Traders uses a variety of database and analytics technologies. As the company begins to migrate existing data workloads and deploy new data workloads to Azure, it needs to understand which Azure technology will be appropriate for each workload. The company's Chief Technology Officer \(CTO\) has assigned you the task of researching the different database options that are available. This will help your company choose the right options for each of your data scenarios.

![Tailwind Traders company logo.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/shared/media/tailwind-traders-logo.png)

Today's applications are required to be highly responsive and always online. To achieve low latency and high availability, instances of these applications need to be deployed in datacenters that are close to their users. Applications need to respond in real time to large changes in usage at peak hours, store ever-increasing volumes of data, and make this data available to users in milliseconds. To help your company reach its goals, Azure database services are globally distributed, and Azure supports many of the industry standard databases and APIs.

The following video provides a brief overview for several of the database services that are available on Azure.

In this module, you'll learn more about several of the primary database services that are available on Azure, and you'll analyze some of the reasons why each of these services might be the right choice for your data needs.

### Learning objectives <a id="learning-objectives"></a>

After completing this module, you'll be able to describe the benefits and usage of:

* Azure Cosmos DB
* Azure SQL Database
* Azure SQL Managed Instance
* Azure Database for MySQL
* Azure Database for PostgreSQL
* Azure Synapse Analytics
* Azure HDInsight
* Azure Databricks
* Azure Data Lake Analytics

### Prerequisites <a id="prerequisites"></a>

* You should be familiar with basic computing concepts and terminology.
* You should be familiar with basic database concepts and terminology.

## Explore Azure Cosmos DB

* 4 minutes

Over the years, Tailwind Traders has acquired several smaller companies. Each of these companies had teams of developers who used different database services and various APIs to work with their data. A long-term plan might be to eventually move all of the disparate data to a common database service. For now, though, you'd like to enable each of these teams to work with an environment where they can use their existing skills. Fortunately for you, Azure Cosmos DB can help out.

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-database-fundamentals/media/icon-service-azure-cosmos-db.png)

Azure Cosmos DB is a globally distributed, multi-model database service. You can elastically and independently scale throughput and storage across any number of Azure regions worldwide. You can take advantage of fast, single-digit-millisecond data access by using any one of several popular APIs. Azure Cosmos DB provides comprehensive service level agreements for throughput, latency, availability, and consistency guarantees.

Azure Cosmos DB supports schema-less data, which lets you build highly responsive and "Always On" applications to support constantly changing data. You can use this feature to store data that's updated and maintained by users around the world.

For example, Tailwind Traders provides a public training portal that is used by customers across the globe to learn about the different tools that Tailwind Traders creates. Tailwind Traders developers maintain and update the data. The following illustration shows a sample Azure Cosmos DB database that's used to store data for the Tailwind Traders training portal website.

[![Diagram of Azure Cosmos DB databases in a training portal website.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-database-fundamentals/media/azure-cosmos-db.png)](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-database-fundamentals/media/azure-cosmos-db-expanded.png#lightbox)

Azure Cosmos DB is flexible. At the lowest level, Azure Cosmos DB stores data in atom-record-sequence \(ARS\) format. The data is then abstracted and projected as an API, which you specify when you're creating your database. Your choices include SQL, MongoDB, Cassandra, Tables, and Gremlin. This level of flexibility means that as you migrate your company's databases to Azure Cosmos DB, your developers can stick with the API that they're the most comfortable with.

## Explore Azure SQL Database

* 4 minutes

Azure SQL Database is a relational database based on the latest stable version of the Microsoft SQL Server database engine. SQL Database is a high-performance, reliable, fully managed, and secure database. You can use it to build data-driven applications and websites in the programming language of your choice, without needing to manage infrastructure.

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-database-fundamentals/media/icon-service-sql-database.png)

### Features <a id="features"></a>

Azure SQL Database is a platform as a service \(PaaS\) database engine. It handles most of the database management functions, such as upgrading, patching, backups, and monitoring, without user involvement. SQL Database provides 99.99 percent availability. PaaS capabilities that are built into SQL Database enable you to focus on the domain-specific database administration and optimization activities that are critical for your business. SQL Database is a fully managed service that has built-in high availability, backups, and other common maintenance operations. Microsoft handles all updates to the SQL and operating system code. You don't have to manage the underlying infrastructure.

You can create a highly available and high-performance data storage layer for the applications and solutions in Azure. SQL Database can be the right choice for a variety of modern cloud applications because it enables you to process both relational data and non-relational structures, such as graphs, JSON, spatial, and XML.

You can use advanced query processing features, such as high-performance, in-memory technologies and intelligent query processing. In fact, the newest capabilities of SQL Server are released first to SQL Database, and then to SQL Server itself. You get the newest SQL Server capabilities, with no overhead for updates or upgrades, tested across millions of databases.

### Migration <a id="migration"></a>

Tailwind Traders currently uses several on-premises servers running SQL Server, which provide data storage for your public-facing website \(for example, customer data, order history, and product catalogs\). In addition, your on-premises servers running SQL Server also provide data storage for your internal-only training portal website. Tailwind Traders uses the website for new employee training materials \(such as study materials, certification details, and training transcripts\). The following illustration shows the types of data that your company might store in the Azure SQL Database training portal website.

[![Diagram of Azure SQL Database in a training portal website.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-database-fundamentals/media/azure-sql.png)](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-database-fundamentals/media/azure-sql-expanded.png#lightbox)

You can migrate your existing SQL Server databases with minimal downtime by using the Azure Database Migration Service. The Microsoft Data Migration Assistant can generate assessment reports that provide recommendations to help guide you through required changes prior to performing a migration. After you assess and resolve any remediation required, you're ready to begin the migration process. The Azure Database Migration Service performs all of the required steps. You just change the connection string in your apps.

## Explore Azure SQL Managed Instance

* 4 minutes

Azure SQL Managed Instance is a scalable cloud data service that provides the broadest SQL Server database engine compatibility with all the benefits of a fully managed platform as a service. Depending on your scenario, Azure SQL Managed Instance might offer more options for your database needs.

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-database-fundamentals/media/icon-service-managed-sql-instance.png)

### Features <a id="features"></a>

Like Azure SQL Database, Azure SQL Managed Instance is a platform as a service \(PaaS\) database engine, which means that your company will be able to take advantage of the best features of moving your data to the cloud in a fully-managed environment. For example, your company will no longer need to purchase and manage expensive hardware, and you won't have to maintain the additional overhead of managing your on-premises infrastructure. On the other hand, your company will benefit from the quick provisioning and service scaling features of Azure, together with automated patching and version upgrades. In addition, you'll be able to rest assured that your data will always be there when you need it through built-in high availability features and a 99.99% uptime service level agreement \(SLA\). You'll also be able to protect your data with automated backups and a configurable backup retention period.

Azure SQL Database and Azure SQL Managed Instance offer many of the same features; however, Azure SQL Managed Instance provides several options that might not be available to Azure SQL Database. For example, Tailwind Traders currently uses several on-premises servers running SQL Server, and they would like to migrate their existing databases to a SQL database running in the cloud. However, several of their databases use Cyrillic characters for collation. In this scenario, Tailwind Traders should migrate their databases to an Azure SQL Managed Instance, since Azure SQL Database only uses the default `SQL_Latin1_General_CP1_CI_AS` server collation.

 Note

For a detailed list of the differences between Azure SQL Database and Azure SQL Managed Instance, see [Features comparison: Azure SQL Database and Azure SQL Managed Instance](https://docs.microsoft.com/en-us/azure/azure-sql/database/features-comparison/).

### Migration <a id="migration"></a>

Azure SQL Managed Instance makes it easy to migrate your on-premises data on SQL Server to the cloud using the Azure Database Migration Service \(DMS\) or native backup and restore. After you have discovered all of the features that your company uses, you need to assess which on-premises SQL Server instances you can migrate to Azure SQL Managed Instance to see if you have any blocking issues. Once you have resolved any issues, you can migrate your data, then cutover from your on-premises SQL Server to your Azure SQL Managed Instance by changing the connection string in your applications.

![The process flow for data migration to Azure SQL Managed Instance.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-database-fundamentals/media/migration-process-flow-small.png)

 Note

For a detailed description of the migration process, see [Migration guide: SQL Server to SQL Managed Instance](https://docs.microsoft.com/en-us/azure/azure-sql/migration-guides/managed-instance/sql-server-to-managed-instance-guide)

## Explore Azure database for MySQL

* 4 minutes

Tailwind Traders currently manages several websites on-premises that use the LAMP stack \(Linux, Apache, MySQL, PHP\). As part of your planning for your migration strategy, the different teams at Tailwind Traders have been researching the available service offerings that Azure provides. You've already discovered that the Web Apps feature of Azure App Service provides built-in functionality to create web applications that use PHP on a Linux server running Apache. You've been tasked with investigating whether the database requirements for the web development team will continue to be met after the migration to Azure.

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-database-fundamentals/media/icon-service-azure-database-mysql-server.png)

Azure Database for MySQL is a relational database service in the cloud, and it's based on the MySQL Community Edition database engine, versions 5.6, 5.7, and 8.0. With it, you have a 99.99 percent availability service level agreement from Azure, powered by a global network of Microsoft-managed datacenters. This helps keep your app running 24/7. With every Azure Database for MySQL server, you take advantage of built-in security, fault tolerance, and data protection that you would otherwise have to buy or design, build, and manage. With Azure Database for MySQL, you can use point-in-time restore to recover a server to an earlier state, as far back as 35 days.

Azure Database for MySQL delivers:

* Built-in high availability with no additional cost.
* Predictable performance and inclusive, pay-as-you-go pricing.
* Scale as needed, within seconds.
* Ability to protect sensitive data at-rest and in-motion.
* Automatic backups.
* Enterprise-grade security and compliance.

These capabilities require almost no administration, and all are provided at no additional cost. They allow you to focus on rapid app development and accelerating your time-to-market, rather than having to manage virtual machines and infrastructure. In addition, you can migrate your existing MySQL databases with minimal downtime by using the Azure Database Migration Service. After you have completed your migration, you can continue to develop your application with the open-source tools and platform of your choice. You don't have to learn new skills.

[![Diagram of Azure Database for MySQL.](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-database-fundamentals/media/azure-db-for-mysql-conceptual-diagram.png)](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-database-fundamentals/media/azure-db-for-mysql-conceptual-diagram-expanded.png#lightbox)

Azure Database for MySQL offers several service tiers, and each tier provides different performance and capabilities to support lightweight to heavyweight database workloads. You can build your first app on a small database for a few dollars a month, and then adjust the scale to meet the needs of your solution. Dynamic scalability enables your database to transparently respond to rapidly changing resource requirements. You only pay for the resources you need, and only when you need them.

## Explore Azure Database for PostgreSQL

* 4 minutes

As part of its overall data strategy, Tailwind Traders have been using PostgreSQL for several years. You and your team probably already know the benefits of PostgreSQL. Part of your migration is to use Azure Database for PostgreSQL, and you want to make sure that you'll have access to the same benefits as your on-premises server before moving to the cloud.

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-database-fundamentals/media/icon-service-azure-database-postgresql-server.png)

Azure Database for PostgreSQL is a relational database service in the cloud. The server software is based on the community version of the open-source PostgreSQL database engine. Your familiarity with tools and expertise with PostgreSQL is applicable when you're using Azure Database for PostgreSQL.

Moreover, Azure Database for PostgreSQL delivers the following benefits:

* Built-in high availability compared to on-premises resources. There's no additional configuration, replication, or cost required to make sure your applications are always available.
* Simple and flexible pricing. You have predictable performance based on a selected pricing tier choice that includes software patching, automatic backups, monitoring, and security.
* Scale up or down as needed, within seconds. You can scale compute or storage independently as needed, to make sure you adapt your service to match usage.
* Adjustable automatic backups and point-in-time-restore for up to 35 days.
* Enterprise-grade security and compliance to protect sensitive data at-rest and in-motion. This security covers data encryption on disk and SSL encryption between client and server communication.

Azure Database for PostgreSQL is available in two deployment options: **Single Server** and **Hyperscale \(Citus\)**.

**Single Server**

The Single Server deployment option delivers:

* Built-in high availability with no additional cost \(99.99 percent SLA\).
* Predictable performance and inclusive, pay-as-you-go pricing.
* Vertical scale as needed, within seconds.
* Monitoring and alerting to assess your server.
* Enterprise-grade security and compliance.
* Ability to protect sensitive data at-rest and in-motion.
* Automatic backups and point-in-time-restore for up to 35 days.

All those capabilities require almost no administration, and all are provided at no additional cost. You can focus on rapid application development and accelerating your time to market, rather than having to manage virtual machines and infrastructure. You can continue to develop your application with the open-source tools and platform of your choice, without having to learn new skills.

The Single Server deployment option offers three pricing tiers: Basic, General Purpose, and Memory Optimized. Each tier offers different resource capabilities to support your database workloads. You can build your first app on a small database for a few dollars a month, and then adjust the scale to meet the needs of your solution. Dynamic scalability enables your database to transparently respond to rapidly changing resource requirements. You only pay for the resources you need, and only when you need them.

**Hyperscale \(Citus\)**

The Hyperscale \(Citus\) option horizontally scales queries across multiple machines by using sharding. Its query engine parallelizes incoming SQL queries across these servers for faster responses on large datasets. It serves applications that require greater scale and performance, generally workloads that are approaching, or already exceed, 100 GB of data.

The Hyperscale \(Citus\) deployment option supports multi-tenant applications, real-time operational analytics, and high throughput transactional workloads. Applications built for PostgreSQL can run distributed queries on Hyperscale \(Citus\) with standard connection libraries and minimal changes.  


## Explore big data and analytics

* 4 minutes

Several years ago, Tailwind Traders rolled out a new GPS tracking system for all of its delivery vehicles. The new system provides real-time tracking data to your primary datacenter. Your CTO wants your team to look at several years of tracking data in order to determine trends. For example, an important trend might be a spike in deliveries around the holidays that would require hiring additional staff. Through an in-depth analysis of the tracking data that you've recorded, your CTO seeks to predict when changes are necessary, and proactively take the steps that are necessary to manage spikes appropriately.

Data comes in all types of forms and formats. When we talk about big data, we're referring to large volumes of data. In this Tailwind Traders scenario, data is collected from the GPS sensors, which includes location information, data from weather systems, and many other sources that generate large amounts of data. This amount of data becomes increasingly hard to make sense of and to base decisions on. The volumes are so large that traditional forms of processing and analysis are no longer appropriate.

Open-source cluster technologies have been developed, over time, to try to deal with these large datasets. Microsoft Azure supports a broad range of technologies and services to provide big data and analytic solutions, including Azure Synapse Analytics, Azure HDInsight, Azure Databricks, and Azure Data Lake Analytics.

### Azure Synapse Analytics <a id="azure-synapse-analytics"></a>

[Azure Synapse Analytics](https://docs.microsoft.com/en-us/azure/sql-data-warehouse/) \(formerly Azure SQL Data Warehouse\) is a limitless analytics service that brings together enterprise data warehousing and big data analytics. You can query data on your terms by using either serverless or provisioned resources at scale. You have a unified experience to ingest, prepare, manage, and serve data for immediate BI and machine learning needs.

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-database-fundamentals/media/icon-service-azure-synapse-analytics.png)

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-database-fundamentals/media/icon-service-hd-insight.png)

### Azure HDInsight <a id="azure-hdinsight"></a>

[Azure HDInsight](https://azure.microsoft.com/services/hdinsight/) is a fully managed, open-source analytics service for enterprises. It's a cloud service that makes it easier, faster, and more cost-effective to process massive amounts of data. You can run popular open-source frameworks and create cluster types such as [Apache Spark](https://docs.microsoft.com/en-us/azure/hdinsight/spark/apache-spark-overview), [Apache Hadoop](https://docs.microsoft.com/en-us/azure/hdinsight/hadoop/apache-hadoop-introduction), [Apache Kafka](https://docs.microsoft.com/en-us/azure/hdinsight/kafka/apache-kafka-introduction), [Apache HBase](https://docs.microsoft.com/en-us/azure/hdinsight/hbase/apache-hbase-overview), [Apache Storm](https://docs.microsoft.com/en-us/azure/hdinsight/storm/apache-storm-overview), and [Machine Learning Services](https://docs.microsoft.com/en-us/azure/hdinsight/r-server/r-server-overview). HDInsight also supports a broad range of scenarios such as extraction, transformation, and loading \(ETL\), data warehousing, machine learning, and IoT.

### Azure Databricks <a id="azure-databricks"></a>

[Azure Databricks](https://azure.microsoft.com/services/databricks/) helps you unlock insights from all your data and build artificial intelligence solutions. You can set up your Apache Spark environment in minutes, and then autoscale and collaborate on shared projects in an interactive workspace. Azure Databricks supports Python, Scala, R, Java, and SQL, as well as data science frameworks and libraries including TensorFlow, PyTorch, and scikit-learn.

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-database-fundamentals/media/icon-service-azure-databricks.png)

![](https://docs.microsoft.com/en-us/learn/azure-fundamentals/azure-database-fundamentals/media/icon-service-data-lake-analytics.png)

### Azure Data Lake Analytics <a id="azure-data-lake-analytics"></a>

[Azure Data Lake Analytics](https://azure.microsoft.com/services/data-lake-analytics/) is an on-demand analytics job service that simplifies big data. Instead of deploying, configuring, and tuning hardware, you write queries to transform your data and extract valuable insights. The analytics service can handle jobs of any scale instantly by setting the dial for how much power you need. You only pay for your job when it's running, making it more cost-effective.

