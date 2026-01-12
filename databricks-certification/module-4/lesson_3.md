### Structured Streaming

- **Databricks Streaming**: A scalable and fault-tolerant stream processing engine built on Spark Structured Streaming.
- **Stream Sources**: Read data from various sources such as Kafka, Kinesis, Event Hubs, and file systems (e.g., JSON, CSV, Parquet).
- **Stream Sinks**: Write streaming data to various destinations like Delta Tables, Parquet files, Kafka topics, and console output.
- **Micro-batch Processing**: Structured Streaming processes data in small, incremental batches, providing low-latency processing with exactly-once semantics.
- **Stateful Processing**: Maintain state across micro-batches for operations like aggregations, joins, and window functions.

### Streaming Read

- Example of Reading from a Streaming Source (e.g., JSON files):
  ```python
  from pyspark.sql.functions import *

  streaming_df = (spark.readStream
                  .format("json")
                  .load("/path/to/input/data"))
  ```

### Streaming Write

- Example of Writing to a Streaming Sink (e.g., Delta Table):
  ```python
  (streaming_df.writeStream
   .format("delta")
   .outputMode("append")
   .option("checkpointLocation", "/path/to/checkpoint/dir")
   .start("/path/to/delta/table"))
  ```
  - This code snippet sets up a streaming write operation that appends data to a Delta Table, using a specified checkpoint location for fault tolerance.
  - **Checkpointing**: Essential for fault tolerance in streaming applications, allowing recovery from failures by storing progress information.
    - **Output Modes**:
        - `append`: Only new rows are added to the sink.
        - `complete`: The entire result table is written to the sink every time.
        - `update`: Only the rows that have changed since the last trigger are written to the sink.

### Write Output Mode

- **Append Mode**: New data is added to the existing data in the sink. Suitable for scenarios where data is continuously growing.
- **Complete Mode**: The entire result set is written to the sink on each trigger. Useful for aggregations where the full result is needed.
- **Update Mode**: Only the rows that have changed since the last trigger are written to the sink. Ideal for scenarios where only incremental updates are required.

### Trigger of Write

- **Trigger Intervals**: Control how often the streaming query processes new data.
  - Example of Setting Trigger Interval:
    ```python
    (streaming_df.writeStream
     .format("delta")
     .outputMode("append")
     .option("checkpointLocation", "/path/to/checkpoint/dir")
     .trigger(processingTime='10 seconds')
     .start("/path/to/delta/table"))
    ```
    - This code snippet configures the streaming write operation to process new data every 10 seconds.
- **Once Trigger**: Process all available data once and then stop.
- **Continuous Trigger**: Process data as soon as it arrives with minimal latency (experimental feature in Spark).