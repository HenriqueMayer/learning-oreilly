### Databricks Cluster

- Databricks clusters are groups of virtual machines that run data processing tasks. They provide the computational power needed to execute workloads in Databricks.
- Databricks compute is a built on top of **Apache Spark**, an open-source distributed computing system.
    - **Apache Spark**:
      - An open-source unified analytics engine for large-scale data processing.
      - Provides high-level APIs in Java, Scala, Python, and R.
      - Supports in-memory computing for faster data processing.
- The primary unit of operation in Spark is cluster, a set of virtual machines (nodes) organized for workload processing.
- **Cluster Components**:
  - **Driver Node**: Manages the cluster and coordinates tasks.
  - **Worker Nodes**: Execute the tasks assigned by the driver.
  - **Single Node**: A cluster with only a driver node, used for lightweight workloads and development.
```
Databricks Spark Cluster

Driver Node
  |
  |-- Worker Node 1
  |     |-- Executor 1
  |     |-- Executor 2
  |
  |-- Worker Node 2
        |-- Executor 1
        |-- Executor 2
```

- **Cluster Types**:
  - **Standard Clusters**: User-managed clusters where users have full control over configuration and management.
  - **High Concurrency Clusters**: Optimized for concurrent workloads, allowing multiple users to share the same cluster.
  - **Single Node Clusters**: A cluster with only a driver node, suitable for lightweight workloads and development.
- **Cluster Configuration Options**:
  - **Instance Types**: Choose from various VM types based on workload requirements (e.g., memory-optimized, compute-optimized).
  - **Autoscaling**: Enable autoscaling to automatically adjust the number of worker nodes based on workload demand.
  - **Spot Instances**: Use spot instances to reduce costs by utilizing unused cloud capacity.
- **Cluster Management**:
  - **Cluster Policies**: Define policies to enforce cluster configuration standards across an organization.
  - **Monitoring and Logging**: Use built-in tools to monitor cluster performance and access logs for troubleshooting.
  - **Cluster Libraries**: Install and manage libraries on clusters to support various data

### Databricks and Azure
- In Azure Plataform, you can access the Storage Account (Containers)
- In Databricks, select the "Compute" option from the left-hand menu to create and manage clusters.
    - You can see the virtual machine in the Azure Portal under "Virtual Machines" section.
    - We can use a **Pool** of clusters to optimize resource usage and reduce costs.
