### Accessing Data Storage

- Data in Databricks can be accessed through various storage options such as:
  - **Databricks File System (DBFS)**: A distributed file system that is mounted to your Databricks workspace.
  - **Cloud Storage**: Integration with cloud storage services like AWS S3, Azure Blob Storage, and Google Cloud Storage.
  - **Mounting External Storage**: You can mount external storage locations to DBFS for easier access.

- **Unity Catalog Volumes**: A feature of Unity Catalog that allows you to create managed storage locations for your data, providing fine-grained access control and governance.

#### Non-Unity Catalog Data

- **Workspace file**:
    - Create and import files directly into the Databricks workspace.
    - Accessible only within the workspace environment.

- **Cloud object storage**:
    - Directly access data stored in cloud object storage services (e.g., S3, Azure Blob).
    - Requires appropriate access permissions.

- **Demo**:
    - If you import a CSV file into the workspace, it will be stored in the workspace file system.
    `spark.read.csv("/FileStore/tables/your_file.csv")`
    - To access data from cloud storage, you would use the appropriate path, such as `SELECT * FROM s3://your-bucket/your_file.csv` or `SELECT * FROM wasbs://your-container@your-account.blob.core.windows.net/your_file.csv`.
    ```
    1. spark.read.FORMAT("<file_format>").LOAD("<path_to_data>")
    2. SELECT * FROM <table_name>.'<file_path>'
    ```

#### Unity Catalog

- **Unity Catalog** provides a unified governance solution for all data assets in Databricks.
- **Accessing Data**:
    - Data can be accessed through tables and views registered in Unity Catalog.
    - Use SQL commands to query data stored in Unity Catalog.
    - Example:
    ```
    SELECT * FROM catalog_name.schema_name.table_name;
    ```
- **Storage in Unity Catalog**:
    - **Location**: Data can be stored in managed or external locations defined in Unity Catalog.
    - **Tables**: Unity Catalog tables can be created as managed tables (data stored in Unity Catalog-managed storage) or external tables (data stored in external locations).
    - **Volume**: Unity Catalog Volumes can be used to create managed storage locations for data with fine-grained access control.

```sql
CREATE TABLE managed_table_student (
    id INT,
    name STRING,
    age INT
);

CREATE TABLE external_table_delta
LOCATION 's3://your-bucket/external_table_data/'

CREATE EXTERNAL TABLE external_volume 
LOCATION 'abfss://'
```

- You can use the `use catalog` command to switch between different catalogs in Unity Catalog.
```sql
USE CATALOG catalog_name;
USE SCHEMA default;
```
- This allows you to manage and access data across different catalogs and schemas easily.

#### Types of Tables in Unity Catalog

- **Managed Tables**: Data is stored in locations managed by Unity Catalog. Databricks handles the storage and lifecycle of the data.
- **External Tables**: Data is stored in external locations (e.g., cloud storage). Unity Catalog manages the metadata, but the data itself is not managed by Databricks.
- **Managed Tables with Unity Catalog Volumes**: Tables that use Unity Catalog Volumes for storage, providing fine-grained access control.
- **Delta Tables**: Tables that use the Delta Lake format, providing ACID transactions and scalable metadata handling.
- **Volume Tables**: Managed storage locations created using Unity Catalog Volumes for fine-grained access control.