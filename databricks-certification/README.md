### Databricks Data Engineer Associate Certification Course: Data Engineering and Data Science on a Unified Platform
 Link: https://learning.oreilly.com/course/databricks-data-engineer/0642572061371/

---

## Module 1 Summary: Databricks Lakehouse Platform

### Lesson 1: Introduction to Data Lakehouse and Medallion Architecture
- Covers the evolution from traditional **Data Warehouses** (structured, OLAP) to **Data Lakes** (flexible, schema-on-read) to the unified **Lakehouse** approach
- **Databricks Lakehouse** combines the best of both: ACID transactions, structured/unstructured data support, and scalability
- **Delta Lake** is the open-source storage layer enabling ACID compliance
- **Medallion Architecture** organizes data into Bronze → Silver → Gold layers (raw → cleansed → business-ready)

### Lesson 2: Databricks Platform Architecture
- **Control Plane**: Web app, orchestration, Unity Catalog, queries (managed by Databricks)
- **Data Plane**: Compute resources and cloud storage (in user's cloud account)
- **Serverless Compute** (2024): Databricks-managed resources with simplified scaling vs. **Classic Compute** where users manage clusters

### Lesson 3: Databricks Clusters
- Built on **Apache Spark** for distributed computing
- **Cluster structure**: Driver Node + Worker Nodes with Executors
- **Cluster types**: Standard, High Concurrency, Single Node
- **Key features**: Autoscaling, spot instances, cluster policies, pools for optimization

### Lesson 4: Databricks Notebooks and DevOps
- Interactive notebooks supporting **Python, Scala, SQL, R**
- **Magic commands** (`%sql`, `%md`) for multi-language support
- Real-time **collaboration** and **version control** with Git integration
- **CI/CD support** via Azure DevOps, Jenkins, GitHub Actions
- **Databricks CLI** for automation and scripting

---

## Module 2 Summary: Data Storage and Management

### Lesson 1: Accessing Data Storage
- **DBFS** (Databricks File System): Distributed file system mounted to workspace
- **Cloud Storage**: Integration with S3, Azure Blob, GCS
- **Unity Catalog**: Unified governance for all data assets with fine-grained access control
- **Table Types**: Managed tables (Databricks handles storage) vs External tables (user manages storage)

### Lesson 2: Delta Tables
- Core component of Delta Lake with **ACID transactions** and **time travel**
- Built on **Parquet files** (columnar, binary, compressed) + **transaction log** (`_delta_log`)
- Key features: Schema enforcement/evolution, optimized reads, upserts/deletes
- Parquet vs JSON: Binary columnar format vs text row-based format

### Lesson 3: Data Transformation
- SQL and DataFrames for data manipulation
- **CRUD operations**: CREATE, INSERT, SELECT, UPDATE, DELETE, DROP
- **JOIN types**: Inner, Left, Right, Full Outer, Cross
- Aggregation functions: COUNT, COUNT_IF, GROUP BY, DISTINCT

### Lesson 4: JSON, Arrays, and Functions
- Reading/writing JSON data with Spark DataFrames
- Array functions: `explode`, `array_contains`, `size`
- **User-Defined Functions (UDFs)**: Extend Spark functionality with custom Python/Scala code

---

## Module 3 Summary: Delta Lake Operations

### Lesson 1: Delta Lake and Delta Tables
- Delta Lake: Open-source storage layer with ACID transactions for big data
- Transaction log tracks all changes in `_delta_log` directory (JSON files)
- Supports time travel, schema evolution, and optimized queries

### Lesson 2: Table Operations
- **Create**: `CREATE TABLE ... USING DELTA`
- **Convert**: `CONVERT TO DELTA parquet.'path'`
- **Alter**: `ALTER TABLE ADD COLUMNS`, `ALTER COLUMN TYPE`
- **Maintenance**: `VACUUM` (clean old files), `OPTIMIZE` (compact small files)
- **History**: `DESCRIBE HISTORY`, `RESTORE ... TO VERSION AS OF`
- **Merge**: `MERGE INTO` for upserts
- **Copy**: `COPY INTO` for loading from cloud storage

### Lesson 3: Delta Table Transactions and Optimizations
- ACID operations: INSERT, UPDATE, DELETE, MERGE
- **Optimistic concurrency control** for handling simultaneous transactions
- **Optimizations**: Data skipping, Z-Order clustering, compaction, caching

### Lesson 4: Delta Live Tables (DLT)
- Framework for building reliable, maintainable data pipelines
- **Declarative pipelines**: Focus on "what" not "how" (SQL or Python)
- **Automated data quality** checks and monitoring
- **Incremental processing**: Only process new/changed data
- Creates `LIVE TABLE` with built-in lineage tracking

---

## Module 4 Summary: Pipeline Orchestration and Streaming

### Lesson 1: Pipeline Orchestration
- **Live Tables vs Streaming Tables**: DLT-managed vs Spark Structured Streaming
- **Declarative pipelines**: Define "what" not "how" using SQL or Python
- **Autoloader**: Automatically detects and ingests new files as they arrive
  - Supports JSON, CSV, Parquet, Avro formats
  - Auto-manages schema changes and scales efficiently

### Lesson 2: Job Management
- **Jobs**: Automated workflows to run notebooks, JARs, Python scripts
- **Job Clusters**: Dedicated clusters separate from interactive clusters
- **Scheduling**: Periodic execution (hourly, daily) or trigger-based runs
- **Features**: Retries on failure, email/webhook notifications, job dependencies

### Lesson 3: Structured Streaming
- Scalable, fault-tolerant stream processing built on Spark
- **Sources**: Kafka, Kinesis, Event Hubs, file systems
- **Sinks**: Delta Tables, Parquet, Kafka, console
- **Output Modes**: `append`, `complete`, `update`
- **Checkpointing**: Essential for fault tolerance and recovery
- **Triggers**: Processing time intervals, once trigger, continuous

---

## Module 5 Summary: Governance and Access Management

### Lesson 1: Unity Catalog
- Centralized governance for data and AI assets across all workspaces
- **Hierarchy**: Metastore → Catalog → Schema → Tables/Views
- **Features**: Fine-grained access control (table, column, row level), data lineage, cloud IAM integration
- **Row-Level Security**: Create and attach row access policies

### Lesson 2: Access Management
- **Databricks Identities**: Users and groups via cloud IAM (AWS IAM, Azure AD)
- **Privileges**: SELECT, INSERT, UPDATE, DELETE on data objects
- **Commands**: `GRANT`, `REVOKE`, `SHOW GRANTS`
- **Service Principals**: Non-human identities for applications
- **SQL Warehouses**: Optimized compute for interactive SQL queries with auto-scaling and caching

### Lesson 3: Workspace Management
- Organizing workspaces with folders and notebooks
- User roles and permissions management
- Version control integration (GitHub, Azure DevOps)
- **Isolation by LOB**: Separate workspaces per line of business for security, governance, and cost management
