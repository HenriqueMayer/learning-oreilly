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

