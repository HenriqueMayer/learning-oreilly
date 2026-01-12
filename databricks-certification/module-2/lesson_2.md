### Delta Tables

- Delta Tables are the core component of Delta Lake, providing ACID transactions, scalable metadata handling, and unifying streaming and batch data processing.
- They are built on top of Parquet files and use a transaction log (stored in the `_delta_log` directory) to track changes and ensure data integrity.
- Key features of Delta Tables include:
  - **ACID Transactions**: Ensure data consistency and reliability during concurrent read/write operations.
  - **Schema Enforcement and Evolution**: Automatically enforce schema on write and allow schema changes over time.
  - **Time Travel**: Query previous versions of data for auditing, debugging, or historical analysis.
  - **Upserts and Deletes**: Support for MERGE, UPDATE, and DELETE operations to manage data effectively.
  - **Optimized Reads**: Use of data skipping and Z-order clustering to improve query performance.

- **Delta Table Structure**:
  - Data files stored in Parquet format.
    - **Parquet files**:
      - Columnar storage format optimized for performance.
      - Efficient compression and encoding schemes.
      - Designed for complex nested data structures.
      - Binary format:
        ```
        PAR1....[binary data compressed]....PAR1
        ```
        - `PAR1` is the "magic number" that identifies Parquet files.
      - **Parquet vs JSON**:
        | Aspect | JSON | Parquet |
        |--------|------|---------|
        | Format | Text (human-readable) | Binary |
        | Storage | Row-based | Columnar |
        | Compression | Low | High |
        | Query Speed | Slow | Very fast |
        | Read 1 column | Reads ALL data | Reads only that column |
    - Metadata stored in the `_delta_log` directory:
    - E.g.,
    ```
    /path/to/delta-table/
      ├── part-00000-xxxx.snappy.parquet
      ├── part-00001-xxxx.snappy.parquet
      ├── _delta_log/
      │   ├── 00000000000000000000.json
      │   ├── 00000000000000000001.json
      │   └── ...
    ```

- **Creating a Delta Table**:
  ```sql
  CREATE TABLE delta_table_name
  USING DELTA
  LOCATION 's3://path/to/delta-table/';
  ```

- **Converting Existing Parquet Table to Delta**:
  ```sql
  CONVERT TO DELTA parquet.`s3://path/to/parquet-table/`;
  ```

- The `DESCRIBE EXTENDED <table_name>` command provides detailed information about the Delta Table, including its schema, location, and properties.