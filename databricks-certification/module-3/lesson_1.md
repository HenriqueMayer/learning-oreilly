### Delta lake and Delta Table

- **Delta Lake** is an open-source storage layer that brings ACID transactions to big data workloads. It is built on top of existing data lakes and provides reliability, performance, and scalability for data engineering and data science tasks.
- **Delta Tables** are the core component of Delta Lake, providing ACID transactions, scalable metadata handling, and unifying streaming and batch data processing.
- Delta Tables are built on top of Parquet files and use a transaction log (stored in the `_delta_log` directory) to track changes and ensure data integrity.
- Key features of Delta Lake and Delta Tables include:
  - **ACID Transactions**: Ensure data consistency and reliability during concurrent read/write operations.
  - **Schema Enforcement and Evolution**: Automatically enforce schema on write and allow schema changes over time.
  - **Time Travel**: Query previous versions of data for auditing, debugging, or historical analysis.
  - **Upserts and Deletes**: Support for MERGE, UPDATE, and DELETE operations to manage data effectively.
  - **Optimized Reads**: Use of data skipping and Z-order clustering to improve query performance.

- **Delta Table Structure**:
  - Data files stored in Parquet format.

- Transaction log stored in the `_delta_log` directory.
    - Example of a JSON transaction log file:
      ```json
      {
        "add": {
          "path": "part-00000-xxxx.snappy.parquet",
          "size": 123456,
          "modificationTime": 1625247600000,
          "dataChange": true,
          "stats": "{\"numRecords\":1000,\"minValues\":{\"id\":1,\"value\":10},\"maxValues\":{\"id\":1000,\"value\":1000}}"
        }
      }
      ```
    - Example of a JSON transaction log file for a delete operation:
      ```json
      {
        "remove": {
          "path": "part-00001-xxxx.snappy.parquet",
          "deletionTimestamp": 1625247600000,
          "dataChange": true
        }
      }
      ```