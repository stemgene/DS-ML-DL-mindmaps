# Data Classification
## Structured
### Structure created before any data is populated
### Defined during creation
### Created using tables
### Relational model
### Table structure
### Column width
### Data types
### Slow reaction to changes
### Often uses a querying language

## Semi-structured
### Unstructured or NoSQL
### Nonrelational, no foreign keys
### Less organized than structured
### Uses lags for organization and hierarchy
### Serialization language
### Data can be shared without system details

## Unstructured
### Binary, audio, image files
### Nonrelational
### Unstructured or NoSQL
### Structure not defined during creation
### data used in raw format
### defined only when read

# NoSQL Database Types
## Key-value store
## Document database
## Column database
## Graph database

# Common Azure Data Store Models
## Azure SQL database
### Features:
#### Managed relational database
#### Structured and unstructured
#### Online transaction processing (OLTP): scale on demand along with requests
#### Strong security and availability
### Reason to use SQL
#### Requirement for on-demand scaling
#### Focus on security and availability
#### Reduced costs associated with on-site infrastructure
#### More flexible than on-site SQL Server
#### Protected by Azure service level agreement (SLA)
### Benefit or Advantages of Azure SQL Database
#### Reliable performance
#### No admin required
#### Dynamic scaling
#### No downtime
#### Intelligent optimization
#### Global scalability
#### Advanced security
### Working with Data in Azure SQL DB
#### Software Development Kits (SDK)
#### .NET, Python, Java, Node.js
#### Transact-SQL (T-SQL)
#### Azure Data Factory
### Azure SQL Database Security
#### Advanced Threat Protection (ATP)
#### Strong encryption
#### SQL Database auditing
#### Multi-factor authentication (MFA)
#### Azure Active Directory (AAD) authentication
#### Compliance certification

## Azure Cosmos DB: nosql db
### Globally distributed
### Multimodal
### API models
### Advantages
#### 99.99% uptime
#### Regional failover
#### Automatic failover
#### low latency
### Consistency Levels
#### Strong
#### Session
#### Consistent prefix
#### Bounded staleness
#### Eventual
### Working with Data in Azure Cosmos DB
#### Azure Data Factory
#### Azure Cosmos DB API
#### JSON
#### Direct editing
### Security
#### Automatic data encryption
#### IP firewall
#### Virtual networks
#### Token-based user authentication
#### Role-based security with Azure Active Directory (AAD)
#### Compliance certification

## Azure Data Storage: for saving nosql data
### Features and advantages
#### Azure base storage type
#### Scalable object store
#### Messaging store
### Configuration
#### Azure Blob
##### Need to store but not query data
##### Need to work with unstructured data and images
##### Require a cost-effective solution
#### Azure Files
#### Azure Queue
#### Azure table
## Azure Data Lake Storage Gen2: for archiving
## Azure Synapse Analytics: big data, data warehousing
## Azure Stream Analytics: for analyzing data as it's retrieved
## Azure Databricks: analyzing data for ML
## Azure Data Factor: for data transformation and movement
## Azure HDInsight: manage large volumns of data

# Deployment API Models
## SQL API
## MongoDB API
## Gremlin API
## Table API
## Cassandra API