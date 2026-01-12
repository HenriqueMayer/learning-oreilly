### Introduction to Databicks lakehouse Plataform

- **Databricks Architecture (OLD)**:
```
      Control Plane (Databricks Account)             Data Plane (User Cloud Account)

User ----- Administration                 --------      Compute
            1. Web Application                           1. Hardware running Databricks
            2. Compute Orchestration                     |
            3. Unity Catalog                             |
            4. Queries and Code           --------      Storage
                                                         1. Cloud Storage (S3, ADLS, GCS)
```
- **Databricks Architecture (2024)**:
```
        Control Plane (Databricks Account)              Classic Compute Plane (User Cloud Account)
User -----      Administration                 --------      Compute
                 1. Web Application                           1. Hardware running Databricks
                 2. Compute Orchestration                     |
                 3. Unity Catalog                             |
                 4. Queries and Code           --------      Storage
                    |                                        1. Cloud Storage (S3, ADLS, GCS)
                    |
                    |
        Serverless Compute Plane (Databricks Account)
                 1. Serverless Compute
                 2. Managed by Databricks
```
- **Differences between Classic and Serverless Compute**:
  - Classic Compute:
    - User is responsible for managing clusters.
    - More control over cluster configuration.
    - Suitable for workloads with specific performance requirements.
  - Serverless Compute:
    - Databricks manages the compute resources.
    - Simplified management and scaling.
    - Ideal for variable workloads and reducing operational overhead.

### Demo: Databricks Plataform
1. Sing up for Databricks trial account (https://www.databricks.com/try-databricks).
2. Sign up for Azure databricks service (I launch from Azure portal).
3. Access Azure Databricks workspace.