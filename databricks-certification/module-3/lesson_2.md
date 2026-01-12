### table Operations

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

- **Altering a Delta Table**:
  - Add a new column:
    ```sql
    ALTER TABLE delta_table_name ADD COLUMNS (new_column STRING);
    ```
  - Change column data type:
    ```sql
    ALTER TABLE delta_table_name ALTER COLUMN existing_column TYPE INT;
    ```

- **Dropping a Delta Table**:
  ```sql
  DROP TABLE delta_table_name;
  ```

- **Vacuuming a Delta Table**:
  - Removes old files no longer referenced by the Delta Table to free up storage.
  ```sql
  VACUUM delta_table_name RETAIN 168 HOURS;
  ```

- **Optimizing a Delta Table**:
  - Improves query performance by compacting small files into larger ones.
  ```sql
  OPTIMIZE delta_table_name;
  ```

- **Viewing Delta Table History**:
  - Use the `DESCRIBE HISTORY` command to view the history of operations performed on the Delta Table.
  ```sql
  DESCRIBE HISTORY delta_table_name;
  ```

- **Restoring a Delta Table to a Previous Version**:
  - Use the `RESTORE` command to revert the Delta Table to a specific version.
  ```sql
  RESTORE delta_table_name TO VERSION AS OF 2;
  ```

- **Merging Data into a Delta Table**:
  - Use the `MERGE` command to perform upserts (updates and inserts) on the Delta Table.
  ```sql
  MERGE INTO target_table AS t
  USING source_table AS s
  ON t.id = s.id
  WHEN MATCHED THEN
    UPDATE SET t.value = s.value
  WHEN NOT MATCHED THEN
    INSERT (id, value) VALUES (s.id, s.value);
  ```

- **Copying a Delta Table**:
  - Use the `CREATE TABLE AS SELECT` (CTAS) command to create a copy of an existing Delta Table.
  ```sql
  CREATE TABLE new_delta_table AS
  SELECT * FROM existing_delta_table;
  ```
  - **COPY INTO**:
    - Copies data from a source (like cloud storage) into a Delta Table.
    ```sql
    COPY INTO delta_table_name
    FROM 's3://path/to/source/data/'
    FILEFORMAT = 'parquet';
    ```

