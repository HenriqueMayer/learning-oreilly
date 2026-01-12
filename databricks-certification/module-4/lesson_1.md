### Pipeline Orchestration

- **Live Versus Streaming Tables**: Live Tables are managed by Delta Live Tables (DLT) framework, while Streaming Tables are traditional streaming data sources managed by Spark Structured Streaming.
- **Declarative Pipelines**: DLT allows users to define data pipelines declaratively using SQL or Python, focusing on the "what" rather than the "how" of data processing.
- **Data Quality and Monitoring**: DLT provides built-in data quality checks, monitoring, and alerting to ensure the reliability of data pipelines.
- **Incremental Processing**: DLT supports incremental processing, allowing pipelines to process only new or changed data, improving efficiency.
- **Live Table Creation**: DLT creates `LIVE TABLE` objects that automatically track lineage and dependencies, simplifying data management.
- **Example of Creating a Live Table**:
  ```sql
  CREATE LIVE TABLE my_live_table AS
  SELECT *
  FROM source_table
  WHERE condition = 'value';
  ```

- **Autoloader**: A feature in DLT that automatically detects and ingests new data files as they arrive in a specified location, simplifying the data ingestion process.
    - Example of Using Autoloader:
    ```python
    from pyspark.sql.functions import *

    df = (spark.readStream
          .format("cloudFiles")
          .option("cloudFiles.format", "json")
          .option("cloudFiles.schemaLocation", "/path/to/schema")
          .load("/path/to/input/data"))
    ```
    - This code snippet sets up a streaming DataFrame that uses Autoloader to read JSON files from the specified input path, automatically handling schema inference and evolution.
    - **Data Ingestion using Autoloader**:
      - Supports various file formats: JSON, CSV, Parquet, Avro, etc.
      - Automatically manages schema changes over time.
      - Scales efficiently with large volumes of incoming data.
