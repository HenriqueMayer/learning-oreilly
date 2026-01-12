### Introduction to Data Lakehouse and Medallion Architecture

- **Enterprise Data Architecture**
```
(Online Transaction Processing - OLTP)                       (Online Analytical Processing - OLAP)

PC                                                               Analysis
Server      <---> Database <---> ETL ---> Data Warehouse --->    Reporting   ---> User
Mainframe
```
- **Data Warehouse**: Central repository for structured data, optimized for query and analysis.
    - **Tools**: SQL-based querying tools, BI tools
    - **Real World Example**: A retail company uses a data warehouse to analyze sales data across different regions.
    - Examples: Amazon Redshift, Google BigQuery, Snowflake
- **ETL (Extract, Transform, Load)**: Process of moving data from source systems to the data warehouse.
- **OLTP vs OLAP**: OLTP systems handle day-to-day transactions, while OLAP systems are designed for complex queries and analysis.

#### Challenges with Traditional Data Architectures
- **Data Silos**: Different departments maintain separate data stores, leading to inconsistencies.
- **Latency**: Time lag between data generation and availability for analysis.
- **Scalability**: Difficulty in scaling traditional data warehouses to handle large volumes of data

#### Data Lake

- **Definition**: A centralized repository that allows you to store all your structured and unstructured data at any scale.
- **Characteristics**:
    - Stores raw data in its native format
    - Supports various data types (structured, semi-structured, unstructured)
    - Scalable and cost-effective storage solution
    - No schema enforcement at write time (schema-on-read)
- **Tools**: Hadoop, Amazon S3, Azure Data Lake Storage
- **Real World Example**: A media company uses a data lake to store vast amounts of video, audio, and text data for future analysis.
- **A local computer is an example of data lake or data warehouse?**
    - A local computer is more akin to a data lake as it can store various types of data in its native format without strict schema enforcement.
    - A local solution to Data Warehouse would be a relational database management system (RDBMS) like MySQL or PostgreSQL installed on the local machine.

```
OLTP --> Data Lake --> Data Warehouse --> OLAP
```

#### Databricks Lakehouse
```
                +---------------------+
                |   BI and Analytics  |
                +---------------------+
                          ^
                          |
                +---------------------+
                |   Machine Learning  |
                +---------------------+
                          ^
                          |
                +---------------------+
                |  Data Science Work  |
                +---------------------+
                          ^
                          |
                +---------------------+
                |   Delta Lakehouse   |
                +---------------------+
                          ^
                          |
        +---------------------------------------+
        |       Data Engineering & ETL          |
        +---------------------------------------+
                          ^
                          |
                +---------------------+
                |    Data Ingestion   |
                +---------------------+
```
- **Definition**: Combines the best features of data lakes and data warehouses to provide a unified platform for data management and analytics.
- **Key Features**:
    - Supports both structured and unstructured data
    - ACID transactions for data reliability
    - Scalable storage and compute
    - Optimized for machine learning and BI workloads
- **Tools**: Databricks, Delta Lake
    - **Delta Lake**: An open-source storage layer that brings ACID transactions to data lakes, enabling reliable data engineering and data science workflows.
        - **What is ACID?**
            - **Atomicity**: Ensures that all operations within a transaction are completed successfully or none are.
            - **Consistency**: Ensures that a transaction brings the database from one valid state to another.
            - **Isolation**: Ensures that concurrent transactions do not interfere with each other.
            - **Durability**: Ensures that once a transaction is committed, it remains so, even in the event of a system failure.
- **Real World Example**: A financial services company uses Databricks Lakehouse to unify their data engineering, data science, and analytics workflows on a single platform.

#### Medallion Architecture
```
        +---------------------+
        |     Gold Layer     |
        |   (Business Level)  |
        +---------------------+
                  ^
                  |
        +---------------------+
        |     Silver Layer    |
        |   (Cleansed Data)   |
        +---------------------+
                  ^
                  |
        +---------------------+
        |      Bronze Layer   |
        |  (Raw Ingested Data)|
        +---------------------+ 
```
- **Definition**: A data architecture pattern that organizes data into three layers: Bronze, Silver, and Gold.
- **Layers**:
    - **Bronze Layer**: Raw data ingested from various sources, stored in its native format.
    - **Silver Layer**: Cleansed and transformed data, ready for analysis.
    - **Gold Layer**: Business-level aggregates and curated datasets for reporting and analytics.
- **Benefits**:
    - Improved data quality and reliability
    - Clear separation of data processing stages
    - Easier data governance and lineage tracking
- **Real World Example**: An e-commerce company implements Medallion Architecture to streamline their data processing and improve the quality of their analytics reports.

#### Comparison
- **Data Lake**:
    - Stores raw data in its native format
    - Schema-on-read
    - Cost-effective for large volumes of unstructured data
- **Data Warehouse**:
    - Stores structured data optimized for analysis
    - Schema-on-write
    - High performance for complex queries
- **Data Lakehouse**:
    - Combines features of both data lakes and data warehouses
    - Supports ACID transactions
    - Unified platform for data engineering, data science, and analytics
