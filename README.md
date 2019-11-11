# Azure Technical Academy - Architect day3:  Data architectures and security
Third day is focusing on data architectures in Azure and data security.

**For day3 come with access to your own Azure subscription as Owner**

Azure Stencils
* Go to Visio
* Open shapes
* Search for word "cloud" and click for Online results
* Download Microsoft Azure Cloud Icons
* If you have older Visio you can download older stencils directly and copy to Documents/My Shapes folder [here](https://architects.blob.core.windows.net/visio/CnE_CloudV2.7.vss?st=2019-05-20T05%3A27%3A00Z&se=2020-05-21T07%3A27%3A00Z&sp=rl&sv=2018-03-28&sr=b&sig=IELwMsknjeDR3E2fQcfyDa1lOG3hHIiHvLe4gyXMn0U%3D)
* If you are using different tool, download SVG library and import to tool of your choice [here](https://www.microsoft.com/en-us/download/details.aspx?id=41937)

Example solution
- schema https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/identity/azure-ad
- description https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/identity/azure-ad#architecture
- pricing https://azure.microsoft.com/en-us/pricing/calculator/
- example architectures [https://azure.microsoft.com/en-us/solutions/architecture/](https://azure.microsoft.com/en-us/solutions/architecture/)

Timing: 
- 10min intro 
- 50min design
- 20min presentation and recommended solution

# How to upload results of your work
* Download and install storage explorer [here](https://azure.microsoft.com/en-us/features/storage-explorer/)
* Open storage explorer and connect to storage (key will be active only for duration of our workshop)
    * Click on electricity plug icon on left side and select Use a storage account name and key
    * Use following Account Name: architects
    * Use following Account Key: <- will be provided at training date ->
    * Go to architects, Blob Containers, right-click and create container for your group
    * Upload results of your work to container with prefix scenario1 etc.

# Scenarios

## Scenario 1: Practical implementation of governance with Blueprints, Azure Policies, RBAC and ARM

TBD - implement data security policies (encryption), data access policies (RBAC, enforcing AAD authentication for data plane), secure network access to data and package everything as Azure Blueprint

## Scenario 2: Selecting right storage for different needs and types of data

Company has a lot of different data sources and you need to find best storage option based on data types and needs for additional processing.

Source data:
- Traditional structured dataset with orders and payments with need for strong transaction consistency, thousands of transactions per day. System needs to be ready for future growth in both database size and number of concurrent users. Customer expects huge growth in future.
- Various data files in different formats such as JSON, Excel, CSV, PDF and JPG with different types of information such as maintenance records, audit trails, logs, financial data, scans of invoices, user pictures and avatars. Due to security concerns access to different folders needs to be governed with access control rules.
- JSON files and messages with unpredictable structure with need for indexed queries. Due to need for low latency data must be distributed across 3 different regions to optimize performance for both reads and writes.
- Legal document store with ability to setup WORM (Write Once Read Many - also called immutable storage) for legal hold and lifecycle management to optimize costs of live data vs. archive.

Select ideal Azure solution for each data source. Only use PaaS services to optimize operational costs.

## Scenario 3: Moving data

There are various data sources and locations:
- On-premises FTP server with CSV files
- On-premises SQL Server 2017 with order transactional data in multiple countries
- Telemetry data from IoT sensors collected in IoT Hub
- 3rd party SaaS solution with event data pushed as Kafka messages to endpoint of your choice

Design following solutions:
- Every week move files from FTP server to Azure SQL Database in Azure. To minimize cost and operational overhead use serverless platform (no VMs) and design secure way for communicating from on-premises environment to Azure SQL Database.
- Every night after company stores close orchestrate movement of transactional data from all countries SQL Servers to centralize location in Azure as flat files fo further processing. After all files are gathered from all countries use single job to ingest all data into company data warehouse based on Azure Synapse Analytics.
- Telemetry data needs to be analyzed in real time to identify anomalies and notify application systems. Also all RAW data needs to be stored in Azure Blob Storage for forensic audit purposes while aggregated data in database for reporting.
- Find solution to efficiently and reliably receive Kafka messages and use some processing to convert message format, enrich with static data (numbered list, geo-tagging) and push to Event Hub for further aplication processing (consumer)

## Scenario 4: Designing structured data analysis solution

The company needs to create and maintain data warehouse solution for operational as well as historization purposes. The solution needs to be able to fulfil the following requirements:

- the data is pulled every night from 3 transactional database systems DWH, the DWH solution needs to be more powerful for this load so the process does not last into next day business hours
- for the solution must stay cost effective, so there should be 3 compute level tiers defined on DWH automatically changing according to business hours (8am, 6pm, 10pm for load)
- for operational reporting requirements, every LOB has it's own requirements for data models (which take data from the DWH) these models are defined and automatically refreshed according to LOB business needs
- interactive reports are delivered to the end users via mobile application (tablets, phones) as interactive dashboards (end user is notified when the report has been shared with them or it's data has been updated) 

## Scenario 5: Designing semi-structured and unstructured data analysis solution

TBD - design Azure Data Bricks

## Scenario 6: Designing Machine Learning and Cognitive Services

TBD - design custom ML models, model governance and DevOps, position cognitive services

## Contacts

### Tomas Kubica - Cloud Solutions Architect
- https://www.linkedin.com/in/tkubica
- https://github.com/tkubica12
- https://twitter.com/tkubica

### Jaroslav Jindrich - Cloud Solutions Architect
- https://www.linkedin.com/in/jjindrich
- https://github.com/jjindrich
- https://twitter.com/jjindrich_cz

### Filip Slanicka - Specialist Data & AI
- https://www.linkedin.com/in/slanicka/
- https://twitter.com/slanicka