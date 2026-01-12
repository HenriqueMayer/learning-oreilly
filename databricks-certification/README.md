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